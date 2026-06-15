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

## Visual Verification with Browsify

After implementing any UI change, always verify visually:

1. Start the dev server if not running (`npm run dev` or equivalent).
2. Use browsify to open the relevant URL.
3. Take a screenshot with `browsify_screenshot`.
4. Verify the result matches the spec — layout, spacing, typography, color.
5. Check responsiveness at mobile (375px), tablet (768px), and desktop (1280px) widths.
6. Include all screenshot paths in your implementation report.

Never claim `DONE` on a frontend task without a browsify screenshot showing the result.
