# Pre-ship review and scorecard

Run this in full before calling a page done (SKILL.md step 7), and use the Blockers and Distinctiveness parts for Audit mode. It has three layers:

1. **Blockers:** pass/fail gates. One fail means the page does not ship.
2. **Named audits:** procedures that produce evidence (squint, swap, tell scan, icon, contrast, mobile 375, keyboard, performance, content).
3. **Scorecard:** 10 dimensions scored 0 to 3 from that evidence.

## Ship rule

- **SHIP:** every Blocker passes, total score 24/30 or more, no dimension under 2, every audit verified.
- **SHIP AFTER FOUNDER CHECKS:** thresholds met, but one or more audits could not be verified by you (no browser, no deployed preview). List each check, how to do it, and what pass looks like.
- **DO NOT SHIP:** any Blocker fails, total under 24, or any dimension under 2.

On a fail: fix the lowest-scoring dimension first, re-run its audit, rescore, and report both the first and the final score. Do not inflate a score to cross the line; after two fix rounds, report what still fails and why.

Honesty rules:

- Score from evidence you gathered, not from the plan. Write the evidence in the table.
- A dimension whose audit you could not run scores at most 2 and is marked "Not verified".
- Do not report measured numbers (Lighthouse scores, LCP) you did not measure.

## How to review

1. If a browser or screenshot tool is available, capture full-page screenshots at **375, 768, 1280, 1440px** (also 320 for overflow). Look at each at 100% and at 25% zoom.
2. Tab through the whole page with the keyboard only.
3. Run Lighthouse or PageSpeed (mobile profile) and an accessibility scanner (axe DevTools, Lighthouse accessibility) if available.
4. Read every word top to bottom as the target customer.
5. If you cannot run a check, write "Not verified: <check>; founder to confirm by <method>".

## Blockers (must pass)

| ID | Check |
| --- | --- |
| B1 | No invented proof: every logo, quote, metric, user count, press mention, and price is founder-provided or sourced (A9) |
| B2 | Every text/background and control/background pair meets WCAG AA: 4.5:1 body, 3:1 large text and UI boundaries; ratios recorded (A5) |
| B3 | Every interactive element is reachable by keyboard and shows a visible focus indicator (A7) |
| B4 | Primary CTA works end to end: link resolves or form submits, success and error states render |
| B5 | No horizontal page scroll from 320 to 1920px |
| B6 | One `h1`; heading levels do not skip |
| B7 | `prefers-reduced-motion` removes or replaces all non-essential motion |
| B8 | No `[NEED: ...]`, `[DRAFT]`, or lorem visible on a public URL (allowed on a preview) |

## Named audits

### A1 Squint test

- **Do:** view each screenshot at 25% zoom, or blur the live page (`document.body.style.filter = "blur(8px)"` in the console). For each viewport-height screen, write the dominant element and where the CTA is.
- **Pass:** each screen has one dominant element; the CTA is identifiable within about 2 seconds on the hero and final-CTA screens; no screen is an even grey texture.

### A2 Swap test

