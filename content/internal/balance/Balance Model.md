---
title: Balance Model
tags: [internal, balance]
---

# Balance Model

Tüm değerler `TowerNode.swift` ve `EnemyNode.swift` kaynak kodundan alınmıştır. Bu belge oyunun matematiksel temelini tanımlar; rebalance kararları buraya dayanır.

---

## 1. Tower Power Modeli

### Formül

```
TowerPower = DPS × Coverage × Utility × Reliability
```

| Faktör | Tanım | Değer Örnekleri |
|--------|-------|----------------|
| **DPS** | baseDamage × baseFireRate | Kaynak koddan doğrudan |
| **Coverage** | Efektif hedef sayısı çarpanı | Single=1.0, AoE=1.5, Chain(3)=2.5, Spread=1.2 |
| **Utility** | Savaş dışı değer (slow, DoT kalıcılığı) | Frost slow=2.0, Poison DoT=1.3, Fire burn=1.1 |
| **Reliability** | Hedef tutma tutarlılığı | Yüksek range/rate=1.2, Düşük fire rate=0.7 |

### Hesaplanmış Tower Power (base stats)

| Tower | Damage | FireRate | DPS | Coverage | Utility | Reliability | **Power** | Hedef |
|-------|--------|----------|-----|----------|---------|-------------|-----------|-------|
| Arrow | 18 | 1.8/s | 32.4 | 1.0 | 1.0 | 1.2 | **38.9** | 40–45 ✓ |
| Frost | 30 | 1.1/s | 33.0 | 1.0 | 2.0 | 1.0 | **66.0** | 60–70 ✓ |
| Fire | 50 | 0.7/s | 35.0 | 1.5 | 1.1 | 0.7 | **40.4** | 55–65 ← **düşük** |
| Lightning | 48 | 1.1/s | 52.8 | 2.5 | 1.0 | 1.1 | **145.2** | 65–75 ← **3× fazla** |
| Poison | 30 | 1.1/s | 33.0 | 1.2 | 1.3 | 0.9 | **46.3** | 55–65 ← **düşük** |

> **Lightning 3.7× Arrow Power.** Tek tower meta bundan kaynaklanıyor.

---

## 2. Enemy Threat Score Modeli

### Formül

```
ThreatScore = HP × (speed / 50) × abilityMult × resistMult
```

| Faktör | Tanım |
|--------|-------|
| **HP** | Baz can (difficulty modifier öncesi) |
| **speed / 50** | Hız normalizer (50 pt/s = baseline) |
| **abilityMult** | Özel yeteneğin tehdit katkısı (flying, regen) |
| **resistMult** | Kaç tower'ı etkisizleştirdiğine göre ağırlık |

`abilityMult` referans değerleri:
- Uçan (flying): 1.2 — sadece 2/5 tower hedefleyebilir
- Regen: 1.2 — hasar kaybını geri alıyor, burst DPS gerekiyor

`resistMult` referans değerleri:
- Tek resist/immunity: 1.3
- Çift resist/immunity: 1.5
- Üçlü resist/immunity: 1.6–1.8

### Standard Enemy Threat Scores

| Enemy | HP | Speed | SpeedM | AbilM | ResistM | **Threat** | Trait |
|-------|-----|-------|--------|-------|---------|-----------|-------|
| Goblin | 60 | 72 | 1.44 | 1.0 | 1.0 | **86** | — |
| Troll | 200 | 45 | 0.90 | 1.0 | 1.3 | **234** | armorPlated |
| Orc | 240 | 52 | 1.04 | 1.0 | 1.3 | **325** | armorPlated |
| Imp | 130 | 70 | 1.40 | 1.2 | 1.0 | **218** | flying |
| Gnoll | 160 | 65 | 1.30 | 1.2 | 1.0 | **250** | regenerating |
| Plant | 140 | 38 | 0.76 | 1.0 | 1.3 | **138** | poisonResist |

### Map 1 Boss Threat Scores (Cursed Wilds)

| Boss | Wave | HP | Speed | SpeedM | AbilM | ResistM | **Threat** | Traits |
|------|------|----|-------|--------|-------|---------|-----------|--------|
| Ent | 5 | 480 | 28 | 0.56 | 1.0 | 1.3 | **349** | poisonResist |
| Golem | 10 | 900 | 38 | 0.76 | 1.0 | 1.5 | **1026** | armorPlated + poisonResist |
| Medusa | 15 | 1400 | 52 | 1.04 | 1.0 | 1.0 | **1456** | — |
| Crimson Stalker | 20 | 2400 | 48 | 0.96 | 1.0 | 1.0 | **2304** | — |
| Twin Dragon | 25 | 3800 | 30 | 0.60 | 1.0 | 1.5 | **3420** | fireImmune + armor×0.55 |

### Map 2 Boss Threat Scores (Volcanic Inferno)

