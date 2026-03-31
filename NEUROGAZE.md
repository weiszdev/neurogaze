# NeuroGaze — Functional Saccadic Assessment Protocol

**Live:** https://weiszdev.github.io/neurogaze/neuro-saccades-assessment.html
**Repo:** https://github.com/weiszdev/neurogaze

---

## What It Is

NeuroGaze is a browser-based eye movement assessment tool that uses webcam eye-tracking to evaluate saccadic function across 10 clinical gaze zones. It produces a scored report with exercise prescriptions tailored to detected deficits.

No video is recorded. All data stays on the user's device (localStorage).

---

## How It Works

1. **Camera Setup** — Webcam access is requested; face detection confirms the user is positioned correctly.
2. **9-Point Calibration** — User clicks dots on screen to train the eye tracker, followed by a 5-point gaze validation that measures actual accuracy in pixels.
3. **10 Gaze Zones** — A target dot appears in each zone. The user looks at it for 5 seconds while gaze data is collected. A countdown timer shows remaining time. Special zones (Convergence, Antisaccade) get instruction modals explaining what to do.
4. **Symptom Feedback** — After each zone, the user rates difficulty (None / Mild / Significant) and reports symptoms (Headache, Dizziness, Double Vision, Nausea).
5. **Report** — Two views:
   - **My Plan (User View):** Plain-language summary, daily exercise checklist with checkboxes and progress bar, cross-lateral brain reset drills
   - **Practitioner View:** Full clinical data — latency, accuracy, corrective saccades, spider chart, clinical notes, JSON export

---

## The 10 Gaze Zones

| # | Zone | What It Tests |
|---|------|---------------|
| 1 | Horizontal Left | Lateral saccade (leftward) |
| 2 | Horizontal Right | Lateral saccade (rightward) |
| 3 | Vertical Up | Vertical saccade (upward) |
| 4 | Vertical Down | Vertical saccade (downward) |
| 5 | Diagonal Upper-Left | Oblique saccade |
| 6 | Diagonal Upper-Right | Oblique saccade |
| 7 | Diagonal Lower-Left | Oblique saccade |
| 8 | Diagonal Lower-Right | Oblique saccade |
| 9 | Convergence / Near Point | Vergence system, near point |
| 10 | Antisaccade | Inhibitory control (look opposite to cue) |

---

## Scoring

Each zone is scored out of **12 points**:

| Metric | Max | Thresholds |
|--------|-----|------------|
| Saccade Latency | 3 | <200ms = 3, <300ms = 2, <400ms = 1 |
| Gaze Accuracy | 3 | <50px = 3, <100px = 2, <150px = 1 |
| Corrective Saccades | 3 | 0 = 3, 1 = 2, 2 = 1 |
| Subjective Difficulty | 2 | None = 2, Mild = 1 |
| Symptom Report | 1 | None = 1 |

**Total: 120 points** across 10 zones.

| Grade | Threshold |
|-------|-----------|
| Excellent | 83%+ (100+) |
| Good | 58%+ (70+) |
| Fair | 33%+ (40+) |
| Poor | Below 33% |

---

## Exercise Prescription Tiers

### Tier 1 — Maintenance (score 80+)
Core exercises: Smooth Pursuit, Near/Far Focus, Fixation Stability

### Tier 2 — Rehabilitative (score 50-79)
Core exercises + zone-specific drills for weak areas:
- Horizontal weakness: Hart Chart drills
- Vertical weakness: Saccade Metronome
- Diagonal weakness: Diagonal Pursuit
- Antisaccade weakness: Inhibitory control drills
- Convergence weakness: Pencil Push-Ups

### Tier 3 — Intensive + Referral (score below 50)
Full exercise battery + VOR Training, Gaze Stability Drills, and professional referral recommendation.

---

## Cross-Lateral Brain Reset Drills

Arrow-based contralateral movement exercises included in every report. An arrow indicates a direction; the user lifts the **opposite** arm and knee to create cross-body coordination patterns that activate both brain hemispheres.

- 4 cardinal directions (always included)
- 4 diagonal directions (added when diagonal/lateral zones are weak)
- Sets and tempo scale with overall score

---

## User Daily Checklist

The "My Plan" view generates a personalized daily exercise checklist:
- Cross-lateral warm-up
- Smooth pursuit training
- Near/far focus shifts
- Fixation hold
- Zone-specific drills (only for weak areas)
- Cool-down palming

Checkboxes persist per day in localStorage. Progress bar tracks completion.

---

## Tech

- **Single HTML file** — zero dependencies beyond CDN-loaded WebGazer and Google Fonts
- **WebGazer.js 2.1.0** — webcam-based eye tracking via ridge regression
- **No backend** — all processing is client-side
- **localStorage** — assessment history (last 10), daily checklist state
- **Mobile-aware** — compact layout on small screens, gaze dot hidden, camera retry for iOS Safari
- **Print-friendly** — `@media print` styles for PDF export

---

## Known Limitations

- WebGazer accuracy is roughly 100-200px on typical hardware — good enough for zone-level detection, not clinical-grade
- iOS Safari camera init can be finicky — retry button provided
- Phone screens are too small for reliable 10-zone eye tracking; best on laptop/desktop with webcam
- Calibration quality depends on lighting and head stability
- This is a **screening tool**, not a diagnostic instrument

---

## Status

Active development. Current priorities:
- Testing cross-browser camera reliability
- Validating exercise prescription logic with practitioners
- Exploring guided exercise mode (animated targets for in-app training)

---

*Built with Claude Code. Not a medical device.*
