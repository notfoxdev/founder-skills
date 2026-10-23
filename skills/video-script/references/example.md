# Worked example: video-script

> Illustrative and fictional (Ledgerline fixture). Calibrates depth and format only; never reuse its content.

**Request:** "Write our 60-second launch video. We want it animated, not filmed, plus a vertical cut."

**Context used:** `evals/fixture-company.md` as `.foundora/company.md`. Validation stage, no revenue, 2 concierge pilots, no product UI in the file. Buyer is the managing partner; the problem is "can't see which clients are blocked". Tone: direct, tables over paragraphs, US spelling. The journal has the `launch` plan: pilots 2026-10-26 to 2026-11-24, video due 2026-12-04, cohort launch 2026-12-15, channels are personal email and the founder's LinkedIn (Product Hunt skipped), landing page CTA is a call link. Palette and type come from the `website-design` journal entry of 2026-10-20. Hard parts shown: concept chosen against five others by stage, animated UI that does not exist yet carries a Concept label, proof held as `[NEED: ...]` with a swap rule, pushback on the vertical cut, word and frame math shown, a storyboard `motion-video` can build.

---

## Recommendation
Problem-first, 60s, motion graphics: open on the close spreadsheet with "Which client is blocked?", turn into the close board, end on "Book a call at ledgerline dot app". The board is a concept until Priya confirms real UI, so it carries a "Concept" label on screen; the proof line waits on the pilots (`[NEED: pilot outcome by 2026-11-25]`).

Pushback on the vertical cut: your launch channels are email and LinkedIn, where 1:1 fills more of the feed than 9:16 (heuristic). I wrote the 30s 9:16 as asked, but build the 1:1 feed cut first.

## Brief
- Format: launch video | Length: 60s | Aspect: 16:9 master, 1:1 feed cut, 9:16 30s cut | Platform: landing page, founder LinkedIn, launch email link
- Concept: problem-first | Runner-up: before/after, lost because half its runtime would be unbuilt UI | Production: motion graphics (`motion-video`)
- Spine: After watching, a managing partner at a 3 to 15 person firm knows Ledgerline shows every client's close status, including who is blocked and why, and books a call.
- CTA: "Book a call at ledgerline dot app" -> ledgerline.app `[NEED: confirm the button label with landing-page-copy]`
- Word budget: 115 to 135 (calc: 60 x 2.25 = 135 ceiling; 135 x 0.85 = 114.75, floor 115; visual-only time is the 3s end card, under 30%) | Script total: 128

## Concept choice
| Concept | Fit for Ledgerline | Verdict |
| --- | --- | --- |
| Problem-first | The pain is a specific artifact (the close spreadsheet); B2B considered buyer; nothing real to film yet | Pick |
| Before/after | Strong visual, but the "after" is a concept for half the runtime | Runner-up |
| Watch it work | Needs a working product; pilots are concierge | Ruled out by stage |
| Founder story | The 4-year ops credential is the best proof; no founder footage in a motion build | Used as the proof beat |
| Manifesto / teaser | Partners need to see how it works; possible later as a 15s teaser | No |
| Customer-led | No result or permission yet | Not before 2026-12-04 |

## Hook options
1. Pattern: the painful moment | The moment: a client row turning from blocked to ticked | Visual: generic spreadsheet mid-scroll, five fill colors, a cell comment "is this reconciled??" pops open | First line: "Which client is blocked?" | Text: "Which client is blocked?" | Payoff at: 0:24 | Why: every partner has scrolled this sheet, and it reads muted on LinkedIn.
2. Pattern: side by side | Visual: split frame, spreadsheet left, close board right, same 6 sample clients | First line: "Same clients. Two views." | Text: "Spreadsheet vs close board" | Payoff at: 0:02 | Why: instant contrast; but half the first frame is unbuilt UI and the Concept label is tiny at phone size.
3. Pattern: founder confession | Visual: kinetic type over the founder's photo | First line: "Four years. Same spreadsheet." | Text: "4 years running close" | Payoff at: 0:44 | Why: true and strong, but a still photo does not stop a scroll the way motion does.

