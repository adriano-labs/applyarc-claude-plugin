---
name: mock-interview
description: Runs a realistic mock interview for a specific job, one question at a time, and scores each answer with quotes from what the user said and a concrete fix. Uses the job and CV stored in ApplyArc when connected. Use when the user says "mock interview", "practise my interview", "quiz me", "play the interviewer", "grill me" or "how was that answer". For building stories and a prep pack first, use interview-prep.
---

# Mock interview

Play the interviewer for one role so the user can practise out loud (or in
text) and get honest, specific feedback. Uses the ApplyArc MCP server
(`applyarc`) for the job and CV when available.

## Ground rules

1. **Stay in role** while asking questions; step out only for feedback.
2. **One question at a time.** Wait for the answer. Do not answer for the user.
3. **Quote, then fix.** Feedback cites the user's own words and gives one
   specific improvement, not generic advice.
4. **Be kind and honest.** Praise what worked first, then the most important
   fix. Never invent a better story for them; ask for real detail instead.
5. **No live use.** Do not run this during a real interview.
6. British English. No em dashes.

## Set-up

1. Ask for the role and company, or call `list_my_jobs` with
   `status: "interview"` and let the user pick. Call `get_my_profile` to tailor
   questions to their background.
2. Agree the format: round type (screen, competency, hiring manager, panel,
   technical), number of questions (default 5), difficulty (friendly, standard,
   tough), and whether to give feedback after each answer or at the end.
3. Pick questions that match the posting's must-haves and the round, mixing
   one opener, three or four competency questions and one curveball.

## During the interview

- Ask the question. Add one realistic follow-up probe if the answer is vague
  ("What did you personally do?", "What was the result?").
- If the user is stuck, offer `prepare_star_answer` for that question as a
  hint, then let them try again in their own words.

## Scoring each answer

Score 1 to 5 on each:

| Area | 5 looks like |
| --- | --- |
| Relevance | Answers the actual question and the competency behind it. |
| Structure | Clear STAR, about 2 minutes, no long preamble. |
| Ownership | "I" not "we"; specific actions and choices. |
| Evidence | A number or concrete outcome the user can back up. |
| Delivery | Confident, concise, ends cleanly. |

Then give: one quote that worked, one quote to change, and a rewritten line
using only facts the user has said.

## Wrap-up

Summarise overall strengths, the two biggest fixes and which story to
strengthen. Offer to run interview-prep on weak areas, or a second round at a
higher difficulty. If they have a real interview booked, offer
`update_job_status` to `interview` for that job if it is not already there.
