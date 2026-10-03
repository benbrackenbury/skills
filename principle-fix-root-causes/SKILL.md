---
name: principle-fix-root-causes
description: "Apply when fixing a bug. Reproduce it, ask why until you reach the cause, and fix it there. Do not silence the crash with a nil check at the call site."
disable-model-invocation: true
---

# Fix Root Causes

A report names a symptom. The fix belongs at the cause every caller already goes through.

- Reproduce first. If you cannot make it fail, you do not know what you are fixing
- Ask why until the next "why" is outside the program (bad input at a boundary, a real OS limit)
- Patch the shared function, type, or invariant, not each caller that happens to blow up
- A guard that turns a crash into silent wrong data is not a fix
