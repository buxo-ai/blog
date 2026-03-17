---
title: "Release 1.0.1 — Reschedule & Cancel, Done Right"
description: "Invitees can now reschedule and cancel their own bookings. This release also hardens slot validation, fixes timezone display, and plugs a handful of security and reliability gaps."
pubDate: 2026-03-17
tags: ["release", "product", "reschedule", "cancel"]
---

We shipped the reschedule and cancel feature in 1.0.0. This release is about making it *correct*.

After a thorough internal review of the code, we found six gaps between what was planned and what the implementation actually enforced. We fixed all of them, added end-to-end tests, and caught two more bugs in QA. Here's what changed.

---

## What's new

### Invitees can reschedule and cancel their own bookings

Every booking confirmation email now includes a **Manage Booking** link. Click it and you get a simple page where you can:

- Reschedule to any available slot — the same slot picker the invitee used to book in the first place, pre-loaded with their original timezone
- Cancel with an optional reason

No login required. The link is token-gated — it's tied to that specific booking and only works for the person who was invited.

---

## What we fixed

### Reschedule now respects your scheduling rules

Previously, an invitee could reschedule to literally any future time — including midnight on a Sunday, a slot six months out, or times when the host's day was already at capacity.

We fixed this. The reschedule endpoint now enforces the same rules as the original booking:

- **Lead time** — can't book within your configured minimum notice window
- **Scheduling window** — can't book further out than your max booking horizon
- **Max bookings per day** — can't push a day past your daily cap
- **Schedule hours** — can't reschedule to a time outside your configured working hours (e.g. you work Mon–Fri 9–6; an invitee can't reschedule to Saturday at 2am)

### Double-cancel protection

Cancelling the same booking twice used to silently succeed and send duplicate cancellation emails to both the host and invitee. Now the second cancel returns an error immediately, before any emails go out.

### Timezone defaults to the invitee's original timezone

The manage and reschedule pages previously used the browser's local timezone to display the booking time. If an invitee opened their link while traveling or on a different device, the displayed time would be wrong.

Both pages now default to the timezone the invitee used when they originally booked. On the reschedule page, they can still switch timezones if they want — but the default is always the one that matches their original booking.

### Calendar sync failures are now visible

When a reschedule succeeded but the calendar event failed to update (e.g. a brief Google Calendar API error), the booking was silently marked as rescheduled with a stale calendar event. The host would see the new time in Buxo but the old time in their calendar — and not know.

We now surface this explicitly: if the calendar sync fails, the success screen shows a notice saying the calendar event couldn't be updated and the host has been notified.

### Cancel reason no longer logged in server access logs

The cancellation reason text was sent as a URL query parameter (`?cancelReason=...`). Server access logs capture full request URLs, which meant user-entered free text was being written to logs.

The reason is now sent in the request body instead.

---

## Bugs caught in QA

### Hydration error on manage and reschedule pages

Both pages had a `<head>` tag nested inside the React component. In Next.js App Router, this is invalid — `<head>` can't be a child of `<body>` in a client component — and it was producing a React hydration warning on every single page load. Removed.

### Slot engine returning 500 for all slot requests

The `accounts` table in the database was missing a `metadata` column that the slot engine's queries expected. This caused every request to the slots API to return a 500 error, which in turn made the reschedule page show "No available times" for every date. Fixed by adding the missing column.

---

## Under the hood

- `isWithinHostHours()` in the slot engine is now exported — it was private before, which meant the reschedule endpoint couldn't reuse it and had to duplicate the logic (or skip it, which is what happened)
- Two missing DB columns added: `accounts.metadata` and four columns on `bookings` (`manage_token_hash`, `reschedule_count`, `original_start_time`, `original_end_time`)

---

*If you're self-hosting: run `npm run db:push` in the backend directory before deploying this release.*
