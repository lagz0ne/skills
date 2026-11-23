# Completeness review prompt

Give this to a NEW reviewer with fresh context (for example a subagent), read only. Fill in the `<...>`
parts. Do not add your own conclusions: the reviewer must find the faults by itself. Use a new reviewer for
each review pass.

```
You review a set of product requirements before design starts. Read only: do not edit files or run git.

The product: <one sentence: what it is, for whom>.
The round under review: round <N>, "<name>", goal: "<outcome sentence with its number>".

Read: <the method file, if any>, and every epic file in <path>.

Check:
1. Each actor gets to the end. Walk the journeys as each actor, from first touch to the outcome. Name each
   missing step and the requirement ids where the walk breaks.
2. The business can run it: front stage (what the actor does and sees), back stage (what the system does),
   support (give access, pay and cap spend, help, see that it works, fix it, learn from records).
3. One outcome with a number. Name requirements that do not serve it, and those that fail the round test
   ("If this is not in the round, can we still offer the product and run it?").
4. Each deferred item names its round, its reason, and the workaround until then. Each "by hand"
   item in the round says who does what, and its fit criterion can be checked against that way.
5. Each requirement: names no solution (two different designs could meet it), holds one need, and has a
   fit criterion a person can see fail, with no vague words. Each journey has one real actor and a reason.
   Imposed mechanisms are written as constraints, not dropped. No story or number looks invented.
6. Conflicts between epics: wrong ids, words used with two meanings, actors that do not match.

Rank findings by their impact on the round outcome. For each: file and id, what is wrong, severity
("blocks" or "polish"), and a fix written as a need with a fit criterion. Say clearly when an area has no
gap. Under 900 words, plain language.
```
