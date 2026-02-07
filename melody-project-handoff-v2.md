# Melody Generation & Copyright Project â€” Handoff Doc v2

**Date:** 2025-02-05 (Session 3)
**Previous handoff:** melody-project-handoff.md (v1)

---

## 1. What Was Accomplished This Session

### Pipeline Built & Run
- **melody_pipeline.py** â€” generates all 4-motif Tier 1 chains, applies 4 filters
- **score_chains.py** â€” scores surviving chains on 6 musical quality dimensions

### Filter Results (Tier 1: 23 motifs, 4-motif chains)

| Stage | Count | Survival |
|---|---|---|
| Raw chains (23â´) | 279,841 | â€” |
| After range (Â±14 semitones) | 249,790 | 89.3% |
| After no-repeat | 221,791 | 88.8% |
| After contour (arch/valley preference) | 129,072 | 58.2% |
| After junction quality | 106,821 | 82.8% |
| **Final survivors** | **106,821** | **38.2%** |

### Scoring Results

| Tier | Count | Score Threshold | Purpose |
|---|---|---|---|
| Exceptional (top 5%) | 5,343 | â‰¥ 0.8426 | First registration batch |
| Good (next 15%) | 16,055 | â‰¥ 0.7708 | Second registration batch |
| Acceptable (next 30%) | 32,023 | â‰¥ 0.6869 | Later expansion |
| Below (bottom 50%) | 53,400 | < 0.6869 | Review for documented rejection |

Composite score range: 0.2946 â€“ 0.9790, mean 0.6838.

### Scoring Dimensions (each 0â€“1, weighted sum = composite)

| Dimension | Weight | Mean | What It Measures |
|---|---|---|---|
| Harmonic clarity | 0.25 | 0.673 | Fraction of 3-note windows fitting recognized chords |
| Resolution quality | 0.15 | 0.645 | Final note stability in detected key |
| Climax placement | 0.15 | 0.793 | Peak/trough in golden zone (50â€“80% through) |
| Intervallic variety | 0.15 | 0.810 | Shannon entropy of intervals (penalizes monotony + chaos) |
| Leap resolution | 0.15 | 0.608 | Fraction of leaps resolved by contrary-motion step |
| Key stability | 0.15 | 0.581 | Krumhansl-Kessler correlation with best-fit key |

---

## 2. Data Artifacts

### Files Produced

| File | Size | Contents |
|---|---|---|
| `melody_pipeline.py` | 14 KB | Filter pipeline (filters 1â€“4) |
| `score_chains.py` | 14 KB | 6-dimension scorer |
| `filtered_chains_tier1.json` | 64 MB | 106,821 chains with all metadata, pre-scoring |
| `filtered_intervals_tier1.json` | 5.3 MB | Lightweight: just interval sequences for collision detection |
| `scored_chains_tier1.json` | 98 MB | Full chain records with scores, sorted by composite |
| `top_chains_tier1.json` | 4.9 MB | Top 5% (5,343 chains) for priority review |

### Record Schema (per chain)

```json
{
  "chain_id": 0,
  "score_rank": 1,
  "motif_indices": [11, 0, 11, 18],
  "motif_ids": [["R1"], ["K27"], ["R1"], ["K1", "P1"]],
  "intervals": [0, 0, -7, 2, 0, 0, 2, 3],
  "intervals_str": "0,0,-7,2,0,0,2,3",
  "midi_pitches": [60, 60, 60, 53, 55, 55, 55, 57, 60],
  "net_displacement": 0,
  "pitch_range_rel": [-7, 0],
  "contour_summary": [0, -5, 0, 5],
  "categories_used": ["Pentatonic", "Repeated Notes", "Step-Skip"],
  "detected_key": "C major",
  "key_correlation": 0.8255,
  "chord_suggestions": ["unison", "power", "Csus4", ...],
  "scores": {
    "harmonic_clarity": 1.0,
    "resolution": 1.0,
    "climax": 0.9167,
    "interval_variety": 0.9722,
    "leap_resolution": 1.0,
    "key_stability": 0.9709
  },
  "composite_score": 0.979,
  "quality_tier": "exceptional",
  "collision_status": null,
  "collision_matches": [],
  "collision_distance": null,
  "curation_vote": null,
  "curation_notes": null,
  "curation_timestamp": null
}
```

### Representation Decisions
- **Transposition-invariant**: primary key is `intervals` (directed interval sequence), not absolute pitches
- **MIDI pitches anchored at C4 (60)**: for playback convenience only; the interval sequence is what matters for collision detection and copyright
- **Chord suggestions logged per 3-note window**: supports future harmonic coherence pass and replayability
- **Detected key + correlation stored**: supports future key-aware filtering and registration grouping

---

## 3. Key Design Decisions & Rationale

### Chain Model: Overlapping Motifs
Each 3-note motif shares its last note with the first note of the next motif. A 4-motif chain = 9 notes = 8 intervals. This is musically natural (phrases connect) and gives the right length for copyright relevance.

### Contour Filter: Arch/Valley Preference
The non-zero net displacements must form at most 2 contiguous groups with exactly 1 sign transition (riseâ†’fall = arch, fallâ†’rise = valley). Zeros allowed anywhere (plateaus). Rejects zigzag (2+ transitions), strong monotonic drift (3+ same sign), and static (all zero). Cut 42% of chains.

