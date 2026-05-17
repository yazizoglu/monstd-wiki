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
| [[Physical]] | [[Arrow Tower]], [[Fire Tower]] | Flying (**+65%**) | Armored (−35%) | Area (Fire Tower); Arrow targets flying |
| [[Fire]] | [[Fire Tower]] | Frost-immune (**+85%**) | Fire-immune (−75%) | Area splash |
| [[Frost]] | [[Frost Tower]] | Fire-immune (**+85%**) | Frost-immune (−75%) | Slows enemies |
| [[Lightning]] | [[Lightning Tower]] | Armored (**+75%**) | Lightning-resist (−70%), Frost-immune (−40%) | Chains to nearby targets |
| [[Poison]] | [[Poison Tower]] | Regenerating (**+100%**) | Poison-resist (−75%) | Damage over time |

---

## Resistance System

Resistances reduce incoming damage from a specific element. An enemy with `fireImmune` takes only 25% of incoming Fire damage but full damage from everything else.

---

## Strong vs Feedback

When a tower scores a strong-vs hit, the actual damage number floats above the enemy in the tower's element color (orange for Fire, yellow for Lightning, blue for Ice, green for Poison, white for Physical). This makes the matchup advantage directly readable in battle.

---

## Design Notes

- Counter bonuses are now large enough to be decisive — the right tower clears its target type roughly twice as fast
- Resist penalties remain severe — the wrong tower is still significantly less effective
- At least two damage types should always be viable on any given level
- No single element should hard-counter more than two resistance types
