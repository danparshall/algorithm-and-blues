# Melody Generation & Copyright Project â€” Handoff Doc

**Date:** 2025-02-05  
**Source chats:** "Copyright protection for musical arrangements and derivatives" + "Building on copyright protection for musical arrangements"

---

## 1. Core Strategy

Generate novel melodies by combining **common, public-domain musical motifs** (scÃ¨nes Ã  faire) into original sequences, then register the *selection and arrangement* as the copyrightable creative act.

**Legal backbone:** Ninth Circuit precedent holds that a *collection of otherwise unprotectable elements* may be eligible for copyright protection if those elements are numerous enough and their selection and arrangement original enough that the combination constitutes an original work of authorship.

---

## 2. Legal Foundations

### What doesn't escape copyright
- Transposing to another key â€” still the same work
- Uniform duration changes (doubling/halving all notes) â€” still substantially similar

### Minimum copyrightable length
- No bright-line rule in U.S. law
- Very short phrases are hard to protect; no statutory cutoff (e.g., "must be 8 bars")
- VMG Salsoul case: 0.23-second horn hit was at issue (de minimis)

### Substantial similarity / "quoting"
- No fixed percentage or bar count = infringement
- Courts weigh both quantitative (how much taken) and qualitative (was the "heart" taken)

### Strengthening originality via documentation
- Maintaining a database log with up/down votes on each generated piece strengthens the "human creative selection" argument
- Timestamped curation records demonstrate the aesthetic judgment that makes the arrangement copyrightable

### Cost
- U.S. Copyright Office: ~$65 per registration (single work, online filing)
- Group registration options available for collections

---

## 3. Motif Vocabulary

### Tier 1 â€” "Inevitable" motifs (Very High frequency): **23 unique motifs**
- Scale fragments, arpeggiated triads, neighbor tones, basic pentatonic motion, common leap-step resolutions
- Patterns any tonal composer *must* use
- Strongest scÃ¨nes Ã  faire defense

### Tier 2 â€” "Standard practice" motifs (High frequency): **45 additional motifs**
- Still entirely defensible as stock building blocks
- Broader coverage, slightly weaker per-motif legal argument

### Combined: **68 total motifs**

---

## 4. Combinatorial Analysis (4-motif chains)

| Pool | Raw Combinations | Melody Length |
|------|-----------------|---------------|
| Tier 1 only (23 motifs) | **~280,000** | 10â€“12 notes |
| Tier 1+2 (68 motifs) | **~21.4 million** | 10â€“12 notes |

### After transition filters (Tier 1 estimates)

| Filter | Survival Rate | Running Total |
|--------|--------------|---------------|
| Start | â€” | 280,000 |
| Range (stay within ~18 semitones) | ~55% | ~154,000 |
| No immediate motif repetition | ~87% | ~134,000 |
| Contour coherence (arch shapes) | ~40% | ~54,000 |
| Junction interval quality | ~75% | ~40,000 |
| Implied harmonic coherence | ~70% | ~28,000 |

**Estimated musically coherent output: ~25,000â€“50,000 melodies** (filters are correlated, so real number may be 40Kâ€“60K)

---

## 5. The Existing Melody Landscape

### Catalog sizes
- Estimated 80â€“200M human-created songs worldwide
- ~100K new songs/day uploaded to streaming platforms
- ~10 melodic phrases per song â†’ 800Mâ€“2B phrase instances
- Distinct interval sequences (deduplicated): tens to hundreds of millions

### Riehl/Rubin "All the Music" project
- Generated 471 billion melodies (every possible 8-note, 12-beat combination in one octave)
- Released under Creative Commons Zero
- **Critical weakness:** U.S. Copyright Office says works "produced by a machine or mere mechanical process without creative input from a human author" are not protectable â€” so they likely never held copyright to relinquish
- **This strengthens our approach:** our method involves human-designed vocabulary, musically-informed rules, and documented human curation

### Collision estimate for our Tier 1 output
- ~10â€“30% of 280K raw candidates likely match existing copyrighted phrases
- After transition filtering, collision rate drops (filtered candidates are more specific)
- Need a comparison tool (e.g., Lakh MIDI Dataset) to verify

---

## 6. Creative Selection & Curation Strategy

### The selection problem
If the pipeline produces ~30K melodies and we keep ~28K, a court could argue that's not meaningfully different from keeping everything â€” which weakens the "creative selection" argument. But creative judgment is distributed across the *entire* pipeline, not just the final vote:

- **Choosing** to work with 23 motifs out of hundreds of possible interval pairs â€” that's selection
- **Designing** the transition rules (why 18 semitones? why penalize zigzag?) â€” those encode aesthetic preferences
- **Setting** filter thresholds â€” each one is a creative judgment about what sounds good

### Recommended curation approach
- Organize final output into tiers: "exceptional / good / acceptable"
- Register the top tier first â€” "5,000 gems from 280,000 candidates" is a much stronger narrative than "28,000 out of 30,000"
- **Document rejection reasoning** as carefully as approvals â€” "I rejected this because the contour felt predictable" demonstrates active aesthetic judgment
- No case law establishes a minimum rejection rate, but the *narrative* matters

### Album-level creativity
Sequencing melodies into albums with intentional aesthetic arcs (tension/release, tempo variation, emotional progression) adds a recognized additional layer of creative arrangement. This also provides a natural framework for selective curation â€” melodies that don't *fit* anywhere get cut.

---

## 7. Registration Strategy

### Two-tier content approach
1. **Tier 1 first** â€” register melodies built from the 23 "inevitable" motifs to force the legal question quickly
2. **Tier 2 expansion** â€” broader coverage using all 68 motifs

### Filing options (per U.S. Copyright Office)

| Method | Songs per Filing | Separate Statutory Damages per Song? | Cost/Song |
|---|---|---|---|
| Individual (Standard Application) | 1 | Yes | $65 |
| Group Unpublished Works | up to 10 | Yes (CO position) | ~$6.50 |
| **GRAM (Group Works on Album)** | **up to 20** | **Yes (CO position)** | **~$3.25** |
| Collective Work (album as single work) | unlimited | **No â€” one award for whole album** | lowest |

### Key findings
- **Collective work registration weakens per-song enforcement.** Under Â§504(c)(1), "all the parts of a compilation constitute one work" for statutory damages purposes. An album registered as a collective work gets *one* damages award even if every song is infringed.
- **GRAM group registration preserves per-song damages.** The Copyright Office's position is that group registrations are *not* compilations/collective works, so each song may receive a separate statutory damages award. This is the CO's interpretation â€” not yet heavily litigated.
- **GRAM is the recommended filing method**: album-scale pricing (~$3.25/song at 20 tracks) without the statutory damages penalty.
- **Caveat:** Confirm with an IP attorney before filing at scale, as the separate-damages position for group registrations hasn't been extensively tested in court.

---

## 8. Next Steps (for new session)

1. **Build transition rules** â€” implement the 5 filters (range, no-repeat, contour, junction quality, harmonic coherence) against the actual motif data
2. **Get real filtered count** â€” replace estimates with computed numbers
3. **Collision detection** â€” check outputs against existing melody corpora
4. **Human curation pipeline** â€” MIDI playback + up/down vote logging system
5. **Copyright registration workflow** â€” batch filing strategy

---

## 9. Key Data Artifacts

The previous session produced Python code that:
- Analyzed interval frequencies from a corpus
- Categorized motifs into Very High / High frequency tiers
- Computed combinatorial counts at various chain lengths

This code should be reconstructed in the new session from the motif definitions (the 23 Tier 1 and 45 Tier 2 interval pairs).
