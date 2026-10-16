# Closing Protocol

Every Grooya session opens with a declaration of what was read and ends with
a decision, a recorded next action, and receipts. The goal is simple: no
session can claim work that did not happen, and no session ends as a filing
exercise.

---

## 1. CONTEXT READ (first response, before any session content)

```
CONTEXT READ:
- Career profile: read
- Learning roadmap: read
- Prior Grooya session: [date + location] OR "None, first session"
- Career goal record: [read / not configured]
- Open items assigned to this skill: [N, one line each] OR "None"
```

If this block is missing from the first response, the session has skipped its
opening sequence. Go back and do it.

---

## 2. Close with a decision, not a record

Do these three things in order, before the SESSION CLOSE block.

### A. Decide

Answer this in one short paragraph, in the reply where the user can read it:

> Given what this session actually found, what is the single most useful next
> action, and who owns it?

**One action. One owner.** Not a list. Not ranked options. Not "and also". If
three things feel equally urgent, the decision is not made yet. Pick the one
that unblocks the other two, and say why the others wait.

The owner is a named person or agent. "The system" is not an owner.
"Whoever picks this up" is not an owner.

**If nothing follows from this session, say exactly that and skip to C.** A
review that confirmed the plan is still valid is a fine outcome. Inventing a
next step creates a task nobody needed. A forced next step is worse than none.

### B. Record it as one real task

Create one item in the task tracker:

```
Task:          [action verb + specific outcome, not "follow up on X"]
Owner:         [who must DO it]
Status:        To do
Planned date:  [a real date]
Written by:    Grooya
Notes:         [enough context that the owner can act WITHOUT re-reading
                this session: what was found, why this action follows,
                and where the evidence lives. One short paragraph.]
```

The Notes field is what fails most often. Write it for someone who was not
here. "Per today's session" is not context. "Three of the five target
postings ask for process-modelling notation; the user has none on record; the
plan's block 2 covers it; the course link is in the learning roadmap" is
context.

**Decisions only the user can make do not become tasks.** List them under
USER: ACTION NEEDED. A session that surfaces four decisions and one action
writes one task and four lines, not five tasks.

**Check for duplicates first.** Update an existing open item rather than
creating a second one.

### C. Optional summary message

If a notification channel is configured, send a short summary the user can
read on a phone without opening anything else. About 4 to 6 lines:

1. What the session worked on
2. The one finding that mattered
3. The next action and its owner (the same one from A)
4. One link, if there is a single obvious thing to open

If no send path exists in this session, say so and paste the message anyway:

```
SUMMARY: not sent, no notification channel available in this session.
Message that would have been sent:
[the 4-6 line message]
```

Silently skipping the line makes a missing capability look like a missing
event.

---

## 3. SESSION CLOSE block (end of every session)

```
------------------------------------------
SESSION CLOSE
------------------------------------------
SESSION ENTRY:  [link or path to the saved Grooya session]
WROTE:          [link or path for every record created or changed]
                OR "Nothing, [one sentence why]"
NEXT ACTION:    [the one task from 2B, with owner and date]
                OR "None, [why nothing follows]"
CALENDAR:       [events created with date] / not configured / failed: [error]
SUMMARY SENT:   [sent / not sent, reason]
HANDOFF CHECK:  writing: [met, sent / not met / covered by open item]
                build:   [met, sent / not met / covered by open item]
USER: ACTION NEEDED:
                [only items the user must personally decide or do]
                OR "None"
------------------------------------------
```

---

## 4. Rules that apply to every record written

**Show receipts.** List the actual links or file paths of everything written,
not a description of it. A missing record becomes visible immediately, at no
audit cost.

**Attribution.** If several agents or tools write to the same storage, the
storage often cannot tell them apart. Set a "Written by" field on every
record. "Owner" (who must act) and "Written by" (who created the record) are
different questions. Fill both.

**Dates.**
- Every record gets a date: today, or the day the event actually happened.
- Setting a status to Done sets the done date in the same operation.
- Every new task gets a planned date. Without it there is no planned-versus-
  actual, and nothing can be measured.
- If work took more than one pass, record the number of passes.
- Never guess a date. If the real date is unknown, leave it empty and say why
  in the notes. A wrong date is worse than an absent one.

**Never report a write, send, or event you did not execute.** If it failed,
say it failed and paste the error. Trusting completion claims instead of
checking artifacts is the most common way a system like this quietly drifts
from reality.

---

## 5. Raise a hand

If the session noticed something outside the requested task (an idea, an
inefficiency, a risk), record it as one line in the task tracker or a notes
log. Not a lecture. If there is nothing, say nothing.
