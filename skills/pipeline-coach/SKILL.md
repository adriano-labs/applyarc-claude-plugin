---
name: pipeline-coach
description: Reviews and runs the user's job search pipeline in their ApplyArc tracker. Summarises every stage, spots stale applications, picks the next best actions, moves jobs between stages and drafts follow-up, thank-you and outreach messages. Use when the user asks "what have I applied to", "what should I do next", "review my job search", "weekly job search review", "chase this application", "I got an interview", "I was rejected" or "save this job". For tailoring a new application use job-application; for an offer use offer-negotiation.
---

# Pipeline coach

Keep the user's job search moving with their ApplyArc tracker, via the ApplyArc
MCP server (`applyarc`). The tracker is the source of truth; it is also on
applyarc.com, so anything you change here shows up there.

Why this shape: job searches stall quietly. A short weekly review with one
clear action per stale item keeps momentum and stops good leads going cold.

## Ground rules

1. **Confirm before writing.** List the stage changes and new saves you intend
   and get one yes for the batch. Never move a job on a guess.
2. **Use returned data exactly.** Dates, stages and ids come from
   `list_my_jobs`. Do not invent dates or contacts.
3. **Ask before spending.** Each `generate_for_job` call uses one AI
   generation. Say how many you plan.
4. **Show tool messages as written**, including limit or upgrade messages;
   offer `check_usage` if limits come up.
5. British English. No em dashes.

## Weekly review

1. Call `list_my_jobs` (raise `limit` up to 100 if they track many jobs).
2. Group by stage: wishlist, applied, interview, offer, rejected. Show counts.
3. Flag:
   - **Applied and silent** for about 10 working days or more: suggest a
     follow-up.
   - **Wishlist** items saved more than a week ago: apply, or drop.
   - **Interview** items: check prep is done and a thank-you was sent.
   - **Offer** items: hand off to offer-negotiation.
4. Give the **three actions for this week**, most valuable first.
5. If the pipeline is thin (for example fewer than five active applications),
   say so and suggest saving new roles with `save_job`.

## Actions

- **Log progress:** `update_job_status` with the `jobId`.
- **Save a new role:** `save_job` with title, company, description, and pay or
  url when given.
- **Chase a silent application:** `generate_for_job` with `follow-up`.
- **After an interview:** `generate_for_job` with `thank-you`; put names and
  one specific moment in `notes`.
- **Warm intro or recruiter message:** `generate_for_job` with
  `outreach-message`.
- **Rejection:** move to `rejected`, offer a short note asking for feedback
  (via `follow-up` with that aim in `notes`), and suggest one lesson for the
  next application. Keep the tone encouraging.

`generate_for_job` needs the `job` object (title, company, description,
optional location and url). Reuse the fields returned by `list_my_jobs`; ask
the user to paste the description if it is missing.

## Allowance

If the user asks about limits, call `check_usage` and report what it returns,
including the reset date.
