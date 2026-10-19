# Project Specification — rg/dev Portfolio

## 1. Goal

Build a responsive, polished portfolio for Ravi Gehlot using React, TypeScript, and Vite. The site should communicate backend engineering, systems work, and applied AI. The visual design is taken from the supplied five-page portfolio PDF. The repository is open source from the beginning.

## 2. Scope and page structure

### Home route
- Navigation: `rg/dev`, Journey, Projects, About, Contact.
- Availability indicator: “Open to full-time roles & freelance”.
- Hero: “Ravi Gehlot” and “Backend Engineer, Systems Builder, Applied AI”, plus a scroll cue.
- Journey: five career chapters, each with a date/period, category, short headline, concise summary, and proof/metric tag.
- About: short introduction and one quiet hobbies line: gardening and cooking.
- Contact: “Let’s build something reliable.”, email, GitHub, LinkedIn.

### Projects route
Use numbered rows and optional future case-study routes. Initial projects from the PDF:
1. Material Tracking Platform — FastAPI, RabbitMQ, PostgreSQL, MongoDB.
2. Brand-aware AI Content Platform — Python, ChromaDB, RAG.
3. EHR Extraction Pipeline — Python, Pandas, AWS S3.
4. Virtual Tour Platform — JavaScript, Marzipano.

Project copy must remain editable in a data file rather than duplicated across components. External project links should be configurable and must not be fabricated if unavailable.

## 3. Journey content from the PDF

1. **2016–2019 · Banking** — “Learned reliability the hard way.” Infosys; led a team of five on a Bank of America data pipeline under nightly SLAs. Proof tag: “Nightly batch window −25%”.
2. **2019–2022 · IoT** — “Teaching machines to talk.” MQTT telemetry at Power Plus Electricals, streaming live data from industrial generators to backend servers. Proof tag: “MQTT · real-time telemetry”.
3. **2022–2025 · Cloud kitchen** — “Ran a kitchen. Built its software.” Founded Combo Cosmos, a multi-brand cloud kitchen with seven brands, and built the POS/inventory app. Proof tag: “Food wastage −30%”.
4. **2025–2026 · Robotics** — “Coordinating robots from different vendors.” At Ati Motors, built a vendor-agnostic material tracking platform using RabbitMQ for async telemetry and MongoDB for per-vendor configurations. Proof tag: “New vendor, no schema rewrite”.
5. **NOW · Applied AI** — “Making retrieval reliable.” EHR pipelines for US hospitals and a RAG content platform with hybrid dense and BM25 retrieval. Proof tag: “RAG · hybrid retrieval”.

Keep claims and metrics as shown in the source design unless Ravi explicitly updates them. Do not invent additional claims.

## 4. Design tokens from the PDF

```css
:root {
  --color-bg: #0A0E14;
  --color-surface: #111826;
  --color-border: #1F2937;
  --color-text: #E6EDF3;
  --color-muted: #9AA7B8;
  --color-accent: #38BDF8;
  --color-violet: #8B5CF6;

  --color-banking-bg: #0F1B2D;
  --color-banking-accent: #6C8EBF;
  --color-iot-bg: #17130A;
  --color-iot-accent: #F5A524;
  --color-kitchen-bg: #1A0C09;
  --color-kitchen-accent: #FF4D2E;
  --color-robotics-bg: #06120F;
  --color-robotics-accent: #2EE6A6;
  --color-now-bg: #0A0E14;
  --color-now-accent: #38BDF8;

  --font-display: "Space Grotesk", sans-serif;
  --font-mono: "JetBrains Mono", monospace;
  --container-width: 1160px;
  --page-gutter: 32px;
  --section-space: 96px;
  --card-gap: 24px;
  --radius-card: 16px;
  --radius-button: 12px;
}
```

Typography: Space Grotesk display sizes 64 / 40 / 24 px; body 16–19 px with 1.6 line height; JetBrains Mono labels/tags 12–13 px, uppercase, letter spacing 0.12em.

Breakpoints specified in the PDF: 1280, 768, and 390 px. Use these as design checkpoints, not as a reason to create needless media queries.

## 5. Motion and 3D requirements

- Hero: react-three-fiber wireframe, lazy-loaded, slow rotation and pointer parallax.
- Provide a static SVG or CSS fallback if WebGL is unavailable or the 3D chunk has not loaded.
- Respect `prefers-reduced-motion`; do not animate the 3D scene or scroll reveals when reduced motion is requested.
- Reveal sections with a 24 px fade-up over 500 ms using IntersectionObserver; cards may stagger by 80 ms.
- Journey chapter theme changes when a chapter reaches 40% viewport intersection; transition over 600 ms. Return to default cyan theme in About and Contact.
- Clean up observers, event listeners, animation loops, and GPU resources on unmount.

## 6. Technical decisions

- React + TypeScript + Vite.
- Use npm unless the repository owner deliberately chooses another package manager before initial setup.
- React Router may be added when implementing the Projects route. Do not add routing before needed.
- Three.js stack: `three`, `@react-three/fiber`, and optionally `@react-three/drei` only when a specific helper is justified.
- Avoid a UI framework unless there is a concrete requirement. Prefer CSS modules or plain component CSS; choose one styling strategy and keep it consistent.
- Keep content data separate from presentation.
- No backend required for the initial static portfolio. Contact form integration is a later task; email and social links work without it.
- Hosting target: static host such as Cloudflare Pages, GitHub Pages, Netlify, or Vercel. Select one later; don't configure multiple providers unnecessarily.

## 7. Accessibility and quality

- Semantic landmarks: header, nav, main, section, footer.
- Keyboard-visible focus styles and usable navigation without a mouse.
- All meaningful images have alt text; decorative visuals are hidden from screen readers.
- Good contrast; never use color alone to convey chapter identity.
- Responsive from 390 px upward and avoid horizontal overflow.
- Links have meaningful names; external links use appropriate `rel` attributes when opening a new tab.
- No console errors, React key warnings, or TypeScript errors.

## 8. Out of scope for the first milestone

- All portfolio-specific UI components.
- Three.js / WebGL.
- Contact form service.
- Analytics, CMS, backend, authentication, or database.
- Deploy configuration.

## 9. Definition of done for the complete site

- Home and Projects routes work and match the supplied design direction.
- Journey has all five chapters and the correct theme behavior.
- Projects render from typed data.
- 3D hero loads lazily and has accessible/reduced-motion fallbacks.
- Responsive layout works at 390, 768, 1280, and wide desktop widths.
- `npm run build` succeeds and the browser console is clean.
- README documents setup, scripts, architecture, accessibility, and contribution workflow.
- Repository contains no secrets, personal tokens, or generated build output.
