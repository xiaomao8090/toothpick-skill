# Software, admin and desktop apps

For: SaaS apps, admin panels, dashboards, editors, desktop clients, internal tools.

The goal of software UI is that **people can use it for hours every day without tiring, and get faster over time**. It does not need to dazzle at first sight; it needs to be clear, stable and efficient. The most common AI mistake is to make it a marketing page.

The values below are common practice for reference (measurements of GitHub and ChatGPT are in `benchmarks.md`), not hard requirements. Adjust them to the product.

## Information density

- Common density: body text 13–14px, table rows 32–41px, form controls 32–36px (GitHub repository page: 14px body, 41px rows, 32px buttons).
- Whitespace groups things; it is not there to "look premium". The more useful information fits on a screen without crowding, the better.
- Consider a density toggle (compact / comfortable), especially in table-heavy products.

## Layout

- The classic structure: collapsible sidebar on the left, a top toolbar or breadcrumb, the main content area, and a detail panel on the right when needed.
- Keep the page header short: title and primary actions on one line, not a large heading with a paragraph under it.
- Delete greeting banners like "Welcome back, Alex! 👋".
- The content area spans the full width (tables) or is constrained (forms and settings, about 640–800px).

## Tables (the heart of an admin)

- Text left aligned, **numbers right aligned** with tabular figures (`tabular-nums`) so decimal points line up.
- Header text slightly smaller and lighter, optionally all caps (Latin) or bold, sticky at the top.
- Separate rows with hairlines or zebra stripes, not both.
- Highlight rows on hover; selected rows use a very light tint of the accent.
- Sorting (with the state shown in the header), filters where needed, pagination or virtual scrolling.
- Truncate very long text with an ellipsis and show it in full on hover.
- Action column: one or two common actions visible (or on hover), the rest in a "More" menu.
- An empty table explains why it is empty and offers the next step.

## Forms

- Labels above inputs (easiest to scan); never use the placeholder as the only label.
- Group related fields, with more space or a small heading between groups.
- Mark only the minority: required or optional, whichever is fewer.
- Validate on blur; put the error under the field and say how to fix it (❌ "Invalid format" ✅ "Phone number should be 10 digits").
- The primary button sits at the end of the form, following reading order; destructive actions (delete) are separated from the primary action and need confirmation.

## States (design all of them)

| State | What to do |
|---|---|
| Loading | Skeletons keep the layout still; show a loading indicator only after 300ms |
| Empty | Explain why it is empty plus one next-step button; first use and "no filter results" are two different empty states |
| Error | Say what happened and what the user can do (retry, who to contact); never just an error code |
| No permission | Say which permission is needed and who grants it |
| Partial data | Show "—" for empty fields, never null, undefined or a blank |
| Feedback | A light toast for successful saves (gone after 2–4 seconds); progress for long operations |

## Dashboards

- First ask: what **decision** does the user make each day when opening this page? Show only what supports that decision.
- Every number has context: compared with what (last week? the target?), and is it good or bad.
- Not four identical stat cards in a row. Key metrics can be larger, secondary ones smaller and tighter.
- Chart choice: lines for trends, bars for comparison, pie charts rarely (never with more than 5 categories). Chart colors: greys plus one or two highlight colors, not a rainbow.
- When you need a chart, the chart title states the finding ("Refund rate up 2% from last week"), not "Refund rate trend".

## Interaction and efficiency

- **Keyboard**: shortcuts for common actions, shown in tooltips or menus; sensible Tab order, Esc closes dialogs, Enter submits.
- Consider a command palette (Ctrl/⌘ + K) for feature-rich products.
- Bulk actions: selecting multiple items reveals a bulk action bar at the top or bottom.
- Do not confirm reversible actions; show "Deleted. Undo" instead. Confirm only what cannot be undone.
- Remember the user's choices: filters, sorting, column widths, sidebar state.
- Very little motion: 100–200ms transitions for expand/collapse and appear/disappear only.

## Desktop clients

- Follow platform conventions: on macOS window controls are on the left and menus live in the system menu bar; on Windows controls are on the right.
- Follow the system's light/dark setting and accent color (if the framework supports it).
- On macOS, do not put critical controls at the very bottom of a window (people often drag windows partly off screen).
- The layout still works at the minimum window size; set a minimum window size.
- Provide context menus, consistent with the actions in the main menu.
- Default text is 13px on macOS (the system default) and about 14px on Windows.

## Navigation

- No more than 7–9 top-level items in the sidebar; group them with small headings beyond that.
- The current location is clear: highlighted navigation plus breadcrumbs for deep hierarchies.
- Icons with text; when collapsed to icons only, show the label on hover.
