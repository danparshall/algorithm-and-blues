# Algorithm and Blues

**A community project to explore the boundaries of musical creativity, copyright, and the commons.**

---

## What Is This?

Algorithm and Blues is an experiment at the intersection of music, mathematics, and law.

We're building a system that generates melodic "skeletons" from the most fundamental building blocks of music â€” the scale runs, arpeggios, and neighbor tones that appear in virtually every song ever written. These patterns are so basic they can't be copyrighted individually (lawyers call them *scÃ¨nes Ã  faire* â€” "scenes that must be done").

But here's the thing: **combine enough uncopyrightable elements in an original way, and the combination *is* copyrightable.**

So we're doing exactly that. Algorithmically generating combinations, then letting humans â€” maybe you â€” listen, tweak, and curate them into something worth protecting.

---

## Why Does This Matter?

This project asks a question that will define creative work in the AI age:

> **When a human uses algorithms to generate creative options, then selects and refines the results with genuine aesthetic judgment â€” who's the author?**

We think the answer should be: **the human.**

If we're right, this project will:
- Prove that human curation remains the core of creativity, even with AI assistance
- Generate a catalog of high-quality melodies that we (the community) own
- Create legal precedent protecting human creative agency

If we're wrong, and courts say algorithmic assistance disqualifies work from copyright:
- Everything we create enters the public domain
- Other artists can freely use our melodic vocabulary
- The commons expands massively

**Either outcome is a win.** We're playing a game where both endings are good.

---

## Current Status: Early Days ðŸš§

We're in the **backend and research phase**. Here's what exists:

| Component | Status |
|-----------|--------|
| Motif vocabulary (110 melodic building blocks) | âœ… Complete |
| Rhythm pattern vocabulary (63 patterns) | âœ… Complete |
| Legal research on music copyright | âœ… Substantial |
| Filter pipeline (musical quality rules) | âœ… Prototype |
| Scoring system (ranking melody quality) | âœ… Prototype |
| Corpus analysis (validating against real music) | ðŸŸ¡ In progress |
| Skeleton generator (pitch + rhythm) | ðŸŸ¡ Designed, not built |
| Web platform for community curation | âŒ Not started |
| MIDI playback and editing interface | âŒ Not started |

**What we need**: Developers, musicians, and curious people who want to help build this.

---

## How You Can Help

### ðŸ”§ Developers

We need help building:
- **Corpus analysis tools** â€” MIDI parsing, interval extraction, statistical analysis
- **Skeleton generator** â€” Combining pitch chains with rhythm patterns
- **Web platform** â€” React/Vue frontend, MIDI playback (Tone.js), user accounts, voting system
- **Backend** â€” Database design, API, contribution tracking

**Tech stack** (tentative): Python for analysis/generation, JavaScript for web, PostgreSQL for data.

**To contribute**: Check out the code, read OVERVIEW.md for deep context, and open an issue or PR.

### ðŸŽµ Musicians

Not ready for you *yet* â€” but soon.

When the platform launches, we'll need people to:
- Listen to generated skeletons
- Vote on quality (thumbs up/down)
- Tweak melodies (shift notes, swap rhythms, add embellishments)
- Curate collections into coherent albums

Your ears and taste are the irreplaceable ingredient. The algorithm proposes; you decide.

**To get notified**: Star/watch this repo, or join our community (links coming).

### ðŸ“š Researchers & Lawyers

We're building a legal test case. If you have expertise in:
- Music copyright law
- AI and authorship
- Computational musicology
- Information theory of music

...we'd love to talk. The legal and academic framing matters as much as the code.

### ðŸŒ Everyone Else

- **Spread the word** â€” This project works better with more people
- **Ask questions** â€” If something's unclear, that's a documentation bug
- **Challenge us** â€” If you think we're wrong about something, say so

---

## The Vision

Imagine a tool where you can:

1. **Get a skeleton** â€” A "pretty good" melody generated from universal building blocks
2. **Listen** â€” MIDI playback right in your browser
3. **Tweak** â€” Shift a note, swap a rhythm, add your own flourish
4. **Save** â€” Your version, timestamped, attributed to you
5. **Share** â€” Add it to the community catalog

Every contribution is tracked. Every tweak is documented. The result is a collectively-curated library of melodies with clear provenance â€” either copyrightable as a community work, or a gift to the public domain.

**Wikipedia for melodies.** That's the dream.

---

## Background

This project exists because one person has been thinking about these questions for a long time:

- **Former physicist** â€” Trained to think about spaces, constraints, and combinatorics
- **Amateur musician** â€” Multiple bands, actual recordings, contributed to Wikifonia ~20 years ago
- **Data scientist & software engineer** â€” Can actually build the thing
- **Deep interest in copyright law** â€” From both the music and tech sides
- **Pivoting into AI safety** â€” This is, in a real sense, AI safety research

The question "what does human creativity mean when AI can assist?" isn't just a legal question. It's a question about what humans are *for* in an age of capable AI. This project forces an answer.

---

## Project Structure

```
algorithm-and-blues/
â”œâ”€â”€ README.md                 # You are here
â”œâ”€â”€ OVERVIEW.md               # Deep strategic context (read this for full picture)
â”œâ”€â”€ motif_vocabulary.md       # The 110 melodic building blocks
â”œâ”€â”€ motif_data.json           # Machine-readable motif data
â”œâ”€â”€ RHYTHMS_ALLOWED.md        # The 63 rhythm patterns
â”œâ”€â”€ melody-project-handoff.md # Session 1-2 notes
â”œâ”€â”€ melody-project-handoff-v2.md # Session 3 notes
â”œâ”€â”€ melody-project-handoff-v3.md # Session 4 notes
â””â”€â”€ src/                      # (coming soon)
    â”œâ”€â”€ analysis/             # Corpus analysis tools
    â”œâ”€â”€ generator/            # Skeleton generation
    â””â”€â”€ platform/             # Web application
```

---

## License

TBD â€” We're still working out the right licensing model. Options include:
- **Copyleft (CC-BY-SA)** â€” Anyone can use, derivatives must be open
- **Foundation model** â€” Nonprofit holds registrations, revenue to causes
- **Hybrid** â€” Register compilation for precedent, individual melodies open

Input welcome. This is a community decision.

---

## FAQ

**Q: Isn't this just a scheme to troll the music industry?**

A: Maybe a little. But the motivations are genuine â€” aesthetic, intellectual, and ethical. Either we prove human curation is copyrightable (good for creators in the AI age) or we expand the commons (good for everyone). We're not here to extract; we're here to answer a question that matters.

**Q: Can I really help even if I'm not a musician or developer?**

A: Yes. Listening to melodies and saying "I like this" or "I don't like this" is the core creative act we're trying to validate. No expertise required â€” just ears and opinions.

**Q: What if someone uses this to generate spam copyright claims?**

A: That's a real concern. Our approach emphasizes *quality* and *curation* â€” we're not claiming everything that comes out of the algorithm, only what humans genuinely select. The documentation trail is what makes this defensible. Mass-generating low-quality claims would undermine the entire legal theory.

**Q: When can I actually use the tool?**

A: Not yet. We're still building the foundation. Watch this repo for updates.

---

## Contact

- **GitHub Issues** â€” For bugs, features, and technical discussion
- **Discussions** â€” (coming) For broader conversation
- **Email** â€” (coming) For press, legal, and partnership inquiries

---

*Algorithm and Blues: Because the best melodies might be hiding in the math.*