| Boss | Wave | HP | Speed | SpeedM | AbilM | ResistM | **Threat** | Traits |
|------|------|----|-------|--------|-------|---------|-----------|--------|
| Lav Golem | 5 | 950 | 35 | 0.70 | 1.0 | 1.3 | **865** | fireImmune + armor |
| Rat King | 10 | 2100 | 52 | 1.04 | 1.0 | 1.3 | **2837** | poisonResist |
| Vampire | 15 | 3000 | 50 | 1.00 | 1.3 | 1.3 | **5070** | regenerating + iceImmune |
| Lizardman | 20 | 3300 | 45 | 0.90 | 1.0 | 1.3 | **3861** | armorPlated (×0.38) |
| Demon | 25 | 4600 | 28 | 0.56 | 1.0 | 1.6 | **4122** | fireImmune + lightningResist + armor |

### Map 3 Boss Threat Scores (Frozen Tundra)

| Boss | Wave | HP | Speed | SpeedM | AbilM | ResistM | **Threat** | Traits |
|------|------|----|-------|--------|-------|---------|-----------|--------|
| Ice Golem | 5 | 1100 | 32 | 0.64 | 1.0 | 1.3 | **915** | iceImmune + armor |
| Frozen Knight | 10 | 1750 | 48 | 0.96 | 1.0 | 1.6 | **2688** | iceImmune + lightningResist + armor |
| Vampire | 15 | 3000 | 50 | 1.00 | 1.3 | 1.3 | **5070** | regenerating + iceImmune |
| Lich | 20 | 3600 | 34 | 0.68 | 1.0 | 1.3 | **3182** | iceImmune |
| Frostmourne Demon | 25 | 6000 | 26 | 0.52 | 1.0 | 1.8 | **5616** | iceImmune + lightningResist + armor |

---

## 3. Resist → Efektif DPS Tablosu

Base DPS değerleri (kaynak koddan):

| Tower | Base DPS | vs None | vs Armored | vs Flying | vs fireImmune | vs iceImmune | vs lightningResist | vs poisonResist | vs Regen |
|-------|----------|---------|-----------|-----------|---------------|--------------|--------------------|-----------------|----------|
| Arrow | 32.4 | 32.4 | **21.1** | **42.1** | 32.4 | 32.4 | 32.4 | 32.4 | 32.4 |
| Frost | 33.0 | 33.0 | 33.0 | — | **49.5** | **8.3** | 33.0 | 33.0 | 33.0 |
| Fire | 35.0 | 35.0 | 35.0 | — | **8.8** | **52.5** | 35.0 | 35.0 | 35.0 |
| Lightning | 52.8 | 52.8 | **71.3** | 52.8 | 52.8 | **31.7** | **15.8** | 52.8 | 52.8 |
| Poison | 33.0 | 33.0 | 33.0 | — | 33.0 | 33.0 | 33.0 | **8.3** | **49.5** |

> **Kritik:** Lightning Armored'a karşı 71.3 DPS çıkarıyor. Arrow'un (21.1) 3.4×'i. Bu, Lightning'i armor meta'sında vazgeçilmez kılıyor.

> **Kritik:** Frostmourne Demon'a karşı aktif olan tower'lar: Fire(52.5) + Poison(33.0) + Arrow(32.4) = toplam ~118 DPS. Lightning(15.8) ve Frost(8.3) pratikte etkisiz. Bu "2-tower zorunluluğu" build çeşitliliğini yok ediyor.

---

## 4. Wave Threat Budget (Map 1 — Cursed Wilds)

Tahmini wave budget. Her wave için: `Σ(düşman threat × düşman sayısı)`.

| Wave | Düşman Sayısı | Ort. Threat/düşman | Toplam Normal | Boss Threat | **Wave Toplam** |
|------|---------------|-------------------|---------------|-------------|-----------------|
| 1 | 4 | 86 (goblin) | 344 | — | **344** |
| 2 | 6 | 100 | 600 | — | **600** |
| 3 | 8 | 130 | 1040 | — | **1040** |
| 4 | 10 | 160 | 1600 | — | **1600** |
| **5** | 6 | 120 | 720 | Ent 349 | **1069** |
| 8 | 13 | 220 | 2860 | — | **2860** |
| **10** | 10 | 200 | 2000 | Golem 1026 | **3026** |
| **15** | 15 | 250 | 3750 | Medusa 1456 | **5206** |
| **20** | 18 | 280 | 5040 | Crimson S. 2304 | **7344** |
| **25** | 20 | 300 | 6000 | Twin Dragon 3420 | **9420** |

> Boss wave'lerde threat, normal wave threat'in **üzerine** ekleniyor. Wave 25'te boss+normal toplam ~9400 — wave 1'in **27×'i**.

---

## 5. Difficulty Scaling Analizi

### Mevcut Modifierlar

