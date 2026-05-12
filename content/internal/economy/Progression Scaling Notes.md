---
title: Progression Scaling Notes
tags: [internal, economy]
---

# Progression Scaling Notes

How enemy stats and difficulty scale across levels and difficulty settings.

---

## Level-to-Level Scaling

Each level is a discrete step, not a gradient. Scaling happens at level transitions, not wave-by-wave.

| Level | HP Multiplier | Speed Multiplier | Resistance Depth |
|---|---|---|---|
| Level 1 | 1.0× | 1.0× | 0–1 resistances |
| Level 2 | 1.4× | 1.15× | 1–2 resistances |
| Level 3 | 1.9× | 1.3× | 2–3 resistances |

---

## Difficulty Scaling

Applied on top of the level's base stats.

| Difficulty | HP | Speed | Economy |
|---|---|---|---|
| Easy | −20% | −10% | +20% gold income |
| Normal | 1.0× | 1.0× | Standard |
| Hard | +40% | +20% | −10% gold income |

**Cap:** Hard HP is capped at +40% over Normal (never more than 1.4× Normal HP). Avoid attrition gameplay.

---

## Wave-Within-Level Scaling

Within a level, enemy stats scale linearly from wave 1 to wave 25.

| Wave Range | HP vs Level Baseline |
|---|---|
| 1–5 | 70–85% |
| 6–10 | 85–100% |
| 11–15 | 100–115% |
| 16–20 | 115–130% |
| 21–24 | 130–145% |
| 25 (Boss) | Boss stats — not linear |

---

## Boss Scaling

Bosses are hand-tuned, not formula-scaled. Target:
- Final boss HP: ~8–12× a mid-tier standard enemy at the same level
- Final boss should require 60–80% of the player's max DPS to kill before the path ends
- Mini-bosses: ~3–5× standard enemy HP; no unique mechanics beyond health

---

## Endless Mode Scaling

After wave 25, Endless Mode continues with exponential scaling:

| Wave | HP Multiplier (vs wave 25) | Notes |
|---|---|---|
| 26–35 | 1.0–1.5× | Controlled scaling |
| 36–50 | 1.5–3.0× | Noticeable difficulty jump |
| 51–75 | 3.0–8.0× | Expert range |
| 75+ | 8×+ | Diminishing returns, challenge ceiling |

Leaderboard scores in Endless Mode are the primary competitive metric.
