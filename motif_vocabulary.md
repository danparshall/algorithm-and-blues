# Core 3-Note Melodic Motif Vocabulary
## Building Blocks for Combinatorial Melody Generation

### Notation Convention
Each motif is described as a pair of **directed intervals in semitones**: (iâ‚, iâ‚‚) where positive = ascending, negative = descending, 0 = repeated note. The motif is defined relative to the starting note, making it transposition-invariant.

Example: (+4, +3) means "up a major 3rd, then up a minor 3rd" = ascending major triad arpeggio from any starting note.

---

## Category 1: Scale Runs (Stepwise Motion)
**ScÃ¨nes Ã  faire justification**: Conjunct (stepwise) motion is the most fundamental melodic principle in Western music. Corpus studies show ~60-70% of all melodic intervals are steps. Any tonal melody will contain these patterns.

### Major scale step patterns (3 consecutive scale tones)
| ID | Intervals | Example (in C) | Pattern Name | Frequency |
|----|-----------|----------------|--------------|-----------|
| S1 | (+2, +2) | C-D-E, F-G-A | Ascending whole-whole | Very High |
| S2 | (+2, +1) | E-F#-G (or D-E-F) | Ascending whole-half | Very High |
| S3 | (+1, +2) | E-F-G, B-C-D | Ascending half-whole | Very High |
| S4 | (-2, -2) | E-D-C, A-G-F | Descending whole-whole | Very High |
| S5 | (-1, -2) | F-E-D, C-B-A | Descending half-whole | Very High |
| S6 | (-2, -1) | G-F-E, D-C-B | Descending whole-half | Very High |

### Chromatic patterns
| ID | Intervals | Example | Pattern Name | Frequency |
|----|-----------|---------|--------------|-----------|
| S7 | (+1, +1) | C-C#-D | Ascending chromatic | High |
| S8 | (-1, -1) | D-C#-C | Descending chromatic | High |

### Harmonic minor augmented second patterns
| ID | Intervals | Example | Pattern Name | Frequency |
|----|-----------|---------|--------------|-----------|
| S9 | (+1, +3) | E-F-G# (harm. minor) | Half-aug2nd ascending | Medium |
| S10 | (+3, +1) | G#-B-C (harm. minor context) | Aug2nd-half ascending | Medium |
| S11 | (-3, -1) | G#-F-E | Aug2nd-half descending | Medium |
| S12 | (-1, -3) | C-B-G# | Half-aug2nd descending | Medium |

**Subtotal: 12 motifs**

---

## Category 2: Triad Arpeggios
**ScÃ¨nes Ã  faire justification**: Arpeggiation of triads is one of the two primary types of melodic motion (along with stepwise). Triads are the harmonic foundation of virtually all tonal music. These patterns are functionally indispensable.

### Root position triads (Root â†’ 3rd â†’ 5th)
| ID | Intervals | Example | Chord Type | Frequency |
|----|-----------|---------|------------|-----------|
| A1 | (+4, +3) | C-E-G | Major ascending | Very High |
| A2 | (-3, -4) | G-E-C | Major descending | Very High |
| A3 | (+3, +4) | C-Eb-G | Minor ascending | Very High |
| A4 | (-4, -3) | G-Eb-C | Minor descending | Very High |
| A5 | (+3, +3) | C-Eb-Gb | Diminished ascending | Medium |
| A6 | (-3, -3) | Gb-Eb-C | Diminished descending | Medium |
| A7 | (+4, +4) | C-E-G# | Augmented ascending | Low-Med |
| A8 | (-4, -4) | G#-E-C | Augmented descending | Low-Med |

### First inversion triads (3rd â†’ 5th â†’ Octave)
| ID | Intervals | Example | Chord Type | Frequency |
|----|-----------|---------|------------|-----------|
| A9 | (+3, +5) | E-G-C | Major 1st inv. asc. | High |
| A10 | (-5, -3) | C-G-E | Major 1st inv. desc. | High |
| A11 | (+4, +5) | Eb-G-C | Minor 1st inv. asc. | High |
| A12 | (-5, -4) | C-G-Eb | Minor 1st inv. desc. | High |

### Second inversion triads (5th â†’ Octave â†’ 3rd)
| ID | Intervals | Example | Chord Type | Frequency |
|----|-----------|---------|------------|-----------|
| A13 | (+5, +4) | G-C-E | Major 2nd inv. asc. | High |
| A14 | (-4, -5) | E-C-G | Major 2nd inv. desc. | High |
| A15 | (+5, +3) | G-C-Eb | Minor 2nd inv. asc. | High |
| A16 | (-3, -5) | Eb-C-G | Minor 2nd inv. desc. | High |

