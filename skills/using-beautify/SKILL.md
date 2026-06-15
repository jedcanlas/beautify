---
name: using-beautify
description: Frontend design methodology for distinctive, production-grade UI — use when building any web component, page, or layout
---

# Beautify — Frontend Design Methodology

This skill guides creation of distinctive, production-grade frontend interfaces that avoid generic "AI slop" aesthetics. Implement real working code with exceptional attention to aesthetic details and creative choices.

The user provides frontend requirements: a component, page, application, or interface to build. They may include context about the purpose, audience, or technical constraints.

## Design Thinking

Before coding, understand the context and commit to a BOLD aesthetic direction:
- **Purpose**: What problem does this interface solve? Who uses it?
- **Tone**: Pick an extreme: brutally minimal, maximalist chaos, retro-futuristic, organic/natural, luxury/refined, playful/toy-like, editorial/magazine, brutalist/raw, art deco/geometric, soft/pastel, industrial/utilitarian, etc. There are so many flavors to choose from. Use these for inspiration but design one that is true to the aesthetic direction.
- **Constraints**: Technical requirements (framework, performance, accessibility).
- **Differentiation**: What makes this UNFORGETTABLE? What's the one thing someone will remember?

**CRITICAL**: Choose a clear conceptual direction and execute it with precision. Bold maximalism and refined minimalism both work - the key is intentionality, not intensity.

Then implement working code (HTML/CSS/JS, React, Vue, etc.) that is:
- Production-grade and functional
- Visually striking and memorable
- Cohesive with a clear aesthetic point-of-view
- Meticulously refined in every detail

## Committing to a Direction

Design Thinking picks the *what*; this is how you lock a direction concrete enough to execute and distinct enough to dodge the defaults.

- **Name the voice in three physical words.** Before choosing fonts or color, write three concrete, sensory adjectives — "warm, mechanical, opinionated" or "calm, clinical, careful" — never "modern" or "elegant." Check every later choice against these three.
- **Write a scene sentence.** One line of physical context: who uses this, where, under what light, in what mood. It should force the light/dark decision on its own — if it doesn't, add detail until it does.
- **Anchor to real references, not adjectives.** "Klim Type Foundry orange drench" beats "bold orange." Name actual products, type foundries, or brands you're steering toward.
- **Pick one color strategy per surface:** *Restrained* (a single saturated color, used sparingly — the restraint is the voice), *Committed* (a secondary color carrying ~30%), *Full palette* (a bold multi-color distribution), or *Drenched* (one dominant color owns 60%+ and is the brand). Don't drift between them on one screen.
- **Avoid the second-order reflex lane.** Beyond reflex *fonts*, the whole *editorial-typographic* lane — display serif (often italic) + tiny mono labels + ruled separators + monochrome restraint — is where most AI-adjacent brands now land. Unless the brief literally calls for magazine aesthetics, that's the trained default; look further.
- **Ship imagery when the brief implies it.** A restaurant, hotel, travel, food, or fashion design with zero images is a bug, not minimalism. Use real or generated photography, SVG, or a credible canvas/WebGL scene — never substitute flat colored CSS panels for photographic content.
- **Reveal complexity progressively.** Show what's needed now; place the rest behind clear entry points (accordions, steps, modals). Don't dump every option at once.

## Frontend Aesthetics Guidelines

Focus on:
- **Typography**: Choose fonts that are beautiful, unique, and interesting. Avoid generic fonts like Arial and Inter; opt instead for distinctive choices that elevate the frontend's aesthetics; unexpected, characterful font choices. Pair a distinctive display font with a refined body font.
- **Color & Theme**: Commit to a cohesive aesthetic. Use CSS variables for consistency. Dominant colors with sharp accents outperform timid, evenly-distributed palettes.
- **Motion**: Use animations for effects and micro-interactions. Prioritize CSS-only solutions for HTML. Use Motion library for React when available. Focus on high-impact moments: one well-orchestrated page load with staggered reveals (animation-delay) creates more delight than scattered micro-interactions. Use scroll-triggering and hover states that surprise.
- **Spatial Composition**: Unexpected layouts. Asymmetry. Overlap. Diagonal flow. Grid-breaking elements. Generous negative space OR controlled density.
- **Backgrounds & Visual Details**: Create atmosphere and depth rather than defaulting to solid colors. Add contextual effects and textures that match the overall aesthetic. Apply creative forms like gradient meshes, noise textures, geometric patterns, layered transparencies, dramatic shadows, decorative borders, custom cursors, and grain overlays.

