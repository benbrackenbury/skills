---
name: hostile-feed
description: Treat third-party APIs and public datasets as hostile. Use when parsing Yahoo, CelesTrak, Grok credits, GitHub profile stats, or any JSON you do not control; when an endpoint returns 403; when TypeScript infers a singleton from the first array element; or when a mapping from ids to names starts failing.
---

# Hostile feed

You do not own the other end. It will 403, change shape, return null mid-array, and collapse your types. Parse like the payload wants you to look wrong.

## Before you depend on it

- Find the documented endpoint. Prefer it over scraping HTML.
- Save one real response next to the parser (a fixture, a committed sample, a test). Code written against a remembered shape is how COSPAR ids become "Starlink" for everything.
- Type the payload yourself. Do not let the compiler infer a union from `PAGE_SECTIONS[0]`. The first element is not the type of the list.
- Null is a value. SGP4 and credit APIs return it. Guard at the parse boundary, not in the map marker.

## When it fails

403, rate limit, CORS, empty body, HTML in a JSON slot. That is normal.

- Switch to a known mirror or the `stale-cache` snapshot. Do not retry in a hot loop.
- Keep the original error somewhere a human can see (footer, log, `console.warn`). Silent fallback is how a 403 lasts a week.
- Do not "fix" a 403 by pointing at a random third mirror you have not read. One fallback you tested.

## Joins and names

Stable ids on the left, display names on the right. Look up launch names from COSPAR / catalog ids. If the lookup misses, show the id, not a guessed group name.

Fuzzy string match on "Starlink-1234" is not a join. It will pass until the operator renames the train.

## Types

- Write the union (`"orbit" | "fleet" | ...`) in the source. Do not `as const` a one-element array and then push siblings.
- Parse with a narrow function that returns `T | null`. Callers drop nulls in one place.
- Incremental TS build info and `any` on the wire are how production typecheck fails after local dev looked fine. `tsc` on the same files CI uses.

## Checks

- Feed the parser the fixture, an empty object, and a 403 HTML body. The first yields data. The others yield null and a reason.
- If you map ids to names, include one unknown id in the check. The UI must show the id.
- If TypeScript is in play, a second list entry with a different `id` must still typecheck.
