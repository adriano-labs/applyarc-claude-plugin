---
name: interview-prep
description: Prepares the user for a specific interview from their real experience using ApplyArc. Builds a story bank in STAR form mapped to what the role tests, pulls a company brief, predicts likely questions, drafts "tell me about yourself", "why us" and questions to ask, and runs a debrief afterwards with a thank-you note. Use when the user says "I have an interview", "help me prepare for my interview", "what will they ask me", "STAR answer", "research the company", "questions to ask the interviewer" or "debrief my interview". For scored role-play practice use mock-interview; for an offer use offer-negotiation.
---

# Interview prep

Prepare the user for one interview with one employer. The deliverable is a
**prep pack**: what the round tests, stories mapped to it, a short company
brief, likely questions with a story for each, opening answers, questions to
ask and a logistics checklist. Afterwards, run a debrief that feeds the next
round. Uses the ApplyArc MCP server (`applyarc`); everything also works in plain
conversation.

Why this shape: many employers use structured interviews, with the same
competency questions for every candidate and follow-up probes. Real evidence
that survives "what exactly did you do?" wins, not a memorised script.

## Ground rules

1. **Real stories only.** Situations, actions, numbers and outcomes come from
   the user. Unknown result: ask, use an honest range, or mark `needs number`.
2. **One story, many angles.** A good story answers several questions by
   spotlighting a different part. The facts stay identical.
3. **Prep, not live help.** Do not feed answers during a live interview or
   timed assessment unless the user confirms the employer allows AI help.
   Offer a debrief afterwards instead.
4. **Label sources.** Company facts come from `company-research` output or
   pages the user pastes. Anything from your own background knowledge goes under
   "From memory, may be out of date". Never invent links, dates or figures.
5. **Ask before spending.** Each `generate_for_job` call uses one AI generation.
   List the calls you plan and get one yes.
6. British English. No em dashes.

## Workflow

1. **Pin the interview.** Company, role, round (screen, hiring manager,
   panel, technical, final), format (video, phone, on site), length,
   interviewers if known, and the date. If the job is tracked, call
   `list_my_jobs` with `status: "interview"` to reuse its details; otherwise
   offer `save_job`. If the stage is wrong, offer `update_job_status` to
   `interview`.
2. **Read the CV.** Call `get_my_profile`.
3. **Map what they test.** From the posting, list 4 to 6 competencies (for
   example stakeholder management, ownership, data skills). For NHS and UK
   healthcare roles, include the NHS values.
4. **Generate the core pack.** With the user's yes, run
   `generate_for_job` with `interview-prep`, then optionally
   `company-research` and `questions-to-ask`. Summarise rather than paste
   everything.
5. **Build the story bank.** Aim for 5 to 7 stories covering the
   competencies. For each, draft STAR from the user's words:
   Situation (one line), Task, Action (most of the answer, "I" not "we"),
   Result (number or honest proxy) and a one-line reflection. Use
   `prepare_star_answer` for any question the user finds hard, with
   `vertical: "nhs"` for healthcare roles. See `references/story-bank.md`.
6. **Openers.** Draft "tell me about yourself" (present, past, why this role,
   about 90 seconds), "why this company" (tied to the brief) and "why are you
   leaving". Keep them in the user's voice.
7. **Likely questions.** List 8 to 12, each mapped to a story. Mark the two
   most likely probes per story.
8. **Logistics.** Time zone, link or address, who to ask for, what to bring,
   right-to-work documents, and a 10-minute pre-interview checklist.
9. **Hand over the pack** as one tidy message the user can save.

## After the interview

Ask how it went, which questions came up and what felt weak. Then:

- note gaps and strengthen one story for next time;
- with the user's yes, run `generate_for_job` with `thank-you`, passing names
  and one specific moment from the conversation in `notes`;
- update the stage with `update_job_status` when they hear back.

## Hard questions

- **Gaps or redundancy:** one honest sentence, then what they did and why they
  are ready now.
- **Weakness:** a real, non-core weakness plus a concrete step they took.
- **Salary expectations:** suggest deferring politely or giving a researched
  range; hand off to offer-negotiation for the number.
- **Unlawful questions** (age, family plans, religion): give options to
  redirect; do not give legal conclusions.
