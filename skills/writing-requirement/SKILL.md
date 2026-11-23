---
name: writing-requirement
description: Writes product requirements top down, from the vision, before any design or code. Produces an epic with a problem story, an actor and job story, a measurable outcome, no-gos, constraints, journeys, and numbered requirements that each have a fit criterion that can fail and names no solution; then cuts them into releasable rounds. Use when asked to write, review or change requirements, epics, journeys, user stories, acceptance criteria, a PRD or a release scope, or when someone describes a feature in technical terms that must become a need.
---

# Writing requirements

A requirement says **what** a person needs and **why**. It never says **how**. Screens, buttons, tools,
technologies and data formats belong to the design, which comes later and may meet the need in a way nobody
thought of yet. If only one design can meet a line, that line is a solution, not a requirement
(Torres, opportunity solution trees).

Write top down: from the vision of what the product must be, not from what the product does today. Today's
code is an input only when the build is planned. A requirement that follows a limit of today's product
("up to 3 variants") pulls the product toward that limit.

## The shape

One file per epic (template: [template.md](template.md)). Frontmatter gives the epic in 10 seconds; the text
below it is the agreed text and wins over the frontmatter.

**An epic** is a goal of an actor, not a part of the system ("Get new ads made", not "Video pipeline").
It has:

- **Summary.** At most 150 words in plain language (ASD-STE100: short sentences, one idea each, active
  voice, common words). What changes for the person, the rules one line each, what the reader must decide.
  The approver reads this first; the detail follows for the builders.
- **Problem.** One real story of why the work is hard today. No screen, tool or technology names.
- **Actor and job.** A named role with an example person ("Mai, the project lead of a game"), never "a
  user". A job story: "When ... I want to ... so I can ..." (Klement, via Intercom).
- **Outcome.** What changes for the actor, with a number that can be measured.
- **No-gos.** What this epic will never include. (A requirement for later is *deferred*, not a no-go.)
- **Constraints.** A mechanism imposed from outside (a law, a contract, a system the actor must use) is
  not a design choice: write it as a constraint, with who imposes it (Volere, ISO/IEC/IEEE 29148 keep
  constraints apart from needs).
- **Words.** Terms with one meaning each, used the same way in requirements, design and code (Evans,
  Domain-Driven Design: ubiquitous language).
- **Journeys.** The paths that together give the outcome.

**Never invent facts.** If the person gives no real story or no baseline number, ask. If there is still
none, write it as an assumption and say how it will be measured.

**A journey** has one actor and one scenario (NN/g). It has a **need**, a **trigger**, a **success end** and
**failure ends**. It starts and ends outside the screen. Two roles in one journey means two journeys. A
journey with more than about 12 requirements is too big: split it (Example Mapping). Journey 0 holds the
rules for every journey of the epic, including quality rules such as privacy, access and speed.

**A requirement** has an id, one need, and a **fit criterion**: a check that a person can see, that can
fail, and that names no mechanism (Volere fit criteria; ISO/IEC/IEEE 29148: necessary, singular,
verifiable, implementation-free). A requirement takes its actor and reason from its journey's need; name
them in the line only when they differ.

```
E4.1.10  Mai gets a first result while she still waits.
         Fit: the first new ad is ready within 5 minutes of the ask, in 9 of 10 asks.
E4.1.11  Asking for many ads costs Mai little more time than asking for one.
         Fit: 10 ads take at most 1.5 times as long as 1 ad.
```

**Ids** are `E<epic>.<journey>.<n>`. Numbers may change while a journey is in review; once it is agreed they
are frozen, because design and tests cite them. A new requirement takes the next free number. A removed
number is never used again. After agreement, a text fix keeps the id; a changed need retires the id, takes
a new one, and goes in the decisions log.

Mark every **assumption** as an assumption until someone checks it. A journey with an open question is not
ready.

## The steps

1. **Read what exists.** Earlier epics, the vision, the decisions, the words list. Do not re-ask what is
   already decided. If no vision is written, write three lines of vision first and get them agreed.
2. **Interview in short, numbered questions, each with your pick and its reason.** The person can then
   answer "1. yes 2. no, because ...". When a word is unclear ("strategy"), give a real example from the
   domain first. Ask only what needs the person's judgment: product direction, scope, taste, money.
   **Decide common-sense questions yourself** (permissions, retention, standard flows) by how established
   products do it; write the decision and who made it in the decisions log.
