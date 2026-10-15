<h1 align="center">html-slide-deck</h1>

<p align="center">
  A Claude Code skill that builds a single, self-contained HTML slide deck -<br/>
  no build step, no npm, no dependencies, no account - that opens directly in any browser.
</p>

---

## Why this matters

**The deck you need right now is rarely one you'll pull from a template library.** It's a recap of findings from this session, a quick pitch, a walkthrough you want in front of someone in the next five minutes. Needing an account, a login, or an export pipeline before you can even start is friction that kills momentum on exactly the decks that matter most: the ones born out of a conversation that's still fresh.

This skill skips all of that. One `.html` file, nothing to install, nothing to publish, open it in any browser you already have. The real work it does for you isn't CSS, it's deciding how much a slide can hold before it should split and when a table beats a bullet list, the part of deck-building that actually takes judgment.

**One honest limit:** this isn't a PowerPoint or Google Slides replacement. If someone downstream needs to open your deck in Office and edit it themselves, hand them a different format, this one is built to be viewed and presented, not re-edited in another tool.

## What it does

Ask for a slide deck, a presentation, or a "deck" from a document, a
conversation, or a set of findings, and this skill builds one `.html` file:
a full-viewport slide per section, keyboard/button/swipe navigation, a page
counter, and a print stylesheet that already produces one PDF page per
slide - all inline, nothing to install on the other end, nothing to
publish.

The CSS/JS shell is the easy part. The actual value is
[`references/content-structuring.md`](references/content-structuring.md):
explicit rules for how much text fits on a slide before it should split,
when a comparison table beats bullet points, and how to compress a long
document into slide-sized chunks without losing the substance. That's the
part that's hard to get right, and it's the part most "make me a slide
deck" tools skip.

## Install

```
/plugin install html-slide-deck --marketplace thisismairaj/html-slide-deck
```

Then just ask: "turn this into a slide deck," "make me a presentation from
this," "I need a pitch deck for X."

## Seven slide types, four themes

| Type | Use for |
|---|---|
| `title` | The deck's opener |
| *(plain)* | Bullets - the default: a flat list, steps, supporting points |
| `section` | A divider marking a real change of subject |
| `compare` | 2-4 things held up side by side |
| `table` | A real comparison across 2+ shared dimensions |
| `stat` | Exactly one number worth remembering |
| `quote` | One short, attributed line |

Four built-in themes (`default` dark, `light`, `warm`, `mono`), each a
complete CSS custom-property swap - see
[`references/themes.md`](references/themes.md). Adding a new theme is
copying one block and changing the values; every rule in the stylesheet
reads a variable, never a literal color.

## Examples

Three real decks in [`examples/`](examples/), each a genuinely different
content type, to show the slide-type and theme choices actually vary with
the content rather than defaulting to the same shape every time:

- [`technical-findings.html`](examples/technical-findings.html) - a
  findings recap (dark theme; stat, table, compare, bullets)
- [`product-pitch.html`](examples/product-pitch.html) - a short product
  pitch (warm theme; quote, stat, bullets)
- [`tutorial-walkthrough.html`](examples/tutorial-walkthrough.html) - a
  how-it-works walkthrough (light theme; section, table, bullets)

Open any of them directly in a browser - arrow keys, spacebar, on-screen
buttons, or swipe to navigate; Ctrl/Cmd+P for a one-slide-per-page PDF.

## How it works

`SKILL.md` is the workflow: find the 3-5 things the audience should walk
away remembering, pick a theme deliberately, choose each slide's type by
the shape of its content (not a default), build from `assets/template.html`
by copying and editing its labeled example slide blocks, then look at the
result before calling it done. The template holds the entire visual system
- styles, navigation script, print rules - so a new deck only ever adds or
edits `<section>` blocks, never new CSS or JS, unless a slide genuinely
needs a shape the template doesn't already have.

## Development

Built with the `skill-creator` workflow: a full draft, then a self-test
against three deliberately different content types (the `examples/`
decks above) to check the slide anatomy and content-structuring guidance
actually generalize, rather than just packaging the one reference template
that started it.

## License

MIT
