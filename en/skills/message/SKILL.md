---
name: message
description: Writes the commit message for the staged changes (git diff --cached) in English using the Conventional Commits format. Use it when the user asks to "write the commit", for a "commit message" or to "make the commit".
allowed-tools:
  - Bash(git diff *)
  - Bash(git status *)
---
1. Run `git diff --cached --stat` and `git diff --cached`.
2. If nothing is staged but the user describes the change, use their description; if there is neither, say so and stop.
3. Write ONE title line of ≤ 72 characters: `type(scope): summary` in English, in the imperative mood
   (types: feat, fix, docs, refactor, test, chore).
4. Leave a blank line and, only if the change is not obvious, 1-3 bullets explaining why.
5. Return only the message, with no comments before or after. Do not run `git commit`.