NEVER use generic AI-generated aesthetics like overused font families (Inter, Roboto, Arial, system fonts), cliched color schemes (particularly purple gradients on white backgrounds), predictable layouts and component patterns, and cookie-cutter design that lacks context-specific character.

Interpret creatively and make unexpected choices that feel genuinely designed for the context. No design should be the same. Vary between light and dark themes, different fonts, different aesthetics. NEVER converge on common choices (Space Grotesk, for example) across generations.

**IMPORTANT**: Match implementation complexity to the aesthetic vision. Maximalist designs need elaborate code with extensive animations and effects. Minimalist or refined designs need restraint, precision, and careful attention to spacing, typography, and subtle details. Elegance comes from executing the vision well.

Remember: Claude is capable of extraordinary creative work. Don't hold back, show what can truly be created when thinking outside the box and committing fully to a distinctive vision.

---

## Concrete Design Rules

The guidelines above set the vision; these rules set the floor. Aesthetic direction is free, but craft is not negotiable — hit these numbers unless the design has a deliberate reason not to.

**Spacing & layout**
- Build all spacing from a 4pt scale: 4, 8, 12, 16, 24, 32, 48, 64, 96. No arbitrary values.
- Create rhythm through contrast: tightly group related elements (8–12px), separate distinct groups generously (48–96px). Uniform spacing everywhere reads as machine-generated.
- Touch/click targets are ≥44×44px even when the visual element is smaller — expand the hit area with padding or a pseudo-element.
- Constrain body text to 45–75 characters per line (`max-width: 65ch`).
- Reach for `repeat(auto-fit, minmax(280px, 1fr))` and container queries before hand-written breakpoints.

**Typography**
- Use a modular scale with a ratio ≥1.25 (1.25 / 1.333 / 1.5). Sizes that sit too close together produce a flat, dull hierarchy.
- Body text ≥16px. Line-height 1.5–1.7 for body; tighten for large display.
- Light text on dark needs compensation: +0.05–0.1 line-height, +0.01–0.02em letter-spacing, and bump weight up one notch — dark mode is not just inverted light mode.
- Load fonts with `font-display: swap` plus a metric-matched fallback (`size-adjust`, `ascent-override`) to avoid layout shift.
- Use OpenType features where they matter: `tabular-nums` for aligned data, small-caps for abbreviations.

**Color**
- Author colors in OKLCH, not HSL — it's perceptually uniform; reduce chroma as you approach white/black.
- Tint "neutrals" slightly toward the brand hue (0.005–0.015 chroma). Pure gray looks lifeless beside real color.
- Distribute by the 60-30-10 rule (60% dominant/neutral, 30% secondary, 10% accent) measured by visual weight, not pixel count.
- Meet WCAG contrast: 4.5:1 for body text, 3:1 for large text and UI controls.
- Never set gray text on a colored background — use a darker shade of that same hue, or transparency.

**Motion**
- Three timing tiers: 100–150ms for instant feedback (presses, toggles), 200–300ms for state changes (menus, tooltips), 300–500ms for layout changes (modals, accordions). Under ~80ms reads as instant.
- Easing is ease-out (quart/quint/expo) only. Never bounce or elastic — it dates the work instantly.
- Exit animations run at ~75% of their entrance duration.
- Never animate layout properties (width/height/top/left/margin). Animate `transform` and `opacity`, or use FLIP / `grid-template-rows`.
- Cap staggers (~10 items × 50ms = 500ms max) and always honor `prefers-reduced-motion`.

**Interactive states & copy**
- Every interactive element ships all relevant states: default, hover, focus-visible, active, disabled, loading, error, success.
- Use `:focus-visible` with a real 2–3px outline (never `outline: none`). Validate form inputs on blur, not per keystroke. Labels are always visible — placeholders are not labels.
- Prefer skeleton screens over spinners.
- Errors follow what / why / how-to-fix ("Email isn't valid — it needs an @. Try name@example.com"). Buttons are verb + object ("Create account", "Save changes") — never "OK", "Submit", or "Yes/No".

## Calibrating Intensity

A design can miss by being too timid or too loud. Adjust deliberately — and note "bolder/quieter" means different things on a *brand* surface (marketing, identity) than a *product* surface (tools, dashboards).

