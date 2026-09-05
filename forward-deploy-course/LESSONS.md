# LESSONS.md — Forward Deploy: The FDE Program

> Full session plans for all 13 sessions (0–12). The instructor (`CLAUDE.md`)
> runs one session at a time, gives one step, and waits for the learner to paste
> what they saw. Everything here stays accurate to `SOURCE.md`.

**Lesson format (every session):** Do This First · What Just Happened · Why It
Matters · Key Tradeoff · Apply to Your Work · Check bank.

**Guardrails the instructor enforces in every exercise:**
- **Data rule.** No real personal data about customers, clients, members, employees or anyone else
  goes into Claude Code. Use `data/` (synthetic) or a de-identified sample
  whoever owns the data has approved.
- **Any industry.** Riverbend is a worked example. Every "Apply to Your Work"
  uses the learner's own industry and vocabulary (`data/OTHER_INDUSTRIES.md`). Pasted text is sent to Anthropic's servers.
- **Authority rule.** The agent drafts, decides and logs. It never sends emails,
  deletes anything, or changes a system of record on its own. A human clicks send.
- **No code.** The learner never reads or writes code. Claude Code builds; the
  learner describes, checks and decides. If code appears on screen, the
  instructor summarises what it does in one plain sentence and moves on.
- **Personalise.** Once `user.json` exists, run every exercise on the learner's
  own workflow. The Riverbend practice data is the fallback and the warm-up.
- **Paste-ready.** Anything the learner types or pastes goes in a fenced block.

---

# Start Here

## Session 0 — Get Set Up (and Keep the Data Safe)

### Do This First
1. Sign in or create an account at **https://claude.ai**. Claude Code needs a
   paid plan (Pro, Max, Team or Enterprise). If your organisation is paying,
   the facilitator will tell you which.
2. Install Claude Code. Two routes; pick one.
   - **Desktop app (recommended for most staff):** download at
     **https://claude.ai/download**, open it, and look for the **Code** tab.
   - **Terminal:** open Terminal (Mac) or PowerShell (Windows) and paste:
     ```
     curl -fsSL https://claude.ai/install.sh | bash
     ```
     Windows:
     ```
     irm https://claude.ai/install.ps1 | iex
     ```
     Docs, if anything looks odd: **https://code.claude.com/docs/en/quickstart**
3. Get the course folder. Download the ZIP from
   **https://github.com/youngfonz/course-builder/archive/refs/heads/main.zip**,
   unzip it, and move the `forward-deploy-course` folder into your Documents.
4. Open that folder in Claude Code (Desktop: choose the folder; Terminal: open
   the folder, then type `claude`). Then type:
   ```
   hello
   ```
   You should get a reply. Paste it here.
5. Read the data rule out loud, then confirm you accept it:
   ```
   I accept the data rule: no real personal data about customers, clients, members, employees or anyone else goes into Claude Code during this course.
   ```

### What Just Happened
You installed the **builder**. Claude Code is an AI that can read the files in
this folder, write new ones, and run things. For the rest of the course **it
writes anything that needs writing; you decide what it should do.**

### Why It Matters
Step one of becoming an FDE is "code foundations". You are skipping it, on
purpose, by having a very patient colleague do that part. What you can't skip
is judgment about **what** gets built and **who owns it**. That's this course.

### Key Tradeoff
Desktop app is easier; terminal is what most engineers use and what your
target companies expect. Either works for every session. Switch later if you like.

### Apply to Your Work
The instructor now runs first-time setup: your name, role, industry, a 1–5
comfort rating, and the one workflow you'll build on. Then find your industry's
row in `data/OTHER_INDUSTRIES.md`: the loop you're about to practise on a youth
center is the same loop in your business.

