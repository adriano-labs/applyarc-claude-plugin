---
name: cv-bullet-writer
description: Turns CV duties into strong, honest impact bullets using ApplyArc's free bullet rewriter. Asks for real numbers or honest ranges, offers versions that add numbers, power up wording, match a job posting or cut length, and shows a before and after strength score. Works without an ApplyArc account. Use when the user says "improve this bullet", "make my CV stronger", "quantify this", "rewrite my experience", "my CV sounds weak" or pastes CV lines.
---

# CV bullet writer

Rewrite CV bullets so each one shows what the user did and what changed
because of it. Uses `rewrite_cv_bullet` from the ApplyArc MCP server
(`applyarc`), which needs no account.

## Ground rules

1. **Never invent numbers or results.** If a bullet lacks a result, ask:
   how many, how much, how often, how fast, compared with what? Accept honest
   ranges ("about 30 a week") or non-numeric proof (adopted by three teams).
   Otherwise mark `needs number`.
2. **One bullet per call.** `rewrite_cv_bullet` takes one bullet of at least
   three words.
3. **Keep the user's facts and voice.** Offer the rewrite; the user chooses.
4. British English. No em dashes.

## Pick the mode

| User wants | `mode` |
| --- | --- |
| Generally stronger wording | `power-up` (default) |
| A number in it | `add-numbers` (ask for the real figure first) |
| To fit a job posting | `match-job`, with `jobDescription` |
| Shorter | `make-concise` |

Pass `role` when known; it sharpens the wording.

## Workflow

1. Collect the bullets. If the user is signed in and wants their stored CV
   used, call `get_my_profile` and pick the weakest lines together.
2. For each bullet, ask one question to surface a result if it has none.
3. Call `rewrite_cv_bullet` with the bullet, mode, role and any real numbers
   the user gave (fold them into `bulletText`).
4. Show before, after and the strength scores returned. If the rewrite added a
   claim the user did not give, remove it before showing.
5. Offer a second mode if useful (for example `make-concise` after
   `add-numbers`).

## A strong bullet

Action verb, what you did, scale, result. For example:
"Rebuilt the weekly rota in Excel, cutting agency shifts by about 20% over six
months." Avoid "responsible for", "helped with" and lists of duties.

## Limits

The free rewriter has a daily limit per user. If a limit message comes back,
show it as written. For whole-CV tailoring to a job, hand off to
job-application, which uses the signed-in `resume-optimizer` tool.
