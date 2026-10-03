# Agent Skills

Various agent skills, mostly borrowed from [Cursor pstack](https://github.com/cursor/plugins/tree/main/pstack)

Primarily used within Cursor Agent

## Skills

Model invocable means the agent can start the skill from its description. `No` means the skill sets `disable-model-invocation`, so you have to call it yourself.

| Name | Description | Model invocable | From |
| --- | --- | --- | --- |
| `blast-radius` | Find what a change could break somewhere else before it ships, beyond the diff, and prove the one fact it's safe because of by running real code instead of writing it up. Use for "blast radius of X", "what could this break", or reviewing a small diff you don't trust. | No | [Cursor pstack](https://github.com/cursor/plugins/tree/main/pstack) |
| `cite-the-number` | Every figure shown to a user needs a source, an as-of date, and a unit. For dashboards, stats pages, and any count or price that did not come from code you own. | Yes | me |
| `git-commit` | Add and commit changes to a git repository. | Yes | me |
| `hostile-feed` | Treat third-party APIs and public datasets as hostile. Parse typed payloads, keep a tested fallback for 403s, join on stable ids, and never infer a union from the first array element. | Yes | me |
| `ponytail` | Forces the laziest solution that actually works, simplest, shortest, most minimal. Questions whether the task needs to exist at all (YAGNI), then prefers the standard library, native platform features, and one line over fifty. Levels: lite, full (default), ultra. For coding tasks only. | Yes | [DietrichGebert](https://github.com/dietrichgebert/ponytail) |
| `principle-redesign-from-first-principles` | Apply when integrating a new requirement into an existing design. Redesign as if the requirement had been a foundational assumption from day one, instead of bolting it on. | No | [Cursor pstack](https://github.com/cursor/plugins/tree/main/pstack) |
| `show-me-your-work` | Keep a reviewable decision trail for long-running or unattended work: a TSV log with one row per decision (what, why, evidence, result). Local by default; commit it when a reviewer needs the trail to trust the result. | No | [Cursor pstack](https://github.com/cursor/plugins/tree/main/pstack) |
| `stale-cache` | Fetch live data, keep a last-good snapshot, and label live vs cached. Empty is worse than stale. Zero is a lie if you meant the fetch failed. | Yes | me |
| `units-stay-put` | Pick units once, persist them next to the values, convert in one place, and round-trip the file. For money, FX, millimetres, and timestamps. | Yes | me |
| `unslop` | Cut AI tells from any writing. Must always apply. | Yes | [Cursor pstack](https://github.com/cursor/plugins/tree/main/pstack) |
