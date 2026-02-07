# CLAUDE.md — Project Context for AI Assistants

## Quick Summary

**Algorithm and Blues** generates copyrightable melodies by combining public-domain musical motifs (scènes à faire) into original sequences. The *selection and arrangement* is the copyrightable creative act.

## Project Status

- **Motif vocabulary**: 98 unique interval pairs across 4 tiers (23 Tier 1 "inevitable", 45 Tier 2 "standard practice", 28 Tier 3, 2 Tier 4)
- **Rhythm patterns**: 63 allowed 2-bar patterns (RHYTHMS_ALLOWED.md)
- **Generation model**: Interval-overlap — last interval of motif N must equal first interval of motif N+1. Average branching factor ~2.7
- **Pipeline**: Filter pipeline (range, no-repeat, contour, junction quality) and 6-dimension scorer built in prior sessions but code not yet in repo
- **Corpus analysis**: Designed but not yet executed (needs Lakh MIDI Dataset)
- **Web platform**: Not started

## Key Design Decisions

1. **Interval overlap model** (not note overlap) — every sliding 3-note window is a recognized motif
2. **Transposition-invariant representation** — interval sequences are the primary key, MIDI pitches anchored at C4/60 for convenience
3. **Scoring over hard filtering** for harmonic coherence — continuous signal guides review priority
4. **Temperature-based curation queue** — Boltzmann sampling for human review (designed, not built)

## Key Files

| File | Purpose |
|------|---------|
| README.md | Public-facing project description |
| OVERVIEW.md | Deep strategic context, legal theory, philosophical framing |
| motif_vocabulary.md | Full motif catalog with categories and legal justifications |
| motif_data.json | Machine-readable motif intervals (23+45+28+2 = 98 motifs) |
| RHYTHMS_ALLOWED.md | 63 permitted rhythm patterns with constraints |
| melody-project-handoff*.md | Session-by-session development notes (v1, v2, v3) |

## Tech Stack

- **Python** for analysis and generation (pretty_midi, mido, music21, numpy)
- **JavaScript** for web platform (planned: React, Tone.js)
- **PostgreSQL** for data (planned)

## Important Context

- The author is a real musician (multiple bands, recordings, Wikifonia contributor)
- This is also AI safety research — forcing legal determination on human creativity + AI assistance
- Both main legal outcomes are wins (copyright affirmed OR commons expanded)
- Documentation trail (curation logs, rejection records) is as important as the code
- Quality matters — melodies must be genuinely good to avoid "claim-staking" characterization