### Check bank
- Predict: if you paste a real member's name into Claude Code, where does it go?
  (Answer: to Anthropic's servers for processing. Hence the rule.)
- Predict: what happens if you ask Claude Code to delete a file? (It asks first.
  Say no unless you meant it.)

---

## Session 1 — Works vs. Lands

### Do This First
Paste into Claude Code:
```
Read data/usage_report.csv. Tell me, in plain English and no more than five lines: how many families could use the Family Portal, how many actually did last month, and what the coordinator's enrollment hours did over the six months since it launched.
```
Before you read the answer, write down your guess: **what fraction of eligible
families use the portal?** Then compare. Paste the answer here.

Then:
```
Read data/discovery_transcript.md and tell me in three lines why Denise says families don't use the portal.
```

### What Just Happened
The portal **works**. About 41 of 11,000 families use it, and the coordinator's
hours went **up**. Two problems hide inside "build software": **making it work**
and **making it land**. Almost every failure is the second one.

### Why It Matters
Roughly 95% of AI pilots show no measurable business impact (MIT, 2025). Not
because the model was bad. Because nobody decided where intelligence belonged,
nobody built for the unhappy paths, nobody owned the result. Your organisation
has probably already bought one of these. You are going to build the other kind.

### Key Tradeoff
A tool that does more, versus one that lands. The portal did more than email.
Email won, because it fit how parents actually behave: on a phone, in a car
park, at 5:45. Landing beats capability. Every time.

### Apply to Your Work
In `MY_DEPLOYMENT.md`, under Session 1, write one line: a tool your organisation
bought or built that works and that people route around, and why.

### Check bank
- Predict, then check the numbers: did coordinator hours go up or down after the
  portal launched?
- Predict: which line in the transcript explains the routing-around? Then find it.

---

## Session 2 — What an FDE Is (and the Four Things It Isn't)

### Do This First
Paste:
```
Read every file in data/job_posts/. For each one, tell me which role it really is from this list: sales engineer, consultant, support, product engineer, customer success, forward deployed engineer. One line each, and say what gave it away.
```
Before you look, sort them yourself: A to F. Which one is the FDE? Paste Claude
Code's answer and your own guess.

Then:
```
For the one you called forward deployed engineer, tell me what its unit of success is, in one sentence.
```

### What Just Happened
The FDE advert (C) is the only one whose success is **a deployment that's live
and used**. The others are measured on confidence (sales engineer), a
recommendations deck (consultant), tickets (support), features shipped across
all customers (product engineer), or renewals (customer success).

### Why It Matters
You'll be pitching this work inside your organisation. People will assume you
mean a consultant, or IT support, or "the AI person". The one-line distinction
you can say in a lift: **an FDE builds it and stays until it's used, and their
unit of success is the deployment.**

### Key Tradeoff
The honest costs: range instead of depth, less visible work, exposure when it
fails. If that sounds bad, that's a fine answer, and you'll still finish this
course knowing how to tell a good AI pilot from a doomed one.

### Apply to Your Work
Under Session 2 in `MY_DEPLOYMENT.md`: the one-sentence version of your
workflow's deployment, in the form "live and used by ___ to do ___." If you
have a target company or role, add it under **Target role or company**.

### Check bank
- Predict which advert most people mistake for the FDE (usually A or E). Ask
  Claude Code which is the closest decoy and why.
- Palantir called the role "Delta". Predict what "Echo" did, then ask.

---

# Understand the Business Reality

## Session 3 — Discovery: The Real Process, Not the Wiki Version

### Do This First
Paste:
```
Read data/discovery_transcript.md. List every rule Denise follows that is NOT written down anywhere. Then list every place an enrollment email can arrive. Then tell me the one thing she asked for, in her own words.
```
Paste the result. Then the real exercise: **book 15 minutes this week with the
person who does your workflow today.** Ask only these four questions, and don't
interrupt:

```
1. Can you just show me what happens when one comes in?
2. How long does one take when it's clean? And when it isn't?
3. What's the worst part?
4. If I could take one thing off your plate, what would it be?
```

If they have ten more minutes, add the two best prompts from `HOMEWORK.md`:
```
5. Where does the real information live? Not where it's supposed to.
6. What's a call you make in four seconds that would take someone new an hour to get wrong?
```

Type up what they said (no real names) and paste it into
Claude Code with:
```
Here are my discovery notes. Pull out: the unwritten rules, every input channel, the time per item, and the one thing they asked for. Keep it to ten lines.
```

### What Just Happened
The wiki says "parents enrol via the portal". Reality: forty senders, forwarded
threads, and eleven years of rules in one head. **You sit in the room and watch
someone do it the slow way, and you don't interrupt, because the reason they do
it the slow way is usually load-bearing.**

### Why It Matters
Denise's "no form, no first day" rule looks like bureaucracy until you hear
"2019". If you'd automated past it you'd have shipped something dangerous and
been proud of it. Discovery is how you find the load-bearing walls.

### Key Tradeoff
Asking versus watching. People describe the process they think they follow.
Watching shows the one they actually follow. When you can only do one, watch.

### Apply to Your Work
Fill in the top of `MY_DEPLOYMENT.md`: what the workflow is, a concrete recent
instance (de-identified), inputs, output, volume, minutes per item, owner.

### Check bank
- Predict: what does Denise say is the worst part? (Not the retyping.) Check.
- Predict how many input channels you'll find for your own workflow, then count.

---

## Session 4 — Reading Someone Else's Data

### Do This First
Paste:
```
Open data/enrollment_export.csv. For each column heading, tell me in plain English what you think it means. Then list every way the data is inconsistent or messy: date formats, blanks, duplicates, anything odd. Don't fix anything.
```
Before you read: guess what **PU_AUTH** and **FEE_WVR** mean. Paste the result.

Then:
```
Using data/program_rules.md, which rows in enrollment_export.csv break a rule? Give me the member ID and the rule, one line each.
```

### What Just Happened
You just did the most FDE thing there is: **read a schema written in 2009 by
someone who left, with column names that are abbreviations of words nobody
uses.** Three date formats, a missing birth date, a "duplicate" that's a
sibling, a 12-year-old in 7th grade. This is what real data looks like.

### Why It Matters
The interesting problems were never about the model. They're about **which
system has the truth, whether the data anyone can reach is the data that
matters, and what "correct" means here.** You can't decide where intelligence
belongs until you've seen the mess it has to live in.

### Key Tradeoff
Clean it up first, versus build on it as it is. Cleaning feels responsible and
eats a quarter. FDEs build on top of what exists and make the agent tolerate
the mess. Never propose a migration.

### Apply to Your Work
Get a **de-identified** sample of your workflow's data (whoever owns the data
approves it; if it's your business, that's you). Ask Claude Code to explain its columns and list its inconsistencies. Write
the three ugliest under Session 4 in `MY_DEPLOYMENT.md`.

