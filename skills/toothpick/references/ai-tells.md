# The AI-tell list

Every entry says three things: **what it looks like**, **why it reads as AI**, and **when it is actually fine**.

This is not a list of bans. Every pattern here can be right for the right project. The problem is that an AI does it **regardless of the project**. So before using one, ask: was this chosen for this product, or added out of habit?

---

## 1. Style costumes and surface habits (layer two, the ones to watch most)

### Cream paper, large serif headline, terracotta or deep red accent
- **Looks like**: a warm cream background around #F4F1EA, a large serif headline, an accent in terracotta (such as #D97757) or deep red
- **Why it reads as AI**: it is the fixed answer when an AI is asked to be "tasteful and warm". #D97757 also happens to be Claude's own brand color, which makes it stand out even more on someone else's project
- **Fine when**: the brand really has this character, backed by real paper, craft or publishing roots

### Near-black background, one bright accent, monospace type
- **Looks like**: a near-black background such as #0B0B0B or #111, one neon green, amber or vermilion accent, monospace across the whole site or most of it
- **Why it reads as AI**: an AI's fixed idea of "developer tool" or "hacker". In fact the homepages of GitHub, Vercel and Linear do not do this
- **Fine when**: the product really is a terminal tool, and monospace appears only in actual code and commands

### Newspaper hairlines, zero radius, dense columns
- **Looks like**: many black 1px full-width rules cutting up the page, zero radius on everything, information packed into dense columns
- **Why it reads as AI**: an AI's fixed idea of "professional, Swiss, editorial". The whole page turns into a wireframe: cold, hard, flat
- **Fine when**: it is a real newspaper or publication; or light lines organize information in a table or data-dense UI (the GitHub repository page does this, but its lines are light grey #D1D9E0 and form rounded boxes)

### Style symbols posing as content
- **Looks like**: a terminal "$" as the logo, "●" as a status dot, "##" as a label, "[✓]" as a checkbox, a magazine-style "Issue 42"
- **Why it reads as AI**: the symbols borrow the costume of a style but carry no real information. People sense the pretense immediately
- **Fine when**: the symbol shows a real state (the service really is online, so the dot is green)

### Colored stripe on the left of a card
- **Looks like**: a 3–4px colored border on the left of cards, callouts or list items
- **Why it reads as AI**: the stock move when an AI wants to "add some emphasis" to a card
- **Fine when**: rarely. An icon, a word or a whole light background shows state more clearly

### Hard offset shadow
- **Looks like**: an unblurred block shadow such as `box-shadow: 4px 4px 0 #000`
- **Why it reads as AI**: the neo-brutalist costume. On a page that did not choose that style, it is only borrowing one
- **Fine when**: the whole page really is neo-brutalist

### Ghost card
- **Looks like**: a 1px border with a large soft shadow underneath
- **Why it is a problem**: two elevation techniques stacked; the edge goes blurry. Pick one

### Stripes, grids, noise in the background
- **Looks like**: `repeating-linear-gradient` diagonal stripes, two-axis grid lines, `feTurbulence` grain
- **Why it reads as AI**: texture filling the space where there is "nothing to put"
- **Fine when**: the background is something from the subject's world (a drawing, a map, graph paper, a measuring tool)

### Hand-drawn-style SVG illustrations
- **Looks like**: small "sketchy" scenes or doodle lines drawn in SVG
- **Why it is a problem**: it looks amateur. SVG is great for geometry, charts and diagrams; imitating illustration with it shows
- **Instead**: use a real illustration or photograph, or nothing

### Unicode symbols as icons
- **Looks like**: characters such as ★ ✓ ➜ ◆ standing in for icons
- **Instead**: one real icon set, or your own SVGs, with a consistent stroke

### Light or dark chosen by category
- **Looks like**: every developer tool is dark, every lifestyle brand is light
- **Instead**: choose from the use scene: who uses it, where, in what ambient light

### The benchmark look as the default
- **Looks like**: white, neutral grey, one brand color, pill or small-radius buttons, panels with a light grey border and a faint shadow, headings at weight 400–500. The coffee roaster, the database tool and the architecture studio all end up looking like this
- **Why it reads as AI**: it is the next default after "don't make it look like AI". Vercel and GitHub look this way because they are tools whose content is the interface; copied onto another subject, it throws away that subject's own world
- **Fine when**: the page is in Operate mode (dashboards, tools, settings), or the product really is a developer product. For Persuade and Showcase pages, take color, material and imagery from the inventory first, and use the benchmarks only to calibrate craft

### The hollowed-out page
- **Looks like**: every AI-flavored decoration removed and nothing added back; grey text and large empty areas
- **Why it is a problem**: it reads as thin and half-hearted. In blind tests, people even preferred a richer page that still had some AI flavor
- **Instead**: add substance: stronger type contrast, whole fields of color, real pictures of the subject's world, sections written out in full

---

## 2. Template parts

Each of these is minor on its own, but almost every AI page has them, and together they produce the "template" feel.

### A small label above every heading (eyebrow)
- **Looks like**: a line of small all-caps, letter-spaced text above a heading, such as "FEATURES"
- **Why it reads as AI**: it usually just repeats the heading and adds nothing
- **Fine when**: the label really adds category or location information (for example a chapter name in docs)

### Middle-dot metadata
- **Looks like**: strings of phrases joined with ·, such as "Open source · MIT · PostgreSQL"
- **Why it reads as AI**: AIs love this format; a single page can have a dozen
- **Fine when**: one or two places where the items really are parallel metadata, such as an article's author and date

### "→" after links and buttons
- **Looks like**: "Learn more →", "Get started →"
- **Why it reads as AI**: the arrow has become default decoration and no longer means "goes somewhere else"
- **Fine when**: the link really leaves the page, or a group of links needs to distinguish "navigate" from "act"

### Numbering things that are not steps
- **Looks like**: "01 / 02 / 03" in front of features or selling points
- **Why it reads as AI**: numbers imply an order; features do not have one
- **Fine when**: the content really is a sequence, process or timeline

### All-caps labels, small monospace data
- **Looks like**: every small label in all caps with wide tracking; dates and counts set in monospace
- **Why it reads as AI**: templated "polish"
- **Fine when**: numbers in a table need to align (but `font-variant-numeric: tabular-nums` does that without switching to monospace)

### One word in the headline recolored, italicized or bolded
- **Looks like**: "Ship **faster**", or one word in the accent color
- **Why it reads as AI**: one of the most common generated-headline treatments
- **Fine when**: that word truly is the only thing to emphasize, and the site does it only once

### Huge decorative numbers
- **Looks like**: a giant "42", "022" or "2014" filling half the screen next to a small label
- **Why it reads as AI**: the default response to "be bold"; the number often means nothing
- **Fine when**: the number is the most important information on the page (the headline figure of a statistics report, say)

---

## 3. Layer one: the old clichés

### Purple-to-blue gradients, gradient text
- **Why it reads as AI**: the first AI tell people learned to spot
- **Fine when**: the brand color itself is a gradient

### Emoji as icons
- **Why it reads as AI**: they render differently on every system and clash with the interface
- **Fine when**: the product is chat or social, and emoji are part of the content

### The SaaS card kit
- **Looks like**: all content chopped into same-size rounded cards, one radius on everything, the same grey shadow rgba(0,0,0,.1) under each card, gradient blobs in the background
- **Why it reads as AI**: no hierarchy; everything is equally important
- **Fine when**: the content really is a set of equal, independently actionable units (products, files, projects)

### Colored icon tiles
- **Looks like**: every feature gets a rounded square icon in a different color
- **Why it reads as AI**: many colors that mean nothing

### Frosted glass, blurry blobs, grid backgrounds
- **Why it reads as AI**: decoration added when there is nothing else to put
- **Fine when**: glass sits on an element that really floats over content (a header after scrolling) with real content showing through

### "Centered headline, two buttons, three cards, stats bar, testimonials, pricing, FAQ"
- **Why it reads as AI**: every product ends up looking the same
- **Fine when**: every section is backed by real content. The structure is not wrong; inventing content to fill it is

---

## 4. Design for the sake of design

### Asymmetry for its own sake
- **Looks like**: every section offset at 5:7 or 4:8
- **Why it reads as AI**: asymmetry without a reason is performing "design". Most of the benchmark pages are symmetric or centered
- **Fine when**: the content has a real primary and secondary side (a large image on one side, the explanation on the other)

### Everything is "bold"
- **Looks like**: huge headline, huge numbers, clashing colors and animation, all at once
- **Why it is a problem**: when everything is the focus, nothing is
- **Instead**: spend the boldness in one place and keep everything else quiet

### Over-theming
- **Looks like**: once a theme is chosen, every detail leans into it (coffee motifs everywhere on a coffee site, terminal symbols everywhere on a terminal tool)
- **Why it is a problem**: it feels contrived. Good design makes people notice the content, not the "style"
- **Fine when**: the user asked for a strong style, or the subject's own world speaks this language, and every device maps to a piece of content (see "When to commit to a strong concept" in SKILL.md)

---

## 5. Content

### Empty copy
- **Looks like**: "Unlock limitless possibilities", "Empower your business", "Built for the future", "Simple. Fast. Secure."
- **Instead**: say concretely what it does and for whom

### Fabrication
- **Looks like**: invented user counts, testimonials, customer logos, press mentions; a fake logo assembled from symbols
- **Why it is not allowed**: it misleads, and the user may forget to remove it before launch
- **Instead**: leave it out; when a placeholder is needed, mark it [TODO]

### Inventing features the project does not have
- **Looks like**: "Smart recommendations", "One-click PDF export", "Real-time collaboration" on the homepage, and none of it exists
- **Why it is not allowed**: it misleads users, and misleads developers into thinking these are requirements
- **Instead**: read the project first and show only what exists; suggest new features separately in your reply

### Mock data posing as real data
- **Looks like**: dashboards and lists full of attractive hard-coded numbers, not connected to anything, with no note
- **Why it is not allowed**: the page looks finished; the developer has to dig through the code to find that nothing is wired up
- **Instead**: connect the real API; if you cannot, keep mock data in one place with the same fields as the real API, and list it in the placeholder list

### Fake interactions
- **Looks like**: buttons with hover and click animations that do nothing; a hard-coded "Submitted successfully" message
- **Why it is not allowed**: the hardest kind of half-finished work to notice
- **Instead**: disable it and label it "not connected", or list it in the placeholder list

### Ignoring the project and starting a parallel system
- **Looks like**: the project already has a button component, color variables and an icon set, and the new page writes its own
- **Why it is not allowed**: the project ends up with two styles, and every change has to be made twice
- **Instead**: read the project's existing components and style variables first, and build on them

### Perfect example data
- **Looks like**: every name is "John Smith", every amount is round, every title has the same length
- **Why it is a problem**: it cannot reveal wrapping, truncation or alignment problems

---

## 6. Motion

### Every section fades and slides up
- **Why it reads as AI**: the most common default animation
- **Instead**: use self-playing motion once, to direct attention; motion that responds to the user (expanding, confirming) is welcome

### Every card lifts and grows on hover
- **Why it reads as AI**: default "interactivity"
- **Instead**: hover feedback only needs to say "this is clickable"

---

## 7. Software interfaces

### Turning the dashboard into a marketing page
- **Looks like**: a "Welcome back 👋" banner, four same-size stat cards each with a green ↑12%, lots of whitespace
- **Instead**: dashboard users are there to work; information density and efficiency come first. See the GitHub repository page: 14px body text, 41px rows, light grey outlines organizing the information

### Designing only the perfect-data state
- **Instead**: consider loading, empty, error, no-permission and very long content

---

## Found a new AI tell?

Add it in the same format: **what it looks like → why it reads as AI → when it is fine**.
