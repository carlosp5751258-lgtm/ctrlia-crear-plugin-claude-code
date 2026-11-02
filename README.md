# commit-es: tu primer plugin de Claude Code

[Read in English](README.en.md)

English version: [README.en.md](README.en.md) (archivos en `en/`).

`commit-es` es un plugin de Claude Code que redacta mensajes de commit en español con formato Conventional Commits a partir de los cambios preparados (`git diff --cached`). Es el ejemplo completo de la receta «Crear un plugin de Claude Code»: manifiesto, skill, eval y marketplace, todo en este repositorio.

- Receta en español: https://ctrlia.dev/recetas/crear-plugin-claude-code.html
- Recipe in English: https://ctrlia.dev/en/recetas/crear-plugin-claude-code.html

## Instalar

```bash
claude plugin marketplace add carlosp5751258-lgtm/ctrlia-crear-plugin-claude-code
claude plugin install commit-es@ctrlia
```

Después, en un repositorio con cambios preparados (`git add`), escribe `/commit-es:mensaje` o pide «escribe el commit». La skill solo puede ejecutar `git diff` y `git status`, y nunca ejecuta `git commit`: te devuelve el mensaje y tú decides.

Para probarlo sin instalar nada, clona el repositorio y usa `claude --plugin-dir ./ctrlia-crear-plugin-claude-code`.

## Qué incluye

| Ruta | Qué es |
| --- | --- |
| `.claude-plugin/plugin.json` | Manifiesto: nombre `commit-es`, versión, autor y licencia |
| `.claude-plugin/marketplace.json` | Marketplace `ctrlia` que publica este mismo repositorio (`source: "./"`) |
| `skills/mensaje/SKILL.md` | La skill `/commit-es:mensaje` |
| `evals/commit-renombrado/` | Un caso de `claude plugin eval` con evaluadores `regex`, `tool_used` y `llm` |

## Validar y evaluar

```bash
claude plugin validate .
# Eval barato mientras iteras (cada ejecución es una llamada real al modelo y gasta de tu plan)
claude plugin eval . --runs 1 --ablation none --model haiku --max-cost-usd 0.5 --no-publish
```

## Qué se probó

Con Claude Code **2.1.316** en Linux, con `HOME` y `CLAUDE_CONFIG_DIR` temporales: `claude plugin validate .` pasa (con el aviso del directorio de Anthropic por falta de icono, que no impide usarlo), y el marketplace se añade e instala desde una carpeta local. La skill y el eval se probaron durante la preparación de la receta; la instalación desde GitHub no se ha probado todavía.

## Licencia

MIT. Ver [LICENSE](LICENSE).

---
Parte de **[Ctrl+IA](https://ctrlia.dev/)**: programa con Claude Code como un pro, en español. Hecho por Carlos P.