### Scoring as Continuous Signal, Not Hard Gate
Filter 5 (harmonic coherence) from the original plan was implemented as a *scorer* rather than a binary filter. This preserves chains that are harmonically ambiguous but might still be interesting, while ranking them lower. The hard filtering is done by the range/repeat/contour/junction filters; the scoring guides review priority.

### Coverage Maximization > Exhaustive Registration
The legal strategy doesn't require registering all 106K chains. Substantial similarity means each registered melody "claims" a neighborhood in interval-space. Selecting a diverse subset maximizes coverage. This is a set-cover / diversity problem â€” see next steps.

### Temperature-Based Review Queue (Design, Not Yet Implemented)
- Present chains for human review with probability âˆ exp(score / Ï„)
- Low Ï„ â†’ mostly top chains first (build "gems" portfolio fast)
- Raise Ï„ over time â†’ surface mid/low chains for documented rejection
- Log everything: score, temperature at presentation, vote, notes
- The acceptance-rate-vs-temperature curve is itself a legal exhibit

---

## 4. Collision Detection Architecture (Designed, Not Yet Built)

### Target Corpus
- **Lakh MIDI Dataset (LMD)**: 176,581 MIDI files, largest symbolic music corpus
- **Lakh Clean subset**: ~17,000 files with artist labels, ~2,000 with labeled melody tracks
- Analysis page: https://lakhcleananalysis.sourceforge.io/
- The labeled melody tracks can seed a melody-vs-accompaniment classifier for the rest

### Comparison Method
- Extract melody lines from LMD as **interval sequences** (transposition-invariant)
- Check if any chain's 8-interval sequence appears as a **contiguous substring** of any corpus melody's interval sequence
- For partial matching (substantial similarity): use edit distance with threshold
- Store results in `collision_status` / `collision_matches` / `collision_distance` fields

### Key Decisions Still Needed
- Edit distance threshold for "substantially similar" (probably 1â€“2 edits for 8 intervals)
- Whether to also check interval *subsequences* (non-contiguous matches)
- How to handle the 160K+ MIDI files without labeled melody tracks (melody extraction classifier needed)
- Whether to extend beyond LMD (e.g., synthesize a larger corpus from MusicBrainz metadata)

---

## 5. Next Steps (Priority Order)

### Immediate (Next Session)
1. **Similarity-radius deduplication & coverage maximization** â€” this is the biggest gap in the current pipeline. The 106K chains are exactly unique but many are near-duplicates (edit distance 1â€“2 on the 8-interval sequence). Each registered melody "claims" a neighborhood in interval-space (all sequences a court would consider substantially similar). Current chains likely have massive overlap in their claimed neighborhoods.
   - **Step 1: Cluster** â€” group chains within edit distance N of each other, keep highest-scoring representative per cluster. Estimated reduction: 106K â†’ ~10â€“30K cluster centers.
   - **Step 2: Farthest-point selection** â€” from cluster centers, greedily select the set that maximizes minimum pairwise distance (diversity maximization).
   - **Step 3: Coverage estimation** â€” given a selection set and a similarity radius, estimate what fraction of "all musically valid 8-interval sequences" falls within the claimed territory. This produces a concrete number: "these N melodies cover approximately X% of the viable melodic phrase space."
   - **Key design decision**: what edit distance defines "substantially similar"? Likely 1â€“2 edits on 8 intervals. At edit distance 1, each chain covers ~192 neighbors. At edit distance 2, ~18,000. This dramatically affects how many registrations are needed for full coverage.
2. **Collision detection against LMD Clean** â€” download the ~2K labeled-melody files, extract interval sequences, run substring matching against our chains. This gives a real collision rate. Note: collision detection should run *after* similarity deduplication (no point checking near-duplicates separately).
3. **Temperature-based review queue** â€” MIDI playback + vote logging with Boltzmann sampling.

### Soon After
4. **Melody extraction classifier** â€” train on the 2K labeled tracks to identify melody lines in the remaining 174K LMD files.
5. **Tier 2 expansion** â€” run the full pipeline with all 68 motifs (21.4M raw chains). Will need optimization (current pipeline is O(Nâ´) brute force; Tier 2 needs pruning or generation-with-filtering).
6. **Harmonic coherence refinement** â€” consider a proper chord grammar pass on top of the current windowed scorer.

### Registration Phase
7. **GRAM batch filing** â€” group top chains into "albums" of 20, file via GRAM for ~$3.25/melody with per-song statutory damages.
8. **Documentation package** â€” compile the pipeline code, curation logs, and rejection records into an exhibit package for the copyright registration.

---

## 6. Legal Strategy Reminder

The core argument: individual motifs are scÃ¨nes Ã  faire (unprotectable), but the *selection and arrangement* of motifs into specific chains, filtered by musically-informed rules and curated by documented human judgment, constitutes original creative authorship.

Key strengthening factors:
- **The scoring system itself** embodies aesthetic judgment (choice of dimensions, weights, thresholds)
- **Temperature-based review** generates a documented trail of discriminating taste
- **Rejection records** are as important as approvals â€” "I rejected this because..." demonstrates active curation
- **The pipeline code** is itself a creative artifact documenting the selection methodology

Target outcome: Ninth Circuit or comparable court confirms that human-curated combinations of public-domain elements merit copyright protection, establishing precedent for human creative judgment as the copyrightable act even when combinatorial generation assists the process.
