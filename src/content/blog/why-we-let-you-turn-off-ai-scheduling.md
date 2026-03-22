---
title: "Why We Let You Turn Off the Smartest Part of Our Product"
description: "Not every meeting needs AI. Internal syncs, support calendars, office hours — sometimes you just want to show your availability. Now you can choose, per event type."
pubDate: 2026-03-22
tags: ["product", "ai-scheduling", "feature", "customization"]
heroImage: "/images/ai-scheduling-toggle.png"
---

We built Buxo around one idea: your scheduling agent should know your preferences and pick the best times for you. It scores every slot. It reads your instructions. It even asks your invitee what the meeting is about before showing them a single time.

And then our customers told us to let them turn it off.

## The conversations that changed our mind

It started with a support team lead. She had a "Book a Support Session" event type. Her invitees were existing customers with a quick question. They did not need AI curating three perfect slots. They needed to see every available window and pick the one that worked for their lunch break.

Then a founder told us the same thing about his internal 1:1s. His direct reports did not need an intent capture screen asking what the meeting was about. They knew what it was about. It was their weekly sync. They just needed a time.

The pattern was clear. AI scheduling is powerful when context matters: sales calls, investor meetings, hiring screens. But for event types where the invitee already has full context, or where the host just wants maximum availability shown, the intelligence gets in the way.

## What we shipped

A single checkbox in your event type settings: **Enable AI scheduling**.

It is on by default. When it is on, everything works the way it always has. Your agent instructions shape which slots surface. Intent capture asks your invitee why they want to meet. The "Suggested" badge highlights the best options. Your invitees see a curated, opinionated set of times.

When you turn it off, the experience becomes straightforward:

- **No intent capture.** The invitee goes straight to the calendar.
- **No AI scoring.** Every available slot shows up in chronological order.
- **No "Suggested" badges.** All times are equal.
- **No LLM call.** Slots load faster because there is nothing to score.

Your availability rules, calendar conflicts, lead time, daily caps — all of that still applies. Hard constraints are never bypassed. The only thing that changes is whether an AI layer sits on top deciding which of those valid slots to highlight.

## When to turn it off

Here are the event types where our customers are already using this:

**Internal meetings.** Your team does not need an AI picking the best time for a standup. They need to see what is open and grab a slot. Intent capture for a weekly 1:1 is just friction.

**Support calendars.** When a customer needs help, speed matters more than slot curation. Show them everything. Let them pick the earliest time that works.

**Office hours.** Whether it is a professor holding student hours or a founder doing open advisor sessions, the format is simple: here is when I am free, pick a time.

**Simple event types with no instructions.** If you have not written any agent instructions for an event type, the AI is scoring slots with no guidance. Turning it off gives the same result, faster.

## When to keep it on

The AI earns its keep when context shapes the decision:

**Sales discovery calls.** The invitee's intent ("evaluating vendors for Q3") changes which slots make sense. Morning energy for a high-stakes demo. Afternoon for a casual intro.

**Investor meetings.** Your instruction "prefer mornings, no back-to-back" means the AI protects your best hours for your highest-stakes conversations.

**Hiring screens.** Different roles, different interviewers, different slot strategies. The AI handles the nuance so you do not have to rebuild your availability for every req.

**Any event type with soft preferences.** If you have written instructions like "cluster meetings on Tuesday and Thursday" or "keep Fridays light," the AI is the thing enforcing those. Without it, every open slot is fair game.

## One product, two modes

The toggle is per event type, not per account. This is deliberate.

The same founder who wants AI-curated slots for investor meetings wants a dead-simple booking page for team syncs. The same support lead who needs maximum availability for customer sessions might want intelligent scheduling for internal escalation calls.

Your scheduling tool should adapt to the meeting, not force every meeting through the same flow.

## How it works under the hood

For the technically curious: when AI scheduling is off, the slot engine skips the LLM refinement step entirely. No API call to score slots. No prompt construction. No token spend.

The pipeline still runs every other step — candidate generation, host availability filtering, calendar conflict detection, capacity limits, lead time enforcement. The only difference is step 4: instead of asking an AI to score and rank, we sort chronologically and return everything up to your max slots per day.

This means slots load noticeably faster on event types with AI disabled. No waiting for a model to think. Just your availability, served immediately.

---

## The principle

We believe AI should make your scheduling better, not make it mandatory. The smartest thing a product can do is know when to get out of the way.

Some meetings need intelligence. Some meetings need simplicity. Now Buxo handles both.

[Try it in your event type settings at buxo.ai](https://buxo.ai)

---

*Related: [Buxo 1.0.1: Your Invitees Can Now Reschedule Themselves](/blog/release-1-0-1)*
