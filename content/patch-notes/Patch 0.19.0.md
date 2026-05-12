---
title: Patch 0.19.0
tags: [patch-notes]
date: 2026-05
---

# Patch 0.19.0 — Lightning Tower, Sound Engine & Game Feel

*May 2026*

---

## Highlights

- [[Lightning Tower]] properly renamed and re-visually restored with its own asset (was using a placeholder sprite)
- Sound engine rebuilt — SFX no longer cuts out under rapid fire
- Boss escape now correctly costs 3 lives (mini-boss) or 10 lives (final boss) with wave bonus cancelled
- Game speed preference is now saved between sessions
- Sell button added to tower upgrade panel

---

## Bug Fixes

- **Lightning Tower asset** — Tower was using a temporary `tower_sniper` sprite. Renamed to `tower_lightning` with matching imageset. No visual content change — the correct art was always there.
- **Boss escape cost** — Mini-bosses that escaped only cost 1 life instead of 3. Final boss escape now also cancels wave bonus gold (was paying out even on loss).
- **Golem HP bar** — Health bar floated above the Golem's actual art due to the sprite not filling its canvas. Fixed per-type art offset (`healthBarArtHalf`).
- **Tutorial upgrade step** — Upgrade spotlight failed to locate the upgrade button reliably. Now anchors directly to the upgrade button's world position.
- **Range circle during tutorial** — Tower range preview appeared during tutorial steps, cluttering the map. Now hidden while tutorial is active.

---

## Changes

### Sound Engine
Replaced `SKAction.playSoundFileNamed` with a pooled `AVAudioPlayer` system. Same audio files — no content change — but sounds no longer cut each other off when multiple towers fire simultaneously.

### Tower Stat Preview
- **Sell button** added to the stat panel — towers can now be sold directly from the upgrade screen
- Matchup display changed from icon row to text labels (`▲ Strong vs · / ▼ Weak vs`) — easier to read at small sizes

### Tower Menu
- Upgrade path cards repositioned (y: −18 → 0); panel height increased to accommodate sell button

### Boss Trait Badges
- Trait badges (armor, regen, etc.) removed from boss nodes — badges remain on standard enemies only. Boss resistances are communicated through the wave preview instead.

### Game Speed Persistence
Speed multiplier (1× / 2×) is now remembered between sessions. The game launches at your last-used speed preference.

---

## Balance

No balance changes in this patch.

---

## Known Issues

- Game Center leaderboard popup requires App Store Connect configuration before it becomes visible on device
