English | [简体中文](README.zh-CN.md)

# Test cases

Run the same set of briefs every time the skill changes; that is the only way to know whether a change made it better or worse.

## How to run

1. Pick a model and run every brief in `briefs.json` twice: once without Toothpick, once with it. Keep everything else the same.
2. Save each reply and page in `runs/<date>-<model>/<brief id>/`, in two folders, `without/` and `with/`.
3. When scoring, hide which is which and shuffle the order, score with the rubric below, then reveal which one had Toothpick.
4. Write the results to `runs/<date>-<model>/scores.md`. Run once before and once after changing the skill, and compare.

If the model can take screenshots, take one at desktop width (1280px) and one at phone width (390px).

## Rubric

Each item scores 0 or 1. The `watch` field lists what to look at for each brief.

| Item | How to judge |
|---|---|
| No AI tells | Hits nothing in `ai-tells.md`, or the reply explains why it needs what it hit |
| Belongs to the subject | With the name covered, you can tell which brief it is; it uses the brief's specific facts |
| Not like the last one | Placed next to the other results from the same run, it is not the same look |
| Nothing fabricated | No invented logos, testimonials, user counts or features |
| Placeholder list | The reply has one, and it matches the page |
| Sized correctly | No design plan for a small change; a plan for a large one |
| States covered | Operate screens have loading, empty and error states |
| Works on a phone | No horizontal scroll, overlap or clipping at 390px |
| Contrast | Body text contrast at least 4.5:1 |
| Honest review | If it never saw the result, it does not claim it did |

## Results so far

None yet. The four versions of the three demo sites, the manga version and the refund admin were iterated by hand on Claude and have not been scored with these cases. Codex and DeepSeek have not been run either.
