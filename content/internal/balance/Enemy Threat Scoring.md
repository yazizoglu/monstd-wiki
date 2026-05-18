---
title: Enemy Threat Scoring
tags: [internal, balance]
---

# Enemy Threat Scoring

Gerçek kaynak kodu değerlerine dayalı tehdit puanlama sistemi. Tam model için bkz. [[internal/balance/Balance Model]].

---

## Formül

```
ThreatScore = HP × (speed / 50) × abilityMult × resistMult
```

- **speed / 50**: Baseline 50 pt/s. Goblin (72 pt/s) = 1.44×, Twin Dragon (30 pt/s) = 0.60×
- **abilityMult**: flying=1.2, regenerating=1.2, diğer=1.0
- **resistMult**: tek resist=1.3, çift resist=1.5, üçlü resist=1.6–1.8

---

## Standard Enemy Threat Scores

| Enemy | HP | Speed | SpeedM | AbilM | ResistM | **Threat** | Trait |
|-------|-----|-------|--------|-------|---------|-----------|-------|
| [[Goblin]] | 60 | 72 | 1.44 | 1.0 | 1.0 | **86** | — |
| [[Plant\|Frost Plant]] | 140 | 38 | 0.76 | 1.0 | 1.3 | **138** | poisonResist |
| [[Imp]] | 130 | 70 | 1.40 | 1.2 | 1.0 | **218** | flying |
| [[Troll]] | 200 | 45 | 0.90 | 1.0 | 1.3 | **234** | armorPlated |
| [[Gnoll]] | 160 | 65 | 1.30 | 1.2 | 1.0 | **250** | regenerating |
| [[Orc]] | 240 | 52 | 1.04 | 1.0 | 1.3 | **325** | armorPlated |

> Threat 86 (Goblin) ile 325 (Orc) arasında 3.8× fark var. Orc gelen wave'de Lightning Tower olmaması kritik kayıp anlamına gelir.

---

## Map 1 Boss Threat Scores (Cursed Wilds)

| Boss | Wave | HP | Speed | **Threat** | Traits |
|------|------|----|-------|-----------|--------|
| [[Ent]] | 5 | 480 | 28 | **349** | poisonResist |
| [[Golem]] | 10 | 900 | 38 | **1026** | armorPlated + poisonResist |
| [[Medusa]] | 15 | 1400 | 52 | **1456** | — |
| [[Crimson Stalker]] | 20 | 2400 | 48 | **2304** | — |
| [[Twin Dragon]] | 25 | 3800 | 30 | **3420** | fireImmune + armor (×0.55) |

---

## Map 2 Boss Threat Scores (Volcanic Inferno)

| Boss | Wave | HP | Speed | **Threat** | Traits |
|------|------|----|-------|-----------|--------|
| [[Lav Golem]] | 5 | 950 | 35 | **865** | fireImmune + armor |
| [[Rat King]] | 10 | 2100 | 52 | **2837** | poisonResist |
| [[Vampire]] | 15 | 3000 | 50 | **5070** | regenerating + iceImmune |
| [[Lizardman]] | 20 | 3300 | 45 | **3861** | armorPlated (×0.38) |
| [[Demon]] | 25 | 4600 | 28 | **4122** | fireImmune + lightningResist + armor |

---

## Map 3 Boss Threat Scores (Frozen Tundra)

| Boss | Wave | HP | Speed | **Threat** | Traits |
|------|------|----|-------|-----------|--------|
| [[Ice Golem]] | 5 | 1100 | 32 | **915** | iceImmune + armor |
| [[Frozen Knight]] | 10 | 1750 | 48 | **2688** | iceImmune + lightningResist + armor |
| [[Vampire]] | 15 | 3000 | 50 | **5070** | regenerating + iceImmune |
| [[Lich]] | 20 | 3600 | 34 | **3182** | iceImmune |
| [[Frostmourne Demon]] | 25 | 6000 | 26 | **5616** | iceImmune + lightningResist + armor |

---

## Kalibrasyon

- Standard enemy hedef aralığı: **80–350**
- Boss Wave 5 hedef aralığı: **350–1000**
- Boss Wave 25 hedef aralığı: **3000–6000**
- Vampire (Threat 5070) Map 2 ve Map 3'te aynı boss — yüksek threat regenerating+immunity kombinasyonundan geliyor; Poison Tower olmadan bu boss savunulamaz.

---

## Yeni Düşman Eklerken

1. Formülle threat puanı hesapla
2. Aynı map/wave aralığındaki düşmanlarla karşılaştır
3. Threat çok yüksekse: HP veya speed azalt, ya da trait azalt
4. Threat çok düşükse: grup sayısını artır veya stats yükselt
5. İlk göründüğü wave'de playtest yap

*Son güncelleme: v0.19.0. Tam formül ve tower power modeli için bkz. [[internal/balance/Balance Model]].*
