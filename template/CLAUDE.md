# Job Search Workspace — instructions for Claude Code

This file is read automatically by Claude Code every time it starts in this
folder. It teaches Claude the conventions for your search so you do not have to
re-explain them each session. Edit anything below to match how you want to work.

## What this workspace is

A single folder that holds an entire job search: a master resume, one tailored
resume and cover letter per application, a tracker of every role, interview prep,
and coding practice. Claude Code helps create and maintain all of it.

## Source of truth

- `linkedin/profile.md` is the canonical record of your background, your voice,
  and the way you describe your experience. All tailoring should read from it.
  Keep it current.
- `resume.md` and `resume.html` are the master resume. They must stay in sync:
  when one changes, update the other.

## Master tracker — jobs.md

`jobs.md` is one table, one row per role. Flip the Status column as a role moves
through the funnel.

- Status values: `saved` / `applied` / `screen` / `interview` / `offer` / `rejected` / `withdrawn` / `ghosted`
- Do NOT mark a job `applied` until I confirm I actually submitted it. Use
  `saved` until then.
- The Date column is the date the activity happened, not when the row was added.

## Per-application folders

When a role reaches `applied`, or when I ask, create
`applications/<company>-<role>/` containing:

- `job.md`: the posting, an honest fit analysis, and a "gaps / not claimed"
  list so we never overclaim
- `resume.md` and `resume.html`: the resume tailored to this posting
- `cover-letter.md` (and `.html` if the posting wants one)
- `cheat-sheet.md` and `cheat-sheet.html`: interview prep, added once an
  interview is scheduled

Always add a matching row to `jobs.md` when you add an application.

## Optional: Texas TWC work-search log (US / Texas only)

`jobs.md` can double as a Texas Workforce Commission work-search log. Texas
unemployment requires at least 3 work-search activities per week. When I ask for
a TWC report, produce a plain-text weekly summary grouped by week
(Sunday to Saturday), flag any week with fewer than 3 activities, and output it
as a fenced code block so it pastes cleanly into a form. Delete this section if
it does not apply to you.

Activity values: `applied online` / `interview` / `job fair` / `networking` / `workshop` / `staffing agency`

## Writing style

- Write the way I write. Match my voice from `linkedin/profile.md`.
- Avoid em dashes in body text; they read as AI-generated. Use commas, colons,
  or parentheses instead. (Em dashes are fine in titles and headers.)
- Never invent experience, numbers, tools, or dates. If a posting wants
  something I do not have, record it in `job.md` under gaps and leave it off the
  resume.

## Keep things in sync

- `resume.md` and `resume.html` always match.
- Every application folder has a matching row in `jobs.md`.
