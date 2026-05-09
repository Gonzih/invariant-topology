# PLAN: Invariant Topology Hyperframes Demo

## Task Summary
Build a 6-scene, 30-second Hyperframes portrait demo (1080×1920) for "Invariant Topology: The Physics of Identity in Language State Space." The output is a single `hyperframes-demo/index.html` with GSAP animations, plus a rendered `demo.mp4` via Git LFS.

## Approaches Considered

### Approach A: Inline everything in one HTML file (chosen)
- All SVG, CSS, JS inline in index.html
- Pros: self-contained, no build step, easy to debug, required by Hyperframes
- Cons: large file, but fine for demo use

### Approach B: Separate CSS/JS files, bundled
- Would require a bundler
- Cons: Hyperframes likely expects a single HTML file for render; adds complexity

### Approach C: Use a framework (React/Vue) to generate HTML
- Overkill for a static demo
- Cons: requires build step, Hyperframes may not handle SPA well

## Chosen Approach
**Approach A** — single self-contained index.html with all inline CSS, GSAP from CDN, and SVG animations.

## Files to Touch
- `PLAN.md` (this file)
- `TODO.md`
- `hyperframes-demo/index.html`
- `hyperframes-demo/package.json` (from npm init -y)
- `.gitattributes` (git lfs tracking)
- `hyperframes-demo/demo.mp4` (rendered output via git lfs)

## Risks and Unknowns
- `hyperframes` npm package may not be available or may have different API than described
- `npx hyperframes check` validation rules may catch issues not anticipated
- `npx hyperframes render` requires a headless browser (Puppeteer/Chrome) — may fail in this env
- GSAP CDN load in headless render context — may need to ensure offline or cached version
- Git LFS must be installed on system
- The `window.__timelines = { main: tl }` requirement with `paused: true` is Hyperframes-specific
- Portrait aspect ratio 1080×1920 — verify all absolute positioning works
