# Themes

`template.html` ships four themes, each a complete CSS custom-property
override, picked by `<body data-theme="...">`. The default (no attribute) is
the dark theme defined on `:root`.

| `data-theme` | Feel | Good for |
|---|---|---|
| *(omit)* | Dark, cool, green accent | Technical content, engineering updates, default choice |
| `light` | Light, blue accent | Business/exec audiences, printed handouts, projector glare |
| `warm` | Dark brown/orange | Narrative or product-story content, less "dashboard" |
| `mono` | Near-black/white, no color accent | Content where color would be noise - dense data, legal/formal |

Pick one deliberately based on the content and audience - don't default to
the dark theme reflexively just because it's listed first. A deck for a
formal external audience probably wants `light`; a product pitch might want
`warm`; a deck that's mostly a data table might want `mono` so the data's
own color-coding (if any) doesn't compete with the theme's.

## Adding a theme

Copy one of the `[data-theme="..."]` blocks in `template.html`'s `<style>`
and change only the variable values - every rule in the stylesheet reads
`var(--bg)`, `var(--accent)`, etc., never a literal color, so a new theme
block is the only change needed. Keep the same variable names; don't add new
ones unless you're also updating every rule that should use them.

Contrast matters more than hue: keep `--fg` on `--bg` and `--accent` on
`--bg-elevated` both clearly readable - a deck is often viewed on a
projector or a scuffed laptop screen, not a calibrated monitor.