- **Do:** mentally (or literally) replace the logo and name with the closest competitor or alternative from `company.md`, then with an unrelated startup. List every element that would now be wrong.
- **Pass:** 3 or more subject-specific elements, including the signature moment (for example: the artifact, the palette source, the type reasoning, the copy's nouns). Fewer than 3 means the page is generic.

### A3 Tell scan

- **Do:** walk T1 to T22 in `anti-generic.md` against the page and run the code scan there. For each hit, record the reason it survives or the fix.
- **Pass:** zero tells without a written, subject-specific reason. Any unjustified tell caps Distinctiveness at 1.

### A4 Icon audit

- **Do:** inventory every icon: location, job (functional, status, identification), set, stroke, size, style, accessible name or `aria-hidden`.
- **Pass:** no icon fails the deletion test; one set, one stroke weight, one style; sizes from the 16/20/24 scale; functional icons labelled; decorative ones hidden; no icon-in-circle badges; no list where every item carries an icon for decoration.

### A5 Contrast audit

- **Do:** list every pair actually rendered: body, muted, captions, links, labels on the accent, text on tinted bands, placeholder text, input borders, focus ring against paper and against the accent, text over images. Compute each with the script in `color-and-motion.md`.
- **Pass:** every pair meets its threshold on the unrounded value.

### A6 Mobile 375 audit

At 375x667 (and 320 for overflow):

| Check | Pass |
| --- | --- |
| Overflow | No horizontal scroll at 320 or 375 |
| Hero | h1 in 4 lines or fewer, no overflowing word; primary CTA visible without scrolling |
| Text | Body 16px or more; inputs 16px or more; measure under about 45ch on mobile is fine |
| Targets | Primary controls 44x44px; nothing under 24x24px; adjacent targets not touching |
| Nav | Menu button opens and closes, focus moves into the panel and back, Escape closes |
| Tables and wide artifacts | Scroll inside a focusable, labelled region with a visible hint, or reflow |
| Sticky elements | Header 64px or less; nothing sticky covers the CTA or form |
| Rhythm | Mobile section padding in use (not desktop values); splits stacked in a sensible order |

**Pass:** every row passes.

### A7 Keyboard audit

- **Do:** from the address bar, Tab through the whole page, then Shift+Tab back.
- **Pass:** skip link appears first and works; focus order follows visual order; focus is always visible (2px+, 3:1 against its background); menu, FAQ, toggles, and forms work with Enter, Space, and Escape; no focus traps outside open dialogs.

### A8 Performance audit

- **Do:** Lighthouse mobile or PageSpeed Insights on a deployed preview. Record LCP, CLS, and Total Blocking Time (the lab proxy for INP). Note these are lab values; Core Web Vitals "good" is judged on real-user data at the 75th percentile.
- **Pass:** LCP 2.5s or less, CLS 0.1 or less, TBT under 200ms, performance score 90+.
- **If not measurable:** run the static checks instead (font files 4 or fewer, preloads 2 or fewer, LCP element identified and not animated in, images sized and in AVIF/WebP, no effect libraries added), score at most 2, and mark "Not verified".

### A9 Content audit

- **Do:** read every visible string and number.
- **Pass:** no lorem; every number has a source; every quote and logo has permission; button labels are specific verbs; empty, error, and success states have real words; `[NEED]` and `[DRAFT]` markers are listed for the founder.

## Scorecard

| # | Dimension | Evidence from | 0 | 1 | 2 | 3 |
| --- | --- | --- | --- | --- | --- | --- |
| 1 | Distinctiveness | A2, A3 | Works unchanged with a competitor's logo | 1 to 2 specific elements, or an unjustified tell | 3+ specific elements, signature moment present | 3+ specific elements, signature moment passes all five tests in `anti-generic.md`, zero unjustified tells |
| 2 | Hierarchy | A1 | No dominant element on most screens | Dominant element but CTA lost | Passes on most screens | Passes on every captured screen at every width |
| 3 | Typography | Plan vs build | Default face, flat sizes | Pairing by habit or scale not followed | Pairing from the brief, scale followed, one miss (tracking, measure, figures) | Pairing reasoned, computed scale, display tracking, measure, tabular figures, balanced headlines |
| 4 | Colour | A5, plan | Contrast failures | Palette not from the brief, or accent everywhere | All pairs pass, one accent, minor overuse | All pairs pass with recorded ratios, colours named from the brief, accent under 10%, neutrals tinted |
| 5 | Layout and rhythm | Screenshots, wireframe | No grid, centred everything | Grid but 4+ left edges or identical adjacent sections | Grid and axis held, density varies, one repeat | Column spans deliberate, 3 or fewer left edges, density map followed, spacing only from the scale |
| 6 | Imagery and icons | A4 | Fake UI or stock posing as proof | Decorative icons or mixed sets | Real or labelled artifacts, icons disciplined, one miss | Every image real or labelled, every icon has a job, one set and stroke |
| 7 | Motion | Code, reduced-motion check | Motion on everything, or layout properties animated | Several decorative effects | Purposeful, transform/opacity only, one extra effect | Only feedback plus the signature sequence, durations and easing from tokens, designed reduced-motion state |
| 8 | Mobile | A6 | Overflow or broken hero | 2+ A6 rows fail | 1 A6 row fails | Every A6 row passes |
| 9 | Accessibility | A7, scanner, markup | Blocker-level failures | Several issues (labels, alt, landmarks) | Scanner clean, one manual issue | Scanner clean, keyboard audit passes, landmarks, alt text, form errors, and zoom to 200% verified |
| 10 | Performance and build hygiene | A8, code | Unbounded fonts or images, effect libraries | Budgets broken in 2+ places | Static checks pass, not measured | Measured targets met, tokens only (no raw hex or arbitrary values) |

Total out of 30. Ship threshold: 24, with no dimension under 2.

## Detailed checks (evidence for the scorecard)

Typography

- [ ] Body measure 60 to 75ch; hero subhead under about 55ch; h1 max-width set in `ch`.
- [ ] Display tracking -0.02em or tighter; body tracking 0; caps tracked +0.04em or more.
- [ ] Line-heights match the token table and sit on the 4px baseline; no body text under 1.45.
- [ ] `text-wrap: balance` on headlines; no single-word last lines in headlines.
- [ ] Two families plus an optional mono at most; 4 font files or fewer.
- [ ] Prices, tables, dates in tabular figures. Proper quotes, apostrophes, and dashes.

Colour

- [ ] Accent only on the primary action, signature moment, and (if passing) links and focus.
- [ ] Information never conveyed by colour alone.
- [ ] No stray hex values outside the token set.
- [ ] Dark sections (if any) recomputed for contrast; dark mode only if the test in `color-and-motion.md` passed.

Layout

- [ ] Grid columns and gutters match the plan; alignment axis held.
- [ ] Adjacent sections differ in composition or density.
- [ ] All spacing from the scale; proximity rule holds (inside a group at most half the space between groups).
- [ ] Only one filled button per viewport.

Components and states

- [ ] Buttons: default, hover, active, focus-visible, disabled, loading.
- [ ] Links in body text underlined.
- [ ] Forms: visible labels, correct `type`/`autocomplete`, inline errors with `aria-describedby`, success announced.
- [ ] FAQ disclosures keyboard-operable and announce state.

Accessibility

- [ ] `lang` on `html`; landmarks `header`, `nav`, `main`, `footer`; skip link works.
- [ ] Meaningful `alt` on content images, `alt=""` on decoration; screenshots described by what they show.
- [ ] Video: captions available; autoplay muted; pause control if over 5 seconds.
- [ ] Zoom to 200%: no clipped or overlapping text. Nothing flashes more than 3 times per second.

Performance

- [ ] Fonts self-hosted or framework-loaded, `font-display` set, fallback metrics adjusted, 2 preloads or fewer.
- [ ] Images AVIF/WebP with dimensions, responsive `srcset`/`sizes`, lazy below the fold; hero image under about 200KB.
- [ ] No layout shift from late banners, embeds, or cookie bars.

Content and meta

- [ ] `<title>` about 50 to 60 characters and meta description about 140 to 160 characters.
- [ ] Open Graph image 1200x630, `og:title`, `og:description`, `twitter:card`.
- [ ] Favicon and apple-touch-icon present; canonical URL set; preview deployments `noindex`.
- [ ] Analytics event on the primary CTA if the founder uses analytics.
- [ ] Privacy and terms links present if collecting data.

## Critique output (paste into the answer)

```markdown
### Blockers
| ID | Result | Evidence |
| --- | --- | --- |
| B1 | Pass/Fail | ... |

### Audits
| Audit | Result | Evidence / fix applied |
| --- | --- | --- |
| A1 Squint | Pass/Fail/Not verified | ... |

### Scorecard
| Dimension | First pass | Final | Evidence / fix |
| --- | --- | --- | --- |
| Distinctiveness | 0-3 | 0-3 | ... |
**Total:** <first>/30 -> <final>/30 (threshold 24, none under 2)
**Verdict:** SHIP | SHIP AFTER FOUNDER CHECKS | DO NOT SHIP, because ...
```
