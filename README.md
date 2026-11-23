# skills

Agent skills in the [Agent Skills](https://platform.claude.com/docs/en/agents-and-tools/agent-skills/overview)
format: one folder per skill, a `SKILL.md` with `name` and `description`, and files it loads only when needed.

| Skill | Command | What it does |
|---|---|---|
| [writing-requirement](skills/writing-requirement/SKILL.md) | `/lagz0ne:writing-requirement` | Writes product requirements top down, before design: epics, journeys, requirements with fit criteria that can fail and name no solution, cut into releasable rounds. |

## Install

Claude Code ([plugins](https://code.claude.com/docs/en/plugins)):

```
/plugin marketplace add lagz0ne/skills
/plugin install lagz0ne@lagz0ne-skills
```

Or copy a skill folder into `~/.claude/skills/` (personal) or `.claude/skills/` (one project).

## License

MIT
