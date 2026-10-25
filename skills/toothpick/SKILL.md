---
name: toothpick
description: "Use when designing or changing any user interface: websites, landing pages, marketing sites, admin panels, desktop software, mobile apps, components, dashboards, forms, dark mode, color, typography, READMEs and diagrams. Also for requests like \"make a page\", \"make it look nicer\", \"restyle this\" or \"build the frontend\". Helps spot and remove the templated look and common flaws of AI-generated interfaces, and produce restrained, precise design that grows out of the product itself."
---

# Toothpick: pick out the AI flavor, ship an interface that holds up

## What this guide is

There are no rules here like "always use this font" or "never use that color". You may use any color, typeface or layout.

It does two things:
1. **Helps you recognize the AI flavor**: which choices are an AI's unthinking defaults, and why people spot them instantly.
2. **Helps you avoid common flaws**: the mistakes that make an interface look rough, cheap or unprofessional.

There is one test: **was this choice made for this product, or would you have made it for any product?** The second is the AI flavor.

The user's explicit style, brand guidelines and existing code style always win, even when what they ask for is one of the "AI flavors" listed below.

---

## What the AI flavor is

On every design decision, an AI drifts toward the most common option. It comes in two layers.

**Layer one, the old clichés**: purple-to-blue gradients, emoji as icons, identical rounded cards with grey shadows, the "centered headline plus three feature cards" landing page, copy like "unlock limitless possibilities". Many people already recognize these.

**Layer two, pretending to have taste**: once told "don't make it look AI-generated", an AI switches to another, equally fixed outfit:
- Cream paper background, large serif headline, terracotta or deep red accent, posing as "warm and tasteful"
- Near-black background, one neon green, amber or vermilion accent, monospace everywhere, posing as "hacker"
- Newspaper-style black hairlines, zero border radius, dense columns, posing as "Swiss and professional"
- An all-caps label above every heading, "A · B · C" middle-dot strings everywhere, "→" after every link, monospace for every small data label, "01 / 02 / 03" on content that is not a sequence
- Huge decorative numbers, asymmetry for its own sake, a terminal "$" prompt or a "●" status dot used as decoration

Layer two is harder to notice because it looks "designed". It is the same problem as layer one: **the style was put on, not grown out of the product.**

The full list, with why each item reads as AI and when it is actually fine, is in `references/ai-tells.md`.

## What good interfaces look like

`references/benchmarks.md` has measurements from Vercel, GitHub, ChatGPT, Google and Linear. What they share:

- Very few colors: almost entirely black, white and grey, plus one functional color
- One type family; headings are large but not heavy
- Light separation: whitespace, pale thin outlines, very faint shadows, not black rules and heavy shadows
- The product itself is the hero; decoration is close to zero
- One focal point per screen

These are a reference, not a template. A coffee shop should not look like Vercel, but it should be just as restrained and precise, with the content in front.

---

## Workflow

### 1. Understand what this is: read the project first, then the visitor
- **In an existing project, read it before you touch anything.** Before any plan or code, find out:
  - Which features the project really has (read the README, routes, pages and API; do not guess from page titles)
  - Existing components, style variables, icon set and fonts. New UI uses them; do not start a parallel system
  - The data model and the real fields the API returns. Build the UI on those fields
  - The existing vocabulary in the copy. Keep calling the same thing by the same name

  Write down in a few lines "what the project has", and base the plan on it. For anything you cannot read (for example, the backend is not in the repo), ask the user or state your assumption plainly.
