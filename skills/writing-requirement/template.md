# Epic file template

Save as `docs/epics/<id>-<slug>.md` (or the project's own place). Flat frontmatter keys, one file per epic
(prior art: Jekyll/Hugo front matter, MADR `status`/`date`, Backstage `catalog-info.yaml`).

Status values: `draft` (being written), `in-review` (complete, waiting for the approver), `agreed` (the
approver agreed; ids frozen; design may start).

```markdown
---
id: E<n>
title: "<the actor's goal, in their words>"
actor: "<role> (example: <name>)"
status: draft
goal: "<the outcome sentence, with its number>"
updated: <YYYY-MM-DD>
journeys:
  - { id: E<n>.1, title: "<journey title>", status: draft }
requirements:
  - { id: E<n>.1.1, round: 1, short: "<a few words>" }
  - { id: E<n>.1.2, round: 1, by_hand: "<who does what, until product screens exist>", short: "<a few words>" }
deferred:
  - { what: "E<n>.1.3 <short>", round: <n or later>, reason: "<why it can wait>", until_then: "<workaround, or none>" }
no_gos:
  - "<what this epic never includes>"
constraints:
  - { what: "<the imposed mechanism or rule>", by: "<law, contract, or system that imposes it>" }
decisions:
  - { date: <YYYY-MM-DD>, by: "<person or agent>", what: "<the decision>" }
open:
  - "<question that blocks agreement>"
assumptions:
  - "<what we believe but have not checked, and how it will be checked>"
design_notes:
  - "<a mechanism someone proposed, kept for the design stage>"
sources:
  - "<prior art read for this epic>"
related: [<other epic ids>]
---

# E<n>: <title>

## Summary

<At most 150 words, plain language. What changes for the person. The rules, one line each. What the
approver must decide.>

## Problem

<One real story of why the work is hard today. No screen, tool or technology names.>

## Actor and job

<Role, example person.> When <situation>, I want to <motivation>, so I can <expected outcome>.

## Outcome

<What changes for the actor, with a number. If no baseline exists: an assumption, and how it will be
measured.>

## No-gos

- <...>

## Constraints

- <imposed mechanism or rule> (imposed by <...>)

## Words

| Word | Meaning |
|---|---|

## E<n>.0 Rules for every journey

| Id | Requirement | Fit criterion | Round |
|---|---|---|---|
| E<n>.0.1 | <a quality rule: privacy, access, speed ...> | <a check a person can see, that can fail> | 1 |

## E<n>.1 <Journey title>

- **Need:** <who needs what, and why>
- **Trigger:** <...>
- **Success end:** <...>
- **Failure ends:** <...>

| Id | Requirement | Fit criterion | Round |
|---|---|---|---|
| E<n>.1.1 | <one need> | <a check a person can see, that can fail> | 1 |
```
