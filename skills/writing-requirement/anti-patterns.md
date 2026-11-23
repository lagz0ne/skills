# Anti-patterns

An epic, journey or requirement that shows one of these is rewritten before review. The
rows mix levels: "no real actor" and "no outcome" are checked on the epic and the journey; a requirement
takes its actor and reason from its journey.

| Anti-pattern | Test | Bad | Good |
|---|---|---|---|
| Solution in the requirement | Only one design could meet it | "A Remake button on the hook part" | "The lead can get new variants of the part of an ad that loses viewers" |
| No real actor | It says "a user" | "As a user ..." | "Mai, the project lead of a game" |
| No outcome | No "so that", no number | "The lead can make variants" | "... so that a campaign has fresh ads every week" |
| By system part | An epic per service or screen | "Video pipeline epic" | "Get new ads made" |
| Clicks as steps | The step names a control | "Click Run, then Keep" | "Mai keeps the ad she likes" |
| Cannot fail | No one can show it false | "The ads are good" | "Each ad carries the strategy the lead asked for" |
| Many actors | Two roles in one journey | "The lead and the owner approve ..." | One journey each |
| Vague words | fast, easy, nice, intuitive, robust | "Ads come fast" | "The first new ad within 5 minutes" |
| Written after the code | Describes what was built | "The plan card shows the total" | The need first, then the design |
| Bottom up | Follows a limit of today's product | "Up to 3 variants per ask" | "The lead decides how many ads" |
| Product only | No one can run it | "The lead gets ads made" (no one gives access or caps spend) | The round also has the access, spend and support the business needs |
| Nice to have in the round | The round test says it can wait | "Round 1 has a dark theme" | "Deferred to round 2: dark theme" |
| Two needs in one line | "and" joins two checks that can pass apart | "She can undo and restore for 30 days" | Two requirements, each with its own fit |
| Design question at requirement time | Asks about a format, default or layout | "Which date format?" | Note it for the design stage; write the need it serves |
| Constraint lost | A mechanism imposed from outside is dropped as "solution" | (the accounting tool she must use is gone) | "Constraint: invoices reach her accounting tool (imposed by the finance team)" |

## Quick self-check for one line

1. Could two very different designs both meet it? (If no: solution.)
2. Does it, or its journey, name a real actor and a reason?
3. Could a person watching the product show the fit criterion false?
4. Is every adjective backed by a number or an observable fact?
5. Does it hold one need only?
