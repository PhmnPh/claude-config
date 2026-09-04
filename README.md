# claude-config

Personal Claude Code skills. Cloned into `~/.claude` on every machine.

```bash
git clone --recurse-submodules git@github.com:PhmnPh/claude-config.git ~/.claude-config
rsync -a ~/.claude-config/ ~/.claude/
```

Or, on a fresh machine before Claude Code creates `~/.claude`:

```bash
git clone --recurse-submodules git@github.com:PhmnPh/claude-config.git ~/.claude
```

`vendor/humanizer-ru` is a submodule tracking https://github.com/Vladimir-Human/humanizer-ru. Update it with `git submodule update --remote --merge`. `skills/humanizer-ru` is a thin wrapper with `disable-model-invocation: true`, so the skill stays out of the model prompt and runs only on `/humanizer-ru`.

Team skills live in the ml-dev plugin repo, not here. A skill moves there once it has proven useful.

## Codex

Codex reads the same SKILL.md format from `~/.codex/skills`. Symlink each skill there once:

```bash
for d in ~/.claude/skills/*/; do ln -sfn "$d" ~/.codex/skills/$(basename "$d"); done
```

Claude Code subagents live in `agents/`; Codex has no such directory, so `comment-sicko` also exists as a skill and is delegated to with `$comment-sicko`.