Recommended: 1, because the spreadsheet is the alternative the buyer lives in and frame 1 is already moving.

## Script
| Time | Scene | VISUAL | AUDIO / VO | Words | wps |
| --- | --- | --- | --- | --- | --- |
| 0:00 to 0:02 | S01 hook | Spreadsheet mid-scroll, comment "is this reconciled??" pops open. Text: "Which client is blocked?" | "Which client is blocked?" Scroll SFX, no music. | 4 | 2.0 |
| 0:02 to 0:08 | S02 problem | Pull back: 40 rows, filters toggle, a cell flips yellow to orange. Text: "Close, in a spreadsheet" | "Month-end close for dozens of clients, run from one spreadsheet and an inbox." Music in, low. | 13 | 2.2 |
| 0:08 to 0:14 | S03 problem | Email threads stack over the sheet; a reviewer's tick is erased and redone. Text: "Who's stuck? What's done?" | "Partners can't see who's stuck. Reviewers redo work because nobody knows what's already reconciled." | 14 | 2.3 |
| 0:14 to 0:16 | S04 turn | Cells slide into a ruled board on ledger paper. "Concept" label appears top-left. | "So we're building this." Music lifts on the bar. | 4 | 2.0 |
| 0:16 to 0:24 | S05 product | Board: 6 sample clients by 6 steps; ticks fill one row per second. Text: "One row per client. One column per step." | "Every client is a row. Every close step is a column. A tick shows it's done, and who did it." Soft tick SFX per row. | 20 | 2.5 |
| 0:24 to 0:32 | S06 product | Zoom 2x on C-04, stopped at AP, note "Waiting on client: card statement". Text: "Blocked: waiting on client" | "This one's stuck at payables. The reason is right on the row: waiting on the client's card statement." | 18 | 2.3 |
| 0:32 to 0:38 | S07 product | Open C-01: reconciled accounts with initials and dates in mono. Text: "Already reconciled. Not redone." | "Open a client and see what's already reconciled, so nobody redoes Tuesday's work." | 13 | 2.2 |
| 0:38 to 0:44 | S08 product | Pull back to the partner summary: "5 of 6 ready for review. 1 blocked." Text: "5 ready. 1 blocked." | "Partners see the whole month at a glance. Nothing hiding in a tab." | 13 | 2.2 |
| 0:44 to 0:52 | S09 proof | Founder photo in a ledger-paper frame. Lower third: "[NEED: founder name], CEO". Cards: "4 years running bookkeeping ops", then "Piloted by 2 firms" | Founder VO: "I ran operations at a bookkeeping firm for four years. Two firms piloted Ledgerline this fall." | 16 | 2.0 |
| 0:52 to 0:57 | S10 CTA | Back on the board: C-04 resolves to a tick. Text: "Book a call: ledgerline.app" | "Run close for a small firm? Book a call at ledgerline dot app." | 13 | 2.6 |
| 0:57 to 1:00 | S11 end | End card: wordmark, "ledgerline.app", "Book a call". Held 3s. | Music resolves on the last frame. | 0 | 0 |

Beat shares: problem 12s (20%, under the 25% problem-first limit), product moment 28s (47%), proof 8s (13%), CTA plus end card 8s. Densest row: S10 at 2.6 words per second.

