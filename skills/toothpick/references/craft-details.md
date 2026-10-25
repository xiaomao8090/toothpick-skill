# Craft details

Good interfaces rarely come from one big decision; they come from many small details adding up. These are the ones AI most often skips, and the ones that show at a glance whether the work was really done.

Collected from several open-source projects, which are more complete and worth reading directly:
- Vercel: Web Interface Guidelines (https://github.com/vercel-labs/web-interface-guidelines)
- Jakub Krehel: make-interfaces-feel-better (https://github.com/jakubkrehel/make-interfaces-feel-better)
- Paul Bakaus: impeccable's craft floor (https://github.com/pbakaus/impeccable)

When fixing details, use the project's existing styling approach (Tailwind in a Tailwind project, plain CSS in a CSS project). Never introduce a second styling system for a small fix.

## Surfaces: radius, shadows, borders

- **Nested radii are concentric**: outer radius = inner radius + padding. The same radius on parent and child is the most common reason something "feels off".
- **Shadows for elevation, borders for structure**: a border that only exists to suggest depth becomes a layered translucent shadow; borders that mean division, selection or focus stay.
- **One elevation technique at a time**: border or shadow. A 1px border with a large soft shadow underneath becomes a "ghost card".
- **At least two shadow layers**: one for ambient light (large and faint), one for direct light (small and firm). Shadows have offset and blur; a zero-offset colored glow is decoration, not depth.
- **Translucent borders are crisper**: for example `rgba(0,0,0,.08)`, which works on any background.
- **A very faint outline on images**: `rgba(0,0,0,.1)` in light mode, `rgba(255,255,255,.1)` in dark mode. Use pure black or white with opacity, not a tinted grey, or it reads as dirt on the edge.
- **On colored backgrounds**, tint borders, shadows and secondary text toward the same hue instead of using grey.

## Alignment and type

- **Every element aligns to something**: a grid, a baseline, an edge or an optical center. Nothing is placed "roughly".
- **Optical over geometric alignment**: buttons with icons, play triangles and asymmetric icons often look off when geometrically centered; nudge them by 1–2px.
- **Balance icon and text weight**: regular text (400) with 1.5px icon strokes, semibold (600) with 2px. One icon set per interface; never mix.
- **`text-wrap: balance` on headings**, `text-wrap: pretty` on body text, to avoid a single word on the last line.
- **Numbers that change or are compared** use `font-variant-numeric: tabular-nums`.
- On macOS, `-webkit-font-smoothing: antialiased` on the root gives crisper text.
- Use the ellipsis character "…", not three periods "...".
- Use a non-breaking space between number and unit: `10&nbsp;MB`.
- Put more space above a heading than below it, so the heading groups with what follows.

## Browser-native parts

The cheapest signal that a page was built rather than assembled, and the one models skip most often: you did not draw these, but they ship with the page.
- Text selection color: `::selection`
- Caret color: `caret-color`
- Scrollbars (especially in dark interfaces)
- Focus rings: use `:focus-visible`, and never let sticky headers cover them
- Link underline position: `text-underline-offset`
- `color-scheme: dark` in dark themes, so scrollbars and native controls follow
- `<meta name="theme-color">` matching the page background
- Native `<select>` on Windows needs an explicit background and text color

## Interaction

- **Pressing gives feedback**: about `scale(0.96)` on press; never below 0.95.
- **Hover, pressed and focus states have more contrast than rest**, not less.
- **Hit areas**: at least 44×44px on touch, at least 40×40px in dense desktop UI (WCAG minimum 24px). Extend small visuals with a pseudo-element. Hit areas never overlap.
- **What looks clickable is clickable, and what is clickable looks it**. No dead zones.
- **Navigation uses real links** (`<a>`), so Ctrl/⌘-click and middle-click open new tabs.
- **State lives in the URL**: filters, tabs, pagination, expanded panels survive refresh and sharing.
- **Loading buttons** keep their label and add an indicator; spinners or skeletons appear after about 150–300ms and stay at least about 300–500ms to avoid flicker.
- **Skeletons match the final layout exactly**, so nothing jumps.
- **Prefer undo over a confirmation dialog**; confirm only destructive actions that cannot be undone.
- **No modal for a task that does not need to interrupt the user**.
- **Tooltips**: delay the first in a group; the rest appear without delay.
- **Every screen has a next step or a way back**; no dead ends.

## Motion

- Animate only `transform` and `opacity` for smoothness; never write `transition: all`, list the properties.
- Interactive state changes use CSS transitions (interruptible); keyframes are for staged sequences that play once.
- Exits are softer than entrances: a small offset, not a full-height slide.
- No custom animation on high-frequency actions; each trigger costs attention.
- Motion is never the only feedback; a state change also gets color, an icon or a label.
- Do not animate every element on first load; staged entrances are for rare, important moments, about 100ms apart.
- To review motion, slow it to 10% in the browser's animation panel; whatever feels off at 10% is what feels "somehow wrong" at full speed.

## Forms

- Every input has a `<label>`, and clicking the label focuses the input.
- With a single input, Enter submits; in a textarea, ⌘/Ctrl+Enter submits and Enter adds a line.
- Never block paste or keystrokes (let people type into a numbers-only field, then show an error).
- Do not pre-disable the submit button; let people submit and see what is missing.
- Errors appear next to their fields; after submit, focus moves to the first error.
- Set the right `type`, `inputmode` and `autocomplete` so phones show the right keyboard and autofill works.
- Placeholders show an example value, such as "+1 (555) 123-4567".
- Inputs on mobile are at least 16px, or iOS Safari zooms the page.
- Warn before leaving with unsaved changes.

## Content and copy

- Explain inline whenever possible; tooltips are a last resort.
- The page `<title>` reflects the current content.
- Never rely on color alone for state; add text or an icon.
- Icon-only buttons have an `aria-label`.
- Dates, times, numbers and currency follow the user's locale; within one context, amounts all have two decimals or none.
- Layouts hold up with very short, typical and very long content.
