---
name: units-stay-put
description: Pick units once, persist them next to the values, and never mix them in the UI or the file. Use when storing geometry, money, FX, timestamps, or anything with a dimension; when converting USD to GBP; when a CAD or JSON document has a units field; or when a number would change meaning if the unit were silently swapped.
---

# Units stay put

A number without a unit is not data. Pick the unit at the boundary where the value enters the system, write it down, and keep it until a human asks for another unit.

## Pick once

- Geometry: millimetres, one up-axis, written in the file (`"units": "mm"`). Snap and inspector use the same unit.
- Money: store the source currency the API gave you (`priceUsd`). Convert at display time with a stamped rate (`usdToGbp`). Do not save a converted total as if it were the source.
- Time: UTC in storage (`2026-10-03T17:09:52Z`). Local only in the label.

Do not add a units framework. A string field next to the values is enough.

## Convert in one place

One function, two inputs: source amount and rate (or scale). It returns the display amount. Callers do not multiply inline in the template.

If the rate is missing or stale, do not convert. Show the source unit. Mixed FX is how a P&L flips sign without the price moving.

## Files

Round-trip the document. Save, open, compare. The units field and every length or price must come back identical, not "close enough after float". If you have a `.cad` or `data.json`, that test is the spec.

Changing units in an existing file is a migration, not a save. Bump a version field. Old files keep old units until you convert them on purpose.

## UI

- The inspector and the headline use the same unit, or they label the conversion.
- Axes, grid, and typed input agree (mm with mm snap, not mixed with inches in the status bar).
- Colour is not a unit. Green does not mean GBP.

## Checks

- Put a value in, persist, reload. Same number, same unit field.
- Convert with a known rate (100 USD × 0.756 = 75.6 GBP). One assertion.
- Drop the rate. The UI still shows 100 USD, not 0 or 100 GBP.