## On-screen text
| Time | Text | Hold | Size / position |
| --- | --- | --- | --- |
| 0:00 to 0:03 | Which client is blocked? | 3.0s (min 2.7s; carries 1s into S02) | 110px, center |
| 0:03.5 to 0:07.5 | Close, in a spreadsheet | 4.0s | 72px, lower left |
| 0:09 to 0:12 | Who's stuck? What's done? | 3.0s | 72px, lower left |
| 0:14 to 0:44, 0:52 to 0:57 | Concept (persistent label) | 35s | 60px, top-left, inside 5% margin |
| 0:17 to 0:21.5 | One row per client. One column per step. | 4.5s (min 3.9s) | 72px, top |
| 0:25 to 0:28 | Blocked: waiting on client | 3.0s | 96px, beside the zoomed row |
| 0:33 to 0:36 | Already reconciled. Not redone. | 3.0s | 72px, top |
| 0:39 to 0:42 | 5 ready. 1 blocked. | 3.0s | 96px, center |
| 0:45 to 0:48 | 4 years running bookkeeping ops | 3.0s | 72px, lower third |
| 0:48.5 to 0:51.5 | Piloted by 2 firms | 3.0s | 72px, lower third |
| 0:53 to 0:57 | Book a call: ledgerline.app | 4.0s | 96px, center |

## Shot list
None: full motion build. The only captured assets are the founder photo and the VO recording.

## Storyboard hand-off