### Check bank
- Predict: is row 10237 (Chloe Nguyen) a duplicate? Check against the rules.
- Predict: how many rows have a grade that disagrees with the birth date? Ask.

---

## Session 5 — Decide Where Intelligence Belongs

### Do This First
Paste:
```
Compare data/enrollment_export.csv with data/attendance_export.csv. Which members are enrolled but have never checked in? Which have checked in but aren't in the enrollment export? Which file would you trust for "who is actually in the program", and why?
```
Paste the result. Then the wishlist:
```
Read data/requests.md and data/program_rules.md. For each of the ten requests, give me one line: a) how much of Denise's twenty minutes it saves, b) how much authority it hands the AI (low/medium/high), c) how much of the existing system it would need to replace. Then tell me which THREE you'd build first, and which ones you'd refuse, and why.
```
Before you look, pick your own three. Paste both.

### What Just Happened
Requests 2 and 3 (extract the fields, flag the rule-breakers) save most of the
time with **low authority** and **no migration**. Request 4 (replace the system)
and 9 (auto-approve and confirm) are quarter-eaters or hand the AI Denise's
name. You just **decided where intelligence belongs: the smallest build that
moves the most work with the least model authority.**

### Why It Matters
The single highest-value thing an FDE does is **kill a requirement** that would
have consumed a quarter and shipped something nobody wanted. You can only do it
credibly if you know it's technically possible and you're close enough to know
it's pointless.

### Key Tradeoff
More authority means more time saved and more exposure. Denise said "I want to
click send" and "it should be my name on it." Build up to the line she drew,
not past it. Two systems disagreeing is normal; pick the one people act on.

### Apply to Your Work
Fill the **Where intelligence belongs** section of `MY_DEPLOYMENT.md`: the
smallest build, what it decides, what it never does alone, who clicks send.
Write the requests you're refusing and why. You'll need that list in Session 11.

### Check bank
- Predict which request Denise would veto hardest (9), then ask Claude Code to
  argue her side.
- Predict: enrolled but never checked in, how many? Then check.

---

# Build It

## Session 6 — One Model, One Platform: The Agent Loop

### Do This First
One model, one platform, zero switching for the rest of the course. Paste:
```
Build me a small tool in this folder called the Enrollment Agent. When I give it the path to one email in data/intake_emails/, it should: read the email, pull out child's name, date of birth, grade, program, site and guardian phone, decide which program code (ASP, TN or SUM) and site code (RB1 or RB2) apply, and write a new row in the same format as data/enrollment_export.csv to a file called output/proposed_rows.csv. It must NOT edit enrollment_export.csv and must NOT send anything. Describe what you're going to build in five plain lines before you build it. Don't show me code.
```
Read the five lines. If they match what you meant, say `go`. Then:
```
Run the Enrollment Agent on data/intake_emails/01_clean.txt and show me the row it produced.
```
Paste the row. Then run it on `02_missing_dob.txt` and paste that too.

