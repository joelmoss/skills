# skills

Personal agent skills for Claude Code and Codex, in the shared `SKILL.md` format.

## Install

```sh
npx skills add joelmoss/skills -g -a claude-code -a codex
```

To edit in place on this machine, install from the local checkout instead, so the
installed skills link back to this working copy:

```sh
npx skills add ~/dev/skills -g -a claude-code -a codex
```

## Layout

Each skill is a folder under `skills/` holding a `SKILL.md` with `name` and
`description` frontmatter.
