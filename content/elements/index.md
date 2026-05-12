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
| [[Physical]] | [[Arrow Tower]], [[Cannon Tower]] | Flying enemies | Armored, Fire-resistant | Area (Cannon) |
| [[Frost]] | [[Frost Tower]] | Fire-resistant | Frost-resistant | Slows |
| [[Lightning]] | [[Lightning Tower]] | Armored | Frost-resistant | Chain |
| [[Poison]] | [[Poison Tower]] | Regenerating | Poison-resistant | DoT |

---

## Resistance System

Resistances reduce incoming damage from a specific element. An enemy with `fire_resist` takes reduced damage from [[Fire]] but full damage from everything else.

No resistance exists for **Arcane** damage — it bypasses all elemental resistances. *(Planned for future towers.)*

---

## Design Notes

- At least two damage types should always be viable on any given level
- Resistances should be communicated clearly in the UI and in enemy tooltips
- No single element should hard-counter more than two resistance types
