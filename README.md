# Agent skills

Personal skills for Claude Code and Codex.

## Layout

```text
claude/
├── agents/
└── skills/

codex/
└── skills/
```

Keep shared behavior aligned across both skill trees. Put Claude-specific
frontmatter and Agent tool instructions under `claude/`. Put Codex-compatible
frontmatter and subagent instructions under `codex/`.

## Install for Claude Code

Link each Claude skill into `~/.claude/skills` and each agent into
`~/.claude/agents`.

```bash
mkdir -p ~/.claude/skills ~/.claude/agents
for directory in "$PWD"/claude/skills/*/; do
  ln -sfn "$directory" ~/.claude/skills/"$(basename "$directory")"
done
for file in "$PWD"/claude/agents/*.md; do
  ln -sfn "$file" ~/.claude/agents/"$(basename "$file")"
done
```

## Install for Codex

Link each Codex skill into `~/.codex/skills`.

```bash
mkdir -p ~/.codex/skills
for directory in "$PWD"/codex/skills/*/; do
  ln -sfn "$directory" ~/.codex/skills/"$(basename "$directory")"
done
```

Restart or open a new task after changing installed skills.
