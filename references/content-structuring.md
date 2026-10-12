# Content structuring

This is the actual value of this skill. The CSS/JS shell is a solved problem;
deciding what goes on which slide, and when one slide should become two, is
not. Read this before filling in `template.html`, not after.

## The one-idea-per-slide budget

A slide is read in a few seconds, not studied. Budget accordingly:

- **A heading is a claim, not a topic label.** "Hyperscale removes the 1 TB
  wall" teaches the reader something before they've read a single bullet.
  "Storage Limits" teaches them nothing - it's a label for a folder, not a
  slide. If you can't compress the point into a heading, you don't know the
  point well enough yet; go back to the source material.
- **A bullets slide holds at most 5-6 bullets**, each one line at the deck's
  base size - roughly 10-14 words. If a bullet needs two lines to make its
  point, it is almost always two separate points wearing one bullet.
- **Total body text per slide, heading included, tops out around 60-90
  words.** Past that, the slide stops being something glanced at and becomes
  something read, which defeats the format.

## When to split one slide into two

Split, don't shrink. Shrinking the font or tightening the layout to fit more
text defeats the actual purpose of a slide (legible from the back of a room,
absorbed in seconds) - it's optimizing the wrong constraint.

Split when:
- A bullets slide would need more than ~6 bullets to say what it needs to say.
- The content mixes two claims that don't share one heading. If you find
  yourself writing a heading with "and" joining two different ideas, that's
  the seam - split there.
- A natural beat exists in the material (a transition, a new section of the
  source document). Promote that seam into a `slide--section` divider instead
  of just starting a new bullets slide - it tells the audience the subject is
  changing, not just continuing.

Two sequential slides under the same heading ("X, continued") are a legitimate
pattern when a single claim genuinely needs more supporting points than one
slide holds - better than violating the bullet budget to force it onto one.

## Choosing the right slide type for the content's actual shape

Don't default to bullets for everything. The content has a shape; match it:

- **`bullets`** - a flat list without a row/column structure: supporting
  points under one claim, sequential steps, a short list of features. The
  default, but not the only option.
- **`compare`** (card grid) - 2-4 things being held up side by side, each
  described by its own short list, where the things themselves (not a shared
  set of dimensions) are the organizing axis. "Three ways to install this"
  is a `compare`.
- **`table`** - a real comparison across 2+ shared dimensions for 2+ items,
  where the grid shape *is* the information. The tell: you keep writing
  sentences shaped like "A has X but B has Y, while A is Z and B is W" - that
  sentence is already a table that hasn't been drawn yet. If every item
  doesn't have a value for every dimension, it's not a table, it's a
  `compare`.
- **`stat`** - exactly one number the audience should walk away remembering.
  Use it rarely - a deck with five stat slides has no stat slide, because
  nothing stood out from the rest. Reserve it for the number that's actually
  the point.
- **`quote`** - a single short line worth repeating verbatim, attributed.
  Not a place to park a long explanation in italics.
- **`section`** - a divider with no body content at all, just a label. Use
  it to mark a real change of subject in a deck long enough to have parts
  (roughly 10+ slides); skip it in a short deck, where it's just a speed bump.

## Compressing a long document or conversation into slides

This is the hard part, and where most decks fail - either by trying to
include everything (nothing stands out) or by summarizing so hard the
substance disappears (nothing is actually said).

1. **Read once for the 3-5 things a reader must walk away remembering** - the
   actual decisions, numbers, or conclusions, not the topics discussed. These
   become your section headings (as claims, per above), and roughly the
   number of major sections in the deck.
2. **For each one, pull only the 2-4 facts that justify it.** Cut everything
   else: caveats that don't change the conclusion, context already implied
   by the heading, process narrative ("first we tried X, then Y, then
   finally Z worked") - unless the audience specifically needs the journey
   and not just the destination, in which case the journey *is* one of your
   3-5 things, not scaffolding around it.
3. **Numbers survive compression; adjectives don't.** "Cut load time 40%" is
   information. "Significantly improved performance" is filler wearing the
   shape of information - if the source material has a real number, use it;
   if it doesn't, don't invent one to sound more concrete than the source
   actually is.
4. **If you can't find 3-5 things**, the material may not need a deck. A
   single `stat` slide, or three `bullets`, might be the honest length - a
   padded 12-slide deck for a 3-bullet idea serves the format, not the
   audience.

## Worked example

Source: a long technical write-up about a database storage tier comparison,
including the history of how the numbers were found, several caveats, and a
final recommendation.

**Bad compression** (keeps everything, becomes a transcript):
> Slide: "Background" - 9 bullets covering the investigation's timeline.

**Bad compression** (cuts too hard, becomes meaningless):
> Slide: "Storage" - "Some tiers have more storage than others."

**Right compression** (claim headings, real numbers, right type per shape):
> Slide 1 (`stat`): **4 TB** - "the ceiling both Premium and General Purpose
> share, despite looking like different products"
> Slide 2 (`table`): **Where the ceilings actually land** - Premium/General
> Purpose/Hyperscale rows, Max storage + How it scales columns
> Slide 3 (`bullets`): **General Purpose is the right first move** - 3 bullets
> on why, pulled from the write-up's own recommendation section