### What Just Happened
You built an **agent loop**: real input (an email), a **decision** (which
program and site), a real output (a row). Ugly, and it works, by Friday. On the
second email it either guessed a birth date or left it blank. Notice which. That
is the next three sessions.

### Why It Matters
"Judgment transfers, tool-hopping doesn't." You now understand what an agent is
by having one, which beats any explanation. Everyone else in your organisation
talking about AI is describing a demo. You have a thing that ran.

### Key Tradeoff
Automate one workflow you understand deeply, versus something impressive. The
impressive thing dies at death #1 (built for the demo). The boring thing you
understand ships.

### Apply to Your Work
Describe your own workflow's loop to Claude Code in the same shape: **input →
decision → output**, using your de-identified sample. Ask it to build a second
tool for yours. Note under Session 6 what the first ugly run got right and wrong.

### Check bank
- Predict what the agent does with a missing birth date **before** you run 02.
  Then run it. The gap is the lesson.
- Predict which fields it gets wrong on the clean email (usually none). Check.

---

## Session 7 — Give It the Veteran's Rules

### Do This First
Paste:
```
Run the Enrollment Agent on data/intake_emails/03_counselor_thread.txt and data/intake_emails/05_sibling.txt. Show me what it proposed for each.
```
Predict first: will it treat the sibling as a duplicate? Will it try to enrol
the counsellor's three kids? Paste the results. Then:
```
Update the Enrollment Agent so that before it decides anything it reads data/program_rules.md and applies every rule in it. Add a DECISION column with one of: ready_to_confirm, hold_ask_family, waitlist, waitlist_priority, pending_not_enrolled, escalate_to_human, forward_kindly, duplicate_keep_earlier. Add a REASON column quoting the rule it used. Tell me in three lines what changed, no code.
```
Then re-run both emails and paste the new decisions.

