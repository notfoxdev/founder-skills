# Pre-ship review checklist

Run every item before calling the page done. Mark each Pass / Fail / N/A in the critique table. A single Fail in the Blockers group means the page does not ship.

## How to review

1. If a browser or screenshot tool is available, capture full-page screenshots at **375, 768, 1280, 1440px** wide (add 320 and 1920 if time allows). Look at each one at 100% and zoomed out to 25% (the squint test).
2. Tab through the whole page with the keyboard only.
3. Run Lighthouse or PageSpeed (mobile profile) and an accessibility scanner (axe DevTools, Lighthouse a11y) if available.
4. Read every word on the page once, top to bottom, as the target customer.
5. If you cannot run a check, write "Not verified: <check>, founder to confirm by <method>".

## Blockers (must pass)

- [ ] No invented proof: every logo, quote, metric, user count, press mention, and price is founder-provided or sourced. Gaps show `[NEED: ...]`.
- [ ] All text meets WCAG AA contrast (4.5:1 body, 3:1 large text and UI boundaries). Ratios recorded.
- [ ] Every interactive element is reachable by keyboard and shows a visible focus indicator.
- [ ] Primary CTA works end to end (link resolves, form submits, success and error states render).
- [ ] No horizontal scroll at 320–1920px.
- [ ] One `h1`; heading levels do not skip.
- [ ] `prefers-reduced-motion` removes or replaces all non-essential motion.

## Distinctiveness

- [ ] Swap test: with a competitor's logo, the page would no longer fit. Name the elements that make it specific.
- [ ] Each banned tell from SKILL.md is absent or has a written reason.
- [ ] The signature moment exists, is singular, and ties to the customer's material world.
- [ ] Colour and type choices trace back to the brief, not to defaults.
- [ ] The hero artifact is real (product, code, output, honest prototype), not decoration.

## Hierarchy and composition

- [ ] Squint test: each screen has one dominant element and a clear path to the CTA.
- [ ] 5-second test: the headline, who it is for, and the action are clear from the first viewport at 1280x800 and 375x812.
- [ ] Only one primary (filled) button visible per viewport.
- [ ] Distinct left edges per screen: 3 or fewer.
- [ ] Adjacent sections differ in composition or density; no run of identical "heading + three items" blocks.
- [ ] Whitespace is generous and consistent: all spacing comes from the scale.

## Typography

- [ ] Body measure 60–75ch; hero subhead under about 55ch.
- [ ] Display tracking tightened (-0.02em or tighter); body tracking 0; caps tracked +0.04em or more.
- [ ] Line-heights match the token table; no body text under 1.45.
- [ ] Headlines use `text-wrap: balance`; no single-word last lines in headlines or short paragraphs.
- [ ] No more than two families plus a mono; at most 4 font files loaded.
- [ ] Numerals in prices and tables are tabular.
- [ ] Proper quotes, apostrophes, and dashes.

## Colour

- [ ] Accent used for primary action and signature moment; under about 10% of the surface.
- [ ] Information never conveyed by colour alone (errors, required fields, pricing highlights, chart series).
- [ ] Neutrals are tinted consistently; no stray greys outside the token set.
- [ ] Dark sections (if any) re-checked for contrast.

## Components and states

- [ ] Buttons: default, hover, active, focus-visible, disabled, loading all designed.
- [ ] Links in body text are underlined.
- [ ] Forms: visible labels, correct `type`/`autocomplete`, inline errors with `aria-describedby`, success announced.
- [ ] Mobile nav: `aria-expanded`, focus trapped while open, Escape closes, focus returns.
- [ ] FAQ disclosures operable with keyboard and announce state.
- [ ] Tap targets 44x44px or larger.
- [ ] Empty, loading, and error states have real copy.

## Accessibility (beyond blockers)

- [ ] `lang` attribute on `html`.
- [ ] Landmarks: `header`, `nav`, `main`, `footer`; skip link works.
- [ ] Images: meaningful `alt` for content, `alt=""` for decoration. Screenshots described by what they show.
- [ ] Video: captions available; autoplay is muted, has pause control if over 5 seconds.
- [ ] Zoom to 200%: no clipped or overlapping text.
- [ ] Nothing flashes more than 3 times per second.

## Responsive

- [ ] Designed at 375px, not just shrunk from desktop.
- [ ] Splits stack cleanly below 768px; media order makes sense.
- [ ] Display type scales with `clamp()` and does not overflow at 320px.
- [ ] Tables and pricing readable on mobile.
- [ ] Sticky elements do not cover content or the CTA on small screens.

## Performance

- [ ] Lighthouse performance (mobile) 90+ if measurable. LCP under 2.5s, CLS under 0.1, INP under 200ms.
- [ ] Fonts self-hosted or framework-loaded, `font-display: swap`, above-the-fold files preloaded (2 max), fallback metrics adjusted.
- [ ] Images AVIF/WebP, sized with `width`/`height` or `aspect-ratio`, responsive `srcset`/`sizes`, lazy below the fold.
- [ ] Hero image under about 200KB; hero video under about 3MB with a poster image.
- [ ] No layout shift from late-loading banners, embeds, or cookie bars.
- [ ] No unused JS libraries added for effects.

## Content and meta

- [ ] No lorem ipsum, no `[DRAFT]` left unless the founder accepted it.
- [ ] `<title>` (50–60 characters) and meta description (140–160 characters) set.
- [ ] Open Graph image 1200x630, `og:title`, `og:description`, Twitter/X card.
- [ ] Favicon and apple-touch-icon present.
- [ ] Analytics event on the primary CTA if the founder uses analytics.
- [ ] Legal links (privacy, terms) present if collecting data.

## Critique table (paste into output)

| Group | Check | Result | Fix applied / note |
| --- | --- | --- | --- |
| Blockers | ... | Pass/Fail | ... |
