# ApplyArc for Claude

Your job search workspace inside Claude. This plugin connects Claude to your
ApplyArc account and adds six job search skills and six slash commands: tailor
an application to a posting, write stronger CV bullets, prepare for and
practise interviews, run a weekly review of your pipeline, and negotiate an
offer. It works with the jobs and CV you already keep in ApplyArc, so you never
paste the same details twice.

Three tools work without an account. Account tools ask you to sign in with your
ApplyArc login the first time you use them.

## Install

In Claude Code:

```text
/plugin marketplace add adriano-labs/applyarc-claude-plugin
/plugin install applyarc@applyarc-plugin-marketplace
```

In Claude (web, desktop and mobile), add ApplyArc from the Directory.

## Skills

| Skill | What it does |
| --- | --- |
| `job-application` | Reads a job posting, scores your fit, tailors your CV and writes a cover letter, then saves the job to your tracker. |
| `cv-bullet-writer` | Turns duties into honest impact bullets, asking for real numbers instead of inventing them. No account needed. |
| `interview-prep` | Builds a prep pack for a tracked job: likely questions, STAR stories from your CV, questions to ask, and a debrief afterwards. |
| `mock-interview` | Plays the interviewer one question at a time and scores each answer with a concrete fix. |
| `pipeline-coach` | Weekly review of your tracker: stale applications, next actions, follow-ups and thank-you notes. |
| `offer-negotiation` | Breaks down an offer, plans one clear counter, drafts the email and call script, and role-plays the call. |

## Commands

| Command | Use it to |
| --- | --- |
| `/applyarc:tailor` | Tailor an application to a pasted job posting. |
| `/applyarc:bullet` | Strengthen one CV bullet. |
| `/applyarc:interview` | Build an interview prep pack. |
| `/applyarc:mock` | Run a scored mock interview. |
| `/applyarc:pipeline` | Review your job pipeline. |
| `/applyarc:negotiate` | Plan an offer negotiation. |

## Tools from the ApplyArc MCP server

No account: `rewrite_cv_bullet`, `preview_cover_letter`, `prepare_star_answer`.

With your ApplyArc account: `get_my_profile`, `check_usage`, `list_my_jobs`,
`save_job`, `update_job_status`, `generate_for_job`.

## Data and network use

- The plugin connects to the ApplyArc MCP server at
  `https://claude-mcp.applyarc.com/mcp`, which calls applyarc.com APIs over
  HTTPS. It does not contact any other service.
- Sign-in uses OAuth 2.0 with PKCE and your ApplyArc login. It happens only
  when you first use an account tool. Claude never sees your password.
- With your permission, account tools read your tracked jobs, stored CV profile
  and AI allowance, and can save jobs or change their status in your ApplyArc
  account.
- AI generation uses your ApplyArc allowance (a free tier is included).
- The connector stores nothing itself. Your data stays in your ApplyArc
  account, under the [ApplyArc privacy policy](https://applyarc.com/privacy).
- You can disconnect at any time from Claude settings.

## Support

Help and contact: [applyarc.com/support](https://applyarc.com/support).
Terms: [applyarc.com/terms](https://applyarc.com/terms).

## Licence

MIT. See [LICENSE](LICENSE).