3. **Turn solution talk into need.** People often speak in mechanisms ("an @ to find a file", "OAuth to
   Drive", "a Remake button"). Ask what that lets them do and why, write that, and keep the mechanism as a
   design note. Keep it as a constraint only if it is truly imposed from outside. Do not ask design
   questions (formats, defaults, layouts) now; note them for the design stage.
4. **Fill the epic** in the order of the shape above, Summary last (it summarizes what is there).
5. **Check each line against the anti-patterns** in [anti-patterns.md](anti-patterns.md). Rewrite every
   line that shows one.
6. **Make it smaller.** Find overlaps with other epics; join or move lines rather than add new ones.
7. **Cut the round** (below). Give every requirement its round; write the deferred list.
8. **Completeness review by a fresh reader.** Give a reviewer with no context (a new subagent, read only)
   the files and the prompt in [review-prompt.md](review-prompt.md), not your conclusions. Fix what it
   finds. Repeat with a new reviewer each pass until it finds nothing that blocks, or stop after 3 passes
   and report what is open. If no fresh reviewer is available, say plainly that no fresh review was done.
9. **The approver agrees.** Set `status: agreed`, freeze the ids, log the date. Design starts only now.
   With no approver available, stop at `in-review`, list what needs a person's decision, and never set
   `agreed` yourself.

**Scale it.** A small change to an existing epic: add lines to its journey and do steps 3, 5 and 8 only.
A project with no rounds: use its own release unit (a milestone, a version), or skip step 7 but still
write the deferred list.

Later, each fit criterion becomes a test, and each core journey becomes one end-to-end test in the actor's
words (Vocke, *The Practical Test Pyramid*).

## Rounds: cut by outcome, not by priority list

A **round** is a testable product with one goal: the requirements that must be built and released
together. It is a *minimum viable business*, not only a minimum viable product: the whole offer, so that
the people behind the product can also run it (give access, pay and cap spend, support, see that it works,
fix it, learn from records). Each later round is a layer on a whole that works and leaves a whole that works.

**The round test** for each requirement (DSDM MoSCoW, MUST = Minimum Usable SubseT):
*"If this is not in the round, can we still offer the product and run it?"*

- **No:** it is in the round.
- **Yes:** it is **deferred**: the need is not met this round. Write its round (or `later`), the reason,
  and the workaround until then (who does what by hand, or that nobody does).

A line is not in a round only because it is nice, and not out of a round only because it is hard. The
outcome sets the round: do not cut what the outcome needs to make the round smaller. If every line passes
the round test, the outcome is too large (DSDM keeps Musts to about 60% of the effort).

**In the round, by hand** is different from deferred: the need *is* met this round, by a script or a
manual step instead of product screens, and its fit criterion is checked against that way (mark it
`round: 1, by_hand: "<who does what>"`). It gets its product screens in a later round.

A round is complete when:

1. **Each actor gets to the end.** Walk the journeys in order, as each actor, from first touch to the
   outcome (the backbone of Patton's story map; the smallest *successful* release, more than a walking
   skeleton).
2. **The business can run it.** Check the three layers of a service blueprint: front stage (what the actor
   does and sees), back stage (what the system does for it), support (what the business does to run it).
3. **It has one outcome sentence with a number,** and every requirement in it serves that outcome.
4. **The deferred list is written,** each item with its round and what happens until then.

## Traps

| Trap | Do this instead |
|---|---|
| Gap-checking the epic against today's code | Requirements come from the vision; code is for build planning |
| Copying the person's mechanism into the line | Write the need; keep the mechanism as a design note, or a constraint if imposed |
| Inventing a story or a baseline number | Ask; else write an assumption and how it will be measured |
| Reviewing your own epic and finding it fine | A fresh reviewer with no context, a new one each pass |
| Long text the approver must read first | The 150-word Summary on top |
| Setting `agreed` with no approver | Stop at `in-review` and list the open decisions |

## Sources

Patton, *User Story Mapping*; Cockburn, *Writing Effective Use Cases*; ISO/IEC/IEEE 29148; Robertson and
Robertson, Volere requirements template (fit criteria, constraints); INCOSE *Guide for Writing
Requirements* (no vague words); Wynne, Example Mapping (Cucumber); Alan Klement, job stories (Intercom
blog); NN/g on journey mapping and service blueprints; Shape Up ch. 6 (problem, no-gos); Teresa Torres,
opportunity solution trees; DSDM MoSCoW; Evans, *Domain-Driven Design*; Vocke, *The Practical Test
Pyramid*; ASD-STE100 Simplified Technical English.
