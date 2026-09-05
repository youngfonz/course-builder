# SOURCE.md — Canonical Source Material

> This is the source of truth. If a lesson and this file disagree, this file
> wins. Every lesson, exercise and check traces back to something here. Each
> section names where it came from; statistics carry a citation.

---

## 1. The Forward Deploy playbook (primary source)

The course is built on the **Forward Deploy** series and roadmap by Fonz Morris
(Beyond Code Collective). Three artefacts:

- Video: *The One Job AI Can't Touch, No One Explains* — youtube.com/watch?v=hc1nx2tzoa8
- Video: *5 Steps to Become a Forward Deployed Engineer (2026)* — youtube.com/watch?v=4pz2_TnQocI
- PDF: *The FDE 30-Day Roadmap* — forwarddeploy.fonz.sh/fde-roadmap.pdf

### 1.1 Two problems hiding inside "build software"

> "You shipped it. The tests pass. The latency is good... Six months later, you
> open the dashboard and check the usage numbers. **41 people out of 11,000.**
> The software works perfectly. Almost nobody uses it. This is the normal
> outcome. Not the failure case, the normal one."

- Problem one: **making it work.** Problem two: **making it land** inside a real
  organisation, with real data messier than your fixtures, and real people who
  already have a way of doing this they like better than yours.
- Almost every engineer is optimised for the first problem. Almost every failure
  happens in the second. The FDE exists in that gap.

### 1.2 What an FDE is, and the four things it isn't

An FDE is a real engineer who works **inside the customer's world** instead of
inside the vendor's codebase. Not a demo, a slide deck or a recommendation memo.
Production work against the customer's actual data, sitting with the people who
will use the thing.

| Confused with | The difference |
|---|---|
| Sales engineer | Works before the deal; output is **confidence**. FDE works after; output is a **working system**. |
| Consultant | Tells you what to do and leaves. FDE **builds it and stays until it's used**. |
| Support | Reactive and ticket-shaped. FDE work is **proactive and outcome-shaped**. |
| Product engineer who talks to customers | Owns the **surface of the product**. FDE owns **whether a specific customer succeeds**. |

> "The FDE's unit of success is not a feature. It's a **deployment**."

### 1.3 Why the role exists: Palantir, then every AI company

- Palantir built the role to sell into places "where normal enterprise software
  goes to die": government agencies, banks, hospitals. Thirty years of data, no
  clean schema, a very good reason for every strange thing they do. So they sent
  engineers, not to advise but to build.
- The FDEs kept building the same things for different customers. Those patterns
  were pulled back into the core product. **The deployment layer became the R&D
  function.**
- Every AI company hit the same wall: a model that "can do almost anything in
  general and nothing in particular." The demo is stunning; then it hits a real
  company, and the hard problems were never about the model:
  - which **system of record** has the truth in it
  - whether the data anyone can get to is the data that matters
  - what **"correct" even means** for this customer, and who decides
  - whether the humans doing the job today will **adopt it or route around it**
- None of that is solved by a better model. All of it is solved by an engineer
  standing inside the problem.

### 1.4 The texture of the job

- You read someone else's schema. Written years ago by someone who left, with
  column names that are abbreviations of words nobody uses any more.
- You write **glue**. Unglamorous, deeply specific, and the reason the thing
  works at all.
- You sit in rooms and watch someone do their job the slow way, and **you don't
  interrupt**, because the reason they do it the slow way is usually load-bearing.
- You **say no, constantly**. The single highest-value thing an FDE does is kill
  a requirement that would have consumed a quarter and shipped something nobody
  wanted. You can only do that credibly if you're technical enough to know it's
  possible and close enough to know it's pointless.
- You **carry a number**: not story points, but whether this deployment is in
  production and being used by the people it was built for.

### 1.5 The honest costs, and what you get

