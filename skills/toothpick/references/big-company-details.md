# Details from big-company design guidelines (checked against the originals)

> Purpose: a detail checklist for AI building UI. Each item names its source; [practice] marks common industry practice rather than a specific company's official text.
> Compiled: October 2026

---

## 1. Dark mode (where the AI flavor shows most easily)

### 1. White text on black looks heavier: adjust the weight, not the size
- Why: the irradiation illusion. At the same weight, light text on a dark background looks thicker.
- What to do: make the weight **slightly lighter** in dark mode (for example 400 → 350 for body text, or about -50 on a variable font's GRAD axis).
- Do not change size or tracking: text reflows and the layout jumps. Type designers also note that tracking only helps a little and does not fix the heaviness.
- CSS example (the font needs a GRAD axis, like Roboto Flex; otherwise nudge the variable wght axis):
  ```css
  body { --GRAD: 0; font-variation-settings: "GRAD" var(--GRAD); }
  @media (prefers-color-scheme: dark) { body { --GRAD: -50; } }
  @media (prefers-color-scheme: dark) and (prefers-contrast: more) { body { --GRAD: 150; } }
  ```
- The right value depends on the font: switch between light and dark until the weight looks the same.
- Sources: nerdy.dev (Adam Argyle), TypeDrawers type designer discussion

### 2. No pure black background, and colors are not simply inverted
- Material: the dark base is **#121212** (dark grey), not #000.
- Apple: dark mode is not an inversion of light mode; "many colors are inverted, some are not". Use semantic colors, not hard-coded values.
- IBM Carbon dark theme backgrounds: Gray 90 **#262626** / Gray 100 **#161616**.
- Sources: Material Dark Theme, Apple HIG Dark Mode, Carbon Color

### 3. In the dark, nearer means lighter: show elevation with lightness, not shadow
- Shadows are almost invisible on dark backgrounds, so elevation comes from lighter surfaces:
  - Material 2: translucent white over #121212, 9% at 4dp and 12% at 8dp (higher means lighter).
  - Apple iOS: two sets of backgrounds, base (darker, recedes) and elevated (lighter, advances); popovers and modal sheets use elevated automatically.
  - Carbon: each added layer in a dark theme is one step lighter (Gray 100 → 90 → 80 → 70); **never put a component darker than the background in a dark theme**.
  - Light themes work the other way: Carbon alternates white and Gray 10 rather than getting darker.
- Fluent (Microsoft): shadows need more opacity in dark mode (low elevation 14% → 28%), or they disappear.

### 4. Text hierarchy through opacity (Material)
- White text on dark: high emphasis **87%**, medium **60%**, disabled **38%**.
- Apple's equivalent: primary, secondary, tertiary and quaternary label colors.

### 5. Desaturate colors
- Saturated colors "vibrate" and glare on dark backgrounds.
- Material: use the **200 tone** (a lighter one) of the primary color in dark themes; tones 50–400 work best.
- Use the primary color on only one or two brand elements (logo, primary button).
- Ant Design: in dark mode "avoid highly contrasting colors or content", which tire the eyes over time; keep the information hierarchy the same as in light mode.

### 6. Images and icons need their own treatment
- White-background images "glow" in a dark interface: dim them slightly. (Apple)
- When a dark icon disappears on a dark background, add a thin outline; some icons need separate light and dark versions. (Apple)
- Illustrations are desaturated and re-toned for dark mode. (Material)

### 7. Contrast
- Minimum **4.5:1** (WCAG AA body text); Apple recommends aiming for **7:1** with custom colors, especially for small text.
- Large text (24px and up) 3:1, graphics and chart elements 3:1. (Carbon)
- Also test with the system's Increase Contrast and Reduce Transparency settings. (Apple)

### 8. Interaction states go in opposite directions in light and dark (Carbon)
- Hover: elements on dark backgrounds get lighter, on light backgrounds darker (a half step).
- Active: two steps; selected: one step.
- Focus: 2px, Blue 60 in light themes and white in dark themes, at least 3:1 contrast.
- Disabled: always from the grey family, with no hover or focus.

### 9. Follow the system
- Apple: **do not offer an app-specific appearance setting**; follow the system setting (websites may offer a toggle, but should follow `prefers-color-scheme` by default).
- Support Auto mode: the appearance may change while the app is running.

---

## 2. Typography

- **Size floors** (Apple): iOS default 17pt, minimum 11pt; macOS default 13pt, minimum 10pt.
- **Avoid thin weights**: Ultralight, Thin and Light are hard to read at small sizes; use Regular, Medium, Semibold or Bold. (Apple)
- **Use as few typefaces as possible**; too many obscure the hierarchy and look undesigned. (Apple)
- **Tracking follows size**: smaller text needs more tracking, larger text less (tighten large headings). Apple's system fonts have a tracking table that varies by size.
- **Leading**: tighter in dense interfaces, looser for long reading (Apple: tight -2pt, loose +2pt).
- **Tabular figures**: numbers in tables, prices and timers use `font-variant-numeric: tabular-nums`, or they jump sideways when they change. [practice]
- **CJK**: body line height about 1.6–1.8, looser than Latin; add space around Latin words and numbers in mixed text (or rely on the font's own handling). [practice]

---

## 3. Motion

### Duration (grows with distance and area; both Material and Carbon say so)
| Use | Carbon | Material 3 |
|---|---|---|
| Micro-interactions such as buttons and toggles | 70ms | 50–100ms |
| Fades | 110ms | 150–200ms |
| Small expansion, short movement | 150ms | 200–300ms |
| Expansion, toasts | 240ms | 300–400ms |
| Large expansion, important notifications | 400ms | 450–600ms |
| Background dimming, full-screen transitions | 700ms | 700–1000ms |

### Easing
- Decelerate on entrance, accelerate on exit, standard easing for elements on screen throughout:
  - Material standard: `cubic-bezier(0.2, 0, 0, 1)`; emphasized entrance: `cubic-bezier(0.05, 0.7, 0.1, 1)`; emphasized exit: `cubic-bezier(0.3, 0, 0.8, 0.15)`
  - Carbon productive (tool UIs): standard `cubic-bezier(0.2, 0, 0.38, 0.9)`, entrance `cubic-bezier(0, 0, 0.38, 0.9)`, exit `cubic-bezier(0.2, 0, 1, 0.9)`
- Carbon separates "productive" motion (buttons, dropdowns, tables; restrained) from "expressive" motion (opening a page, primary actions; occasional). **Tools should be mostly productive**; AI tends to make everything bounce and float.
- Always support reduced motion (`prefers-reduced-motion`), and never rely on motion alone to convey information. (Carbon)

---

## 4. Size and layout

- **Hit targets**: Apple 44×44pt, Material 48×48dp; WCAG 2.5.8 minimum 24×24 CSS px (44×44 at AAA). Icons can be small; the hit area cannot.
- **Concentric nested radii**: inner radius ≈ outer radius − padding (0 when the padding exceeds the outer radius). At WWDC25 Apple made concentricity a core of its new design language. A common AI mistake: a 16px card with a 16px button inside it.
- **Order by importance**: the most important things at the top and leading side; use alignment and indentation for hierarchy; keep related things close and unrelated things apart. (Apple)
- **Progressive disclosure**: too many options on one screen make it harder to use; tuck secondary features into menus or collapsed sections. (Apple)
- **macOS windows**: avoid critical controls at the very bottom of a window (people often drag windows partly off screen). (Apple)
- **Functionality stays when space changes**: a narrow layout may turn the sidebar into a tab bar, but the features stay the same. (Apple)

---

## 5. Self-check questions for AI (distilled from the rules above)
1. Is dark mode just a black background with white text? (Check weight, elevation by lightness, desaturation, images, shadows)
2. Is any card darker than the background in dark mode? Any long white text on pure #000?
3. Is the primary color used all over the screen? (It should appear in only one or two places)
4. Are nested radii concentric?
5. Do number columns use tabular figures?
6. Is every animation 300ms ease? (Duration should scale with area; entrances and exits use different curves)
7. Are hit targets at least 44px?
8. Are hover, active, focus and disabled states all present, and do they go the right way in light and dark?

---

## Sources
- Apple HIG – Dark Mode: https://developer.apple.com/design/human-interface-guidelines/dark-mode
- Apple HIG – Typography: https://developer.apple.com/design/human-interface-guidelines/typography
- Apple HIG – Layout: https://developer.apple.com/design/human-interface-guidelines/layout
- WWDC20 typography notes: https://wwdcnotes.com/notes/wwdc20/10175
- Material Design – Dark theme: https://m2.material.io/design/color/dark-theme
- Material dark theme walkthrough: https://blog.prototypr.io/how-to-design-a-dark-theme-for-your-android-app-3daeb264637
- Material motion tokens: https://github.com/material-components/material-components-android/blob/master/docs/theming/Motion.md
- IBM Carbon – Color: https://carbondesignsystem.com/elements/color/overview/
- IBM Carbon – Motion: https://carbondesignsystem.com/elements/motion/overview/
- Microsoft Fluent 2 – Elevation: https://fluent2.microsoft.design/elevation
- Ant Design – Dark mode: https://ant.design/docs/spec/dark
- Irradiation illusion and the GRAD axis: https://nerdy.dev/adjust-perceived-typepace-weight-for-dark-mode-without-layout-shift
- Type designers on white on black: https://typedrawers.com/discussion/comment/54288
- Concentric corners: https://nilcoalescing.com/blog/ConcentricRectangleInSwiftUI
- Target size: https://allaccessible.org/blog/wcag-258-target-size-minimum-implementation-guide
