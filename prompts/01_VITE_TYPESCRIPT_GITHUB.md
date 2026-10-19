# Assignment 01 — Vite + React + TypeScript + GitHub Baseline

## Goal
Create the smallest clean React + TypeScript + Vite repository baseline for the `rg/dev` portfolio. Do not implement the portfolio UI yet.

## Human setup commands
Run these in the terminal from the parent directory where the project should live:

```bash
npm create vite@latest rg-dev-portfolio -- --template react-ts
cd rg-dev-portfolio
npm install
npm run dev
```

Open the local URL Vite prints and confirm the starter page loads. Stop the server with Ctrl+C.

Then add the supplied `specs/` and `prompts/` documents to the repository. Update the README as described below. Inspect the generated `.gitignore` before staging anything.

## Qwen task

You are editing an existing Vite React TypeScript starter. Keep the task deliberately small.

### Allowed changes
- Replace `README.md` with a concise project README.
- Add the `specs/` and `prompts/` documents supplied by the developer if they are not already present.
- Make only minimal cleanup changes to the starter page if needed to make its purpose clear, but do not build the actual portfolio design.

### Forbidden changes
- Do not add dependencies.
- Do not add React Router, Three.js, Tailwind, a component library, animation packages, a backend, or a contact form service.
- Do not create portfolio components yet.
- Do not delete or rewrite Vite/TypeScript configuration without a concrete issue.
- Do not add fake project URLs, credentials, or personal contact information beyond the values explicitly in the project spec.

### README must contain
- Project name: `rg/dev Portfolio`.
- One-sentence purpose.
- Requirements: Node.js LTS and npm.
- Setup commands: `npm install`, `npm run dev`.
- Quality commands: `npm run build`, `npm run lint` (only if the scaffold has the script).
- Link/list of `specs/PROJECT_SPEC.md`, `specs/ARCHITECTURE.md`, and `specs/QWEN_WORKFLOW.md`.
- Note that Three.js is a later milestone and is not part of the initial scaffold.
- Open-source contribution note: issues and pull requests are welcome; contributors should run the build before submitting.

### Output contract
Return only:
1. A short summary.
2. Exact file paths changed.
3. Patch or complete contents of changed small files.
4. Commands the developer should run to verify the result.
5. Any assumptions.

Do not claim tests passed unless the developer ran them. Do not generate more than 3 changed code/config files; documentation files do not count if they are the supplied spec files.

## Developer verification

```bash
npm run lint
npm run build
npm run dev
```

Run `npm run lint` only if the generated `package.json` defines it. Verify the starter page loads, `git diff` is understood, and no secrets or generated files are staged.

## GitHub steps (developer, not Qwen)

1. Create a new empty GitHub repository named `rg-dev-portfolio` (do not initialize it with a second README or license if local files already exist).
2. Locally:

```bash
git init
git add .
git commit -m "chore: scaffold Vite React TypeScript app"
git branch -M main
git remote add origin https://github.com/<YOUR_GITHUB_USERNAME>/rg-dev-portfolio.git
git push -u origin main
```

3. Replace `<YOUR_GITHUB_USERNAME>` with the actual GitHub username. Never paste a personal access token into code, prompts, or remote URLs.
4. Open the GitHub repository and confirm the files and first commit are visible.
5. Add a license only after choosing one deliberately. For a permissive portfolio repository, MIT is a common option, but the owner should make the choice.
