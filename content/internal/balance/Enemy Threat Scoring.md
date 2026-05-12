---
title: Enemy Threat Scoring
tags: [internal, balance]
---

# Enemy Threat Scoring

A framework for rating enemies consistently and identifying gaps or over-tuned entries.

---

## Scoring Dimensions

Each enemy is rated across four axes (1–5):

| Axis | Description |
|---|---|
| **Speed** | How fast the enemy crosses the map |
| **Durability** | Effective health after resistance modifiers |
| **Counter Pressure** | How much the enemy forces a specific defensive response |
| **Group Density** | How many appear per wave, relative to their threat |

**Threat Score = (Speed + Durability + Counter Pressure) × Group Density modifier**

---

## Current Enemy Scores

| Enemy | Speed | Durability | Counter Pressure | Group Mod | Threat |
|---|---|---|---|---|---|
| [[Goblin]] | 4 | 1 | 1 | 1.5× | 9 |
| [[Wolf]] | 5 | 2 | 2 | 1.3× | 12 |
| [[Skeleton]] | 3 | 3 | 3 | 1.2× | 11 |
| [[Golem]] | 1 | 5 | 5 | 0.8× | 9 |
| [[Flying Bat]] | 3 | 2 | 4 | 1.2× | 11 |

---

## Calibration Notes

- Target threat range for standard enemies: **8–14**
- Enemies below 8 should appear in larger groups or be removed
- Enemies above 14 should be reclassified as mini-boss tier
- Bosses are not scored on this scale — they have their own phase-based threat model

---

## Usage

When introducing a new enemy type:
1. Score it across all four axes
2. Compare to existing enemies in the same level
3. Adjust group size or stats until threat score sits in target range
4. Playtest specifically at the wave it is introduced