Costs: depth traded for range; less legible work (no repo that shows what you
did); travel; exposure (when the deployment fails, it's yours). "If those
trade-offs sound bad, this genuinely isn't your role. And that's a fine answer."

In exchange: a **short feedback loop to reality** (days, not quarters);
**judgment**, not opinions, after a few deployments you can tell in the first
meeting whether something will work; **leverage**, because the FDE is the only
person who sees the product, the customer and the gap between them at once; and
**durability**, because the hard part was never the code, it's judgment under
ambiguity in a room full of competing incentives.

### 1.6 The five steps (from the short video)

1. **Code foundations** — Python, Git, SQL, APIs.
2. **The AI stack** — large language models, prompting, retrieval, agents.
3. **Ship real deployments** — build, deploy and debug in production.
4. **Customer skills** — discovery calls, live demos, translating between
   business and technical. "That's the forward part of the job."
5. **Land the role** — a deployed portfolio, certifications, interview reps.
   "Proof beats resumes."

*Course note:* this course is for non-technical staff. Step 1 is done **by**
Claude Code, not by the learner. Steps 2 to 5 are done by the learner, with
Claude Code as the builder.

### 1.7 The three stages of the job (roadmap)

1. **Understand the business reality.** Not the wiki version. The real process,
   with its 40 senders, forwarded threads, and rules that live in one veteran's
   head.
2. **Decide where intelligence belongs.** The smallest build that moves the most
   work with the least model authority.
3. **Build it and own it until it works.** Through the failures, in production,
   with a number attached.

### 1.8 The 30-day roadmap (roadmap, verbatim structure)

**Week 1 — Build an agent loop end to end.** Pick one model and one agent
platform. "Ignore everyone telling you to stay model agnostic; judgment
transfers, tool-hopping doesn't." Build an agent that takes a real input (an
email, a PDF, a form), makes a decision, and produces a real output.
Checklist: one model, one platform, zero switching for 30 days · automate one
workflow you personally understand deeply · ship something ugly that works by
Friday.

**Week 2 — Make it survive failure.** "There's one happy path and a thousand
unhappy ones, and the exceptions are the job." Feed it garbage: wrong file
types, missing fields, contradictory instructions, the weird forwarded thread.
Every failure becomes a handler, a retry, or a graceful escalation to a human.
Checklist: list 20 ways it breaks, fix or fence every one · add an audit trail,
every decision logged, every action reversible · decide what it should refuse
to do on its own.

**Week 3 — Make it measurable.** "Businesses measure revenue, risk, and cost.
Nothing else." Attach the agent to one of those numbers and build the eval that
proves it. Run 50 test cases. "When 41 pass, the 9 failures are the
deliverable." Checklist: 50 eval cases from real examples, not invented ones ·
investigate every failure, no celebrating pass rates · state the result in
business terms: hours saved, errors caught, days recovered.

**Week 4 — Defend it like a VP.** "Nobody buys AI; people buy not getting
fired." Show the before, the after, and the number. Never say "audit" (call it a
sprint). Never propose a migration (build on top of what exists). Make the
person who sponsored you look brilliant. Checklist: one-page writeup (broken
workflow, what you built, what changed) · a 5-minute demo **through** the
unhappy paths, not around them · publish it; the writeup is your portfolio.

### 1.9 The five deaths of an AI pilot (roadmap)

| # | Death | The check |
|---|---|---|
| 1 | Built for the demo, not reality | Has it seen the real inputs, including the ugly ones? |
| 2 | Forced a migration | Does it work on top of the stack they already have? |
| 3 | Happy path only | What happens on the 20 worst inputs you listed? |
| 4 | No owner after launch | Whose name is on it in 90 days? (It should be yours.) |
| 5 | Moves no metric | Which of revenue, risk or cost does it visibly change? |

---

## 2. The pilot-failure statistic

- **"95% of enterprise generative-AI pilots deliver no measurable P&L impact."**
  Source: MIT NANDA initiative, *The GenAI Divide: State of AI in Business
  2025* (August 2025). The roadmap cites this as "95% of AI pilots fail" and
  attributes the failure not to models but to the absence of three things:
  nobody decided where intelligence belongs, nobody built for the unhappy paths,
  nobody owned the result.
- The instructor may quote the figure as "roughly 95% of pilots show no
  measurable business impact (MIT, 2025)". It must not be presented as "95% of
  AI projects crash" or similar.

## 3. History of the role (secondary sources)

