# Agents

Skills live in `skills/<category>/<skill>/SKILL.md`, with reference files beside them. Every skill listed in `.claude-plugin/plugin.json` must exist on disk, and every skill on disk must be listed there.

When editing a skill, keep `SKILL.md` to the steps and push reference into sibling files linked from the step that needs them. Bump `version` in `plugin.json` and add a line to `CHANGELOG.md`.