| Difficulty | HP Mult | Spawn Interval | Wave Bonus Mult | Start Gold | Lives |
|------------|---------|----------------|-----------------|------------|-------|
| Easy | ×0.65 | 1.00s | ×1.4 | 130g | 30 |
| Normal | ×1.00 | 0.70s | ×1.0 | 95g | 20 |
| Hard | ×1.40 | 0.52s | ×0.7 | 75g | 15 |

### Net Tehdit Farkı (Hard vs Normal)

```
Threat(Hard) / Threat(Normal) = HP×1.40 × (spawnInterval_Normal / spawnInterval_Hard)
                               = 1.40 × (0.70 / 0.52)
                               = 1.40 × 1.35
                               ≈ 1.89×
```

Hard modunda tehdit ~%89 artıyor. Gelir ise wave bonus ×0.7 ve start gold 75g → yaklaşık %25 azalıyor.

**Sonuç:** Hard'da ~2× tehdit, ~%75 gelir = net ~2.5× daha zor. Bu matematiksel gap kasıtlıysa tutarlı, ama oyunculara hissettirilen fark çok sert.

---

## 6. Tespit Edilen İmbalanslar

### I. Lightning Tower dominant (en kritik)

| Metrik | Değer | Hedef |
|--------|-------|-------|
| Base Power | 145.2 | 65–75 |
| DPS vs Armored | 71.3 | ~45 |
| Efektif chain DPS (3 hedef) | 158.4 | ~90 |

**Kök neden:** baseDamage=48 diğerlerinden %46 yüksek (avg 30–35) + chain Coverage=2.5 + armor bonus 1.35. Üçü üst üste.

**Rebalance önerisi:**
- baseDamage: 48 → 32 (DPS: 52.8 → 35.2)
- Sonuç Power: 35.2 × 2.5 × 1.0 × 1.1 = **96.8** (hâlâ hedefe yakın, chain upgrade ile diferansiye edilir)

### II. Fire Tower underpowered

| Metrik | Değer | Hedef |
|--------|-------|-------|
| Base Power | 40.4 | 55–65 |
| Fire rate | 0.7/s | 0.85/s |

**Kök neden:** AoE avantajı (Coverage=1.5) düşük fire rate (Reliability=0.7) ile dengeleniyor ama bu fazla cezalandırıcı. Coverage avantajı reliability kaybını tam telafi etmiyor.

**Rebalance önerisi:**
- baseFireRate: 0.7 → 0.85 (DPS: 35.0 → 42.5)
- Sonuç Power: 42.5 × 1.5 × 1.1 × 0.85 = **59.6** ✓

### III. Poison Tower underpowered

| Metrik | Değer | Hedef |
|--------|-------|-------|
| Base Power | 46.3 | 55–65 |
| vs Regenerating | 49.5 DPS | yeterli |
| vs Poison Resist | 8.3 DPS | — |

**Kök neden:** DoT spread (Coverage=1.2) ve persist (Utility=1.3) avantajları baseDamage=30 ile yetersiz kalıyor. Regen counter rolünü oynayabiliyor ama genel DPS rekabetçi değil.

**Rebalance önerisi:**
- baseDamage: 30 → 36 (DPS: 33.0 → 39.6)
- Sonuç Power: 39.6 × 1.2 × 1.3 × 0.9 = **55.7** ✓

### IV. Boss resist duvarı çok sert (Map 3)

Frostmourne Demon'a karşı aktif tower sayısı: 2/5 (Fire + Poison). Lightning ve Frost pratikte etkisiz.

**Rebalance önerisi (opsiyonel):**
- `lightningResist` multiplier: ×0.30 → ×0.45 (hâlâ %55 ceza, Lightning kısmen katkı sağlar)
- `fireImmune` multiplier: ×0.25 → ×0.35 (hâlâ %65 ceza, "sıfır hasar" hissi gider)

---

## Hedef Tower Power ve Role Matrix

### Hedef Power Değerleri

| Tower | Şu an | Hedef | Delta |
|-------|-------|-------|-------|
| Arrow | 38.9 | 40–45 | ✓ |
| Frost | 66.0 | 60–70 | ✓ |
| Fire | 40.4 | 55–65 | +15–25 |
| Lightning | 145.2 | 65–75 | −70 |
| Poison | 46.3 | 55–65 | +10–20 |

### Tower Role Matrix

| Tower | Swarm | Tank/Armor | Fast | Flying | Boss |
|-------|-------|------------|------|--------|------|
| Arrow | B | C | A | **S** | C |
| Fire | **S** | C | C | F | B |
| Frost | B | C | **S** | C | A |
| Lightning | A | **S** | B | A | C |
| Poison | B | **S** | C | F | **S** |

S=Güçlü, A=İyi, B=Normal, C=Zayıf, F=İşe yaramaz

---

*Son güncelleme: v0.19.0. Bu belge TowerNode.swift ve EnemyNode.swift kaynak koduna dayalıdır — değerler değişirse güncellenmeli.*
