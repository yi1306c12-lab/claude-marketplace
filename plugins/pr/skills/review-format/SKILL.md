---
name: review-format
description:
  The required layout for a review comment — Conventional Comments labels, blocking and non-blocking decorations, and the split between Requested changes and Tips.
  Load this whenever writing a review, and whenever asked how a review should be laid out.
---

# Review format

Follow [Conventional Comments](https://conventionalcomments.org/).
Open every item with a label, and every item under `Requested changes` with a decoration as well.

Never leave the strength of a request to be inferred from its label.
The label says what kind of remark it is; the decoration says how strongly it is being asked for, and `nitpick` and `issue` can each be either.

## Sections

Write two sections, in this order: `Requested changes`, then `Tips`.

Use only these two, however many things you looked at.
A title that needs changing is an item under `Requested changes` like any other finding, and a title checked and found fine is a `note` under `Tips`.

Keep the two apart.
Mixing them makes a review impossible to answer point by point.

Put section headings at `##`, and items under `Requested changes` at `###`.

State explicitly when a section has no items.
A silent section reads as an oversight rather than a clean result.

## Labels

Use only these labels.

| label | meaning | section |
| --- | --- | --- |
| `issue` | something is wrong and has to change | Requested changes |
| `suggestion` | a concrete alternative worth adopting | Requested changes |
| `question` | an answer is needed before the change can be judged | Requested changes |
| `nitpick` | preference only; declining it costs nothing | Requested changes |
| `note` | background, operational detail, or a point checked and found fine | Tips |
| `praise` | something worth keeping as it is | Tips |

## Decorations

Use only `(blocking)` and `(non-blocking)`.

- `(blocking)` — the pull request is not merged until this is applied or explicitly declined.
- `(non-blocking)` — the pull request can be merged as it is; the item may be handled later or not at all.

Write a decoration on every item under `Requested changes`, even where the label seems to make it obvious.
Write none on items under `Tips`; the section already says nothing is being asked for.

## Requested changes

Give each item its own heading:

    ### <n>. <label> (<decoration>): <subject>

Put the reason, and any proposed content, in the body under that heading.
A heading gives the item an anchor the author can link to, and keeps code blocks out of list indentation.

Number the items continuously across the whole section, so that each can be accepted or declined by number.
Do not restart the numbering per label.

Order `(blocking)` items before `(non-blocking)` ones.

Cite the location as `path:line`, and give the reason rather than just the instruction.
The author needs enough to disagree with you.

Never speculate.
Say what you could not verify when verifying was not possible in this environment, instead of reporting it as a finding.

## Tips

Put everything for which no change is requested here: background, alternatives considered and rejected, operational notes, and points checked and found fine.

Write these as unnumbered list items rather than headings, so that the section is unmistakably not a to-do list:

    - <label>: <subject>
