---
title: Elements
tags: [elements]
---

# Elements

Every tower deals one damage type. Every enemy has zero or more resistances. Understanding this matchup layer is the core strategic depth of MonsTD.

---

## Damage Type Overview

| Element | Towers | Strong vs | Weak vs | Special |
|---|---|---|---|---|
| [[Physical]] | [[Arrow Tower]], [[Cannon Tower]] | Flying (+30%) | Armored (−35%) | Area (Cannon); Arrow targets flying |
| [[Frost]] | [[Frost Tower]] | Fire-immune (+50%) | Frost-immune (−75%) | Slows enemies |
| [[Lightning]] | [[Lightning Tower]] | Armored (+35%) | Lightning-resist (−70%) | Chains to nearby targets |
| [[Poison]] | [[Poison Tower]] | Regenerating (+50%) | Poison-resist (−75%) | Damage over time |

---

## Resistance System

Resistances reduce incoming damage from a specific element. An enemy with `fire_resist` takes reduced damage from [[Fire]] but full damage from everything else.

---

## Design Notes

- At least two damage types should always be viable on any given level
- Resistances should be communicated clearly in the UI and in enemy tooltips
- No single element should hard-counter more than two resistance types
