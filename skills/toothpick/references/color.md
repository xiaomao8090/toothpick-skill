# Color

## Approach

- **Greys first, then the functional color**. Over 90% of the benchmark pages is black, white and grey (see `benchmarks.md`); color appears only where the user's attention is needed: the primary button, links, states.
- **Greys can be pure neutral**. Vercel and ChatGPT use pure neutral greys; GitHub uses a very slight cool. Claims like "greys must always be warm-tinted" have no basis. What matters is one consistent grey scale.
- **Color comes from the product's world**. A tea brand, a bank and a children's app should draw color from entirely different places. Do not reach for the same "tasteful" palette every time.
- **Colors should be clean**. Dirty, muddy, greyed colors (low-saturation browns, ochres and dark reds together) look old and cheap, unless the brand really is retro.
- **Less is more**. When a screen shows more than three hues, ask what each one is saying.
- **Write the plan as 4–6 named values**: background, primary text, secondary text, border or divider, functional color, plus a status color if needed.

## Common problems

- Accent color everywhere → it stops being an accent
- Pure black #000 body text on pure white → harsh contrast; the big products use near-blacks like #171717, #0D0D0D, #1F2328
- Dark borders → the page becomes a wireframe; benchmark borders are light greys like #EBEBEB and #D1D9E0, or thin rings like rgba(0,0,0,.08)
- Heavy shadows → benchmark shadows are typically only 4%–8% opacity
- Red versus green as the only signal → color-blind users cannot tell; add an icon or text
- Insufficient contrast → body text at least 4.5:1, aim for 7:1 on small text

## Dark mode

Dark mode is not an inversion; design it on its own (details in section 1 of `big-company-details.md`):
1. Dark grey background, not pure black (around #121212); higher layers are lighter
2. Shadows are barely visible in the dark; build hierarchy with surface lightness and translucent white hairlines
3. Text is not pure white; secondary text is dimmer
4. Colors are desaturated and slightly lightened
5. White text on dark looks heavier, so body weight can be slightly lighter
6. Images with white backgrounds are slightly dimmed

### Implementation
```css
:root {
  --bg: #FFFFFF; --surface: #FAFAFA; --text: #171717;
  --text-2: #5C5C5C; --border: rgba(0,0,0,.08); --accent: /* choose per project */;
}
@media (prefers-color-scheme: dark) {
  :root:not([data-theme="light"]) {
    --bg: #121212; --surface: #1A1A1A; --text: #EDEDED;
    --text-2: #A1A1A1; --border: rgba(255,255,255,.1); --accent: /* desaturated version */;
  }
}
:root[data-theme="dark"] { /* same as above, for a manual toggle */ }
```
- Components reference variables only, never hard-coded colors
- Follow the system by default; when a manual toggle exists, the user's choice wins
