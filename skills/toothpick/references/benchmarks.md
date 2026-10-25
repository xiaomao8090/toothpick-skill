# Benchmarks measured from real products

> Actual computed styles read in a browser in October 2026, at 1440px wide.
> **These are a reference, not a standard.** They are all tech products; a coffee shop or an architecture studio copying their look is just as wrong.
> What to learn is the practice behind them: restraint, precision, consistency, and the product itself as the hero.

## Per-site data

### Vercel homepage
- Background #FAFAFA, white panels; body text #171717, secondary text #4D4D4D (pure neutral grey)
- One family, Geist; Geist Mono appears only in code and product mockups
- Headings 48–64px, **weight 400–450** (not bold), tracking about -0.06em, line height about 1.17
- Most text is 14px or 18px
- Buttons are 40px tall; primary is near-black with white text, secondary is white; radius is fully rounded or 8px
- **Almost no borders or dividers on the whole page** (only 4 elements have a border). Panels use a thin ring `0 0 0 1px rgba(0,0,0,.08)` plus a very faint 2px shadow
- Panel radius is mostly 6px
- Each section is about 850px tall, with lots of whitespace
- Blue #0072F5 is used almost only for links
- Product imagery (images, code mockups, interface mockups) takes about 29% of the page area

### GitHub homepage
- Dark #0D1117; Mona Sans plus Mona Sans Mono
- H1 64px at weight 425, H2 40px at 460, centered
- Primary button green #08872B, radius 6px, 48px tall
- Product imagery takes about 46% of the page area
- Content max width 1280px

### GitHub repository page (product UI)
- White background; body 14px with 21px line height, color #1F2328; secondary #59636E; links #0969DA
- Borders are everywhere (250+ elements), but all light grey #D1D9E0, forming boxes with 6px radius
- File list rows 41px tall; small buttons 28px tall with 12px text; regular buttons 32px
- The lesson: **lines are not the problem; their color, weight and purpose are**. In product UI, light grey outlines organize information; they are not decoration

### ChatGPT home (product UI)
- Background #FCFCFC, text #0D0D0D, secondary #5D5D5D; system font
- Only about 20 pieces of visible text on the whole screen; extremely restrained
- Only one shadow on the page, on the input: `0 0 0 1px rgba(0,0,0,.04), 0 2px 8px rgba(0,0,0,.04), 0 4px 80px 8px rgba(0,0,0,.024)`
- Input 768×52px with 28px radius
- Sidebar items 36px tall, 10px radius, transparent until hover
- Log-in button 44px tall, fully rounded, black

### Google homepage
- White, Arial / Google Sans
- Search box 584×52px with 26px radius
- Buttons 36px tall, 8px radius, light grey #F8F9FA
- Sign-in button blue #0B57D0, fully rounded
- Only two shadows on the page, both very faint

### Linear homepage
- Background #08090A, text #F7F8F8, secondary #8A8F98 / #62666D
- Inter Variable plus Berkeley Mono
- H1 64px, weight 510, tracking -0.022em, line height 1.0; H2 48px at 510, left aligned
- Each section is about 1240px tall
- Much of the 12–14px text on the page is actually **product interface drawn in HTML**; that is the main reason it looks good
- Radius 8px / 12px; separation with low-opacity white

## What they share

1. **Almost only black, white and grey**, plus one functional color (links or the primary button). Greys are pure neutral or a very slight cool.
2. **One type family is enough**; monospace is used only for code and product mockups, never to create a "technical" mood.
3. **Headings are large but not heavy** (weight 400–510) with tightened tracking. Impact comes from size and whitespace.
4. **Body text 14–16px**, mostly 14px in product UI.
5. **Light separation**: pale 1px rings or borders, very faint shadows, 6–12px radius. None of them cut the page up with black full-width rules.
6. **The product is the hero**: 25–46% of a marketing page is product imagery.
7. **One focal point per screen**, no decorative symbols, numbering or labels.
8. **No "style"**: none of them is "something-style". Their identity comes from the product, the content and the precision of the craft.

## How to use this reference

- For tech products, tools and SaaS, the magnitudes of these values are a direct reference.
- For other industries, take the principles (restraint, precision, consistency, content first); colors and type come from that industry's own world.
- When unsure, use these values as a check: are my headings too heavy? Too many colors? Lines too dark or too many? More decoration than content?
