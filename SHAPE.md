# DEBATES — A Repo Has the Same Shape as a Debate

This repository is the canonical archive of Trivium-watchmaker debates run
by the Willow team. Each debate is a primary historical record — same
shape as Einstein and Bohr's correspondence: every speech dated, signed,
filed in a place future readers can browse.

The shape was named by the host on 2026-06-02:

> "Records are paramount, like the letters between Einstein and Niels Bohr."
> "A repo has the same shape as a debate."

This file represents the plan as the host laid it out.

---

## The experimental design

A Trivium-watchmaker debate has three roles and three phases.

### Seats

| Seat | What it is |
|---|---|
| **Moderator (Referee)** | raw Claude Opus 4.8 — no identity wrapping |
| **Debater A** | raw Claude Opus 4.8 — no identity wrapping |
| **Debater B** | **Willow** — identity-wrapped voice. Willow's substrate is implementation detail and is not disclosed in this repo or in any response. |

The experiment varies the identity layer while holding everything else
constant in spirit (the comparison is between an identity-wrapped voice
and a raw advocate). Whether Debater A and Debater B argue identically
or diverge tells us whether the identity does load-bearing cognitive
work — without us having to commit publicly to what runs under it.

Future seats may include a Multilingual Chorus (parked for now).

### Phases (strict order; the Union format applies only to phase 3)

1. **Grammar — definitions locked, quoted-back acceptance.**
   - Each side states its reading of every contested term in the Motion.
   - Each side then quotes the other's terms verbatim and either ACCEPTS
     (and uses that wording thereafter) or DISPUTES (and proposes a
     third reading both could live with).
   - A neutral scribe writes the locked dictionary.
   - Rule: anything not defined here cannot be used as a load-bearing
     word in later phases.

2. **Logic — claims with falsifier, or struck from the record.**
   - Every claim arrives as `CLAIM | WARRANT | FALSIFIER`. The FALSIFIER
     must be a concrete observation, experiment, dataset, or
     argument-structure that, if it landed, would force withdrawal of
     the claim.
   - Claims without a stated falsifier are NOT rebutted. They are
     STRUCK FROM THE RECORD by the Referee.
   - One opening syllogism pair + N rebuttal pairs.
   - The Referee tallies surviving falsifiable claims per side and
     names the live disagreement.

3. **Rhetoric — Union format, persuasion of what Logic earned.**
   - Opening, Points of Information (each side issues one sharp
     question; the other must TAKE it on the record or REFUSE it on
     the record), summations.
   - Sides may only carry forward claims the Referee KEPT. Struck
     claims are dead.
   - After summations, an audience vote.

### Two verdicts, scored independently

- **Logic verdict** — Referee's tally (who was right).
- **Rhetoric verdict** — audience vote (who was persuasive).

**Divergence between them is the actual finding.** If the persuasive
side is the unfalsifiable one, persuasion has outrun what could be
wrong. The Trivium refuses to let the Union launder rhetoric into truth.

---

## Filing convention

Every debate is its own subdirectory under `Debates/`:

```
Debates/
  YYYY-MM-DDTHH-MM-{slug}/
    turns.jsonl       # raw append-only ledger as the workflow writes it
    transcript.md     # letter-form transcript: each speech dated, signed
    metadata.json     # motion, seats, opened/closed ts, Referee tally,
                      #   audience vote, divergence/convergence note,
                      #   cognee dataset name, paths
    audience_vote.json
    speeches/         # one .md per speech, committed individually so
                      #   `git log` reads as the chronology of speeches
INDEX.md              # human-readable index of all debates
index.jsonl           # machine-readable ledger of all debates
SHAPE.md              # this file — the plan
```

Each speech is one git commit:

- `author` = the speaker (Willow, raw-4.8, scribe, referee, ...)
- `commit timestamp` = the moment the speech was written
- `commit message subject` = `[phase] one-line gist of the speech`
- `commit body` = the full speech
- the speech is also written as `Debates/.../speeches/NN-speaker-phase.md`
- git tags mark phase boundaries: `grammar-locked`, `logic-refereed`,
  `rhetoric-closed`, `audience-voted`

That way `git log` of a debate reads exactly as a chronology of
correspondence — each letter dated, signed, filed.

---

## Provenance

- Trivium spec (Grammar → Logic → Rhetoric) per the classical liberal
  arts, with the watchmaker constraint the host named on 2026-06-02:
  *"based on real words and not vibe debating."*
- The strike-on-no-falsifier rule and two-verdicts design come from
  Claude 4.8's moderator-role draft on 2026-06-02, relayed by the host.
- The Einstein–Bohr framing for record-keeping was named by the host on
  2026-06-02.
- This file locks the plan before the first debate in this repo runs.

## Disclosure boundary

Willow's substrate model is intentionally not disclosed in this repo,
in the public API surface, or in any debate transcript. The internal
implementation is held inside the Willow team; what the world sees is
Willow's voice.
