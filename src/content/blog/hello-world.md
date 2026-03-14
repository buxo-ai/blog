---
title: "Introducing Buxo: Your Calendar, Trained by You"
description: "We built a scheduling agent you train in plain English. No AI at runtime. 3 slots, not 30. Here is why we are replacing Calendly for founders."
pubDate: 2026-03-14
tags: ["launch", "announcement", "scheduling"]
heroImage: "/images/introducing-buxo.png"
---

During my fundraise, I had 3 Calendly links.

One for West Coast investors. One for East Coast. One for Europe.

Every time someone booked, I manually opened the next slot so the link didn't look dead. I was spending 30 minutes a week managing the tool that was supposed to *save* me time.

That's when I realized: **your scheduling tool knows *when* you're free. It has no idea *how* you think.**

"Keep mornings free." "Batch investor calls on Tuesdays." "No meetings on board days." "VIPs get priority slots."

These aren't settings. They're opinions. No dropdown menu can capture them.

So we built Buxo.

---

## What is Buxo?

Buxo is a scheduling agent you train in plain English.

Instead of toggling 15 settings, you type what you want:

> "Keep mornings free for deep work. Batch investor calls on Tuesdays and Thursdays. Show 3 slots, not 15. Ask what the meeting is about before showing any times."

Buxo compiles your instructions into deterministic booking rules. At runtime, there is **zero AI**: same input, same slots, every time. Predictable. Trustworthy.

Your invitees see a normal booking page. They pick a time. Done. They have no idea an agent is running behind it.

---

## Why 3 slots, not 30?

Here's what we found surprising: when you show someone 15 open time slots, you're signaling *"I have nothing going on."*

Buxo shows 3 slots. The same 3 for everyone, whether they're in San Francisco, New York, or London, displayed in their local timezone.

When one gets booked, the next highest-scored slot appears automatically. Like a waitlist, not a buffet.

Fewer options means faster decisions and fewer no-shows. Scarcity by design.

---

## Intent before access

Before anyone sees a time slot, they answer one question: **"What's this meeting about?"**

You get context before giving away your calendar. The person booking sees it as professional gatekeeping, not friction. You get to know the *why* before you commit the *when*.

---

## Skills: scheduling wisdom from real founders

Don't want to set it up from scratch? Browse Skills, pre-built scheduling configurations from real founders:

- **Fundraise Mode**: batch investor calls, 48h lead time, intent capture, max 3 visible slots
- **Deep Work Defender**: mornings blocked, afternoons stacked, buffer between calls
- **Hiring Sprint**: dedicated interview windows, team calendar coordination

One click to install. One click to customize for your workflow.

---

## How it works under the hood

For those who care about the architecture:

1. **You type** natural language scheduling preferences
2. **An LLM compiles** them into typed rule objects at config time (time preferences, day routing, calendar awareness, proximity stacking, invitee conditions)
3. **At runtime**, slot generation uses seeded deterministic hashing. No LLM, no latency, no hallucination
4. **Waterfall release**: show N slots. When one books, the next highest-scored slot appears
5. **Timezone-agnostic**: everyone sees the same absolute times, displayed in their local timezone

Same link. Same device. Same day. Same slots. Deterministic and reproducible.

---

## Why we built this

The scheduling market isn't broken in an obvious way. Calendly works. SavvyCal works. Cal.com works.

But they all share the same assumption: show all your availability and let people pick.

We think that's wrong for people with opinions about their time. Founders, executives, anyone whose calendar isn't just "whenever I'm free."

Your calendar should reflect how you think. Not just when you're available.

---

## Try it today

Buxo is live. Free to start. You can switch from Calendly in 2 minutes, and your invitees won't notice a difference.

**One link. Trained by you. No AI touching your invitees.**

[Get started at buxo.ai](https://buxo.ai)

---

*We'll be sharing engineering deep dives, product updates, and scheduling insights on this blog. If you want to follow along, subscribe to the [RSS feed](/rss.xml).*
