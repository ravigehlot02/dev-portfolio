# rg/dev — Developer Portfolio

A personal developer portfolio built with **React, TypeScript, and Three.js** to showcase my engineering journey, selected projects, and work across backend systems, distributed applications, and applied AI.

The portfolio combines a minimal dark interface with chapter-based visual themes, subtle motion, and an interactive 3D hero.

> **Status:** Under active development.

## Overview

The portfolio is designed around five chapters of my professional journey:

- **Banking:** Reliable data pipelines and nightly processing systems.
- **IoT:** MQTT telemetry and industrial generator monitoring.
- **Cloud Kitchen:** Operational software, POS, and inventory management.
- **Robotics:** Vendor-agnostic material tracking and asynchronous telemetry.
- **Applied AI:** Retrieval-augmented generation (RAG) and hybrid information retrieval.

A separate Projects page will present selected work, its technical architecture, and relevant implementation details.

## Planned Features

- Responsive layouts for desktop, tablet, and mobile.
- Minimal dark interface with reusable design tokens.
- Chapter-specific themes that change as visitors scroll.
- Animated section reveals using the Intersection Observer API.
- Interactive 3D hero using Three.js and React Three Fiber.
- Static fallback for the 3D visual.
- Reduced-motion support for accessibility.
- Dedicated project listings and optional case-study pages.
- Links to GitHub, LinkedIn, and email.

Features will be implemented incrementally and documented as they become available.

## Technology Stack

| Technology | Purpose |
|---|---|
| React | Component-based user interface |
| TypeScript | Type-safe application code |
| Vite | Development server and production build |
| CSS | Design tokens, responsive layouts, and themes |
| Three.js | 3D rendering |
| React Three Fiber | React integration for Three.js |
| Git and GitHub | Version control and collaboration |

Additional libraries will be introduced only when a specific feature requires them.

## Design System

The initial design is based on a small set of reusable color tokens.

| Token | Value |
|---|---|
| Background | `#0A0E14` |
| Surface | `#111826` |
| Border | `#1F2937` |
| Primary text | `#E6EDF3` |
| Muted text | `#9AA7B8` |
| Cyan accent | `#38BDF8` |
| Violet accent | `#8B5CF6` |

**Typography**
- Space Grotesk for headings.
- JetBrains Mono for technical labels and tags.
- System sans-serif fallbacks for body text.

**Layout**
- Maximum content width: 1160px.
- Default page gutter: 32px.
- Section spacing: 96px.
- Card gap: 24px.
- Card radius: 16px.

Chapter themes will use CSS custom properties to keep the styling reusable and maintainable.

## Getting Started

### Prerequisites

Install the following before starting:

- Node.js with npm.
- Git.
- Visual Studio Code or another editor.

### Installation

Clone the repository:

```bash
git clone <YOUR_GITHUB_REPOSITORY_URL>
cd rg-dev-portfolio
```

Install dependencies:

```bash
npm install
```

Start the development server:

```bash
npm run dev
```

Vite will print the local development URL in the terminal.

### Build for Production

Run the production build:

```bash
npm run build
```

Preview the production build locally:

```bash
npm run preview
```

Run these commands from the project root.

## Project Structure

The application structure will evolve as features are added. The intended organization is:

```text
rg-dev-portfolio/
├── public/                 # Static assets
├── src/
│   ├── components/         # Reusable UI components
│   ├── sections/           # Page sections
│   ├── data/               # Typed portfolio content
│   ├── styles/             # Design tokens and global styles
│   ├── three/              # 3D components and scene logic
│   ├── App.tsx             # Application composition
│   └── main.tsx            # Application entry point
├── specs/                  # Project specifications
├── prompts/                # Small implementation tasks
├── index.html
├── package.json
├── tsconfig.json
├── vite.config.ts
└── README.md
```

Directories will be added when they are needed. The structure above describes the target organization, not a claim that every directory already exists.

## Development Workflow

This repository uses a feature-branch workflow.

1. Start from an up-to-date `main` branch.
2. Create a branch for one feature or task.
3. Implement a small, focused change.
4. Run the relevant checks.
5. Review the diff and commit the changes.
6. Push the branch and open a pull request.
7. Merge into `main` after review and verification.

Example:

```bash
git switch main
git pull origin main
git switch -c feat/design-tokens
```

After making and testing the changes:

```bash
npm run build
git status
git diff
git add <FILES_TO_COMMIT>
git commit -m "feat: add portfolio design tokens"
git push -u origin feat/design-tokens
```

Use the actual changed file paths in place of `<FILES_TO_COMMIT>`.

## Working with AI Coding Tools

AI coding assistants, including local Qwen models, may be used to generate small implementation patches.

The development approach prioritizes:

- One bounded task at a time.
- Explicit file boundaries and acceptance criteria.
- Small, reviewable changes.
- Manual inspection of generated code.
- Verification before merging.
- Minimal dependencies and a clear component architecture.

AI-generated code is reviewed and tested before it becomes part of the main branch.

## Deployment

The intended deployment target is a static hosting platform such as Cloudflare Pages, GitHub Pages, Netlify, or Vercel.

The final platform will be selected after the application structure and routing strategy are established.

## Contributing

This project is being developed in the open.

Bug reports, suggestions, and improvements are welcome. Before contributing, please check the existing specifications and open issues to avoid duplicating work.

For substantial changes, open an issue or discuss the proposed approach before submitting a pull request.

## License

A license has not yet been selected. Until a license is added to the repository, permission to reuse, modify, or redistribute this project's code should not be assumed.

## Contact

**Ravi Gehlot**

- GitHub: [@ravigehlot02](https://github.com/ravigehlot02)
- Email: [ravigehlot02@gmail.com](mailto:ravigehlot02@gmail.com)

LinkedIn and other professional links can be added when their final URLs are available.
