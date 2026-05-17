---
title: Patch 0.20.0
tags: [patch-notes]
date: 2026-05
---

# Patch 0.20.0 — Enemy Rework, Elemental Balance & Map Fixes

*May 2026*

---

## Highlights

- [[Imp]] reworked with a flying hover animation — now visually distinct from walking enemies
- [[Gnoll]] becomes the primary ground threat in Volcanic Inferno (vi2–vi4); Goblin removed from those maps
- **Elemental counter bonuses buffed** — strong-vs multipliers increased across all elements; matchups are now decisive
- Strong vs interactions display the actual damage number in element color
- Island world map ship navigation bugs fixed

---

## Enemy Changes

### Imp — Flying Visual Rework
Imps now hover. The icon bobs up and down continuously with rapid wing-flap scaling and a red fire glow pulse. The ground shadow is reduced to a small, dim ellipse to indicate the creature is airborne. Imp size increased (~29% larger) to improve readability among other enemies.

### Gnoll — Size & Role Increase
Gnoll size increased to match [[Knight]] visually. In Volcanic Inferno maps vi2, vi3, and vi4, Gnoll now replaces Goblin as the baseline filler enemy — arriving from wave 1 and forming the primary ground threat. In vi1, Goblin remains for the first four waves as a transition.

### Lav Golem — Size Increase
Lav Golem size significantly increased to reflect its role as the first major boss of Volcanic Inferno. Now visually comparable to [[Golem|Stone Golem]] in presence.

---

## Volcanic Inferno Enemy Composition

Goblin is a Cursed Wilds enemy and has been removed from the Volcanic Inferno mid-to-late maps.

| Map | Goblin | Troll | Gnoll | Imp |
|---|---|---|---|---|
| vi1 (Lava Fields) | Waves 1–4 only | Moderate | From wave 5 | From wave 6 |
| vi2 (Magma Bend) | **Removed** | Moderate | **Primary filler** | From wave 5 |
| vi3 (Sulfur Maze) | **Removed** | Reduced | **Primary filler** | From wave 4 |
| vi4 (The Caldera) | **Removed** | Reduced | **Primary filler** | From wave 5 |

---

## Combat Feedback

### Strong vs Damage Numbers
When a tower hits an enemy it is strong against, a floating damage number now appears instead of the generic "WEAK!" label. The number is displayed large in the tower's element color (orange for Fire, yellow for Lightning, blue for Ice, green for Poison, white for Physical). This makes the mechanic legible mid-wave — players can see exactly how much bonus damage the correct counter is dealing.

RESIST text (small, gray) is unchanged.

---

## Bug Fixes

- **Island ship navigation** — After completing Volcanic Inferno, ship now correctly sails to Frozen Tundra instead of Storm Lands. Root cause: island index order mismatch between victory screen and world map.
- **Island ship direction (3rd island)** — After completing Frozen Tundra, ship now departs from Frozen Tundra correctly instead of arriving from the wrong direction.
- **Arrow Tower split-shot range** — Extra arrows were targeting enemies outside the tower's range. Fixed: only in-range enemies are eligible for multi-arrow targets.
- **Tower upgrade animation** — Upgrade pop animation was running on an invisible node. Now animates the full tower with golden icon flash and floating "▲ LVN" label.
- **Island path animation** — Directional arrow markers now appear along the newly drawn path when returning to island after completing a level.

---

## Balance

### Elemental Counter Multipliers — Buffed

Strong-vs multipliers increased to make elemental matchups decisive. The right counter now deals roughly 1.65–2× the damage of a neutral tower against its target type.

| Element | Strong vs | Old | New |
|---|---|---|---|
| Physical | Flying | +30% | **+65%** |
| Fire | Frost-resistant | +50% | **+85%** |
| Frost | Fire-resistant | +50% | **+85%** |
| Lightning | Armored | +35% | **+75%** |
| Poison | Regenerating | +50% | **+100%** |

Resist multipliers unchanged. The asymmetry between penalty (−70–75%) and reward is intentional — it's always more costly to use the wrong tower than it is beneficial to use the right one, but the right tower now provides a meaningful advantage rather than a minor nudge.
