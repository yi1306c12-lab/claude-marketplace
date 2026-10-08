---
name: review
description:
  The procedure for reviewing a pull request — what to gather, in what order to judge the title, body, and diff, and where to post the result.
  Load this whenever asked to review, check, or look over a pull request, even when the request is phrased casually and even when no PR number is given explicitly.
---

# Reviewing a pull request

The pull request number is whatever number the request names.
If no number is given, use `$ARGUMENTS`.

## What you may write

The author writes every committed change by hand.
Your writes are limited to pull request bodies and comments.
When a file needs to change, put the proposed content in your review comment for the author to apply.

A request to review is not a request to commit.
Do not approve the pull request either; approval is the author's decision to seek elsewhere.

Keep scratch files under `tmp/` in the working tree.
Writes outside the working tree are refused, so `/tmp` will fail.

Pass long text as `gh ... --body-file <file>`, never inline with `--body`.
Backticks and `$` in a body would otherwise be expanded by the shell before GitHub ever sees them.

## Your process

### 1. Gather

Fetch these once.

- `gh pr view <number> --json title,body,headRefName,files`
- `gh pr diff <number>`
- The linked issue, from `gh pr view <number> --json closingIssuesReferences`.
  - Branches are created with `gh issue develop`, which is what establishes that link. If it comes back empty, fall back to the leading number of the head branch name.

If there is no linked issue, say so and review from the diff alone.

If a fetch fails, note which one and continue with the rest.
Say in the report what you could not read, so nobody mistakes a gap for a clean result.

### 2. Judge the title

Follow the `pr:review-title` skill.

### 3. Write the body

Follow the `pr:edit-body` skill.

Do this before reviewing the diff.

### 4. Review the diff

Report:

- bugs
- security problems
- performance problems
- inconsistencies with the surrounding code

Cite each finding as `path:line` and give the reason, not just the instruction — the author has to be able to disagree with your reasoning.

Never speculate: if verifying a finding was not possible in this environment, say what you could not verify rather than guessing at it.

### 5. Report

Format the report as described in the `pr:review-format` skill.

Write the report to `tmp/pr-review.md` and post it with `gh pr comment <number> --body-file tmp/pr-review.md`.

Write it in Japanese.
Everything posted to GitHub is written in Japanese, even though this file and the rest of the repository's instructions are in English.
