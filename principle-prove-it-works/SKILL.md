---
name: principle-prove-it-works
description: "Apply after finishing a task, before calling it done. Verify against the real artifact: run the feature, read the value, inspect the diff. Compiling is not proof."
disable-model-invocation: true
---

# Prove It Works

Done means you checked the real thing, not a proxy. "It compiles", "the tests I didn't run would pass", and a writeup of what should happen are not checks.

- Run the feature the way a user would, or the smallest command that exercises the same path
- Read the actual output, file, UI, or return value. Do not trust a summary you wrote
- If you cannot run it, say so and say what you did instead. Do not round that up to done
