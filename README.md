# How I Used Claude Code to Manage My Whole Job Search

This is a step-by-step walkthrough of how I ran an entire job search, managing
applications, interviews, and offers, out of a single folder on my computer that
I worked through with Claude Code.

I wrote it for friends and family who are not programmers. If you can install one
app and type sentences into it, you can do everything here. There is a
ready-to-copy starter kit in the [`template/`](template/) folder: copy it and you
have the skeleton of your own search before you type a single word.

## Contents

- [Intro: what Claude Code is, and why it fit this so well](#intro-what-claude-code-is-and-why-it-fit-this-so-well)
- [Step 1: Build the master resume and LinkedIn profile by interview](#step-1-build-the-master-resume-and-linkedin-profile-by-interview)
- [Step 2: One Claude Code session per job you apply to](#step-2-one-claude-code-session-per-job-you-apply-to)
- [Step 3: Have Claude build a cheat sheet for every screen and interview](#step-3-have-claude-build-a-cheat-sheet-for-every-screen-and-interview)
- [Step 4: Have Claude create coding drills to practice on (for technical roles)](#step-4-have-claude-create-coding-drills-to-practice-on-for-technical-roles)
- [Step 5: Use Claude to manage timing, and to advise on competing offers](#step-5-use-claude-to-manage-timing-and-to-advise-on-competing-offers)
- [A few honest caveats](#a-few-honest-caveats)
- [Start your own](#start-your-own)

---

## Intro: what Claude Code is, and why it fit this so well

**What it is.** Most people meet AI through a chat window: you paste text in, you
copy answers back out, and the moment you close the tab it forgets everything.
Claude Code is different. It is a version of Claude that runs inside a folder on
your laptop and can read and write the files in that folder. When you say "make a
resume tailored to this job," an actual `resume.html` file appears in your folder,
ready to open and print. Next week you can say "what was my salary floor again?"
and it reads its own notes back to you.

**Why a job search is a perfect fit.** A job search is not one task. It is a
hundred small tasks spread over weeks, and the genuinely hard part is remembering
all of it: which company wanted what, how you described that one project, who you
already talked to, which offer expires first. A folder full of files, plus an
assistant that can read and write those files, turns "remember everything" into
"it is all written down, and I can just ask." You are never starting from a blank
page, because the folder already knows your background, your voice, and your
history.

Two quiet features do a lot of the work:

- **An instructions file** named `CLAUDE.md` that Claude reads automatically every
  time it starts. It holds your standing rules ("write the way I write," "do not
  mark a job applied until I confirm I submitted it") so you never repeat yourself.
  The starter kit includes one you can edit.
- **Memory**, a small set of notes Claude keeps about you across sessions, so on a
  brand new day it still remembers who you are and what you are looking for.

**How to set it up.** Three steps, and only the first is required.

1. **Install Claude Code.** It runs on Mac, Windows, and Linux. Search for
   "install Claude Code," follow the official instructions, and sign in. On
   Windows the smoothest path is through WSL (a free Microsoft add-on the
   installer walks you through). This is the only genuinely technical step, and it
   is one time.
2. **Make a folder for your search** and copy the [`template/`](template/) folder
   into it. `Documents/job` is a fine home. That folder is now your whole search.
3. **(Optional but smart) Back it up privately.** Ask Claude Code itself to "set
   up git and push this to a new private GitHub repo" and it walks you through it.
   Keep it **private**: this folder will hold real personal details.

Then open Claude Code in that folder and start talking. Everything below is what I
actually said, in order.

---

## Step 1: Build the master resume and LinkedIn profile by interview

The best decision I made early was to **not** start from my old resume. Old
resumes are full of stale phrasing that quietly shapes everything you write next.
Instead I had Claude interview me, one role at a time, and draft a clean master
resume and LinkedIn profile from the conversation. The result sounded like me
describing my work, not like a document I was copying.

The opening prompt was about this simple:

```
Read CLAUDE.md, then interview me to build my master resume and my LinkedIn
profile from scratch. Do not use any old resume. Ask me about my background one
role at a time: what I worked on, what I owned, the projects I am proud of, and
my skills. Then draft both in my own words.
```

Answer its questions in plain language and let it write. You end up with a
`resume.md` (plain text, easy to edit), a `resume.html` (styled, prints to a clean
one-page PDF), and a `linkedin/profile.md` that becomes the source of truth every
tailored resume reads from later. I paste the LinkedIn version straight into the
LinkedIn website by hand.

---

## Step 2: One Claude Code session per job you apply to

This is the core of the whole system. For **every** job I applied to, I started a
**new** Claude Code session and opened it with this exact prompt:

```
I want to apply to this job. Tailor a resume and cover letter (both html), and
I'll let you know if any other questions need answering during the application:
<paste in job posting link> <paste in job description text>
```

(Replace the two `<...>` pieces with the real link and the pasted job description.)
Claude reads your master resume and LinkedIn profile, then writes a resume and
cover letter tailored to that specific posting, plus an honest fit analysis and a
"gaps / not claimed" list so you never overclaim. As the application form asks for
things ("Why do you want to work here?", "Describe a time you..."), paste those
questions back into the same session and let it draft answers in your voice.

A few small moves made the session-per-job habit pay off:

- **Turn the HTML into a PDF.** Job sites want a PDF. On a Mac I opened the
  `resume.html` in Safari and chose **File > Export as PDF**, which produced a
  perfect single page every time. On Windows that was not as straightforward, so
  the easy path there is to **ask Claude Code itself to make the PDF for you**
  ("convert resume.html to a single-page PDF"), which works the same on any
  computer. The full Mac and Windows playbook is in
  [`pdf-export.md`](pdf-export.md).

- **Rename the session so you can find it later.** Type `/rename` and Claude gives
  the session a clear name (for example, the company and role). Next time you want
  to come back to that exact job, type `/resume`, pick it from the list, and all
  of that job's context is right where you left it.

- **Mark it applied once you actually submit.** After I finished the application,
  I told the same session:

  ```
  Mark as applied
  ```

  Nothing gets marked applied until you really hit submit. Everything starts as
  "saved." This keeps your tracker honest.

- **Feed every email, call, and interview back into that job's session.** When a
  recruiter emailed to schedule a phone screen or interview, I pasted the email
  straight into that job's session. I also told the session every time I actually
  had a screen or an interview. Two things come from this:

  1. **Contacts and details get saved** in that job's folder, so before any call I
     can ask "who am I talking to and what do they care about?" and get it back.
  2. **It doubles as your unemployment work-search log.** If you collect
     unemployment, most US states make you log a minimum number of job-search
     activities each week. In Texas, where I am, it is at least three, and phone
     screens and interviews count as activities, not just applications. Because
     every application, call, and interview is already a dated row in my tracker, I
     could say "fill out my work-search log for last week" and Claude produced a
     clean, grouped summary ready to drop into the state's PDF, flagging any week
     that fell short of the minimum. One table served both my pipeline and the
     official record, with no double entry.

  > **Tip: connect your email so you never paste again.** Claude Code can link to
  > Gmail through what is called an MCP integration. Type `/mcp` inside Claude Code
  > to set it up. Once it is connected, instead of copying an email in, you just
  > say "check my inbox and update my pipeline," and it reads the recruiter emails
  > and updates your files itself. I wired this up late and wish I had done it on
  > day one. (Fair caveat: it means the assistant can read your email. Easy trade
  > during an active search, and you can disconnect it the day you stop.)

---

## Step 3: Have Claude build a cheat sheet for every screen and interview

Once interviews started, I had Claude build a one-page "cheat sheet" for each one,
generated from that job's folder so it stayed consistent with what I had actually
claimed:

```
I have an interview scheduled for this role. Make me a one-page cheat sheet (html)
I can pull up on my phone right before the call: their product in plain terms, my
best stories mapped to the questions they are likely to ask, my salary range, and
short notes on each interviewer.
```

Because the prep came from the same folder as the resume, it never contradicted
what I had told them on paper. I formatted these as HTML so I could open them on my
phone in the parking lot two minutes before the call.

---

## Step 4: Have Claude create coding drills to practice on (for technical roles)

My field has live coding interviews, and a year of leaning on AI had quietly
rusted my ability to write code cold, without autocomplete. So I had Claude make
practice drills with one strict rule attached: **drill me, do not solve it for
me.**

```
Create coding drills so I can practice for a technical interview. Give me the
problems and a way to check my answers, but do NOT write the solutions for me. I
will write the code by hand, and you grade it.
```

If your field has technical interviews, this is the use most people miss, because
the instinct is to let the AI just write the code. Here the whole point is the
opposite: you want the reps.

---

## Step 5: Use Claude to manage timing, and to advise on competing offers

Late in a search the hard part stops being "write things" and becomes "keep it all
straight." At one point I had several late-stage processes running at once and an
offer with a deadline ticking. Because every role, interview, and offer was already
written down in the folder, I could just talk it through: ask Claude to lay out the
timeline, work out how to ask one company to speed up while politely buying time
from another, and pressure-test whether an expiring offer was worth taking before
a later interview even happened. It is genuinely useful here as a sounding board,
because for once it actually has the full picture of your search in front of it.

---

## A few honest caveats

- **It will overclaim if you let it.** Tailoring a resume and exaggerating one are
  the same motion. The "gaps / not claimed" list is the guardrail. Read what it
  writes.
- **You are still the one searching.** The folder removes busywork and keeps you
  organized. It does not apply for you or know your worth in a negotiation.
- **Keep it private.** Your real folder holds real names, salary numbers, and notes
  about people. If you back it up to GitHub, make the repo private. Only a
  sanitized, generic copy like this starter kit belongs in public.
- **It is just files.** Nothing is locked in. It is plain text and HTML in a folder
  you own, readable in any editor even if you stop using the tool tomorrow.

---

## Start your own

1. Install Claude Code.
2. Copy the [`template/`](template/) folder somewhere as your `job` folder.
3. (Optional, but do it early) Connect Gmail with `/mcp`.
4. Open Claude Code in the folder and run the Step 1 prompt to build your resume
   and LinkedIn profile.
5. For each job, start a fresh session with the Step 2 prompt, then `/rename` it.
6. Let the folder grow. Ask Claude to tidy up when it gets messy.

That is the whole method: a folder that remembers, an assistant that can read and
write it, and a few rules you set once. Want to share this guide with someone? See
[`PUBLISHING.md`](PUBLISHING.md). Good luck. You have got this.
