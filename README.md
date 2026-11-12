# Skills for product engineers

Agent skills I use to ship UI that holds up in production: small, readable and easy to make your own. They work with Claude Code, Codex, Copilot and any agent that reads `SKILL.md`.

## ui-state-matrix

Every screen has more states than its happy path. `ui-state-matrix` finds them all and makes them clickable.

**One state per truth.** Every distinct thing the system can know (each API response, each pending write, each role) becomes its own state. Each state says what the person sees, the exact words, and the way out.

What it produces:

1. **A state matrix**: surfaces × states (loading, empty, error, success, pending and slow), plus offline, partial, disabled, roles, reduced motion and mobile when the flow has them.
2. **Opens and decisions**: what the product gets wrong today, with evidence, and the questions only the team can answer, each with a recommendation.
3. **Interactive boards**: one per surface, with a state switcher, in [Claude Design](https://claude.ai) when you have a canvas, or as a single HTML page when you don't.
4. **Motion that fits**: the design system's own tokens, once and stop, and a static version under reduced motion.

**[See an example board →](https://marcello0liveira.github.io/skills/)** (source: [`examples/file-upload.md`](examples/file-upload.md))

Try it:

```
Map every state of the checkout flow with ui-state-matrix.
```

## Install

Pick one per agent. Installing both gives you the skill twice.

<details open>
<summary><strong>Claude Code plugin</strong> (updates itself)</summary>

```bash
claude plugin marketplace add marcello0liveira/skills
claude plugin install mrcll-skills@mrcll
```

</details>

<details>
<summary><strong>skills.sh</strong> (copies editable files into your project)</summary>

```bash
npx skills add marcello0liveira/skills
```

</details>

<details>
<summary><strong>By hand</strong></summary>

Copy `skills/design/ui-state-matrix/` into `.claude/skills/` (or your agent's skills folder).

</details>

## How it compares

Checklists for loading, error and empty states already exist. This skill adds three things: it derives states from the API contract instead of a generic list, it records the exact copy and the way out for each one, and it ends in boards you can click through with your team.

## License

MIT · [Marcello Oliveira](https://mrcll.me)
