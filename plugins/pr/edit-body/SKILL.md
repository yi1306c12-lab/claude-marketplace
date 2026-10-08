---
name: edit-body
description:
  How to rewrite the body of a pull request so that each change maps to the part of the issue it addresses.
  Load this whenever reviewing a pull request, and whenever asked to write, rewrite, or improve a PR description.
---

# Pull request bodies

Apply the body directly rather than proposing it.
A pull request body is pull request text, not code, so writing it is within what you may write.

Work from the diff and the linked issue already gathered in this session.
Do not fetch them again.

## What the body is for

Map each change to the part of the issue it addresses.
The issue says why the change is needed; the body says how this change answers it.

Do not restate the issue.
Restating it wastes the reader's time and hides the one thing they came for: whether the change covers what was asked.

Call out changes that fall outside the issue, with the reason they were needed.
These are the ones most likely to surprise a reviewer, and leaving them unmentioned is how unrelated work slips in unnoticed.

Describe what changed and why from the diff alone when no issue is linked, and say that none was.

## What to keep

Keep whatever the author already wrote.
They know things about the change that the diff does not show.

Add structure and the issue mapping around the existing text rather than replacing it.

## Applying it

Write the body to `tmp/pr-body.md`, then apply it:

    gh pr edit <number> --body-file tmp/pr-body.md

Name the issue you used as the source of the mapping in your review report.
The author needs to see whether you resolved the right one.