```yaml
storyboard:
  title: Ledgerline launch, 60s master
  version: 1
  fps: 30
  resolution: 1920x1080
  aspect: "16:9"
  duration_s: 60
  duration_frames: 1800
  safe_area: "5% title-safe; bottom 15% clear for captions"
  style:
    source: website-design journal entry 2026-10-20
    palette: { paper: "#F6F3EA", ink: "#1B2420", pencil: "#59625C", rule: "#C5D3C2", tick-red: "#A3341F", reconciled: "#2D5C4C" }
    type: { display: Libre Caslon Display, body: IBM Plex Sans, mono: IBM Plex Mono }
    min_text_px: 60
  audio:
    vo: "Founder, recorded line by line [NEED: VO files by 2026-11-20]"
    music: { mood: "warm, mid-tempo, light piano and soft percussion, lifts on the turn", bpm: 120, frames_per_beat: 15, source: "[NEED: licensed track covering website and LinkedIn]" }
  labels:
    - { text: "Concept", scenes: [S04, S05, S06, S07, S08, S10], position: top-left, persistent: true }
  scenes:
    - id: S01
      beat: hook
      start_s: 0.0
      start_frame: 0
      duration_s: 2.0
      duration_frames: 60
      on_screen_text: "Which client is blocked?"
      visual: Generic spreadsheet (no vendor branding), client codes C-01 to C-40, five fill colors
      motion: Already scrolling fast at frame 0; decelerates; comment bubble pops open by frame 30
      transition_out: cut on bar (frame 60)
      vo: "Which client is blocked?"
      audio: Scroll SFX frames 0 to 25, no music
      assets:
        - { name: spreadsheet mock, type: svg, status: NEED }
    - id: S02
      beat: problem
      start_s: 2.0
      start_frame: 60
      duration_s: 6.0
      duration_frames: 180
      on_screen_text: "Close, in a spreadsheet"
      visual: Same sheet, pulled back to 40 rows; filter menu toggles; one cell flips yellow to orange
      motion: Slow pull back, slightly too much to take in; one change at a time, never more than 1 per second
      transition_out: cut on bar (frame 240)
      vo: "Month-end close for dozens of clients, run from one spreadsheet and an inbox."
      audio: Music enters low at +0f
      assets:
        - { name: spreadsheet mock, type: svg, status: NEED }
    - id: S03
      beat: problem
      start_s: 8.0
      start_frame: 240
      duration_s: 6.0
      duration_frames: 180
      on_screen_text: "Who's stuck? What's done?"
      visual: Three email thread cards stack over the sheet; a reviewer tick is erased and redrawn
      motion: Cards drop in on beats, crowding the frame; the redo feels tedious, not dramatic
      transition_out: morph on bar (frame 420); sheet cells become board cells
      vo: "Partners can't see who's stuck. Reviewers redo work because nobody knows what's already reconciled."
      audio: Paper SFX per card on beats
      assets:
        - { name: email thread cards, type: svg, status: NEED }
    - id: S04
      beat: turn
      start_s: 14.0
      start_frame: 420
      duration_s: 2.0
      duration_frames: 60
      on_screen_text: none
      visual: Cells slide into a ruled board on paper; Concept label appears top-left
      motion: Disorder snaps into order, like a ledger being ruled; settled by frame 20
      transition_out: cut on bar (frame 480)
      vo: "So we're building this."
      audio: Music lifts at +0f
      assets:
        - { name: close board concept, type: svg, status: NEED }
    - id: S05
      beat: product
      start_s: 16.0
      start_frame: 480
      duration_s: 8.0
      duration_frames: 240
      on_screen_text: "One row per client. One column per step."
      visual: Board with sample clients C-01 to C-06 by 6 close steps; initials beside each tick
      motion: Ticks fill one row per second, left to right, calm and steady
      transition_out: push into C-04 on bar (frame 720)
      vo: "Every client is a row. Every close step is a column. A tick shows it's done, and who did it."
      audio: Soft tick SFX once per row (6 total)
      assets:
        - { name: close board concept, type: svg, status: NEED }
        - { name: tick SFX, type: audio, status: NEED }
    - id: S06
      beat: product
      start_s: 24.0
      start_frame: 720
      duration_s: 8.0
      duration_frames: 240
      on_screen_text: "Blocked: waiting on client"
      visual: 2x zoom on row C-04, stopped at the AP step in tick-red, note "Waiting on client: card statement"
      motion: Zoom settles by frame 15; cursor travels to the note and clicks at +60f; note expands; hold still to read
      transition_out: cut on bar (frame 960)
      vo: "This one's stuck at payables. The reason is right on the row: waiting on the client's card statement."
      audio: Click SFX at +60f
      assets:
        - { name: cursor, type: svg, status: NEED }
    - id: S07
      beat: product
      start_s: 32.0
      start_frame: 960
      duration_s: 6.0
      duration_frames: 180
      on_screen_text: "Already reconciled. Not redone."
      visual: Client C-01 checklist, reconciled accounts with initials and dates in mono, reconciled green
      motion: Panel slides in from the row; items confirm top to bottom, one per beat pair
      transition_out: pull back on bar (frame 1140)
      vo: "Open a client and see what's already reconciled, so nobody redoes Tuesday's work."
      audio: none added
      assets:
        - { name: client checklist concept, type: svg, status: NEED }
    - id: S08
      beat: product
      start_s: 38.0
      start_frame: 1140
      duration_s: 6.0
      duration_frames: 180
      on_screen_text: "5 ready. 1 blocked."
      visual: Full board plus partner summary line "5 of 6 ready for review. 1 blocked."
      motion: Pull back to the whole month; summary line types on; one calm hold
      transition_out: cut on bar (frame 1320)
      vo: "Partners see the whole month at a glance. Nothing hiding in a tab."
      audio: none added
      assets:
        - { name: partner summary concept, type: svg, status: NEED }
    - id: S09
      beat: proof
      start_s: 44.0
      start_frame: 1320
      duration_s: 8.0
      duration_frames: 240
      on_screen_text: "[NEED: founder name], CEO / 4 years running bookkeeping ops / Piloted by 2 firms"
      visual: Founder photo in a paper frame with a pencil rule; lower third, then two cards in sequence
      motion: Slow 3% push on the photo; cards swap at +105f
      transition_out: cut on bar (frame 1560)
      vo: "I ran operations at a bookkeeping firm for four years. Two firms piloted Ledgerline this fall."
      audio: Music drops one layer under the founder's voice
      assets:
        - { name: founder photo, type: photo, status: NEED }
    - id: S10
      beat: cta
      start_s: 52.0
      start_frame: 1560
      duration_s: 5.0
      duration_frames: 150
      on_screen_text: "Book a call: ledgerline.app"
      visual: Back on the board; C-04 AP cell resolves to a tick
      motion: The blocked cell ticks at +30f, the payoff of the hook; then hold
      transition_out: cut on beat (frame 1710)
      vo: "Run close for a small firm? Book a call at ledgerline dot app."
      audio: Tick SFX at +30f
      assets:
        - { name: close board concept, type: svg, status: NEED }
    - id: S11
      beat: end
      start_s: 57.0
      start_frame: 1710
      duration_s: 3.0
      duration_frames: 90
      on_screen_text: "ledgerline.app / Book a call"
      visual: End card on paper, wordmark in ink, URL, CTA words; reduced-motion poster is this frame
      motion: Static
      transition_out: end
      vo: none
      audio: Music resolves at frame 1800
      assets:
        - { name: wordmark, type: svg, status: NEED }
```

