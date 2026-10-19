# Architecture and File Boundaries

## Proposed structure after the initial scaffold

```text
rg-dev-portfolio/
├── public/
│   ├── favicon.svg
│   └── images/
├── src/
│   ├── app/
│   │   ├── App.tsx
│   │   └── routes.tsx              # only when routing is added
│   ├── components/
│   │   ├── layout/
│   │   │   ├── SiteHeader.tsx
│   │   │   ├── SiteFooter.tsx
│   │   │   └── Container.tsx
│   │   ├── home/
│   │   │   ├── HeroSection.tsx
│   │   │   ├── JourneySection.tsx
│   │   │   ├── JourneyChapter.tsx
│   │   │   ├── AboutSection.tsx
│   │   │   └── ContactSection.tsx
│   │   ├── projects/
│   │   │   ├── ProjectList.tsx
│   │   │   └── ProjectRow.tsx
│   │   └── motion/
│   │       └── Reveal.tsx
│   ├── features/
│   │   └── hero-scene/
│   │       ├── HeroScene.tsx
│   │       ├── HeroSceneFallback.tsx
│   │       └── useReducedMotion.ts
│   ├── data/
│   │   ├── journey.ts
│   │   └── projects.ts
│   ├── styles/
│   │   ├── tokens.css
│   │   └── global.css
│   ├── types/
│   │   └── portfolio.ts
│   └── main.tsx
├── specs/
├── prompts/
├── .gitignore
├── README.md
├── package.json
├── tsconfig.json
└── vite.config.ts
```

This is a target structure, not a demand to create every file at once. Introduce each file only when its task starts.

## Component contracts

- `SiteHeader`: navigation only; no journey data or WebGL logic.
- `HeroSection`: title, subtitle, scroll cue, and a lazy-loaded visual slot. It must still render if the scene fails.
- `HeroScene`: owns canvas/scene behavior only. No site navigation, text content, or global theme changes.
- `JourneySection`: maps typed journey data to `JourneyChapter` components and coordinates the active chapter theme.
- `JourneyChapter`: renders one chapter and reports no global side effects itself.
- `AboutSection`: introduction and hobbies line; resets the page theme to default via a clearly defined parent-level mechanism.
- `ProjectList`: maps typed project data to rows.
- `ProjectRow`: presentation of one project; no data fetching.
- `Reveal`: optional reusable intersection-based reveal; obeys reduced motion and disconnects its observer.

## Data contracts (later task)

```ts
export interface JourneyChapterData {
  id: 'banking' | 'iot' | 'kitchen' | 'robotics' | 'now';
  period: string;
  category: string;
  headline: string;
  description: string;
  proof: string;
  theme: {
    background: string;
    accent: string;
  };
}

export interface ProjectData {
  id: string;
  number: string;
  title: string;
  description: string;
  technologies: string[];
  href?: string;
}
```

Do not implement these interfaces in the initial scaffold task. They are for the later data-model task.

## Dependency policy

Add a dependency only when a named task needs it. Keep the initial Vite scaffold close to the official template. Add routing, icon packages, animation libraries, and Three.js in separate reviewed commits, not all at project creation.
