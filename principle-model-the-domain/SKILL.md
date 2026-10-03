---
name: principle-model-the-domain
description: "Apply when choosing types and data structures, or when logic is a pile of conditionals about the same idea. Encode the domain in a structure so the rest of the code is obvious."
disable-model-invocation: true
---

# Model the Domain

Get the data shape right first. Downstream code should look inevitable.

- Name the things the program is about (a document, a job, a permission), not the screens that show them
- Put illegal combinations out of reach with types, enums, or constructors, not comments
- If the same idea is checked in three `if`s, it wants a type or a table, not a fourth `if`
- Change the model when the requirement changes. Do not leave the old shape and branch around it
