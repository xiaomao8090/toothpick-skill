# READMEs and mind maps

For: project READMEs, GitHub landing pages, documentation home pages, and the mind maps, structure diagrams and flowcharts inside a README.

A README is "Persuade plus Read": first make people understand within seconds what this is and whether it is worth using, then let them install and use it without friction.

---

## 1. Readers give you a few seconds

Someone opening a README needs three answers within seconds: **what is this, what does it do for me, and why should I believe it.**

So the first screen holds only three things:
1. **The name**
2. **One sentence**: specific enough that the reader can decide "do I need this". ❌ "A powerful design tool" ✅ "A skill that helps AI spot the AI flavor when building interfaces"
3. **One piece of visual evidence**:
   - Projects about results (design, images, typography): a before and after from the same input
   - Tools (CLIs, libraries): a screenshot of a real run, or a 3–8 second animation
   - Interface projects: a screenshot of the product interface

Under the image, say in a sentence or two what it shows. Do not make the reader guess.

## 2. Order sections by the reader's questions

The questions in the reader's head, in order:
1. What is this? (first screen)
2. How is it different from similar projects?
3. How do I install it?
4. How do I use it, and how does it work? (a good place for a mind map or flowchart)
5. Is there evidence? (examples, comparisons, data)
6. What are the limitations?
7. File structure, contributing, credits, license

Order the README this way, not by the project's directory structure. Internal details like the file tree go near the end.

## 3. Make it scannable

- **Headings state the conclusion**: "No style library", not "Features"
- **Bold the first sentence of each paragraph**, so reading only the bold text gives the gist
- **Use tables for things people compare**: install methods per platform, versions, options
- **Code blocks run as pasted**; no explanations inside commands
- **Fold long content**: full lists, FAQs and changelogs go in `<details>` so the main line stays short

## 4. Credibility comes from real things

- **Only real badges**: license, version, build status. None if you have none
- **Never invent**: star counts, downloads, "used by 1000+ teams", testimonials, company logo walls
- **Write a "Limitations" section**: say plainly what it does not do and when it does not fit, ideally with a real example
- **Credit your sources**: which projects you drew on, which you did not adopt and why
- **Examples are reproducible**: give the paths to example files so readers can open them

## 5. The AI flavor in READMEs

| Looks like | Why it reads as AI | Fine when |
|---|---|---|
| An emoji before every heading: 🚀 Quick start, ✨ Features, 📦 Install | Templated; the emoji carry no information | A playful community project, consistent throughout |
| A row of colorful badges | Quantity posing as activity | Every badge is information readers actually check |
| A "Features" list of "powerful", "flexible", "easy to use" | Empty words that fit any project | Each item says concretely what it does |
| A big centered logo and slogan, with the explanation only further down | The first screen does not answer "what is this" | A famous project everyone already knows |
| "⭐ Star us if you like it!" at the end | Boilerplate | Not needed |
| A table of contents longer than the content | Readers scroll a long way to reach the point | Long documentation-style READMEs where a TOC really helps |

## 6. Craft details on GitHub

- **Switch images for dark mode** with `<picture>`; readers using GitHub's dark theme see the dark version automatically
  ```html
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="docs/mindmap-dark.png">
    <img alt="Say what this image shows" src="docs/mindmap-light.png">
  </picture>
  ```
- **Alt text on every image**, so readers know what is there when it fails to load or when using a screen reader
- **Sharp images**: export at 2x, keep each one to a few hundred KB
- **Motion**: GitHub accepts video uploads, which are much sharper and smaller than GIFs; keep a GIF under 8 seconds, with a first frame that makes sense on its own
- **Screenshots with real content**: no lorem ipsum, no "Example project 1, Example project 2"
- **Reference images by relative path** from a folder such as `docs/` in the repo; do not depend on external image hosts

## 7. Bilingual and multilingual READMEs

- **One file per language**: `README.md` is the default (usually English for an international project), with `README.zh-CN.md` and so on alongside
- **A language switcher on the first line** of every version, for example `English | 简体中文`, with the current language as plain text and the others as links
- **Keep versions in sync**: same sections in the same order; when one changes, change the others in the same commit
- **Localize images that contain text**: a mind map or diagram with words in it needs one version per language (and per light/dark theme)
- **Do not machine-translate word for word**: rewrite headings and examples so they read naturally in each language; keep code, commands and file names identical

---

## 8. Mind maps

A mind map in a README answers "what parts make up this project, and how does it work". It is an explanatory figure, not decoration.

### First decide whether to draw one
- Only two or three parts → a paragraph or a list is enough
- The parts happen in order → draw a flowchart, not a mind map
- Several parallel parts, each with content underneath → a mind map fits

### Structure
- **Center**: the project name and one sentence on what it does
- **4 to 7 branches**. More cannot be taken in at a glance; fewer is better as a list
- **2 to 7 leaves per branch**
- **Leaves carry real content**: a key word plus a line of grey detail, such as "Old clichés: gradients, emoji icons, card kits", not just "Old clichés"
- **Split the two sides by role**: for example, the left side says "what it is", the right side "how to use it"
- **Number only real steps**

### Visual
| Common AI approach | Instead |
|---|---|
| One color per branch, a rainbow | Mostly black, white and grey; one accent color on the single most important branch |
| An emoji on every node | No icons; hierarchy through size and weight |
| Every node the same size | The center is heaviest (a dark block), branch names large and bold, leaves small on a light background |
| Thick, dark connectors with arrowheads | Thin, light grey curves; the accented branch's line uses the accent color |
| Nodes crammed together, text cut off | Leaf text does not wrap; generous space between branches |

- **Export both light and dark versions** and place them with `<picture>`
- **Size**: design at about 1600px wide and export at 2x; GitHub's content column is about 900px wide, and leaf text must stay readable when scaled down
- **Keep the source**: draw the map in HTML or SVG and commit the source, such as `docs/mindmap.html`, so changes do not require redrawing
- **Mermaid works too**: GitHub supports the `mindmap` syntax and it is the easiest to edit, but the default colors are a rainbow and the styling is hard to control. Fine for internal docs; for a public README, a custom drawing is better

### Where it goes
At the start of the "how it works" section, after the reader already knows what the project is. Not on the first screen: that space is for the evidence image.

---

## Self-check
- From the first screen alone, could someone who has never heard of the project say what it does?
- Reading only headings and bold text, does the whole thing make sense?
- Any invented numbers, badges or testimonials?
- Is there a "Limitations" section?
- Do images work in dark mode, and do they all have alt text?
- Shrunk to 900px wide, is the mind map's leaf text still readable?
- For multilingual READMEs: does every version have the language switcher, and are the sections in sync?
