---
name: principle-attack-the-premise
description: "Apply when two or more fixes that share one premise have failed the same check. Question the premise instead of writing another fix that assumes it."
disable-model-invocation: true
---

# Attack the Premise

If the last two patches failed the same way, the shared assumption is the bug.

- Stop adding another branch that assumes the same story about how the system works
- List who holds the state you care about (process, disk, cache, the other service). The imbalance is usually there
- Change the story, then make one fix that matches the new one
- One more retry of the same idea is not persistence. It is a loop
