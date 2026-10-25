# Websites and marketing pages

For: homepages, landing pages, campaign pages, product pages, personal sites, portfolios, blogs.

A marketing page has a few seconds to make people understand "what is this, and what does it do for me", and to make them believe it.

## Answer three questions first

1. Who is the visitor, and where are they coming from?
2. What is the one thing they should do after reading?
3. **What is the single most persuasive thing you have?** The product interface, a real photograph, a working demo, a piece of work, a menu...

The answer to question 3 is the hero of the first screen. On the benchmark marketing pages, 25%–46% of the area is product imagery (see `benchmarks.md`); their persuasion comes from the product itself, not from layout tricks.

## Common problems and why

**The first screen is only a slogan**
A slogan does not say what it is. Use one concrete sentence and let the hero (product imagery and so on) appear right away.

**Decoration instead of content**
Without assets, an AI fills the layout with gradients, blurry blobs, huge numbers and geometric shapes. Better: draw the product interface in HTML/CSS (much of the small text on Linear's homepage is drawn product UI), or use clean typography and whitespace.

**Inventing content to fill a structure**
No real testimonials, no testimonial section. No data, no stats bar. No customers, no logo wall. The content you really have decides how many sections there are.

**Every section looks the same**
If every block is "heading plus three columns", the page has no rhythm. Choose the presentation from the shape of the content: one large image, a demo, a comparison, a list.

**Too little whitespace, or messy whitespace**
Benchmark sections are typically 850–1250px tall, mostly whitespace. Whitespace needs a system: consistent spacing at the same level, tight inside groups, loose between them.

**No decision about alignment**
Centering suits short lines and focal moments like the first and last screens; long text reads better left aligned. Both are fine; what matters is having a reason and staying consistent.

**Too many primary buttons**
One primary action per screen; secondary actions are visibly weaker.

**Heavy separation**
Black rules, heavy shadows and thick borders make a page hard and noisy. Prefer whitespace and background lightness; when you need a box, use a pale thin outline and a very faint shadow.

## Images and assets

- Prefer real assets supplied by the user.
- Without assets: draw a product interface mockup, use pure typography, or leave a clearly marked slot such as [TODO: product screenshot].
- Do not hotlink random images from the web; they break and may have copyright problems.
- Screenshots are sharp (2x resolution), with light frames and shadows.

## Responsive

- Always check phone width (about 375px): no horizontal scrolling, 16–20px side margins.
- Large headings shrink on phones (`clamp()`) but stay clearly larger than body text.
- Multiple columns become one; side-by-side buttons stack.

## Basics

- `font-display: swap`; preload the fonts used on the first screen.
- Give images width and height to avoid layout shift; lazy-load images below the fold.
- `<title>`, `meta description`, favicon.
