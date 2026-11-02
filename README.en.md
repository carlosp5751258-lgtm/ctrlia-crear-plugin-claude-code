# commit-en: your first Claude Code plugin

[Leer en español](README.md)

The Spanish version (the `commit-es` plugin) is in the repository root and in [README.md](README.md); the English plugin, `commit-en`, is in `en/`.

`commit-en` is a Claude Code plugin that writes commit messages in English in the Conventional Commits format from your staged changes (`git diff --cached`). It is the complete example from the "Create a Claude Code plugin" recipe: manifest, skill, eval and marketplace, all in this repository's `en/` folder.

- Recipe in English: https://ctrlia.dev/en/recetas/crear-plugin-claude-code.html
- Receta en español: https://ctrlia.dev/recetas/crear-plugin-claude-code.html

## Install

```bash
git clone https://github.com/carlosp5751258-lgtm/ctrlia-crear-plugin-claude-code.git
claude plugin marketplace add ./ctrlia-crear-plugin-claude-code/en
claude plugin install commit-en@ctrlia-en
```

Then, in a repository with staged changes (`git add`), type `/commit-en:message` or ask "write the commit". The skill can only run `git diff` and `git status`, and it never runs `git commit`: it gives you the message and you decide.

To try it without installing anything, clone the repository and use `claude --plugin-dir ./ctrlia-crear-plugin-claude-code/en`.

## What's inside

| Path | What it is |
| --- | --- |
| `en/.claude-plugin/plugin.json` | Manifest: name `commit-en`, version, author and license |
| `en/.claude-plugin/marketplace.json` | The `ctrlia-en` marketplace that publishes this same folder (`source: "./"`) |
| `en/skills/message/SKILL.md` | The `/commit-en:message` skill |
| `en/evals/commit-rename/` | A `claude plugin eval` case with `regex`, `tool_used` and `llm` graders |

## Validate and evaluate

```bash
cd ctrlia-crear-plugin-claude-code/en
claude plugin validate .
# Cheap eval while iterating (each run is a real model call and uses your plan)
claude plugin eval . --runs 1 --ablation none --model haiku --max-cost-usd 0.5 --no-publish
```

## What was tested

With Claude Code **2.1.316** on Linux, with a temporary `HOME` and `CLAUDE_CONFIG_DIR`: `claude plugin validate .` passes (with the Anthropic directory warning about the missing icon, which does not prevent using it), and the marketplace can be added and installed from a local folder. The skill and the eval were tested on the Spanish version while preparing the recipe; the English copy in `en/` passes `claude plugin validate .`, but its eval has not been run. Installing from GitHub has not been tested yet.

## License

MIT. See [LICENSE](LICENSE).

---
Part of **[Ctrl+IA](https://ctrlia.dev/en/)**: code with Claude Code like a pro. Made by Carlos P.
