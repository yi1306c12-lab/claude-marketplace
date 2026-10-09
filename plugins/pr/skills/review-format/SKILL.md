---
name: review-format
description:
  The required layout for a review comment — Conventional Comments labels, blocking and non-blocking decorations, and the split between Requested changes and Tips.
  Load this whenever writing a review, and whenever asked how a review should be laid out.
---

# Review format

Follow [Conventional Comments](https://conventionalcomments.org/) under the `Requested changes` section.

Never leave the strength of a request to be inferred from its label.
The label says what kind of remark it is; the decoration says how strongly it is being asked for, and `nitpick` and `issue` can each be either.

## Sections

Write two sections, in this order: `Requested changes`, then `Tips`.

Use only these two, however many things you looked at.

A title that needs changing is an item under `Requested changes` like any other finding.

Put section headings at `##`, and items under `Requested changes` at `###`.

State explicitly when a section has no items.
A silent section reads as an oversight rather than a clean result.

## Labels

Open each item under `Requested changes` with one of these:

| label | meaning |
| --- | --- |
| `issue` | something is wrong and has to change |
| `suggestion` | a concrete alternative worth adopting |
| `question` | an answer is needed before the change can be judged |
| `nitpick` | preference only; declining it costs nothing |

## Decorations

Use only `(blocking)` and `(non-blocking)`.

- `(blocking)` — the pull request is not merged until this is applied or explicitly declined.
- `(non-blocking)` — the pull request can be merged as it is; the item may be handled later or not at all.

Write a decoration on every item under `Requested changes`, even where the label seems to make it obvious.

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

## Tips

Report only what the diff cannot show:

- what you changed in the pull request body
- an unchecked claim that no finding rests on
- an input you could not read
- an alternative you weighed and rejected

Write each as an unnumbered list item, so that the section is unmistakably not a to-do list.
