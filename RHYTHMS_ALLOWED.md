# Allowed Rhythm Patterns for Melody Generation

## Overview

This document defines the **79 allowed 2-bar rhythm patterns** for melody generation. These patterns form the rhythmic skeleton for 4-bar melodic phrases (the 2-bar pattern repeats with pitch transformation).

## Notation

- `Q` = Quarter note (1 beat, attack)
- `H` = Half note (2 beats, attack on first beat) â€” also covers `Q.` (quarter + rest)
- `.` = Rest (1 beat, no attack)
- `|` = Bar line
- `.Q` prefix = One quarter-note pickup (anacrusis)

## Constraints Applied

1. **Beat 1 must have attack** â€” Bar 1 always starts with Q or H
2. **Beat 5 must have attack** â€” Bar 2 always starts with Q or H
3. **Resolution rule** â€” Bar 2 endings determine pickup requirement:
   - Ends with QQ â†’ not allowed (too rare)
   - Ends with single Q â†’ MUST become .Q pickup
   - Ends with H â†’ resolved (no pickup)
   - Ends with rest â†’ resolved (no pickup)
4. **Pickup restriction** â€” Only single quarter-note pickup (.Q) allowed
   - .H (half-note pickup) excluded as rare
   - QQ (two quarter pickups) excluded as rare

## Bar Pattern Vocabulary

### 9 Base Bar Patterns

| Pattern | Attacks | Ending | Starting |
|---------|---------|--------|----------|
| QQQQ | 4 | QQ | Q |
| QQH | 3 | H | Q |
| QHQ | 3 | Q | Q |
| HH | 2 | H | H |
| HQQ | 3 | QQ | H |
| H.Q | 2 | Q | H |
| QQ.. | 2 | rest | Q |
| QH. | 2 | rest | Q |
| H.. | 1 | rest | H |

### Bar 2 Options by Ending Type

| Bar 2 Pattern | Ending | Becomes | Display |
|---------------|--------|---------|---------|
| QQQQ | QQ | â€” | *excluded* |
| HQQ | QQ | â€” | *excluded* |
| QHQ | Q | .Q pickup | QH. |
| H.Q | Q | .Q pickup | H.. |
| QQH | H | resolved | QQH |
| HH | H | resolved | HH |
| QQ.. | rest | resolved | QQ.. |
| QH. | rest | resolved | QH. |
| H.. | rest | resolved | H.. |

---

## Complete Pattern List

### NO PICKUP (Resolved) â€” 45 patterns

Patterns where Bar 2 ends with H or rest.

| # | Pattern | Attacks |
|---|---------|---------|
| 1 | QQQQ \| QQH | 7 |
| 2 | QQQQ \| HH | 6 |
| 3 | QQQQ \| QQ.. | 6 |
| 4 | QQQQ \| QH. | 6 |
| 5 | QQH \| QQH | 6 |
| 6 | QHQ \| QQH | 6 |
| 7 | HQQ \| QQH | 6 |
| 8 | QQQQ \| H.. | 5 |
| 9 | QQH \| HH | 5 |
| 10 | QQH \| QQ.. | 5 |
| 11 | QQH \| QH. | 5 |
| 12 | QHQ \| HH | 5 |
| 13 | QHQ \| QQ.. | 5 |
| 14 | QHQ \| QH. | 5 |
| 15 | HH \| QQH | 5 |
| 16 | HQQ \| HH | 5 |
| 17 | HQQ \| QQ.. | 5 |
| 18 | HQQ \| QH. | 5 |
| 19 | H.Q \| QQH | 5 |
| 20 | QQ.. \| QQH | 5 |
| 21 | QH. \| QQH | 5 |
| 22 | QQH \| H.. | 4 |
| 23 | QHQ \| H.. | 4 |
| 24 | HH \| HH | 4 |
| 25 | HH \| QQ.. | 4 |
| 26 | HH \| QH. | 4 |
| 27 | HQQ \| H.. | 4 |
| 28 | H.Q \| HH | 4 |
| 29 | H.Q \| QQ.. | 4 |
| 30 | H.Q \| QH. | 4 |
| 31 | QQ.. \| HH | 4 |
| 32 | QQ.. \| QQ.. | 4 |
| 33 | QQ.. \| QH. | 4 |
| 34 | QH. \| HH | 4 |
| 35 | QH. \| QQ.. | 4 |
| 36 | QH. \| QH. | 4 |
| 37 | H.. \| QQH | 4 |
| 38 | HH \| H.. | 3 |
| 39 | H.Q \| H.. | 3 |
| 40 | QQ.. \| H.. | 3 |
| 41 | QH. \| H.. | 3 |
| 42 | H.. \| HH | 3 |
| 43 | H.. \| QQ.. | 3 |
| 44 | H.. \| QH. | 3 |
| 45 | H.. \| H.. | 2 |

