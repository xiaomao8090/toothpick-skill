# Screenshot review checklist

After taking screenshots, look at them with these questions. The goal is to find problems, not to tick boxes.

## At a glance
- Cover the product name: could this page belong to any other product? If so, which layer is the problem: color, type, structure or copy?
- What do you see first? Is it the thing this page most needs you to see?
- Is there more decoration than content?
- Is anything "performing design": huge numbers, deliberate asymmetry, theme symbols, a style costume?
- The other way round: has the page been hollowed out? After removing decoration, did you add substance (type contrast, whole fields of color, real imagery, full content)?
- Does the page use the things from step 2 that belong only to this subject?
- Does every section make a claim? Were sections without one deleted?

## AI flavor (see references/ai-tells.md)
- Does it hit one of the style-costume combinations?
- Any template parts: labels above headings, "A · B · C", "→", numbering on things that are not steps, one word recolored?
- Any layer-one clichés: gradients, emoji icons, the card kit, blurry blobs in the background?
- If something hits, can you say why this product needs it? If not, change it.

## Craft
- Lines: too many, too dark? Could whitespace or a background tint do the job?
- Shadows: too heavy?
- Color: how many hues on one screen? What does each one say? Are the colors clean?
- Type: is the hierarchy clear? Are headings too heavy? Too many sizes?
- Spacing: consistent at the same level? Tight inside groups, loose between them?
- Alignment: does everything sit on the same set of guides?
- Radius: proportional to element size? Concentric when nested (outer = inner + padding)?
- Browser-native parts: selection color, caret color, scrollbars, focus rings, underline offset? (see references/craft-details.md)

## Content
- Does the copy say what it is and what it does, or is it selling?
- Any invented data, testimonials or logos?
- Does the interface show any feature the project does not have?
- Any hard-coded mock data posing as real data? Any buttons or forms that look like they work but are not connected?
- Does the new UI use the project's existing components and style variables?
- Were professional facts (technical, standards, data) checked?
- Is the placeholder list attached to the reply?
- Does the example data look real? Does very long content break the layout?
- Do button labels say what will happen?

## Quality floor
- At phone width (about 375px): any horizontal scrolling, overlap or clipping?
- Is text contrast sufficient?
- Can you see where focus is when pressing Tab?
- Are hover, pressed and disabled states all there?
- Were loading, empty and error states considered?
- Dark mode (if built): designed on its own, or a simple inversion?
- Does everything still work with reduced motion?

## README (if this is a README)
- From the first screen alone, could someone who has never heard of the project say what it does?
- Reading only headings and bold text, does the whole thing make sense?
- Any invented badges, numbers or testimonials? Is there a "Limitations" section?
- Do images have alt text? Do they work in dark mode?
- Shrunk to about 900px wide, is the mind map's leaf text still readable? (see references/readme.md)

## Finally
- Remove one unnecessary thing.
- Explain the design idea to the user in a sentence or two.