Checks: frames 60+180+180+60+240+240+180+180+240+150+90 = 1800; every duration a whole number of 15-frame beats; every scene 2.7 words per second or less; every card meets its hold; Concept label covers every board scene.

Use `motion-video` to build it.

## Audio
- VO: founder, voice only, recorded line by line in a soft room, 3 takes each, before the build starts | Music: warm mid-tempo at 120 BPM `[NEED: licensed track and source, confirmed by founder; check it covers boosted LinkedIn posts if you boost later]` | SFX: scroll (S01), paper (S03), tick per row (S05), click (S06), the payoff tick (S10)

## Captions and accessibility
- Burned-in: 1:1 and 9:16 cuts | Caption file: `.vtt` on the website (on by default for muted autoplay), `.srt` for any 16:9 LinkedIn upload | Safe zones: 9:16 text inside x 60 to 920, y 250 to 1520 | Muted read test: pass (the text column alone tells problem, product, proof, CTA)
- Caption lines at most 42 characters (16:9) and 32 (9:16). Densest caption rate: S10 at about 12 characters per second, under 17. Hand-check "Ledgerline", "reconciled", "payables".
- Contrast: ink on paper 14.34:1 (per `website-design`). Ticks fill at 1 per second, well under 3 changes per second.

## Cutdowns
| Cut | Aspect | Length | Source scenes | VO words (budget) | Reframing / changes |
| --- | --- | --- | --- | --- | --- |
| Feed | 1:1, 1080x1080 | 60s | All | 128 (115 to 135) | Board rebuilt square, captions burned in; build first |
| Vertical | 9:16, 1080x1920 | 30s | S01, S02, S04, S05, S06, new CTA | 66 (58 to 67) | Rebuilt vertical; proof dropped, carried by the post text |
| Hero loop | 16:10 | 8s | S06 into S10 tick | none | Silent, C-04 goes from blocked to ticked; under about 2MB |

Vertical 30s cut:

| Time | Scene | VISUAL | VO | Words | wps |
| --- | --- | --- | --- | --- | --- |
| 0:00 to 0:02 | C01 (S01) | Sheet mid-scroll, full-bleed vertical. Text: "Which client is blocked?" | "Which client is blocked?" | 4 | 2.0 |
| 0:02 to 0:08 | C02 (S02) | Sheet pulls back, rows stacked tall. Text: "Close, in a spreadsheet" | "Month-end close for dozens of clients, run from one spreadsheet and an inbox." | 13 | 2.2 |
| 0:08 to 0:10 | C03 (S04) | Cells snap into a vertical board. Concept label top-left inside the safe box | "So we're building this." | 4 | 2.0 |
| 0:10 to 0:18 | C04 (S05) | 6 client rows, 3 step columns visible, pans to the other 3 on a bar. Text: "One row per client" | S05 line | 20 | 2.5 |
| 0:18 to 0:26 | C05 (S06) | C-04 fills the safe box at 80px note text. Text: "Blocked: waiting on client" | S06 line | 18 | 2.3 |
| 0:26 to 0:30 | C06 (new) | C-04 ticks, then wordmark and "Book a call: ledgerline.app" | "Book a call at ledgerline dot app." | 7 | 1.8 |

