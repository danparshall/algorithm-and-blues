# Melody Generation & Copyright Project â€” Handoff Doc v3

**Date:** 2025-02-05 (Session 4)
**Previous handoff:** melody-project-handoff-v2.md

---

## 1. What Was Accomplished This Session

### Key Realization: Chain Length Was Wrong

Original (overlapping) model gave us only 9 notes â€” too short for copyright. We explored two fixes, then discovered a critical error in our overlap model.

### The Breakthrough: Interval Overlap vs. Note Overlap

**Note overlap (what we initially assumed):**
- Motif 1 ends on note C, Motif 2 starts on note C
- Any motif can follow any other motif
- 6 motifs â†’ 23â¶ = 148 million combinations

**Interval overlap (the correct model):**
- Motif 1 = intervals (iâ‚, iâ‚‚), Motif 2 = intervals (iâ‚‚, iâ‚ƒ)
- The LAST interval of motif N must EQUAL the FIRST interval of motif N+1
- This is a **massive constraint** â€” average branching factor is only ~2.7

**Corrected combinatorics with interval overlap:**

| Motifs | Intervals | Notes | Raw chains |
|--------|-----------|-------|------------|
| 6 | 7 | 8 | 3,048 |
| 8 | 9 | 10 | 20,903 |
| 10 | 11 | 12 | 143,283 |
| 11 | 12 | 13 | 375,123 |

**For 12 notes: ~143K chains** â€” completely tractable!

### Why Interval Overlap is Better

1. **Musically meaningful**: Every sliding 3-note window is a recognized motif. The melody is "always in vocabulary."

2. **Legally stronger**: The entire melody is built from overlapping public-domain patterns, not blocks connected by arbitrary glue.

3. **Tractable**: 143K is small enough to enumerate exhaustively, no sampling needed.

### What We Still Need to Verify

- Does the interval-overlap model match how real melodies work?
- What % of 3-note windows in real music match our Tier 1 motifs?
- The real test: **how does it sound?**

### Code Written (May Need Revision)

`melody_pipeline_v2.py` â€” implements the NON-overlapping model with junctions. This was built before we understood interval overlap correctly. It works but may be superseded by a simpler interval-overlap generator.

**Sample run (500K chains, junction model):**
- Filter survival: ~23%
- Dedup reduction: 500K â†’ 3,507 representatives (0.7%)

---

## 2. What Needs To Happen Next: Corpus Analysis

Before committing to the interval-overlap model, we need empirical validation from real melodies.

### Questions to Answer

1. **Motif coverage**: What % of 3-note sliding windows in real melodies match our 23 Tier 1 motifs? If it's high (>70%), the interval-overlap model is validated. If low, our motif vocabulary is incomplete.

2. **Transition frequencies**: Among our 23 motifs, which transitions actually occur? (Motif A â†’ Motif B requires A's second interval = B's first interval.) Are some transitions 100Ã— more common than others?

3. **Gap analysis**: When a 3-note window does NOT match a Tier 1 motif, what is it? Should we add more motifs, or are these genuinely rare patterns?

4. **Phrase length**: What's the distribution of melodic phrase lengths? Is 12 notes a reasonable target?

5. **Interval bigrams**: What's the overall interval-to-interval transition matrix? (This tells us if stepwise motion dominates, etc.)

### Recommended Corpus: Lakh MIDI Dataset

- **Full LMD**: 176,581 MIDI files
- **LMD-matched**: 45,129 files matched to MSD (has metadata)
- **Download**: http://hog.ee.columbia.edu/craffel/lmd/lmd_matched.tar.gz (~3.5GB)
- **Analysis page**: https://colinraffel.com/projects/lmd/

Alternative: Wikifonia (MusicXML lead sheets) if we want melody-only files, but it's been taken down. Archive.org may have mirrors.

### Analysis Pipeline to Build

```
1. Download corpus (LMD-matched or subset)
2. Parse MIDI files, extract melody tracks
   - Heuristic: highest-pitched monophonic track, or track named "melody"/"vocal"
   - Or use the ~2K labeled melody tracks from LMD-Clean
3. Convert to interval sequences (transposition-invariant)
4. For each melody, extract all 3-note sliding windows as (interval1, interval2) pairs
5. Compute:
   a. Match rate: % of windows that match Tier 1 motifs
   b. Match rate: % of windows that match Tier 1+2 motifs
   c. Unmatched window census: what are the common non-matching patterns?
   d. Transition matrix: given we're in motif A, probability of each motif B following
   e. Interval bigram distribution (what follows what at the raw interval level)
   f. Phrase length distribution (if boundary detection is feasible)
```

### Python Libraries Needed

- `pretty_midi` or `mido` for MIDI parsing
- `music21` for MusicXML (if using that format)
- Standard: `json`, `collections.Counter`, `numpy`

---

## 3. Interval-Overlap Transition Data

For the interval-overlap model, a motif can only follow another if the first motif's second interval equals the second motif's first interval.

**Tier 1 motifs grouped by first interval (what can FOLLOW a motif ending with this interval):**