### ONE QUARTER PICKUP (.Q) â€” 18 patterns

Patterns where Bar 2 originally ends with single Q (QHQ or H.Q), which wraps to become pickup.

| # | Pattern | Attacks |
|---|---------|---------|
| 46 | .Q QQQQ \| QH. | 6 |
| 47 | .Q QQQQ \| H.. | 5 |
| 48 | .Q QQH \| QH. | 5 |
| 49 | .Q QHQ \| QH. | 5 |
| 50 | .Q HQQ \| QH. | 5 |
| 51 | .Q QQH \| H.. | 4 |
| 52 | .Q QHQ \| H.. | 4 |
| 53 | .Q HH \| QH. | 4 |
| 54 | .Q HQQ \| H.. | 4 |
| 55 | .Q H.Q \| QH. | 4 |
| 56 | .Q QQ.. \| QH. | 4 |
| 57 | .Q QH. \| QH. | 4 |
| 58 | .Q HH \| H.. | 3 |
| 59 | .Q H.Q \| H.. | 3 |
| 60 | .Q QQ.. \| H.. | 3 |
| 61 | .Q QH. \| H.. | 3 |
| 62 | .Q H.. \| QH. | 3 |
| 63 | .Q H.. \| H.. | 2 |

---

## Summary Statistics

| Category | Count |
|----------|-------|
| No pickup (resolved) | 45 |
| One quarter pickup (.Q) | 18 |
| **TOTAL** | **63** |

### By Attack Count

| Attacks (2-bar) | Patterns | Notes (4-bar phrase) |
|-----------------|----------|---------------------|
| 2 | 2 | 4 notes |
| 3 | 14 | 6 notes |
| 4 | 23 | 8 notes |
| 5 | 18 | 10 notes |
| 6 | 5 | 12 notes |
| 7 | 1 | 14 notes |

### Sweet Spots for Copyright

- **8 notes** (4 attacks): 23 patterns â€” good for shorter phrases
- **10 notes** (5 attacks): 18 patterns â€” medium phrases  
- **12 notes** (6 attacks): 5 patterns â€” optimal for copyright (per corpus analysis)

---

## Usage Notes

### 4-Bar Phrase Construction

A complete melodic phrase uses the 2-bar rhythm twice:

```
[Pickup?] | Bar 1 | Bar 2-remainder | Bar 3 | Bar 4-remainder |
          |<-- Rhythm A ----------->|<-- Rhythm A (repeated) ->|
          |<-- Melody M ----------->|<-- Transform(M) -------->|
```

Where Transform(M) might be:
- Transposition (up a 3rd, 5th, or octave)
- Inversion (ascending â†’ descending)
- Sequence (same contour, different starting note)
- Slight variation

---

## Combinatorics

With 63 rhythm patterns and the melodic space from corpus analysis:

| Rhythm attacks | Rhythm patterns | Melodic options (Tier 1) | Combinations |
|----------------|-----------------|--------------------------|--------------|
| 4 | 23 | ~10K (4-note phrases) | ~230K |
| 5 | 18 | ~50K (5-note phrases) | ~900K |
| 6 | 5 | ~143K (6-note phrases) | ~715K |

**Total tractable space: ~2 million melody+rhythm combinations** before filtering.

After musical quality filters, estimated viable melodies: **100Kâ€“500K**