- What is the product or content? Who is it for? If this is unclear, make a concrete assumption, say it in one line, and move on instead of asking repeatedly.
- **Decide the mode of this page** (judge the page, not the product: a developer tool's homepage is Persuade, its dashboard is Operate):

| Mode | What success means for the visitor | Examples | Where the design effort goes |
|---|---|---|---|
| Persuade | Decides and acts | Homepage, landing page, campaign, pricing | A point of view and impact; persuade with real imagery |
| Operate | Completes a task | Admin, dashboard, editor, settings, tools | Scannable, consistent, efficient; personality lives in precise details |
| Read | Understands the content | Docs, articles, help center, changelog | Clear structure, a comfortable reading experience |
| Showcase | Is immersed in the work | Portfolio, gallery, case studies | The work leads, the interface recedes |

  Matching references: Persuade and Showcase use `references/web.md`, Operate uses `references/app-desktop.md`, mobile additionally uses `references/mobile.md`. Project READMEs and the mind maps or diagrams inside them use `references/readme.md`.
- **Refinement or redesign?** A refinement keeps the existing style, copy and behavior and changes only what is in scope. A redesign replaces the overall look but keeps product facts, content and features. Do not patch a new style onto the old one halfway.

### 2. Inventory what belongs only to this subject
Write down 8–12 concrete things that **belong to this client and to no competitor**: the name and what it means, the street and city, the door number and shop sign, materials and colors, its numbers (seats, altitude, years in business), its constraints (one batch a month, closed in winter), its rituals (the oven is lit at five), the printed things of its world (receipts, labels, timetables).

Design ideas come from this list, not from "what websites in this industry usually look like". An open-source skill we drew on ran blind tests: the winning pages used items from such a list; the losing pages had good compositions built on generic industry ideas.

### 3. Write the argument before choosing sections
Every section of a marketing page should be **a claim plus its evidence**, one line each:
```
Hero: three roasts this week, shipped Friday → evidence: three bags, the roast date
Beans: each one has a clear origin and flavor → evidence: real origin, altitude, cupping notes
...
```
Delete any section without a claim. This keeps you out of the stock "hero, logo wall, three features, testimonials, pricing, FAQ" structure.

### 4. Write a short plan
- Color: 4–6 values, each with where it is used
- Type: which typefaces and what each one does
- Layout: one sentence on the idea, a simple ASCII wireframe if useful, and the alignment
- Hero: the most persuasive thing on this page, and which assets you **actually have** (do not design around images that do not exist)

### 5. Check the plan: default or choice?
- Given a similar brief, would I arrive at roughly the same plan? If yes, that part is a default; go back to the list from step 2 for ideas.
- Does it hit anything in `references/ai-tells.md`? If yes, change it, or be able to say why this product needs it.
- Is there more decoration than content?

Say briefly in your reply what you changed and why.

### 6. Build
- Manage colors and spacing with CSS variables. Watch selector specificity so classes do not override each other (section padding especially).
- Example content is real and specific, and the numbers add up.
- When the page shows the product's interface (for example the screenshot slot on a SaaS homepage), build it as a real fragment of that product: real data, numbers that add up, one clear finding. Not grey blocks and fake numbers.
- Craft details are in `references/craft-details.md`.

### 7. Look at the result, fix in batches, then remove one thing
- Look at real sizes: desktop, phone (about 375px), dark mode if you built it. Look once, fix everything together; do not screenshot after every tweak.
- Go through `checklist.md`.
- Like checking the mirror before leaving the house, remove one accessory.

### Restraint is not emptiness
Removing decoration is only half the job. A page that lost its labels, rules and cards and gained nothing in their place reads as thin, and can lose to a richer page that still has some AI flavor. The other half is **substance**: bolder type scale, whole fields of color, real pictures of this subject's world, every section filled with its full content.

When you deliver, explain the design idea in a sentence or two so the user can redirect easily, and attach the placeholder list (see "Fake nothing, fool no developer").

### When the user asks for changes
| The user says | It means |
|---|---|
| Bolder | Bigger scale contrast, whole fields of color, a larger hero. Not more decoration |
| Quieter / too busy | Fewer colors and less motion, fewer type sizes, remove secondary elements |
| Simplify | Delete sections and elements without a claim; keep the core |
| More polish | Craft: alignment, spacing, radius, shadows, states, browser-native parts |
| Is it ready to ship? | Errors, empty states, very long content, other languages, edge cases |

---

## Fake nothing, fool no developer

Users and developers should both be able to tell what is real and what is not done yet.

**Nothing fake in front of end users**
- No invented logos, customer logo walls or partner badges. No fake logo assembled from symbols like "$", "▲" or "●"; without a logo, the product name in plain text is enough.
- No invented user counts, satisfaction rates, growth figures, testimonials or press mentions.
- Check professional facts (technical details, standards, regulations, data) before writing them. If you cannot get it right, leave it out.

**Nothing that fools the developer**
- **No invented features**: every feature shown in the interface exists in the project or was explicitly requested. Do not add "smart recommendations" or "one-click export" to make the page look better.
- **Mock data never poses as real data**: connect the real API when you can. When you cannot, keep mock data in one place (for example `mock/`), with the same fields as the real API, and mark it as mock in the code. Do not hard-code attractive numbers into components so the page looks "done".
- **No fake interactions**: a button, form or link that is not wired up must not get a click animation that pretends it works. Disable it and label it "not connected", or list it in the delivery notes.
- **Demos and concepts built from scratch** may use a fictional brand and data, but the page must say it is an example.

**Attach a placeholder list when you deliver**

List in your reply what still stands between this and a real launch, for example:
```
Placeholders
- Mock data: mock/orders.ts (fields follow the GET /api/orders response)
- Not connected: "Export CSV" button, "Subscribe" form submission
- To replace: homepage testimonials [TODO], product screenshot [TODO]
- Assumptions: refunds have only three states (pending, refunded, declined), please confirm
```
If there are none, write "None".

## Copy

Words are part of the design; boilerplate reads as AI as much as a templated layout.
- Say what it is and what it does instead of selling: ❌ "Unlock your team's potential" ✅ "Turn meeting recordings into a to-do list"
- Buttons say what will happen: ❌ "Submit" ✅ "Save changes". Use the same word for the same action throughout the flow.
- Errors say what happened and how to fix it; no apologies, nothing vague.
- Empty states tell the user what they can do next.
- No labels, subtitles or slogans that do no work.

## Quality floor

Not worth announcing, but always required:
- Enough text contrast (body text at least 4.5:1)
- Visible keyboard focus
- Hover, pressed and disabled states on every interactive element
- No horizontal scrolling, overlap or clipping at phone width
- Respect the system's reduced-motion setting
- Loading, empty and error states are designed too
- Dark mode is not a simple inversion (see `references/big-company-details.md`)

## Reference files

| File | Contents |
|---|---|
| `references/ai-tells.md` | The AI-tell list: what it is, why, and when it is fine |
| `references/benchmarks.md` | Measurements from Vercel, GitHub, ChatGPT, Google and Linear |
| `references/craft-details.md` | Craft details: radius, shadows, alignment, icons, interaction, forms, browser-native parts |
| `references/readme.md` | How to structure and write a project README, and how to design the mind map inside it |
| `references/big-company-details.md` | Details from Apple, Google, IBM and Microsoft guidelines (dark mode, motion, hit targets) |
| `references/typography.md` | Typography principles and the technical notes for CJK fonts |
| `references/color.md` | Approach to color and implementing dark mode |
| `references/web.md` | Common problems on websites and marketing pages |
| `references/app-desktop.md` | Common problems in software, admin and desktop apps |
| `references/mobile.md` | Common problems on mobile |
| `checklist.md` | Questions to ask while reviewing screenshots |
