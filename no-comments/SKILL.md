---
name: no-comments
description: Strip comments that restate the code. Keep a comment only when it records a non-obvious why that types and names cannot. Use when reviewing a diff, cleaning a file, or before you add a comment.
---

# No comments

Comments that narrate what the next line does go stale and train the reader to skip them. Delete those. Do not add new ones.

Keep a comment only when all of these are true:

- It says why, not what
- The why is not already in the type, name, or test
- Removing it would make a later change silently wrong

`TODO` without an owner or a trigger is a comment. Delete it or make it a check.

After you edit, grep the diff for `#`, `//`, `/*`. If a line is a caption for the code, cut it.
