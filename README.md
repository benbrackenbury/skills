# Agent Skills

Various agent skills, mostly borrowed from [Cursor pstack](https://github.com/cursor/plugins/tree/main/pstack)

Primarily used within Cursor Agent

## Skills

Model invocable means the agent can start the skill from its description. `No` means the skill sets `disable-model-invocation`, so you have to call it yourself.

| Name | Description | Model invocable | From |
| --- | --- | --- | --- |
| `blast-radius` | Find what a change could break somewhere else before it ships, beyond the diff, and prove the one fact it's safe because of by running real code instead of writing it up. Use for "blast radius of X", "what could this break", or reviewing a small diff you don't trust. | No | [Cursor pstack](https://github.com/cursor/plugins/tree/main/pstack) |
| `correct` | Find the mistakes agents keep repeating in this repo and make each one impossible. Try architecture first, then types, then a lint whose error names the fix, then a test, and write docs last. Prove each check fails on a real past mistake. Repeat this each time the operator corrects you. Use for /correct. | No | [Cursor pstack](https://github.com/cursor/plugins/tree/main/pstack) |
| `git-commit` | Add and commit changes to a git repository. | Yes | me |
| `ponytail` | Forces the laziest solution that actually works, simplest, shortest, most minimal. Questions whether the task needs to exist at all (YAGNI), then prefers the standard library, native platform features, and one line over fifty. Levels: lite, full (default), ultra. For coding tasks only. | Yes | [DietrichGebert](https://github.com/dietrichgebert/ponytail) |
| `show-me-your-work` | Keep a reviewable decision trail for long-running or unattended work: a TSV log with one row per decision (what, why, evidence, result). Local by default; commit it when a reviewer needs the trail to trust the result. | No | [Cursor pstack](https://github.com/cursor/plugins/tree/main/pstack) |
| `unslop` | Cut AI tells from any writing. Must always apply. | Yes | [Cursor pstack](https://github.com/cursor/plugins/tree/main/pstack) |
| `web-design-guidelines` | Review UI code for Web Interface Guidelines compliance. Use when asked to "review my UI", "check accessibility", "audit design", "review UX", or "check my site against best practices". | Yes | [Vercel Labs](https://github.com/vercel-labs/agent-skills/tree/main/skills/web-design-guidelines) |
