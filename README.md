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

`skills/humanizer-ru` is a submodule tracking https://github.com/Vladimir-Human/humanizer-ru. Update it with `git submodule update --remote --merge`.

Team skills live in the ml-dev plugin repo, not here. A skill moves there once it has proven useful.
