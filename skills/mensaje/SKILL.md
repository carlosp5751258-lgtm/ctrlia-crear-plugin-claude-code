---
name: mensaje
description: Redacta el mensaje de commit de los cambios preparados (git diff --cached) en español y con formato Conventional Commits. Úsala cuando el usuario pida «escribe el commit», «mensaje de commit» o «haz el commit».
allowed-tools:
  - Bash(git diff *)
  - Bash(git status *)
---
1. Ejecuta `git diff --cached --stat` y `git diff --cached`.
2. Si no hay nada preparado pero el usuario describe el cambio, usa su descripción; si no hay ni una cosa ni la otra, dilo y para.
3. Escribe UNA línea de título de ≤ 72 caracteres: `tipo(ámbito): resumen` en español, en imperativo
   (tipos: feat, fix, docs, refactor, test, chore).
4. Deja una línea en blanco y, solo si el cambio no es obvio, 1-3 viñetas con el porqué.
5. Devuelve solo el mensaje, sin comentarios antes ni después. No ejecutes `git commit`.