### Partial arpeggios (Root â†’ 3rd only, 3rd â†’ 5th only, etc.)
| ID | Intervals | Example | Pattern Name | Frequency |
|----|-----------|---------|--------------|-----------|
| A17 | (+4, 0) | C-E-E | Major 3rd + repeat | High |
| A18 | (+3, 0) | C-Eb-Eb | Minor 3rd + repeat | High |
| A19 | (0, +4) | C-C-E | Repeat + major 3rd | High |
| A20 | (0, +3) | C-C-Eb | Repeat + minor 3rd | High |

**Subtotal: 20 motifs**

---

## Category 3: Neighbor Tone Patterns
**ScÃ¨nes Ã  faire justification**: Neighbor tones (upper and lower) are one of the most fundamental ornamental/embellishment patterns in tonal music. They appear in every genre, every era, and are explicitly taught as basic compositional technique.

### Upper neighbors (depart upward, return)
| ID | Intervals | Example | Pattern Name | Frequency |
|----|-----------|---------|--------------|-----------|
| N1 | (+1, -1) | C-Db-C | Half-step upper neighbor | Very High |
| N2 | (+2, -2) | C-D-C | Whole-step upper neighbor | Very High |
| N3 | (+1, -2) | C-Db-Cb(=B) | Chromatic upper, diatonic return | Medium |
| N4 | (+2, -1) | C-D-Db(=C#) | Diatonic upper, chromatic return | Medium |

### Lower neighbors (depart downward, return)
| ID | Intervals | Example | Pattern Name | Frequency |
|----|-----------|---------|--------------|-----------|
| N5 | (-1, +1) | C-B-C | Half-step lower neighbor | Very High |
| N6 | (-2, +2) | C-Bb-C | Whole-step lower neighbor | Very High |
| N7 | (-1, +2) | C-B-C# | Chromatic lower, diatonic return | Medium |
| N8 | (-2, +1) | C-Bb-B(=Cb) | Diatonic lower, chromatic return | Medium |

### Double neighbor / changing tone
| ID | Intervals | Example | Pattern Name | Frequency |
|----|-----------|---------|--------------|-----------|
| N9 | (+2, -4) | C-D-Bb (upper then skip to lower) | Upper neighbor escape | Medium |
| N10 | (-2, +4) | C-Bb-D (lower then skip to upper) | Lower neighbor escape | Medium |
| N11 | (+1, -3) | C-Db-Bb | Chromatic upper escape | Medium |
| N12 | (-1, +3) | C-B-D | Chromatic lower escape | Medium |

**Subtotal: 12 motifs**

---

## Category 4: Step-Skip Combinations
**ScÃ¨nes Ã  faire justification**: The principle of "step then leap" and "leap then step" (often in opposite directions) is one of the oldest and most universal voice-leading conventions. These patterns appear wherever melody exists.

### Step up then skip up (continuation)
| ID | Intervals | Example | Pattern | Frequency |
|----|-----------|---------|---------|-----------|
| K1 | (+2, +3) | C-D-F | Whole step + min 3rd up | High |
| K2 | (+2, +4) | C-D-F# | Whole step + maj 3rd up | Medium |
| K3 | (+1, +3) | B-C-Eb | Half step + min 3rd up | Medium |
| K4 | (+1, +4) | B-C-E | Half step + maj 3rd up | Medium |
| K5 | (+2, +5) | C-D-G | Whole step + P4 up | High |
| K6 | (+2, +7) | C-D-A | Whole step + P5 up | Medium |

### Step up then skip down (reversal / arch)
| ID | Intervals | Example | Pattern | Frequency |
|----|-----------|---------|---------|-----------|
| K7 | (+2, -3) | C-D-B | Step up, skip down (m3) | High |
| K8 | (+2, -4) | C-D-Bb | Step up, skip down (M3) | Medium |
| K9 | (+2, -5) | C-D-A(below) | Step up, skip down (P4) | High |
| K10 | (+1, -3) | C-Db-Bb | Half up, skip down (m3) | Medium |

### Skip up then step down (leap-step resolution)
| ID | Intervals | Example | Pattern | Frequency |
|----|-----------|---------|---------|-----------|
| K11 | (+3, -1) | C-Eb-D | Min 3rd up, half step down | High |
| K12 | (+3, -2) | C-Eb-Db | Min 3rd up, whole step down | High |
| K13 | (+4, -1) | C-E-Eb | Maj 3rd up, half step down | High |
| K14 | (+4, -2) | C-E-D | Maj 3rd up, whole step down | High |
| K15 | (+5, -1) | C-F-E | P4 up, half step down | Very High |
| K16 | (+5, -2) | C-F-Eb | P4 up, whole step down | High |
| K17 | (+7, -1) | C-G-F# | P5 up, half step down | Medium |
| K18 | (+7, -2) | C-G-F | P5 up, whole step down | Very High |

### Descending mirrors of above (selected highest-frequency)
| ID | Intervals | Example | Pattern | Frequency |
|----|-----------|---------|---------|-----------|
| K19 | (-2, -3) | E-D-B | Step down + skip down | High |
| K20 | (-2, -5) | E-D-G(below) | Step down + P4 down | High |
| K21 | (-3, +1) | Eb-C-Db | Skip down, half step up | High |
| K22 | (-3, +2) | Eb-C-D | Skip down, whole step up | High |
| K23 | (-4, +1) | E-C-Db | Maj 3rd down, half step up | High |
| K24 | (-4, +2) | E-C-D | Maj 3rd down, whole step up | High |
| K25 | (-5, +1) | F-C-Db | P4 down, half step up | High |
| K26 | (-5, +2) | F-C-D | P4 down, whole step up | Very High |
| K27 | (-7, +2) | G-C-D | P5 down, whole step up | Very High |
| K28 | (-7, +1) | G-C-Db | P5 down, half step up | Medium |

**Subtotal: 28 motifs**

---

## Category 5: Repeated Note Patterns
**ScÃ¨nes Ã  faire justification**: Note repetition is one of the most basic rhythmic/melodic devices. Repeated notes with a step or skip departure are extremely common in vocal and instrumental music.

| ID | Intervals | Example | Pattern Name | Frequency |
|----|-----------|---------|--------------|-----------|
| R1 | (0, 0) | C-C-C | Triple repeat | Very High |
| R2 | (0, +1) | C-C-C# | Repeat + half step up | High |
| R3 | (0, +2) | C-C-D | Repeat + whole step up | Very High |
| R4 | (0, -1) | C-C-B | Repeat + half step down | High |
| R5 | (0, -2) | C-C-Bb | Repeat + whole step down | Very High |
| R6 | (0, +5) | C-C-F | Repeat + P4 up | High |
| R7 | (0, +7) | C-C-G | Repeat + P5 up | High |
| R8 | (0, -5) | C-C-G(below) | Repeat + P4 down | Medium |
| R9 | (0, -7) | C-C-F(below) | Repeat + P5 down | Medium |
| R10 | (+2, 0) | C-D-D | Step up + repeat | High |
| R11 | (-2, 0) | D-C-C | Step down + repeat | High |
| R12 | (+5, 0) | C-F-F | P4 up + repeat | Medium |
| R13 | (+7, 0) | C-G-G | P5 up + repeat | Medium |
| R14 | (-5, 0) | F-C-C | P4 down + repeat | Medium |

**Subtotal: 14 motifs**

---

## Category 6: Pentatonic Patterns
**ScÃ¨nes Ã  faire justification**: The pentatonic scale (Do-Re-Mi-Sol-La) is arguably the most universal musical structure on Earth, appearing independently across virtually every culture. Patterns confined to the pentatonic scale have an extremely high probability of appearing in future music.

### Pentatonic skips (non-stepwise pentatonic motion)
| ID | Intervals | Example | Pattern Name | Frequency |
|----|-----------|---------|--------------|-----------|
| P1 | (+2, +3) | C-D-F | Do-Re-Fa (pent step+skip) | Very High |
| P2 | (+3, +2) | F-A-B (in C pent: F-G-A remap)| Pentatonic 3rd motion | High |
| P3 | (-2, -3) | A-G-E | La-Sol-Mi descending | Very High |
| P4 | (-3, -2) | E-C-Bb (context dep.) | Pent skip + step desc. | High |
| P5 | (+2, +2) | C-D-E | Do-Re-Mi (shared w/ S1) | Very High |
| P6 | (+3, +4) | A-C-E (Am arp, pent subset) | Minor pent arp asc | Very High |
| P7 | (-4, -3) | E-C-A | Minor pent arp desc | Very High |

*Note: Many pentatonic patterns overlap with Categories 1-2. Listed here are the distinctly pentatonic sequences.*

**Subtotal: 7 motifs (some shared with other categories)**

---

## Category 7: Cadential / Tendency Tone Patterns
**ScÃ¨nes Ã  faire justification**: Tendency tone resolutions (leading tone â†’ tonic, scale degree 4 â†’ 3) are the most fundamental voice-leading patterns in tonal music. They literally define tonality. Any tonal composition must use these.

| ID | Intervals | Example (in C major) | Pattern Name | Frequency |
|----|-----------|---------------------|--------------|-----------|
| C1 | (+1, +5) | B-C-F (Ti-Do + up to Fa) | Resolution + 4th up | High |
| C2 | (+1, -7) | B-C-D(below) (Ti-Do-Re below) | Resolution + drop | Medium |
| C3 | (-1, -2) | Fa-Mi-Re (4-3-2) | Descending resolution | Very High |
| C4 | (+2, +1) | Re-Mi-Fa (2-3-4) | Ascending approach | Very High |
| C5 | (-2, -1) | Re-Do-Ti (2-1-7) | Cadential descent | Very High |
| C6 | (+1, 0) | Ti-Do-Do | Resolution + hold | High |
| C7 | (-1, 0) | Fa-Mi-Mi | Resolution + hold | High |
| C8 | (+2, -1) | Sol-La-Sol# wait... | â€” | â€” |

*Note: Many cadential patterns overlap with scale runs (Cat 1) when viewed as intervals. Their importance here is as functional resolutions, reinforcing the scÃ¨nes Ã  faire argument from a different angle.*

**Replacing C8:**
| C8 | (-2, +1) | Re-Do-C# (approach from above, chromatic lower neighbor to Re) | Chromatic approach | Medium |

**Subtotal: 8 motifs**

---

## Category 8: Octave and Large-Interval Patterns
**ScÃ¨nes Ã  faire justification**: Octave leaps and large interval patterns (especially P4, P5, octave) are standard melodic vocabulary used for emphasis, register change, and dramatic effect. Extremely common in vocal and instrumental music.

| ID | Intervals | Example | Pattern Name | Frequency |
|----|-----------|---------|--------------|-----------|
| L1 | (+12, -2) | C-C(8va)-Bb | Octave up + step down | High |
| L2 | (+12, -1) | C-C(8va)-B | Octave up + half down | Medium |
| L3 | (-12, +2) | C-C(8vb)-D | Octave down + step up | High |
| L4 | (+7, +5) | C-G-C(8va) | P5 + P4 (octave outline) | High |
| L5 | (+5, +7) | C-F-C(8va) | P4 + P5 (octave outline) | High |
| L6 | (-7, -5) | C-F(below)-C(8vb) | Descending octave outline | High |
| L7 | (-5, -7) | C-G(below)-C(8vb) | Desc octave outline alt | High |
| L8 | (+7, -7) | C-G-C | P5 up + P5 down (return) | Medium |
| L9 | (+5, -5) | C-F-C | P4 up + P4 down (return) | Medium |

**Subtotal: 9 motifs**

---

## Summary

| Category | Count | Justification Strength |
|----------|-------|----------------------|
| 1. Scale Runs | 12 | â˜…â˜…â˜…â˜…â˜… (strongest â€” literally the definition of melody) |
| 2. Triad Arpeggios | 20 | â˜…â˜…â˜…â˜…â˜… (foundational harmonic vocabulary) |
| 3. Neighbor Tones | 12 | â˜…â˜…â˜…â˜…â˜… (universal embellishment) |
| 4. Step-Skip Combos | 28 | â˜…â˜…â˜…â˜…â˜† (voice-leading conventions) |
| 5. Repeated Notes | 14 | â˜…â˜…â˜…â˜…â˜† (basic rhythmic/melodic device) |
| 6. Pentatonic | 7 | â˜…â˜…â˜…â˜…â˜… (cross-cultural universal) |
| 7. Cadential | 8 | â˜…â˜…â˜…â˜…â˜… (defines tonality itself) |
| 8. Large Intervals | 9 | â˜…â˜…â˜…â˜†â˜† (standard but less frequent) |
| **TOTAL** | **~110** | |

*Note: Some motifs appear in multiple categories (e.g., P1 and K1 are both (+2,+3)). After deduplication, the unique motif count is approximately **90-100**.*

---

## Combinatorial Implications

With ~100 unique motifs combined into sequences:

| Sequence Length | Motifs | Combinations | Notes in Melody |
|----------------|--------|--------------|-----------------|
| 3 motifs | 100 | 1,000,000 | 7-9 notes |
| 4 motifs | 100 | 100,000,000 | 10-12 notes |
| 5 motifs | 100 | 10,000,000,000 | 13-15 notes |
| 6 motifs | 100 | 1,000,000,000,000 | 16-18 notes |

The **sweet spot for copyright protection** (12-15 notes = 4-5 motifs) yields 100M to 10B candidate sequences before any filtering.

### Filtering will reduce this dramatically:
- Musical validity constraints (avoid awkward register jumps, enforce range limits)
- Transition smoothness (prefer shared tones or stepwise connections at motif boundaries)
- Duplicate/near-duplicate removal
- Human aesthetic curation (the documented up/down vote process)

**Estimated viable candidates after automated filtering**: ~1-10M
**Estimated keeper rate from human curation**: ~1-5%
**Final curated melodies per generation cycle**: ~10,000-500,000

This is a highly tractable pipeline.