**To push a bland design bolder**
- *Brand*: real typographic risk, extreme scale, a committed point of view. *Product*: stronger hierarchy and weight contrast, one sharper accent, more deliberate density — not theatrics.
- Jump type scale 3–5× between hero and surroundings (not 1.5×); pair extreme weights (900 with 200, not 600 with 400).
- Let one color own ~60%, raise saturation, add sharp high-contrast accents and tinted neutrals, intentional multi-stop gradients.
- Break the grid: asymmetry, overlap for depth, 70/30 or 80/20 splits, diagonal flow, full-bleed elements, 100–200px gaps.
- One signature entrance, shown once — not scroll-fade-rise on every section (the saturated default). Avoid glassmorphism.

**To calm a loud, noisy design**
- *Brand*: restrained palette, more whitespace, typographic air — drama down, POV intact. *Product*: fewer accents, flatter cards, less color and motion until the tool disappears into the task.
- Drop saturation to ~70–85%, move to a neutral-dominant palette with a ~10% accent, lighten weights (900→600, 700→500), thin or remove borders.
- Shorten motion distances (10–20px, not 40px), gentler ease-out, and cut any animation not serving a clear purpose.

**Ambitious, "technically extraordinary" effects** — reach for these when the context rewards it: View Transitions API (morph list→detail), `@starting-style`, scroll-driven animations (`animation-timeline: scroll()`), spring physics, `@property` for animatable gradients, WebGL/WebGPU/Canvas, virtual scrolling, OffscreenCanvas/Web Workers, WASM. Guardrails: target 60fps (floor 50), lazy-init and pause off-screen work, **always** honor `prefers-reduced-motion` with a beautiful static fallback, no sound without explicit opt-in, and degrade gracefully (progressive enhancement).

**Delight, tastefully** — *brand* surfaces can spread personality across copy, transitions, and discovery rewards; *product* surfaces earn delight only at specific moments (completion, first run, error recovery, milestones) — everywhere else it reads as noise. Keep each moment under ~1s, skippable, and varied (not the same animation every time). Confetti is for real milestones, not every click. Loading copy must be product-specific ("Crunching your latest numbers…", "Syncing your team's changes…") — never the AI-slop clichés ("Herding pixels", "Teaching robots to dance").

## Anti-Patterns — the AI Tells

Beyond the generic-aesthetic warning above, these specific patterns are instant "an AI made this" giveaways. Treat each as a smell to remove, not a default to reach for:

- **Side-tab accent border** — a >1px colored stripe on one edge of a card. Use a full hairline border, a background tint, or a leading glyph instead.
- **Icon tile above heading** — a 32–128px rounded square holding an icon, stacked over an h1–h6. The universal template tell.
- **Italic serif hero headline** — Fraunces / Playfair / Recoleta italic at hero scale as the primary H1. Skip unless the context is genuinely editorial.
- **Flat type hierarchy** — heading sizes <1.25× apart. Use fewer sizes with more contrast.
- **Nested cards** — cards inside cards. Use spacing and dividers instead.
- **Monotonous spacing** — the same gap everywhere. See the rhythm rule above.
- **Reflex font choices** — Inter, Space Grotesk, DM Sans/Serif, Plus Jakarta, Outfit, IBM Plex, Fraunces, Newsreader, Lora. If one of these was your first instinct, look further.

---

## Production Craft Bar

"Done" means production-grade, not a happy-path mockup. Before shipping, clear this bar:

