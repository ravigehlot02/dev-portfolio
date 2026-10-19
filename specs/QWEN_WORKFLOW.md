# Qwen 14B Workflow: Small Patches, Not Whole-Website Telepathy

## Operating principle

Treat Qwen as a junior pair programmer with a short working memory. Give it one narrow task, a small amount of context, and an explicit output contract. The human developer owns architecture, review, testing, and integration.

## Rules for every task

1. One task should normally touch no more than 1–3 files.
2. Ask for a plan of at most 5 bullets before code when a task has multiple steps.
3. Ask for complete contents only for new or very small files. For existing files, ask for a focused diff or exact replacement region.
4. Never ask Qwen to invent existing file contents. Paste the current file when edits depend on it.
5. Do not let it rename files, add packages, restructure folders, or change configuration unless the task explicitly allows it.
6. Require TypeScript types and explicit error handling where relevant. Avoid `any`; if it proposes `any`, it must justify why.
7. Ask it to list assumptions and files changed. If it lacks context, it must ask for the missing file rather than guessing.
8. Integrate one patch, run checks, inspect the browser, and commit before moving on.
9. Keep one source of truth for tokens, journey content, and project content.
10. Never paste secrets, access tokens, private keys, or `.env` values into prompts or Git.

## Standard response contract for Qwen

Ask Qwen to return:

- **Purpose:** one sentence.
- **Files changed:** exact paths.
- **Patch:** code only for those files, with no unrelated edits.
- **Checks:** commands to run and expected result.
- **Assumptions / risks:** short list, or “None”.

For a coding task, do not accept a giant essay followed by several unrelated files. If the answer is too large, split the task.

## Human verification loop

For each task:

1. Read the patch before applying it.
2. Apply only the requested changes.
3. Run `npm run build` and any task-specific checks.
4. Start the dev server and inspect the affected behavior at desktop and mobile sizes.
5. Check the browser console and terminal.
6. Review `git diff`.
7. Commit with a message describing one logical change.

## Git conventions

- Branches: `feat/<small-task>`, `fix/<issue>`, `docs/<topic>`.
- Commits: `chore: scaffold Vite React TypeScript app`, `docs: add portfolio implementation spec`, `feat: add site header`.
- Avoid committing broken intermediate work to `main`.
- Do not commit `node_modules`, `dist`, `.env`, IDE caches, or OS metadata.

## Prompt context budget

For each task, send only:
1. Relevant paragraph from `PROJECT_SPEC.md`.
2. Relevant file contract from `ARCHITECTURE.md`.
3. Current contents of the file(s) being edited.
4. The exact task prompt.

Do not send the entire project history every time. Humans invented context windows and then immediately filled them with noise.