### What Just Happened
You gave the agent the rules that lived in one veteran's head. The counsellor
thread went to **escalate_to_human** ("a counsellor about more than one child is
a situation"). The sibling went to **ready_to_confirm** with sibling priority,
not "duplicate". This is **grounding**: the model answers from the customer's
own documents, not from general knowledge.

### Why It Matters
"Whether the humans doing this job today will adopt it or quietly route around
it" comes down to whether it knows **their** rules. A generic model doesn't know
about 2019. Written-down rules are also the first time Denise's knowledge has
existed outside Denise, which matters the week she's on holiday.

### Key Tradeoff
Rules written down versus rules learned from examples. Writing them down is
slower and auditable; you can point at the line that caused a decision. For
anything with a person's name on it, auditable wins.

### Apply to Your Work
Sit with your workflow's owner for ten minutes and write **their** rules into a
file (no personal data). Give it to your tool the same way. Note under Session 7
the rule that surprised you most.

### Check bank
- Predict the decision for `04_wrong_inbox.txt` before running it. Check the
  REASON column: does it quote the right rule?
- Predict what happens to the 12-year-old 7th grader (case 9 in
  `data/eval_cases.csv`). Then ask the agent.

---

## Session 8 — Make It Survive Failure

### Do This First
Paste:
```
Run the Enrollment Agent on every email in data/intake_emails/. Give me a table: file, decision, reason. Then list every way it could break on a real inbox that we have NOT seen yet. Aim for 20. Think about wrong file types, missing fields, contradictory instructions, forwarded threads, non-English, attachments that aren't there, two children in one email, and anything mentioning custody, medication or an IEP.
```
Paste the table and the list. Then:
```
For each of the 20, tell me whether we should FIX it (handle it properly), FENCE it (refuse and hand to a human with a clear note), or ESCALATE it (always a human). Then implement all 20. Add an audit log: every decision written to output/audit_log.csv with the time, the file, the decision, the reason, and the row it proposed, so anything can be reversed. Tell me what you did in five lines, no code.
```
Run it on all eight emails again. Paste the audit log.

### What Just Happened
"There's one happy path and a thousand unhappy ones, and **the exceptions are
the job**." Email 07 says the form is attached; nothing is. Email 08 mentions
medication. Email 06 names two sites. The agent now **fixes, fences or
escalates** each, and every decision is **logged and reversible**.

### Why It Matters
Death #3, happy path only, is how most pilots die. The 20-item list is the
difference between a demo and a deployment. Also: the day it makes a bad call,
the audit log is what lets Denise undo it in one minute instead of an afternoon.

### Key Tradeoff
Handle everything, versus refuse gracefully. A refusal with a clear note ("I
couldn't find the attachment, please check") is a **feature**. An agent that
guesses a birth date is a liability. Decide what it should **refuse to do on
its own**.

### Apply to Your Work
Fill **Twenty ways it breaks** in `MY_DEPLOYMENT.md` for your own tool, with
fix / fence / escalate for each, and have Claude Code implement them and add an
audit log. Write the three it must always refuse.

### Check bank
- Predict what 07 (no attachment) does now. Run it. Check the audit log line.
- Invent one nasty email of your own (fictional). Predict, run, compare.

---

# Own It

## Session 9 — Make It Measurable

### Do This First
Paste:
```
Read data/eval_cases.csv. Run the Enrollment Agent against every case that points at a file, and for the text-only cases create a short fictional email that matches the description and run that. Compare the agent's decision to expected_decision. Give me: pass count out of 20, and for EVERY failure, the case, what we expected, what it did, and your best guess why.
```
Predict your pass count first. Paste the results. Then:
```
Now help me write 30 more eval cases, to reach 50, based on realistic variations of the eight emails. No real people. Add them to data/eval_cases.csv and re-run everything. Same report.
```
Then the number:
```
Denise spends about 20 minutes per enrollment email and handles 15 to 70 a week. Using our pass rate and the decisions that still go to a human, estimate hours saved per week in a quiet month and in the spring rush. State it in one sentence a director would understand. Show your working in plain English.
```

### What Just Happened
You built an **eval**: 50 cases from real examples, and a pass count. "When 41
pass, **the 9 failures are the deliverable**." Each failure tells you where it
breaks before a parent finds out. And you turned it into **hours**, because
"businesses measure revenue, risk and cost. Nothing else."

### Why It Matters
Hand-waving on evaluation is a top reason FDE candidates get rejected, and a
top reason internal pilots get quietly cancelled. A number with a baseline
survives a budget meeting. "It seems to help" does not.

### Key Tradeoff
Celebrating the pass rate versus investigating the failures. The pass rate is
for the slide. The failures are for you. Never invent eval cases from
imagination when you have real examples; real ones find real bugs.

### Apply to Your Work
Build the eval for your own tool: 50 cases from de-identified real instances.
Fill **The eval** in `MY_DEPLOYMENT.md`: cases, pass, failures investigated, and
the result in hours, errors or days.

### Check bank
- Predict which of the 20 cases fails (case 19, grade/DOB mismatch, is a usual
  suspect). Run. Compare.
- Predict the hours saved in the spring rush before Claude Code estimates it.

---

## Session 10 — Ship It and Carry the Number

### Do This First
Paste:
```
Make the Enrollment Agent easy for someone who isn't me to use: a one-page HOW_TO.md in plain English with exactly what to do, what the output means, what to do when it says escalate_to_human, and who to contact (leave my name as a placeholder). Then run the five-deaths check from SOURCE.md section 1.9 against what we've built and tell me honestly where it's weak.
```
Paste the five-deaths result. Then the real step, on **your** tool:

1. Put your tool in the hands of **one colleague** who does the workflow.
2. Sit with them for the first three items. Don't touch the keyboard.
3. Agree the number you'll both look at in a week: hours, errors caught, or
   days recovered.
4. Ask Claude Code:
```
Write a one-line weekly check-in I can send my colleague every Friday asking for: items processed, items they had to fix, and time it took. Plain, friendly, short.
```
Paste what your colleague said after the first three items.

### What Just Happened
It's **in production**: used by the person it was built for, on real work, on
top of the tools they already have. And you **carry a number**. Not story
points. Whether it's live and used.

### Why It Matters
Death #4 is "no owner after launch". Death #5 is "moves no metric". Your name is
on this for 90 days and you have a Friday number. That is the entire
difference between the portal in Session 1 and what you've just done.

### Key Tradeoff
Ship something ugly that works, versus polish for another fortnight. Ugly and
in someone's hands this week beats beautiful and on your laptop. You can polish
what people use. You can't polish what they don't.

### Apply to Your Work
Tick the **Five-deaths check** in `MY_DEPLOYMENT.md` honestly. An unticked box
is a Session 12 task, not a failure.

### Check bank
- Predict which death your build is closest to. Then read Claude Code's honest
  answer.
- Predict what your colleague will find annoying first. Watch. Compare.

---

# Defend It

## Session 11 — Defend It Like a VP

### Do This First
Paste:
```
Draft a one-page writeup of the Riverbend Enrollment Agent for a director who has five minutes: 1) the broken workflow in three lines, 2) what we built in three lines, 3) what changed, with the number, 4) what it refuses to do and who stays in charge. Never use the words "audit", "migration", "AI-powered" or "leverage". Make Denise look brilliant, not me.
```
Paste the draft. Read it as the director. Cut anything they'd skip. Then:
```
Plan a five-minute live demo. It must go THROUGH at least two unhappy paths (the missing attachment and the counsellor thread), not around them. Give me a minute-by-minute script in plain English and the one sentence to open with.
```
Then a rehearsal, FDE-interview style. Ask Claude Code:
```
Play a sceptical director. Ask me the three hardest questions about this deployment, one at a time, and grade my answers out of 5 with one line of feedback each.
```

### What Just Happened
"Nobody buys AI; people buy not getting fired." You showed **before, after and
the number**, built on top of what exists, with a human in charge. Demoing
through the failures is what makes people trust it; a happy-path demo makes
them suspicious, and they're right to be.

### Why It Matters
This is also the FDE interview. The signature round is a vague problem and 60
minutes; what's scored is clarifying before solving, naming what's missing,
sequencing by risk, proposing the smallest end-to-end version, and surfacing
failure modes. You have now done every one of those on a real deployment.

### Key Tradeoff
Being the hero versus making the sponsor the hero. The second gets you the next
deployment. The first gets you a nice week.

### Apply to Your Work
Write the one-pager for **your** deployment and plan **your** demo. Rehearse
the three hard questions. Note under Session 11 the question you fumbled.

### Check bank
- Predict the director's first hard question ("what happens when it's wrong?"
  is a favourite). Compare.
- Predict which banned word slipped into your draft anyway. Search for it.

---

## Session 12 — Capstone: Publish, Demo, Hand Over

### Do This First
Three things, in this order.

**1. Publish.** Ask Claude Code:
```
Turn my one-page writeup into a clean single-page web page called writeup.html in an output folder, using the Riverbend example only if I haven't given you my own. No personal data. Then tell me the two simplest ways to share it: as a file, or on a free web page.
```
If you want it live and have a GitHub account (**https://github.com/signup**),
Claude Code can walk you through publishing it with GitHub Pages. The writeup
is your portfolio and, if you're aiming at an FDE role, your application.

**2. Demo.** Deliver the five-minute demo to your facilitator or cohort. Through
the unhappy paths. Then paste what the toughest question was.

**3. Hand over.** Ask Claude Code:
```
Write a handover note for [colleague's role, no name]: how to run the tool, what each decision means, what to do when it escalates, how to undo a decision using the audit log, and who to call for the first 90 days (leave a placeholder). One page, plain English.
```

Finally, score yourself against `RUBRIC.md`. Ask Claude Code to walk through
each row with you and be honest.

### What Just Happened
You did the job before anyone gave you the title. Understood the business
reality. Decided where intelligence belongs. Built it, made it survive failure,
measured it, shipped it, defended it, handed it over. **The unit of success was
a deployment, and it's live.**

### Why It Matters
"Proof beats resumes." Whether your next step is a second workflow in your
organisation or an FDE interview, you now have the thing almost nobody in that
room has: a deployment that is used, with a number, that you can talk about
for five minutes without a slide.

### Key Tradeoff
Stop here, or go again. The second deployment takes half the time, because the
judgment transfers. Pick the next workflow the same way: the one that annoys
someone weekly and has an owner who'll let you build on it.

### Apply to Your Work
Complete the **Capstone — shipped** section of `MY_DEPLOYMENT.md`. Record the
rubric score in `PROGRESS.md`.

### Check bank
- Predict your rubric row that scores lowest. Score honestly. Compare.
- Optional, if you're aiming at the role: ask Claude Code for one FDE
  decomposition case (a vague customer problem) and talk it through out loud
  for 20 minutes, clarifying before solving. Then ask for feedback.