Source: Gergely Orosz, *What are Forward Deployed Engineers, and why are they so
in demand?*, The Pragmatic Engineer newsletter
(newsletter.pragmaticengineer.com/p/forward-deployed-engineers); Palantir blog,
*Dev versus Delta*.

- Palantir created the role in the early 2010s and called it **"Delta."** Teams
  in early Palantir business development were named after NATO alphabet letters.
- Delta engineers were deployment-oriented and often on site; **"Echo"**
  engineers were platform-oriented, responsible for what graduated from a
  deployment into the product.
- Until around 2016 Palantir employed **more FDEs than conventional software
  engineers**. When Foundry launched, many moved into core product, carrying
  field experience with them.
- OpenAI launched its FDE function in early 2025. FDEs there write code on
  customer infrastructure and work with more ambiguity than solutions
  architects. Example: work with John Deere on farmer interventions that also
  improved a public API for all customers.
- Typical time split: site visits and customer work 25–50% of time; the rest is
  product contribution and internal knowledge-sharing.
- Who fits: comfort with ambiguity, travel and unconventional environments
  (air-gapped systems, factory floors). Most postings ask for several years of
  engineering experience.

## 4. Market context (secondary sources, September 2026)

- FDE job postings grew from roughly 640 in April 2025 to about 5,300 in April
  2026 (Aced/Exponent guide, tryexponent.com/blog/what-is-a-forward-deployed-engineer).
- Roughly 90% of organisations report using AI somewhere, far fewer have it in
  production across operations; the bottleneck moved from model capability to
  execution inside complex environments (CIO Dive; TechTarget).
- Companies hiring under FDE or adjacent titles include OpenAI, Anthropic,
  Palantir, Scale AI, Sierra, Ramp, and services firms such as Deloitte and
  Accenture.
- Anthropic's posting asks for a technical customer-facing background and
  production experience with LLMs: prompting, agent development, evaluation
  frameworks, deployment at scale, and "high agency with an ability to navigate
  ambiguity present in complex organizations."
- Compensation figures vary widely by source and level; the instructor should
  not quote a single number as fact. The roadmap cites public postings at
  $280K base (OpenAI) and $300K (Handshake).

## 5. What the interview tests (secondary sources)

Source: Aced/Exponent, *Forward Deployed Engineer Interview: The Definitive 2026
Guide*; Perspective AI interview guides.

- Three things in roughly equal weight: technical depth, customer-facing
  judgment, and reasoning out loud through ambiguity.
- The signature round is the **open-ended decomposition case**: 45–60 minutes,
  a vague customer problem, no single right answer. Example prompt: "A major
  city wants to reduce 911 response times using call data, traffic data and
  ambulance GPS. You have 60 minutes."
- What gets scored: clarifying before solving; naming missing data and
  stakeholders; stating assumptions aloud; decomposing into chunks sequenced by
  risk and value; proposing a walking-skeleton first version; surfacing failure
  modes; talking continuously.
- The single biggest filter: **jumping to a technical solution before scoping.**
- Client-simulation prompts: explain to a non-technical VP why the system cannot
  guarantee 100% accuracy; push back on a feature that compromises data
  governance; explain a three-week slip to a customer's CTO.
- Other common rejections: saying "we" instead of "I", hand-waving on
  evaluation, over-promising in the role-play, preparing as if for a LeetCode
  interview.

## 6. Course-specific facts (this program)

- **Audience:** non-technical staff. The learner never writes code. Claude Code
  builds; the learner directs, checks, decides and owns.
- **Practice environment:** Claude Code, opened in this course folder.
- **Running example:** one real workflow in the learner's organisation that is
  done the slow way today. Captured in `MY_DEPLOYMENT.md`. Optionally, one
  target company or role the learner is aiming at.
- **Data rule:** real personal data about members, families, donors or staff
  never goes into Claude Code during this course. Shipped data in `data/` is
  synthetic. Own-workflow exercises use a de-identified sample approved by the
  learner's supervisor. Anything pasted into Claude Code is sent to Anthropic's
  servers for processing.
- **Authority rule:** during this course the agent drafts, decides and logs. It
  never sends, deletes or changes a system of record on its own. A human clicks
  send.
