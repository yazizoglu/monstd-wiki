---
title: Patch 0.21.0
tags: [patch-notes]
date: 2026-05
---

# Patch 0.21.0 — Lightning Nerf & Knight → Orc Rename

*May 2026*

---

## Highlights

- **Lightning Tower nerfed** — base damage, fire rate, and chain behavior reduced to bring it in line with other towers
- **Knight renamed to Orc** — all in-game text, visuals, code, and wiki updated

---

## Tower Balance

### Lightning Tower — Nerf

Lightning Tower was the dominant pick across nearly all situations, outperforming every other tower in both single-target and group scenarios. Changes target a 24% DPS reduction and narrower chain reach to keep it as the anti-armor specialist without crowding out Arrow, Fire, and Poison.

| Stat | Old | New |
|---|---|---|
| Base Damage | 48 | 40 |
| Base Fire Rate | 1.1/s | 1.0/s |
| Base DPS | **52.8** | **40.0** |
| Default Chain Bounces | 2 | 1 |
| Chain Bounce Range | 110 | 90 |

Path upgrades are also scaled down proportionally. [[Lightning Tower]] remains the primary counter to [[Orc|Orcs]] and other armored enemies — it just no longer replaces every other tower in the lineup.

---

## Enemy Changes

### Knight → Orc

The armored mid-wave enemy has been renamed from **Knight** to **Orc** across the entire game. Stats, role, and behavior are unchanged.

- In-game display name: Knight → **Orc**
- All announcement text, achievement descriptions, and inspect panel updated
- Achievement: "Şövalye Avcısı" → **"Ork Avcısı"** (Defeat 100 Orcs)
- Sprite atlas and frame assets renamed accordingly

The **[[Bosses/Frozen Knight|Frozen Knight]]** boss is a separate entity and retains its name.

---

## Internal

- All code references to `.knight` enum case renamed to `.orc`
- Walk frame assets renamed from `enemy_knight_*` to `enemy_orc_*`
- `TextureCache` atlas lookup updated from `"Knight"` to `"Orc"`