- **Real content, not placeholders.** No lorem ipsum, no "Card Title", no fake avatars where real data belongs.
- **Every state exists:** default, empty (with a clear next action), loading (name what's loading), error (recoverable), plus success where relevant.
- **Edge cases handled:** zero items, one item, 1000+ items, very long strings, emoji, RTL text, network failure, permission denied, slow connection.
- **Internationalization-ready:** budget 30–40% extra width for translation (German runs ~30% longer); let flex/grid grow with content instead of fixing text-container widths. Use logical CSS properties (`margin-inline-start`, `padding-inline`, `border-inline-end`) so RTL works for free. Format dates, numbers, and currency with `Intl.*`, and pluralize via a real i18n library — not `count !== 1`.
- **API failures map to UI:** 400 → field validation, 401 → login, 403 → permission message, 404 → not-found state, 429 → rate-limit message, 500 → generic error + a way to get help.
- **Semantic HTML first:** real headings (h1–h6) and landmarks, labels associated to inputs, buttons vs links used correctly, accessible names, and live regions to announce dynamic changes — before any ARIA patching.
- **Large datasets** use pagination or virtual scrolling with search/filter — never render 10,000 rows at once.

---

## Performance Floor

Craft includes speed. Hold these unless a deliberate trade-off says otherwise:

- **Core Web Vitals:** LCP < 2.5s (optimize the hero, inline critical CSS, preload key assets), INP < 200ms (break up long tasks, defer non-critical JS, offload heavy work to Web Workers), CLS < 0.1 (set image/video dimensions or `aspect-ratio`, reserve space for embeds, never inject content above existing).
- **Images:** modern formats (WebP/AVIF), sized to display (don't ship a 3000px image into a 300px slot), `srcset`+`sizes` for responsive delivery, lazy-load below the fold, ~80–85% quality, via CDN.
- **Breakpoints are content-driven:** start narrow, widen until the layout breaks, add a breakpoint there (usually ~640/768/1024 suffice). Prefer `clamp()` for fluid type/space, and write mobile-first (`min-width` queries layering complexity up).
- **Adapt to input and device:** `@media (pointer: coarse)` / `(hover: none)` for touch (larger targets, no hover-only affordances); respect notches with `env(safe-area-inset-*)` plus `viewport-fit=cover`.
- **Avoid layout thrash:** batch DOM reads, then batch writes — never alternate read/write in a loop. Use `content-visibility: auto` for long lists and `will-change` sparingly.
- **Fonts:** `font-display: swap`, subset with `unicode-range`, preload critical faces, limit weights.
- **Verify on real conditions:** measure on a low-end Android throttled to 3G, not just desktop Chrome — that's where the problems actually show.

---

## Critique Pass

Before declaring a design done, critique it against established usability standards — not just "does it look good." Run two lenses.

**Nielsen's 10 heuristics** — score each 0–4 (0 = absent, 4 = genuinely excellent) and fix anything ≤2:

1. **Visibility of system status** — timely feedback; loading, confirmation, progress, active location, inline validation.
2. **Match between system and real world** — user's language, no unexplained jargon, logical order, familiar metaphors.
3. **User control and freedom** — undo, cancel, clear escape from any state; no traps.
4. **Consistency and standards** — one term per concept, platform conventions, repeated patterns behave the same.
5. **Error prevention** — make mistakes hard before relying on error messages; confirm only the truly destructive.
6. **Recognition over recall** — show options; don't make users remember things across steps.
7. **Flexibility and efficiency** — shortcuts and accelerators for experts without blocking novices.
8. **Aesthetic and minimalist design** — every element earns its place; no decorative noise that competes with content.
9. **Help users recover from errors** — plain-language errors that say what / why / how to fix (no codes alone).
10. **Help and documentation** — discoverable, task-focused help where it's needed.

**Persona walkthrough** — pick the 2–3 personas most relevant to the interface, walk the primary task as each, and report *specific* red flags (name the element that breaks), not generic concerns:

- **Alex (impatient power user)** — skips onboarding, wants keyboard shortcuts and bulk actions. Red flags: forced tutorials, no keyboard path, one-at-a-time workflows, redundant confirmations.
- **Jordan (confused first-timer)** — needs guidance, takes labels literally, abandons rather than puzzle it out. Red flags: icon-only nav, jargon, no visible help, ambiguous next step, no success confirmation.
- **Sam (accessibility-dependent)** — screen reader + keyboard only, may zoom to 200%. Red flags: click-only interactions, missing/invisible focus, meaning by color alone, unlabeled fields, broken SR flow.
- **Riley (deliberate stress tester)** — pushes edge cases, weird input, refresh mid-flow. Red flags: silent failures, broken error recovery, useless empty states, data lost on refresh, inconsistent behavior.
- **Casey (distracted mobile user)** — one thumb, interrupted, slow connection. Red flags: primary actions out of the thumb zone, no state persistence, typing where selection would do, tiny/crowded tap targets.

Persona selection by interface type: landing/marketing → Jordan, Riley, Casey · dashboard/admin → Alex, Sam · checkout → Casey, Riley, Jordan · onboarding → Jordan, Casey · analytics → Alex, Sam · forms/wizards → Jordan, Sam, Casey.

Also keep cognitive load low — humans hold ~4 things in working memory: ≤5 top-level nav items, ≤4 fields per form group, one primary action plus at most one or two secondary.

---

## Visual Verification with Browsify

After implementing any UI change, always verify visually:

1. Start the dev server if not running (`npm run dev` or equivalent).
2. Use browsify to open the relevant URL.
3. Take a screenshot with `browsify_screenshot`.
4. Verify the result matches the spec — layout, spacing, typography, color.
5. Check responsiveness at mobile (375px), tablet (768px), and desktop (1280px) widths.
6. Include all screenshot paths in your implementation report.

Never claim `DONE` on a frontend task without a browsify screenshot showing the result.
