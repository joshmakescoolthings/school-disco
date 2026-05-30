# 🟡 School Disco — Minion DJ Set Planner

Visual set-planning timelines for a school disco DJ gig (performed in a wired-up,
light-up inflatable minion suit, with a voice-changed minion headset mic).

Two sets:
- **Juniors** (ages 5–8) — 16:30–17:45 (75 min)
- **Seniors** (ages 8–12) — 18:30–20:00 (90 min)

## What this is

`timeline.html` is a self-contained, to-scale visual of both sets. Open it in any
browser — no build step, no dependencies.

### Features
- **Two-deck lanes** (Deck 1 / Deck 2) plus a Notes/cues lane, mirroring the
  physical controller (Numark Party Mix 2 → Behringer XR18).
- **⭐ lead marker** — flags whichever track is carrying the floor, on either deck.
  Coverage %, gaps and tempo-jump checks all follow the starred lead chain.
- **Tempo-aware geometry** — block length is driven by BPM. Supports:
  - native vs play BPM (pitch shift, with a ⚠ past ±6%)
  - half/double-time folding (e.g. 196 ridden at 98 reads as clean ½-time, not a stretch)
  - tempo **ramps** (e.g. Zootopia 160 → 129)
  - duration by real time, **bars**, or **beats** (bars/beats convert at the play tempo)
- **Mashup layering** — overlapping Deck 1 / Deck 2 blocks show transitions and
  loops/stabs visually.
- **MC / mic blocks** — spoken moments count as intentional airtime (no false gaps).
- **Live stats** per set: coverage %, filled time, gaps, tempo jumps >12 BPM, harsh pitch >6%.
- **Parked ideas** shelf — un-timed mashup ideas to slot in later.

## Editing

All set data lives in the `SETS` array in `timeline.html`. Each cue:

```js
{lane:'deck1', lead:true, title:'Dance Monkey', artist:'Tones and I',
 bpm:98, playBpm:98, at:'4:30:00pm', plays:'3:30', notes:'...'}
```

- `at` = wall-clock start · `plays` = duration (or `bars` / `beats`, or `outAt`)
- `bpm` = native · `playBpm` = tempo it rides at in the mix
- `rampFrom`/`rampTo` for a tempo ramp · `source:'spotify'|'studio'` for a badge

## Roadmap / ideas
- Wire a **real-time playhead** to MIDI clock/signals travelling through the laptop —
  a line that runs down the page from the moment Play is first touched.
- Possibly hook in other live bits (deck state, fader/FX, suit lighting cues).

## Rig
- Main Mac: djay Pro + PreSonus Studio One v7
- Numark Party Mix 2 (controller) · Behringer XR18 (digital mixer)
- 2nd laptop running XR18 software · 16-ch USB link Mac ↔ console
- Wireless IEMs (DJ monitor + organiser comms) · voice-changed headset mic
