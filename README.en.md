# commit-es: your first Claude Code plugin

[Leer en español](README.md)

`commit-es` is a Claude Code plugin that writes commit messages in Spanish in the Conventional Commits format from your staged changes (`git diff --cached`). It is the complete example from the "Create a Claude Code plugin" recipe: manifest, skill, eval and marketplace, all in this repository.

- Recipe in English: https://ctrlia.dev/en/recetas/crear-plugin-claude-code.html
- Receta en español: https://ctrlia.dev/recetas/crear-plugin-claude-code.html

## Install

```bash
claude plugin marketplace add carlosp5751258-lgtm/ctrlia-crear-plugin-claude-code
claude plugin install commit-es@ctrlia
```

Then, in a repository with staged changes (`git add`), type `/commit-es:mensaje` or ask "escribe el commit". The skill can only run `git diff` and `git status`, and it never runs `git commit`: it gives you the message and you decide.

To try it without installing anything, clone the repository and use `claude --plugin-dir ./ctrlia-crear-plugin-claude-code`.

## What's inside

| Path | What it is |
| --- | --- |
| `.claude-plugin/plugin.json` | Manifest: name `commit-es`, version, author and license |
| `.claude-plugin/marketplace.json` | The `ctrlia` marketplace that publishes this same repository (`source: "./"`) |
| `skills/mensaje/SKILL.md` | The `/commit-es:mensaje` skill (instructions in Spanish) |
| `evals/commit-renombrado/` | A `claude plugin eval` case with `regex`, `tool_used` and `llm` graders |

## Validate and evaluate

```bash
claude plugin validate .
# Cheap eval while iterating (each run is a real model call and uses your plan)
claude plugin eval . --runs 1 --ablation none --model haiku --max-cost-usd 0.5 --no-publish
```

## What was tested

With Claude Code **2.1.316** on Linux, with a temporary `HOME` and `CLAUDE_CONFIG_DIR`: `claude plugin validate .` passes (with the Anthropic directory warning about the missing icon, which does not prevent using it), and the marketplace can be added and installed from a local folder. The skill and the eval were tested while preparing the recipe; installing from GitHub has not been tested yet.

## License

MIT. See [LICENSE](LICENSE).

---
Part of **[Ctrl+IA](https://ctrlia.dev/en/)**: code with Claude Code like a pro. Made by Carlos P.
