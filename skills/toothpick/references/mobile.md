# Mobile

For: iOS and Android apps, mini programs, mobile web.

The core constraints of mobile: **small screens, fingers, often one hand, fragmented attention**.

## Sizes

- Design at 375pt (iPhone) or 360dp (Android), and also check 320 and 430 widths.
- Hit areas at least 44×44pt (iOS) or 48×48dp (Android), with at least 8px between adjacent targets.
- Body text 16–17px (iOS default 17pt), never below 12px. Input text at least 16px, or iOS Safari zooms the page on focus.
- Side margins 16–20px.

## Safe areas

- No content or buttons under the notch, the Dynamic Island or the home indicator.
- On the web, use `env(safe-area-inset-*)` and add `viewport-fit=cover` to the viewport meta tag.
- Fixed bottom buttons add the bottom safe-area height.

## Layout and navigation

- Primary navigation in a bottom tab bar (3–5 items), within reach of a thumb.
- The most important action sits in the lower half of the screen.
- Back: iOS supports swiping from the left edge, Android has the system back button or gesture. Do not intercept them.
- Lists first, cards second. Nested cards waste even more space on mobile.
- Split long forms into steps, a few questions each.

## Interaction

- There is no hover: anything revealed on hover must become tappable or always visible.
- Pressing gives immediate feedback (darken, scale to 0.97, or a ripple) within 100ms.
- Common gestures: pull to refresh, swipe on list items, long press for a menu. Every gesture also has a visible button.
- Prefer bottom sheets to centered dialogs; they are easier with one hand.
- Show the right keyboard for the input: `inputmode="numeric"`, `type="email"`, `type="tel"`.
- When the keyboard opens, the focused input and the submit button stay visible.

## Platform differences

| | iOS | Android |
|---|---|---|
| Font | SF Pro / PingFang | Roboto / the system CJK font |
| Title bar | Centered title (large titles can be left aligned) | Left-aligned title |
| Back | Back button at top left plus edge swipe | System back |
| Primary action | Top right of the navigation bar, or at the bottom | A floating action button (FAB) is an option |
| Switches, pickers | System style | Material style |

For native apps, follow each platform's conventions. For cross-platform apps or mobile web, pick one consistent style, but keep back behavior native.

## Perceived performance

- Skeletons instead of spinners.
- List images show a placeholder color first (the image's dominant color is even better).
- Apply actions in the UI first and sync in the background (optimistic updates); report failures afterwards.
- Make weak or no connectivity explicit, and keep loaded content browsable.

## Mini programs and mobile web

- Mini programs respect the platform's capsule button; do not put your own buttons in the top right.
- On mobile web, prevent layout problems from double-tap zoom, but never disable pinch zoom (it hurts accessibility).
- The layout must not break in landscape.
