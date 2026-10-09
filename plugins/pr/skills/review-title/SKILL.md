---
name: review-title
description:
  How to judge whether a pull request title is appropriate — Conventional Commits format, and whether the chosen type matches what the diff does.
  Load this whenever reviewing a pull request, and whenever asked to check, fix, or suggest a PR title.
---

# Pull request titles

Judge whether the title will still make sense to someone reading `git log` a year from now.
Pull requests here are squash-merged, so the title becomes the commit message verbatim and cannot be corrected without rewriting history.

Judge from the title, the diff, and the linked issue already gathered in this session.
Do not fetch them again.

Never edit the title yourself.
Propose a replacement and leave the change to the author.

## Format

Follow the [Conventional Commits v1.0.0 spec](https://www.conventionalcommits.org/en/v1.0.0/), with two local restrictions: no scope, and no breaking-change marker.
This repository uses neither, so `feat(api)!: ...` is wrong here even though the spec allows it.

Accept only the types below.
The spec itself defines `feat` and `fix`; the rest come from [`@commitlint/config-conventional`](https://github.com/conventional-changelog/commitlint/blob/1d92a16a1c4f48f9e6f98a4a150294895216ea61/%40commitlint/config-conventional/src/index.ts).

| type | meaning |
| --- | --- |
| `build` | Changes that affect the build system or external dependencies |
| `chore` | Other changes that don't modify src or test files |
| `ci` | Changes to CI configuration files and scripts |
| `docs` | Documentation only changes |
| `feat` | A new feature |
| `fix` | A bug fix |
| `perf` | A code change that improves performance |
| `refactor` | A code change that neither fixes a bug nor adds a feature |
| `revert` | Reverts a previous commit |
| `style` | Changes that do not affect the meaning of the code |
| `test` | Adding missing tests or correcting existing tests |

## Type against the diff

Read the diff and determine what the change does.
A valid format with the wrong type is the more common failure, and nothing mechanical will flag it.

Treat changes confined to workflow files as `ci`, not `feat` or `chore`.
Reject `feat` for work described as provisional, trial, or experimental; `feat` claims a capability someone can now rely on.
Look again at new source files under a `chore` or `docs` title.
Prefer any other type over `chore`; an unclear change tends to land there by default.

Take the dominant type for mixed changes.
Suggest splitting the pull request when no type dominates.

## Against the issue

Check that the title describes what the linked issue asked for.
A title that names the implementation where the issue asked for an outcome reads as a non sequitur in `git log`, where the issue is no longer at hand.

## Output

Write nothing when the title is appropriate.

Raise a single item when the title is wrong, and list the replacements in order of preference, each with a short reason.
Correct the type and the format only; how the author words their own change is their call, unless the wording misleads.
