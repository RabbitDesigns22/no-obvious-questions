# no-obvious-questions

**Stop the agent from asking what it already knows.**

`no-obvious-questions` is an agent skill for Claude Code (and any agent that reads `SKILL.md` skills). Agents ask out of habit: "Want me to push it?" right after you said push it. "Which folder is the logo in?" when the folder is one `ls` away. "Should I do it now or later?" Every one of those costs you a message, and it tells you the agent did not look.

## See the difference

> **You:** It passed review, push it.

**Without the skill:** "Should I push it to GitHub now? Once you confirm, I'll push and send you the link."

**With the skill:** it pushes, checks the commit and replies "pushed, commit abc123".

## What it does

Before any question, the agent runs it through 5 checks. If any check resolves it, the agent does the thing instead of asking:

1. Is the answer already in the conversation, the memory, the project's instructions or its files?
2. Can a tool find it?
3. Is it a logical or technical choice with one sensible option?
4. Is it permission for something already authorized?
5. Is it an obvious, riskless "do you also want me to...?"

Only real questions get through: facts only you have (prices, brand choices for a new client), irreversible or outward-facing steps nobody authorized, conflicting instructions, and human-only steps (codes, passwords, payments). They go out once, all together, each with the agent's recommendation. Your safety rules are never overridden.

| Request (same model, Haiku, one run each) | Questions without | With |
|---|---|---|
| "It passed review, push it" | 1 | 0 |
| "Make this week's reel for client X" | 3 | 0 |
| "New client, a spa, start their content" | 5 | 2 (the client-only ones: colors, real photos) |

**Status:** in daily use in the author's own setup. Plain instructions, no scripts, no network calls. MIT. Issues welcome.

**Skip it if** you want the agent to confirm every step with you.

## Install

With the [skills CLI](https://skills.sh):

```bash
npx skills@1.8.1 add https://github.com/RabbitDesigns22/no-obvious-questions/tree/8574703ec965e2388f90bf4ee8264f83b4aed45e
```

Or manually: copy `skills/no-obvious-questions/` into `~/.claude/skills/`.

## Español

**Que el agente no te pregunte lo que ya sabe.** Antes de cada pregunta revisa cinco cosas: si ya está la respuesta, si la puede buscar, si es una decisión lógica, si ya está autorizado o si es obvio y sin riesgo. Si cumple alguna, lo hace en vez de preguntar. Las preguntas que de verdad hacen falta salen juntas, una sola vez y con su recomendación.

Instalar: `npx skills@1.8.1 add https://github.com/RabbitDesigns22/no-obvious-questions/tree/8574703ec965e2388f90bf4ee8264f83b4aed45e`

## More skills from the same setup

This skill is one of 25 from a small agency that runs 20+ Claude Code sessions in parallel for real clients. All of them, with a short line on each: [RabbitDesigns22/claude-skills](https://github.com/RabbitDesigns22/claude-skills).

If it saved you a message, a star helps other people find it.

## License

MIT. Made by [Rabbit Designs](https://github.com/RabbitDesigns22).