| First interval | Count | These motifs can follow a motif ending with this interval |
|----------------|-------|----------------------------------------------------------|
| -7 | 1 | K27 |
| -5 | 1 | K26 |
| -4 | 1 | A4/P7 |
| -3 | 1 | A2 |
| -2 | 4 | K19/P3, S4, S6/C5, N6 |
| -1 | 2 | S5/C3, N5 |
| 0 | 3 | R5, R1, R3 |
| +1 | 2 | N1, S3 |
| +2 | 4 | N2, S2/C4, S1/P5, K1/P1 |
| +3 | 1 | A3/P6 |
| +4 | 1 | A1 |
| +5 | 1 | K15 |
| +7 | 1 | K18 |

**Tier 1 motifs grouped by second interval (what this motif can be followed by):**

| Second interval | Count | Motifs that END with this interval |
|-----------------|-------|-----------------------------------|
| -4 | 1 | A2 |
| -3 | 2 | A4/P7, K19/P3 |
| -2 | 5 | S4, S5/C3, R5, N2, K18 |
| -1 | 3 | S6/C5, N1, K15 |
| 0 | 1 | R1 |
| +1 | 2 | N5, S2/C4 |
| +2 | 6 | N6, R3, S3, S1/P5, K27, K26 |
| +3 | 2 | K1/P1, A1 |
| +4 | 1 | A3/P6 |

**Key observation:** Most motifs end with Â±2 (stepwise), so the "highways" in the transition graph are stepwise connections. Large leap endings (-4, -3, +3, +4) are rare and constrain what can follow.

**Average branching factor:** 2.74 (vs. 23 if unconstrained)

---

## 4. Key Files & Artifacts

### From This Session
- `/home/claude/melody_pipeline_v2.py` â€” generation pipeline with junction rules
- `/home/claude/selected_chains_v2.json` â€” 3,507 representative chains from sample run

### From Project Files
- `/mnt/project/motif_data.json` â€” 23 Tier 1 + 45 Tier 2 motifs with intervals
- `/mnt/project/motif_vocabulary.md` â€” full documentation of motif categories
- `/mnt/project/melody-project-handoff-v2.md` â€” previous session's summary

---

## 5. Specific Tasks for Next Session

### Task 1: Download & Prep Corpus

```bash
# Option A: LMD-matched (45K files, ~3.5GB)
wget http://hog.ee.columbia.edu/craffel/lmd/lmd_matched.tar.gz
tar -xzf lmd_matched.tar.gz

# Option B: Smaller sample for quick iteration
# Grab 1000 random files from LMD
```

### Task 2: Build MIDI Analysis Script

Create `analyze_corpus.py` that:
1. Iterates over MIDI files
2. Extracts melody track (heuristic or labeled)
3. Converts note sequence to intervals
4. Aggregates statistics across corpus

### Task 3: Motif Matching

Load `motif_data.json`, build a lookup dict from interval pairs to motif IDs, then scan corpus for matches.

### Task 4: Report Generation

Output a JSON summary with:
- Interval frequency distribution
- Bigram frequency matrix
- Motif match rates
- Phrase length distribution
- Junction interval distribution (if phrase boundaries detected)

---

## 6. Design Decision Pending Corpus Data

**Current leading approach: Interval-overlap model with 10 motifs (12 notes)**

This gives ~143K raw chains, which is small enough to:
- Enumerate exhaustively
- Apply all filters
- Deduplicate
- Listen to every survivor if needed

**What corpus data will tell us:**

| Finding | Implication |
|---------|-------------|
| High Tier 1 match rate (>70%) | Interval-overlap model is validated; proceed |
| Low match rate (<50%) | Need to expand motif vocabulary or relax overlap constraint |
| Some motifs never appear | Prune vocabulary for tighter legal argument |
| Some transitions dominate | Weight generation toward common transitions |

**Alternative if overlap model fails:** Fall back to non-overlapping model with constrained junctions (the code in `melody_pipeline_v2.py`), but tighten junction vocabulary based on corpus evidence.

---

## 7. Legal Strategy Reminder

We're building this to generate **copyrightable melodies** from public-domain building blocks. The corpus analysis serves two purposes:

1. **Engineering**: Build a generation system that produces musically coherent output
2. **Legal**: Demonstrate that our motifs truly are scÃ¨nes Ã  faire (they appear everywhere in existing music)

The second point means high motif match rates against the corpus are actually *good* for our legal argument â€” it proves these patterns are universal, not original to anyone.

---

## 8. Quick Reference: Motif Counts

| Tier | Count | Description |
|------|-------|-------------|
| Tier 1 (Very High frequency) | 23 | "Inevitable" â€” any tonal composer must use these |
| Tier 2 (High frequency) | 45 | "Standard practice" â€” very common building blocks |
| Tier 3 (Medium frequency) | 28 | Less common but still recognizable |
| Tier 4 (Low-Med frequency) | 2 | Rare (augmented triads) |
| **Total unique** | **98** | After deduplication |

For generation, we focus on Tier 1 (strongest legal defense) with optional Tier 2 expansion.
