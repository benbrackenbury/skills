---
name: stale-cache
description: Fetch live data, keep a last-good snapshot, and show which one the UI is using. Use when a page loads prices, FX, usage, orbits, or any third-party payload; when a GitHub Action writes a JSON cache; or when an API outage should not blank the dashboard.
---

# Stale cache

Live data dies. The page must still tell the truth about the last good payload. Empty is worse than stale. Zero is a lie if you meant "we could not fetch".

## Shape

Three pieces, no extra layers:

1. **Fetch.** Browser or server, on load (and on a timer if the number moves).
2. **Snapshot.** A committed or stored JSON blob with the values and an `updated` ISO timestamp. This is the last good answer, not a mock.
3. **Label.** The UI says live, cached, or loading. A grey dot and "updated 4h ago" beats a spinner that never resolves.

`data.json` with `priceUsd`, `usdToGbp`, and `updated` is enough. Do not add a cache class, Redis, or a service worker until that file is not enough.

## Rules

- On success, render live and optionally write through to the snapshot.
- On failure, render the snapshot and mark it cached. Do not clear the previous numbers.
- Never coerce a missing price to `0`. Missing is a state. Zero is a P&L.
- The snapshot's timestamp is the as-of for cached mode. Do not stamp "now" on old data.
- A scheduled job that only bumps `updated` without changing values is fine. It proves the job ran. A job that overwrites good numbers with an error payload is not.

## What to show

| Fetch | Snapshot | UI |
| --- | --- | --- |
| ok | anything | live + fetch time |
| fail | present | cached + snapshot time |
| fail | missing | error, no fake figures |

Keep FX and the thing it converts stamped separately if they can fail apart. A live share price with a day-old FX rate is mixed stale. Say so, or refuse to convert.

## Checks

- Pull the network on the live request. The page still shows the last numbers and does not look like a crash.
- Break the payload (`{}`, 403, timeout). Same: cached or error, never a green £0.00.
- Confirm the snapshot is actually what the UI reads, not a leftover HTML default.
