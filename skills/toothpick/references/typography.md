# Typography

Typography sets the character of a page. Choose typefaces as carefully as a brand color, not the same one on every project.

## Principles

- **One family is usually enough**. The big products almost all use one family (Vercel uses Geist, GitHub uses Mona Sans, Linear uses Inter) and build hierarchy with size and weight. If you use two, make them clearly different, not two similar sans-serifs.
- **Choose type for this project**. First ask which world the product belongs to: newspapers, tools, children, finance, crafts. Then find type from that world. Do not reach for the same "safe choice" every time.
- **Headings are large, not necessarily heavy**. Benchmark headings are mostly weight 400–510; impact comes from size, tracking and whitespace. Bold everywhere looks clumsy.
- **Tighten tracking on large headings**, more as size grows (reference: Vercel about -0.06em, Linear about -0.022em). Body text is not tightened. CJK text generally does not need negative tracking.
- **Few type sizes**: five or six per page is enough. When the hierarchy is unclear, first try fewer sizes with bigger gaps, not one more size.
- **Line length under 80 characters** (about 35–40 CJK characters). Serif body text can run slightly longer, with more line height.
- **Line height**: about 1.5 for Latin body text; CJK glyphs are fuller, so 1.7–1.8 reads better; 1.0–1.2 for large headings.
- **Aligned numbers**: `font-variant-numeric: tabular-nums` for tables, prices and timers.
- **Punctuation**: curly quotes “ ” in English; full-width punctuation in Chinese.

## Common problems

- All-caps labels everywhere → see `ai-tells.md`
- Three or four typefaces on one page → usually no clear role for each
- Thin weights at small sizes → hard to read (Apple advises avoiding Ultralight, Thin and Light)
- Italic Chinese → Chinese fonts have no true italic; the browser's fake slant looks bad. Emphasize with weight or color
- Monospace for a "technical" feel → monospace is for code and content that must align

## CJK font notes

- CJK web fonts are large (often several MB per weight):
  - For tool UIs, a system font stack is the safest: `-apple-system, "PingFang SC", "Microsoft YaHei", "Noto Sans SC", sans-serif`
  - Noto Sans SC / Noto Serif SC on Google Fonts are sliced and loaded on demand automatically
  - For a distinctive CJK display face, load only the characters you use (subsetting)
- List the Latin font first and the CJK font after it: Latin letters and numbers use the Latin font, Han characters fall back to the CJK font.
- Song (serif) faces look fuzzy at small sizes on Windows; be careful using them for body text.
- Leave a space between Chinese and Latin text or numbers; it reads more comfortably.
