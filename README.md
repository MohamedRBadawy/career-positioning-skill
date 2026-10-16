# Grooya: Career Positioning Skill for Claude

A Claude Agent Skill that runs career positioning as a repeatable system,
not a one-off chat. It reads your saved career context, asks focused
discovery questions, searches the live market, scores your gaps, and builds a
90-day repositioning plan. Each session picks up where the last one ended.

Built by Mohammed Badawy.

Grooya is a product concept. This skill is a working implementation of its
core method.

---

## What it does

- **Discovery.** A structured interview, one question at a time: target role,
  employed or independent, income floor and target, constraints, real weekly
  hours, and energy.
- **Market intelligence.** Live web searches from templates: role demand,
  compensation, tools, automation risk, positioning, regional factors. The
  results are condensed into three lists: valued now, rising, declining.
- **Gap analysis.** Three tiers (strengths to activate, gaps to close, dead
  weight) with a scoring rubric, so rankings are comparable across sessions.
- **Repositioning plan.** Three 30-day blocks. Each has a focus, a weekly
  commitment, a visibility action, the gap it closes, and a "done when"
  outcome.
- **Tracking.** Every session is saved. Return sessions ask only what
  changed. Monthly and quarterly reviews catch drift and stale criteria.

## Who it is for

- Professionals planning a deliberate career move or a shift into
  independent work
- People in a long or open-ended search who need the plan to stay current
- Anyone who wants a career plan grounded in market evidence and their own
  verified work, not generic advice

It is the strategic half of a job search. It does not scan job boards, track
applications, or prepare interviews. Pair it with a separate skill for that.

---

## Install

### Claude Code

Copy the `grooya` folder into your skills directory:

```
~/.claude/skills/grooya/SKILL.md
~/.claude/skills/grooya/references/market-search-templates.md
~/.claude/skills/grooya/references/gap-analysis-rubric.md
~/.claude/skills/grooya/references/closing-protocol.md
```

For a single project, use `.claude/skills/grooya/` inside the project
instead. Start a new session and say "run Grooya" or "career session".

### claude.ai

Zip the `grooya` folder (with `SKILL.md` at the folder root) and upload it
under **Settings > Capabilities > Skills**. Web search must be enabled for
Step 3.

### Configure

Open `grooya/SKILL.md` and fill in the **Configure** table. It lists the
places the skill reads and writes:

- your career profile document
- a session log (one entry per session)
- an evidence library of proof points
- a learning roadmap
- a task tracker for next actions
- optional: a goal record, a calendar, a notification channel, and a writing
  or build handoff

These can be Markdown files in a folder, pages in a notes tool, or database
records. Anything the session can read and write works.

---

## Example session outline

A first session, in outline:

1. **Context read.** Claude reads the profile and roadmap and reports what it
   found. It finds no prior session, so it runs the full flow.
2. **Discovery.** It asks only what the profile does not answer. For example:
   "Employed, independent, or both?" Then: "What is the monthly floor below
   which this does not work?"
3. **Confirmation.** "Here is what I understand. Correct anything wrong
   before I run the market analysis."
4. **Market search.** About ten searches, condensed into valued / rising /
   declining.
5. **Gap analysis.** Tier 1 names the proof points to lead with. Tier 2 lists
   specific skills, scored and ranked. Tier 3 names time to reallocate. It
   ends with one 30-day action.
6. **Plan.** Three 30-day blocks, checked against stated constraints. It ends
   with the most likely failure point.
7. **Save and close.** A new session entry, an updated roadmap, one recorded
   next action with an owner and a date, and a SESSION CLOSE block that links
   everything written.

A return session asks two questions ("What did you complete?" and "Has your
target changed?"), re-checks the market, and changes only the plan blocks
that need it.

---

## Structure

```
grooya/
  SKILL.md                          main workflow: modes, steps 1-8, tone, close
  references/
    market-search-templates.md      expanded query sets in six categories
    gap-analysis-rubric.md          tier tests, 3-axis scoring, disqualifiers
    closing-protocol.md             opening declaration, decision, receipts
```

`SKILL.md` holds the workflow. The references hold the detail that is only
needed at specific steps. Claude loads them when a step points to them.

---

## Design notes

**Read before speaking.** Every session starts by reading saved context and
declaring what was read in a CONTEXT READ block. The skill never asks for
something the profile already answers. This keeps sessions short and makes
skipped context visible.

**Evidence first.** A strength counts only if a named proof point or shipped
work backs it. A gap counts only if at least two independent search sources
show demand for it. A proof point is written only for a skill applied to real
work with a measurable result. Finishing a course does not count. Search
contradictions are surfaced, not averaged away.

**A scoring rubric, not a feeling.** Tier 2 gaps are scored on impact (double
weight), time to close, and difficulty. Ties break toward impact. Hard
disqualifiers override any score: an income gap the user cannot absorb, a
clash with a fixed commitment, or a block that runs past 90 days. The aim is
rankings that stay comparable from one session to the next.

**Constraints are checked, not remembered.** Weekly hours, employment status,
energy, and finances are asked again when they matter. A plan built for last
quarter's capacity is a quiet failure. The plan always states its own most
likely failure point.

**The target is never settled.** Criteria drift in a long search. A quarterly
check re-confirms the criteria themselves, not just the results.

**Close with a decision, not a record.** Each session ends with one next
action and one named owner, or an honest statement that nothing follows. A
forced next step is treated as worse than none. The action is recorded with
a planned date and notes written for someone who was not in the session.

**Receipts over claims.** The SESSION CLOSE block lists links or paths to
everything written. The skill must never report a write, message, or calendar
event that did not happen. If a tool is missing, it says so and pastes what it
would have sent. This rule targets the most common way agent workflows drift:
reported completion that nobody checked.

**Clean dates and attribution.** Done status and done date are set together.
Every task gets a planned date. Unknown dates are left empty with a reason,
never guessed. Records carry "Written by" separate from "Owner". This makes
planned-versus-actual measurable later.

**No recurring reminders for paused work.** A calendar block for a paused
track trains the user to ignore the calendar. The skill checks that a track is
active before scheduling.

**Strategy separate from operations.** Positioning runs monthly or quarterly.
Job scanning runs weekly. Keeping them in separate skills keeps each one
focused, and the description routes requests to the right one.

**Optional handoffs with full briefs.** When a proof point should become
content, or a plan block needs something built, the skill can hand it to a
writing or build agent with a brief complete enough to act on without
questions. It checks for an existing open handoff first and caps rework at
two passes before escalating to the user.
