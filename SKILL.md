---
name: html-slide-deck
description: Build a single, self-contained HTML slide deck - one .html file, inline CSS/JS, no build step, no npm, no external dependencies, no account or publishing platform required - that opens directly in any browser and prints cleanly to PDF. Use this skill whenever the user asks for a slide deck, a presentation, slides, or a "deck," or wants to turn a document, conversation, or set of findings into something presentable - especially when they want a plain file they can open and share immediately rather than a PowerPoint/Google Slides/Keynote file. Also trigger on requests for a pitch deck, a walkthrough deck, a team-update deck, or "something I can present from," even if the user never says "HTML" explicitly.
---

Build one self-contained `.html` file: a full-viewport slide per `<section>`,
keyboard/button/swipe navigation, a page counter, and a clean print
stylesheet - all inline, nothing to install, nothing to publish. The CSS/JS
shell is solved; getting the content structure right is the actual skill -
read `references/content-structuring.md` before writing slide content, every
time, even on a deck you've built many of. It's short, and it's easy to
default back to cramming without it.

## Workflow

1. **Understand the material and the audience.** If the user handed you a
   document, a conversation, or a set of findings, that's your source - don't
   ask them to re-summarize it for you. If they described the deck instead
   (topic, audience, length), work from that. Either way, confirm or infer:
   who's seeing this, roughly how long (a 5-slide update and a 20-slide pitch
   are different problems), and whether a plain file that opens in a browser
   is genuinely what's wanted here (versus a .pptx someone needs to edit in
   PowerPoint afterward - if so, this isn't the right skill).

2. **Find the 3-5 things the audience must walk away remembering.** Read
   `references/content-structuring.md`'s compression section for how to pull
   these out of a longer source without either transcribing everything or
   cutting until nothing concrete is left. These become the deck's spine -
   roughly one section per thing, for anything past a handful of slides.

3. **Pick a theme deliberately**, not reflexively. `references/themes.md`
   lists the four built in (default dark, `light`, `warm`, `mono`) and what
   each fits - match it to the audience and content, don't just take the
   first one every time.

4. **Choose each slide's type by the shape of its content**, not by default.
   Quick reference (full reasoning for each in `content-structuring.md`):

   | Type | Use for |
   |---|---|
   | `title` | The opener. One per deck. |
   | *(plain)* | Bullets - the default: a flat list, steps, supporting points. Max ~6 bullets, one line each. |
   | `section` | A divider marking a real change of subject, in decks long enough to have parts. |
   | `compare` | 2-4 things held up side by side, each with its own short list. |
   | `table` | A real comparison across 2+ shared dimensions for 2+ items - the grid itself is the information. |
   | `stat` | Exactly one number worth remembering. Use rarely, or it stops standing out. |
   | `quote` | One short, attributed line worth repeating verbatim. |

   A heading is a claim ("Hyperscale removes the 1 TB wall"), never a topic
   label ("Storage Limits") - if a point won't compress into a claim-shaped
   heading, you don't understand it well enough yet to put it on a slide.

5. **Build the deck from the template, don't start from a blank file.** Copy
   `assets/template.html` to the output path, then:
   - Set `<title>` and the `data-theme` attribute on `<body>`.
   - For each planned slide, copy the matching `<!-- SLIDE TYPE: ... -->`
     example block, edit its content, and remove the ones you didn't use.
     Duplicate a block for each extra slide of that type.
   - Leave the `<style>`, the footer, the progress bar, and the `<script>`
     untouched - they're the solved part. Don't invent new CSS classes or
     JS behavior unless a slide genuinely needs a shape the template doesn't
     have (see "Extending the template" below) - most content fits what's
     already there.
   - The result is the *entire* deliverable: one `.html` file, nothing else
     to generate, nothing to build.

6. **Open it and look at it** before calling the deck done - a slide that
   reads fine as markdown can still overflow its viewport or break the
   layout in an actual browser. Check the slide count against the planned
   structure, and skim for any bullet that reads like two ideas sharing one
   line.

7. **Mention printing** if it's relevant to how they'll use it: the deck's
   browser print dialog (Ctrl/Cmd+P) already produces one page per slide via
   the built-in print stylesheet - no separate export step needed.

## Extending the template

The six content slide types cover most real decks. If content genuinely
doesn't fit any of them (a code sample, an inline diagram), add a new
`.slide--<name>` block to the `<style>` the same way the existing ones are
built - CSS variables for color, nothing hardcoded - rather than reaching for
an external library or font. The "no external dependencies" constraint is
the point of this skill; an image needs to be inline (a data URI) or left
out, never a remote `<img src>`.

## What this skill is not for

- A deck that needs to be *edited* afterward by someone in PowerPoint or
  Google Slides - hand them a file they can't easily open in those tools.
- Speaker notes, animations beyond the slide-to-slide fade, or embedded
  video - all out of scope for a single dependency-free file; say so rather
  than half-implementing them.
- Anything where the "no build step, opens anywhere" constraint doesn't
  actually matter to the user - if they have PowerPoint open and just want
  slides in it, that's a different task.
