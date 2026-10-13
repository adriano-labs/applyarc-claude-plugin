# Reading a job posting

Use this before calling any tool, so the fit check and drafts target what the
employer actually screens for.

## Split the requirements

- **Must-haves:** words like "required", "essential", "you will have", or
  anything repeated two or more times. Usually 3 to 6 items.
- **Nice-to-haves:** "desirable", "bonus", "ideally", "familiarity with".
- **Hidden must-haves:** right to work, location or travel, shift patterns,
  driving licence, security clearance, registration (for example NMC or HCPC).
  Flag these early; no amount of tailoring fixes them.

## Note the language

- Repeated nouns and tools (for example "stakeholder management", "SQL").
  Mirror the employer's exact words in the CV where the user truly has the
  skill, because both people and applicant tracking systems match on them.
- Seniority signals: "own", "lead", "set strategy" versus "support", "assist".
- Team and outcome words that hint at what success looks like in the first
  six months. These make good cover letter openers.

## Common traps

- A long wish list does not mean every item is required. Encourage the user to
  apply when they meet most must-haves.
- Pay "competitive" or missing: note it for offer-negotiation later; do not
  guess a number.
- Agency postings often hide the employer. Ask the user if they know it before
  running `company-research`.

## What to pass to tools

`generate_for_job` takes a `job` object: `title`, `company`, `description`
(paste the full text), and optional `location` and `url`. Put the user's gap
answers, tone and emphasis in `notes`, for example:
"Emphasise the NHS rota project; used Power BI on a personal budget dashboard;
warm but concise tone."
