---
name: offer-negotiation
description: Helps the user understand and negotiate a job offer with ApplyArc. Breaks down the full package, sets a walk-away point and one clear counter, drafts the negotiation email and call script, and role-plays the call. Use when the user says "I got an offer", "should I accept", "negotiate my salary", "counter offer", "they asked my salary expectations" or "compare two offers". Uses the job in the user's ApplyArc tracker when connected.
---

# Offer negotiation

Help the user get a fair offer without damaging the relationship. Uses the
ApplyArc MCP server (`applyarc`) for the tracked job and the
`salary-negotiation` tool.

Why this shape: most employers expect a respectful counter, and a single,
well-reasoned ask anchored in evidence works better than several small ones.

## Ground rules

1. **No invented numbers.** Salary data comes from the user, the posting, or
   sources they paste. Anything from your background knowledge is labelled
   "From memory, may be out of date" and never presented as market fact.
2. **The user decides.** Lay out options and trade-offs; do not pressure them
   to accept or decline.
3. **Honesty.** Do not invent competing offers or fake deadlines.
4. **No legal or tax conclusions.** Point to official sources (for example
   GOV.UK) and suggest checking with an adviser for contracts.
5. **Ask before spending.** `generate_for_job` uses one AI generation.
6. British English. No em dashes.

## Workflow

1. **Find the job.** Call `list_my_jobs` with `status: "offer"`, or ask for
   the company and role. If the job is not at `offer`, offer
   `update_job_status`.
2. **Capture the full offer.** Base, bonus, equity, pension contribution,
   holiday, notice period, start date, hybrid or remote terms, location,
   probation, benefits, and any deadline. Ask for what is missing.
3. **Know the user's numbers.** Current package, target, and walk-away point.
   Ask what matters beyond money (flexibility, title, learning, start date).
4. **Generate the plan.** With the user's yes, call `generate_for_job` with
   `toolId: "salary-negotiation"`, putting the offer details, target and
   priorities in `notes`.
5. **Pick one counter.** Base it on evidence: the posting's range, the role's
   scope, the user's specific strengths from `get_my_profile`. Prefer one main
   ask plus one fallback (for example sign-on bonus, extra holiday, earlier
   review).
6. **Draft.** A short, warm email: thanks, enthusiasm, the ask with one or two
   reasons, openness to talk. And a 60-second call script with responses to
   "that's our best offer" and "what's your number?".
7. **Rehearse.** Offer to play the hiring manager. After the role-play, quote
   what worked and one line to tighten.
8. **Close.** When the user accepts, confirm the final terms in writing and
   offer to tidy other applications in the tracker (pipeline-coach).

## Comparing offers

Put each offer in a table: base, bonus, pension, holiday, commute or remote,
growth, team, and the user's top two priorities. Highlight the trade-off, then
let the user choose.

## Salary expectations early in the process

Suggest asking for the budgeted range first. If pressed, give a range whose
bottom is a figure the user would be happy with, tied to the role's scope.