```yaml
storyboard:
  title: Ledgerline launch, 30s vertical
  version: 1
  fps: 30
  resolution: 1080x1920
  aspect: "9:16"
  duration_s: 30
  duration_frames: 900
  safe_area: "9:16 box x60-920 y250-1520"
  style: { source: master, min_text_px: 48 }
  audio: { vo: master files, music: { bpm: 120, frames_per_beat: 15, source: master track, edit to 30s } }
  labels:
    - { text: "Concept", scenes: [C03, C04, C05, C06], position: top-left, persistent: true }
  scenes:
    - { id: C01, from: S01, start_frame: 0, duration_frames: 60, visual: vertical sheet }
    - { id: C02, from: S02, start_frame: 60, duration_frames: 180, visual: rows stacked tall }
    - { id: C03, from: S04, start_frame: 240, duration_frames: 60, visual: vertical board }
    - { id: C04, from: S05, start_frame: 300, duration_frames: 240, on_screen_text: "One row per client", motion: "pan to columns 4 to 6 on the bar at +120f" }
    - { id: C05, from: S06, start_frame: 540, duration_frames: 240, visual: "C-04 fills the safe box, note at 80px" }
    - { id: C06, beat: cta, start_frame: 780, duration_frames: 120, on_screen_text: "Book a call: ledgerline.app", visual: "C-04 ticks at +20f, then wordmark", vo: "Book a call at ledgerline dot app.", transition_out: end, assets: [{ name: wordmark, type: svg, status: NEED }] }
```

Checks: 60+180+60+240+240+120 = 900; every cut on a bar line (multiples of 60 frames). Use `motion-video` to build it.

## Self-check
| # | Check | Score | Note |
| --- | --- | --- | --- |
| 1 | Hook strength | 2 | Frame 1 mid-scroll on the real workaround; 4-word line matches the text; paid off at 0:24 and resolved at 0:53 |
| 2 | One message | 2 | Every scene serves "see who is blocked and why"; one CTA |
| 3 | Word budget fit | 2 | 128 in 115 to 135; max row 2.6 wps. Vertical 66 in 58 to 67 |
| 4 | Proof is real | 1 | Credential from `company.md`; pilot line pending the outcome; board labelled Concept |
| 5 | CTA clarity | 2 | One action, said and shown, URL on screen 7s total; button label to confirm |
| 6 | Captions and readability | 2 | Muted read passes; sizes at or above minimums; safe box set for 9:16 |
| 7 | Cutdown plan | 2 | Three cuts with aspect, length, sources, budgets, reframing |

Total: 13/14 -> ship. Check 4 goes to 2 if a pilot firm approves a real result in writing; then S09 becomes that result.

## Open items
- [NEED: pilot outcome by 2026-11-25. Both pilots finished: keep "Two firms piloted Ledgerline this fall". A firm approves a result in writing: replace the S09 pilot line with it, same word count. Neither: cut the pilot line and the card; S09 becomes the credential only (10 words)]
- [NEED: Priya, by 2026-11-06: will the real board exist by 2026-11-27? Yes: switch to hybrid with real screenshots and drop the Concept label. No: build as written]
- [NEED: founder name, founder photo, VO recording by 2026-11-20, licensed music track, wordmark SVG]
- [NEED: CTA button label from `landing-page-copy`, so the video and page say the same words]
- [ASSUMPTION: the video lives on the landing page, the founder's LinkedIn, and the launch email]

## Next step
Founder approves the script, concept, and Concept-label approach by 2026-10-23, so the VO can be recorded by 2026-11-20 and `motion-video` can deliver the master by the launch plan's 2026-12-04 due date.

Logged to `.foundora/journal.md`:

```markdown
### 2026-10-20 — decision: 60s launch video is problem-first, motion-built
- Problem-first concept, painful-moment hook on the close spreadsheet; 128 VO words against 115 to 135; 1:1 feed cut first, 30s 9:16 second
- Motion graphics because no product UI exists; the board carries a Concept label; proof line waits on the pilot outcome
- Revisit 2026-11-06 (real UI?) and 2026-11-25 (pilot result with permission?); master due 2026-12-04
- Source: video-script
```
