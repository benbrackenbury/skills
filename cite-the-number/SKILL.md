---
name: cite-the-number
description: Every figure shown to a user needs a source, an as-of date, and a unit. Use when building dashboards, stats pages, P&L views, or any UI that displays a count, price, rate, or public claim. Use when adding or changing a number that did not come from code the user owns.
---

# Cite the number

If a human will read a number, it is a claim. Claims need a source, a time, and a unit. A bare `8,000` on a page is a bug even when the arithmetic is right.

## When this applies

Dashboards, READMEs, blog posts, admin screens, charts, map badges, commit messages that assert a count. Any time the agent would otherwise write a figure from memory, training data, or "roughly".

## What every figure carries

1. **Value.** The number itself, formatted for the unit (not `158.96` next to a £ sign if the source was USD).
2. **Unit.** GBP, USD, mm, satellites, percent. Written, not implied by colour or icon.
3. **As-of.** A timestamp or a calendar date the source actually supports. Not "today" unless you fetched today.
4. **Source.** A URL, dataset name, or file the reviewer can open. "Public figures" is not a source.

If you cannot fill all four, do not put the number on the page. Say what is missing.

## Do not invent the count

Do not round a Wikipedia memory into a headline. Do not add "about" to paper over a guess. Look the figure up, quote the page, and date it. If two sources disagree, show both or pick one and say why.

Joining two datasets does not create a new sourced number. Mapping COSPAR ids to launch names is a join. The joined count is only as good as the key. If the key is fuzzy (display names, "Starlink Group 6"), stop and use the stable id.

## UI

- Put source and as-of next to the figure, or one click away, not in a footer the reader will not see.
- A live fetch still needs as-of. "Updated 3 min ago" is the as-of. A green dot without a time is decoration.
- Cached data is still a citation. Label it cached. See `stale-cache`.

## Checks before you ship

- Grep the UI for hardcoded numbers. Each one either has the four fields or gets deleted.
- Open the source URL. Confirm the number is still there and the date matches what you show.
- If the number is computed, cite the inputs, not the formula. "26 V3 sats from Flight 14" needs Flight 14's source, not a comment that you counted.
