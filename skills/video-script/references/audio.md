# Audio: voiceover, music, sound design

Read this in step 7 when choosing the audio approach, and before writing VO lines or music cues.

## VO, text-only, or music-only

| Approach | Choose when | Watch out for |
| --- | --- | --- |
| Voiceover | The product needs explaining, runtime is 30s or more, the founder's voice is proof, YouTube or website where sound is often on | Must still work muted: captions plus on-screen text |
| Text-only + music | No one will record, short-form under 30s, global audience, feed-first placement | One card per 2 to 3s; card pace, not VO budget, sets length |
| Music only or silent | Hero loops, GIFs, Product Hunt gallery loops, UI that explains itself | No story beats that rely on words |

Founder voice beats a hired voice for launch videos when the founder is the proof (ran the job, built it). A hired voice is fine for polished explainers; say so in the brief.

## Word budget math

Conversational VO runs about 2.3 to 2.7 words per second (138 to 162 words per minute). Plan at 2.5.

- Ceiling = runtime x 2.25, rounded down. That is 2.5 words per second minus 10% for pauses and visual-only beats.
- Floor = 85% of the unrounded ceiling (runtime x 1.9125), rounded up.
- If more than 30% of runtime is visual-only, use speaking seconds in place of runtime.

| Runtime | Ceiling calc | Ceiling | Floor calc | Floor |
| --- | --- | --- | --- | --- |
| 15s | 15 x 2.25 = 33.75 | 33 | 33.75 x 0.85 = 28.7 | 29 |
| 30s | 30 x 2.25 = 67.5 | 67 | 67.5 x 0.85 = 57.4 | 58 |
| 45s | 45 x 2.25 = 101.25 | 101 | 101.25 x 0.85 = 86.1 | 87 |
| 60s | 60 x 2.25 = 135 | 135 | 135 x 0.85 = 114.75 | 115 |
| 90s | 90 x 2.25 = 202.5 | 202 | 202.5 x 0.85 = 172.1 | 173 |
| 2 min | 120 x 2.25 = 270 | 270 | 270 x 0.85 = 229.5 | 230 |
| 3 min | 180 x 2.25 = 405 | 405 | 405 x 0.85 = 344.25 | 345 |

Sanity check against the speaking range: 135 words at 2.7 words per second takes 50s, leaving 10s of a 60s video for breaths and visual beats. 115 words at 2.3 words per second takes 50s too, so both ends of the range fit.

Per row: words / row seconds must be 2.7 or less. Count hyphenated words as one, numbers as the words spoken ("ledgerline dot app" is 3).

## Writing for the ear

- One idea per line, one breath per line (12 to 18 words, 8 to 12 for nervous speakers).
- Subject first, verb early. "Partners see the whole month" beats "The whole month is visible to partners".
- Contractions and plain words. Say it the way the founder talks.
- "You", not "users". Speak to one viewer.
- Write numbers and URLs the way they are said: "ledgerline dot app", "five of six".
- No parentheses, slashes, or abbreviations the speaker would not say aloud. "AP" on screen can be "payables" in VO.
- Lists of three at most. End lines on the word that matters.
- VO describes why or what it means; the screen shows what. Never narrate what the viewer can already see ("Here I click the button").
- Read aloud against a timer before locking. Mark breaths with `/` and emphasis in bold in the script if useful.

## Recording VO

- Quiet room with soft furnishings, fans and air conditioning off. A USB or lavalier mic 15 to 30cm from the mouth.
- Record line by line, 3 takes each, a beat of silence between. Record a 10s room tone for the edit.
- VO before picture lock for motion builds: the animation is timed to the recorded lines, not the other way round.

## Music: licensing-safe sources

The founder confirms the source and licence; never state that a track is licensed. Typical source types:

- Platform libraries for organic posts on that platform, for example the YouTube Audio Library, TikTok's Commercial Music Library for business accounts, and Meta's Sound Collection. Their terms limit where the track may be used; verify current terms.
- Subscription libraries (for example Epidemic Sound, Artlist, Musicbed) that licence across channels depending on the plan. Check the plan covers paid ads and the website, and whether the channel must be registered to avoid Content ID claims.
- Commissioned or original music with a written licence.

Rules:
- "Royalty-free" does not mean free for any use. Check: organic social, paid ads, website, client work.
- Trending sounds on TikTok or Reels are usually cleared for personal organic use only, not for business accounts or ads. Verify current platform terms.
- Keep the licence or receipt with the project files. Record the track and source in the brief.

## Music and cuts

- Mood in one line: tempo feel, instrumentation, energy arc. "Warm, mid-tempo, light piano and soft percussion, builds into the product moment."
- Arc: cold open (no music or a single hit) on the hook, music enters on the turn, fullest under the product moment, drops or resolves on the CTA.
- Level: music about 15 to 20dB under the VO, ducked under speech.
- Beat-aligned cuts: seconds per beat = 60 / BPM; frames per beat at 30fps = 1800 / BPM. 120 BPM gives 15 frames per beat and 60 per 4/4 bar; 90 BPM gives 20 and 80. Pick a tempo with whole-frame beats when you can, set scene durations in whole beats, and land the big changes (turn, product reveal, CTA) on bar lines.
- If the final track has a different BPM, retime scenes to the nearest beat and recheck the VO rows still fit at 2.7 words per second or less.

## Sound design cues

- Every SFX is tied to an on-screen event at a stated time: a soft click on a UI click, a tick on a completed step, a short whoosh on a push transition.
- Sparingly: at most one SFX every 1 to 2s, none under key VO words.
- No stock "ding" on every animation and no riser on every transition.
- SFX are licensed like music.

## Loudness

About -14 LUFS integrated is a common target for social and YouTube, with peaks below -1 dBTP. Platforms normalise differently and change it; verify current guidance.
