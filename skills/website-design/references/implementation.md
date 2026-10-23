# Implementation

Read this when writing the code. Detect the stack first, then adapt. Examples assume Next.js (App Router) with Tailwind, with plain-CSS, Astro, and plain-HTML equivalents where they differ.

## 1. Detect the stack

| Signal in the repo | Stack | Tokens go in | Fonts | Images | Meta |
| --- | --- | --- | --- | --- | --- |
| `next` in `package.json`, `app/` dir | Next.js App Router | `app/globals.css` (`@theme` for Tailwind v4) | `next/font/google` or `next/font/local` | `next/image` | `export const metadata` in `layout.tsx` / `page.tsx` |
| `next`, `pages/` dir | Next.js Pages Router | `styles/globals.css` | `next/font` | `next/image` | `next/head` |
| `astro` in `package.json`, `astro.config.*` | Astro | `src/styles/tokens.css`, imported in the base layout | Fontsource packages or `@font-face` with files in `public/fonts` | `<Image />` / `<Picture />` from `astro:assets` | `<head>` in the base layout |
| `tailwindcss` v4 (`@import "tailwindcss"` in CSS, no config file needed) | Tailwind v4 | `@theme` block | | | |
| `tailwind.config.*` with `theme.extend` | Tailwind v3 | `:root` vars + `theme.extend` mapping | | | |
| `vite` + `react` / `vue` / `svelte` | SPA | `src/styles/tokens.css` | `@font-face` + preload in `index.html` | `<picture>` with AVIF/WebP | `index.html` head (no SSR: OG tags must be static) |
| Only `.html` files, no `package.json` | Plain HTML | `tokens.css` linked first | `@font-face` + `<link rel="preload">` | `<picture>` | `<head>` |
| None of the above, or not the site's repo | Unknown | Plan only | | | `Stack: [NEED: framework/host]` |

Check the versions in `package.json` before using version-specific APIs. Match existing conventions (file layout, component naming, CSS approach). Add no dependency without the founder's agreement; pin any you add.

## 2. Semantic page skeleton

```html
<html lang="en">
  <body>
    <a class="skip-link" href="#main">Skip to content</a>
    <header>
      <nav aria-label="Main">...</nav>
    </header>
    <main id="main">
      <section id="hero" aria-labelledby="hero-title">
        <h1 id="hero-title">...</h1>
      </section>
      <section id="how-it-works" aria-labelledby="how-title">
        <h2 id="how-title">...</h2>
      </section>
      <!-- one h1, h2 per section, h3 inside; never skip a level -->
    </main>
    <footer>...</footer>
  </body>
</html>
```

Lists are `ul`/`ol`, tables are `table` with `caption` and `th scope`, FAQ is `details`/`summary`, buttons that act are `button`, links that navigate are `a`.

## 3. Tokens as CSS custom properties

Every value in components comes from a token. Replace names and values with the design plan.

```css
/* app/globals.css or styles/tokens.css */
:root {
  /* colour: named by role in the brief; ratios recorded in the plan */
  --color-paper: #F9F6F3;
  --color-surface: #F2F0EC;
  --color-line: #E6E2DC;      /* decoration only */
  --color-boundary: #898580;  /* input borders, 3:1+ on paper */
  --color-muted: #6F6B66;     /* 4.5:1+ on paper and surface */
  --color-ink: #1B1814;
  --color-accent: #B23A1F;
  --color-accent-press: #9A3119;
  --color-on-accent: #FFFFFF; /* label on accent, verified 4.5:1+ */
  --color-focus: #1B1814;

  /* type */
  --font-display: "Display Family", ui-serif, Georgia, serif;
  --font-text: "Text Family", ui-sans-serif, system-ui, sans-serif;
  --font-mono: "Mono Family", ui-monospace, SFMono-Regular, Menlo, monospace;

  --text-display: clamp(3rem, 2.482rem + 2.21vw, 4.25rem);     /* 48 -> 68 */
  --text-h1: clamp(2.5rem, 2.137rem + 1.547vw, 3.375rem);      /* 40 -> 54 */
  --text-h2: clamp(2.125rem, 1.866rem + 1.105vw, 2.75rem);     /* 34 -> 44 */
  --text-h3: 1.4375rem;   /* 23 */
  --text-body-lg: 1.1875rem; /* 19 */
  --text-body: 1rem;      /* 16 */
  --text-caption: 0.8125rem; /* 13 */
  --text-label: 0.75rem;  /* 12 */

  --leading-display: 1.08;
  --leading-h1: 1.1;
  --leading-h2: 1.18;
  --leading-h3: 1.22;
  --leading-body-lg: 1.47;
  --leading-body: 1.5;
  --leading-caption: 1.54;

  --tracking-display: -0.03em;
  --tracking-h1: -0.025em;
  --tracking-h2: -0.02em;
  --tracking-h3: -0.01em;
  --tracking-label: 0.06em;

  /* spacing on a 4px base */
  --space-1: 4px;   --space-2: 8px;   --space-3: 12px;  --space-4: 16px;
  --space-6: 24px;  --space-8: 32px;  --space-12: 48px; --space-16: 64px;
  --space-24: 96px; --space-32: 128px; --space-40: 160px;

  --section-tight: var(--space-12);
  --section-default: var(--space-16);
  --section-generous: var(--space-24);

  --measure: 65ch;
  --content-max: 1200px;
  --gutter: var(--space-4);

  /* shape and depth */
  --radius-sm: 2px;
  --radius-md: 4px;
  --shadow-float: 0 1px 2px rgb(27 24 20 / 0.06), 0 8px 24px rgb(27 24 20 / 0.08); /* menus and popovers only */

  /* motion: see color-and-motion.md */
  --ease-out: cubic-bezier(0.25, 1, 0.5, 1);
  --ease-standard: cubic-bezier(0.2, 0, 0, 1);
  --ease-emphasized: cubic-bezier(0.16, 1, 0.3, 1);
  --dur-fast: 150ms;
  --dur-base: 240ms;
  --dur-slow: 400ms;
}

@media (min-width: 768px) {
  :root {
    --text-h3: 1.75rem;       /* 28 */
    --text-body-lg: 1.375rem; /* 22 */
    --text-body: 1.125rem;    /* 18 */
    --text-caption: 0.875rem; /* 14 */
    --text-label: 0.8125rem;  /* 13 */
    --leading-display: 1.06;  /* 72/68 */
    --leading-h1: 1.11;       /* 60/54 */
    --leading-h2: 1.09;       /* 48/44 */
    --leading-h3: 1.29;       /* 36/28 */
    --leading-body-lg: 1.45;  /* 32/22 */
    --leading-body: 1.56;     /* 28/18 */
    --leading-caption: 1.43;  /* 20/14 */
    --section-default: var(--space-24);
    --section-generous: var(--space-40);
    --gutter: var(--space-6);
  }
}
@media (min-width: 1024px) { :root { --gutter: var(--space-8); } }
```

The neutrals are the warm ramp in `color-and-motion.md`. Computed for this example set: white on `#B23A1F` 5.97:1, `#B23A1F` as text on paper 5.54:1, white on `#9A3119` 7.43:1, ink focus ring on paper 16.43:1 (the 2px offset keeps the ring on paper, not on the accent, where ink would be 2.96:1). Recompute for your palette.

## 4. Map tokens into Tailwind

Tailwind v4 (CSS-first): put colour, font, radius, and container tokens in `@theme`. Tailwind emits them as CSS variables and generates utilities (`bg-paper`, `text-ink`, `font-display`, `rounded-md`, `max-w-content`). Keep section, type-scale, and motion tokens in `:root`. Do not redeclare a token as `var()` of itself; that creates a cycle.

```css
@import "tailwindcss";

@theme {
  --color-paper: #F9F6F3;
  --color-surface: #F2F0EC;
  --color-line: #E6E2DC;
  --color-boundary: #898580;
  --color-muted: #6F6B66;
  --color-ink: #1B1814;
  --color-accent: #B23A1F;
  --color-accent-press: #9A3119;
  --color-on-accent: #FFFFFF;
  --color-focus: #1B1814;

  --radius-sm: 2px;
  --radius-md: 4px;

  --container-content: 1200px;
  --container-measure: 65ch;
}
```

If fonts come from `next/font` variables, use `@theme inline { --font-display: var(--font-newsreader), Georgia, serif; }` where the right-hand variable has a different name from the theme token.

Tailwind v3 (`tailwind.config.ts`):

```ts
import type { Config } from "tailwindcss";

export default {
  content: ["./src/**/*.{ts,tsx,mdx}", "./app/**/*.{ts,tsx,mdx}"],
  theme: {
    extend: {
      colors: {
        paper: "var(--color-paper)",
        surface: "var(--color-surface)",
        line: "var(--color-line)",
        boundary: "var(--color-boundary)",
        muted: "var(--color-muted)",
        ink: "var(--color-ink)",
        accent: "var(--color-accent)",
      },
      fontFamily: {
        display: ["var(--font-display)"],
        text: ["var(--font-text)"],
        mono: ["var(--font-mono)"],
      },
      maxWidth: { measure: "65ch", content: "1200px" },
    },
  },
} satisfies Config;
```

Rules: no arbitrary values like `text-[37px]` or `bg-[#7c3aed]` in components. If you need a new value, add a token and say why. Replace a starter kit's default tokens rather than layering on top of them.

## 5. Type utilities

Define the scale once so components use roles, not sizes:

```css
@layer components {
  .t-display { font-family: var(--font-display); font-size: var(--text-display); line-height: var(--leading-display); letter-spacing: var(--tracking-display); text-wrap: balance; max-width: 18ch; }
  .t-h1      { font-family: var(--font-display); font-size: var(--text-h1); line-height: var(--leading-h1); letter-spacing: var(--tracking-h1); text-wrap: balance; }
  .t-h2      { font-family: var(--font-display); font-size: var(--text-h2); line-height: var(--leading-h2); letter-spacing: var(--tracking-h2); text-wrap: balance; }
  .t-h3      { font-family: var(--font-text); font-size: var(--text-h3); line-height: var(--leading-h3); letter-spacing: var(--tracking-h3); font-weight: 600; }
  .t-body-lg { font-family: var(--font-text); font-size: var(--text-body-lg); line-height: var(--leading-body-lg); max-width: 55ch; text-wrap: pretty; }
  .t-body    { font-family: var(--font-text); font-size: var(--text-body); line-height: var(--leading-body); max-width: var(--measure); text-wrap: pretty; }
  .t-caption { font-family: var(--font-text); font-size: var(--text-caption); line-height: var(--leading-caption); letter-spacing: 0.01em; color: var(--color-muted); }
  .t-label   { font-family: var(--font-text); font-size: var(--text-label); line-height: 1.33; letter-spacing: var(--tracking-label); text-transform: uppercase; font-weight: 600; }
  .tabular   { font-variant-numeric: tabular-nums lining-nums; }
}
```

## 6. Font loading

Next.js (`next/font` self-hosts, subsets, and generates fallback metrics to avoid layout shift):

```tsx
// app/fonts.ts
import { Newsreader, Public_Sans } from "next/font/google";
import localFont from "next/font/local";

export const display = Newsreader({ subsets: ["latin"], weight: ["500"], variable: "--font-newsreader", display: "swap" });
export const text = Public_Sans({ subsets: ["latin"], weight: ["400", "600"], variable: "--font-public-sans", display: "swap" });

// Fontshare or other downloaded fonts: commit the licensed .woff2 files
export const clash = localFont({
  src: [{ path: "./fonts/ClashDisplay-Semibold.woff2", weight: "600", style: "normal" }],
  variable: "--font-clash",
  display: "swap",
});
```

```tsx
// app/layout.tsx
<html lang="en" className={`${display.variable} ${text.variable}`}>
```

Point the role tokens at the generated variables with distinct names: `--font-display: var(--font-newsreader), Georgia, serif;`.

Astro: install a pinned Fontsource package and import it in the base layout (`import "@fontsource-variable/<family>";`), or use `@font-face` with files in `public/fonts` as below.

Plain HTML / Vite:

```html
<link rel="preload" href="/fonts/display-500-latin.woff2" as="font" type="font/woff2" crossorigin>
```

```css
@font-face {
  font-family: "Display Family";
  src: url("/fonts/display-500-latin.woff2") format("woff2");
  font-weight: 500;
  font-style: normal;
  font-display: swap;
  unicode-range: U+0000-00FF, U+0131, U+0152-0153, U+02BB-02BC, U+02C6, U+02DA, U+02DC, U+2000-206F, U+2074, U+20AC, U+2122, U+2191, U+2193, U+2212, U+2215, U+FEFF, U+FFFD;
}
/* Fallback tuned to the web font so the swap does not shift layout.
   Compute the four values for your font with Fontaine or Capsize; these are placeholders. */
@font-face {
  font-family: "Display Fallback";
  src: local("Georgia");
  size-adjust: 100%;
  ascent-override: 90%;
  descent-override: 22%;
  line-gap-override: 0%;
}
```

Subsetting a downloaded font (fonttools; `--flavor=woff2` needs the `brotli` module):

```bash
pyftsubset Display-Medium.ttf --output-file=display-500-latin.woff2 --flavor=woff2 --layout-features='*' \
  --unicodes="U+0000-00FF,U+0131,U+0152-0153,U+02BB-02BC,U+02C6,U+02DA,U+02DC,U+2000-206F,U+2074,U+20AC,U+2122,U+2191,U+2193,U+2212,U+2215,U+FEFF,U+FFFD"
```

Check the licence allows modification (subsetting) before you subset. OFL fonts do; some commercial licences do not.

Budget: at most 4 files, preload at most 2 (the above-the-fold display weight and body regular), `crossorigin` on every font preload.

## 7. Base styles

```css
html { color-scheme: light; -webkit-text-size-adjust: 100%; }
body {
  background: var(--color-paper);
  color: var(--color-ink);
  font-family: var(--font-text);
  font-size: var(--text-body);
  line-height: var(--leading-body);
  -webkit-font-smoothing: antialiased;
}
:where(a) { color: inherit; text-decoration-line: underline; text-underline-offset: 0.2em; text-decoration-thickness: 1px; }
:where(a, button, input, select, textarea, summary, [tabindex]):focus-visible {
  outline: 2px solid var(--color-focus);
  outline-offset: 2px;
  border-radius: var(--radius-sm);
}
img, video, svg { max-width: 100%; height: auto; display: block; }
.skip-link { position: absolute; left: var(--space-4); top: -100px; z-index: 10; }
.skip-link:focus { top: var(--space-4); }
.sr-only { position: absolute; width: 1px; height: 1px; padding: 0; margin: -1px; overflow: hidden; clip: rect(0, 0, 0, 0); white-space: nowrap; border: 0; }
```

## 8. Layout primitives

```tsx
// components/Section.tsx
type SectionProps = {
  id: "hero" | "proof" | "problem" | "how-it-works" | "features" | "pricing" | "faq" | "final-cta";
  rhythm?: "tight" | "default" | "generous";
  labelledBy?: string;
  children: React.ReactNode;
};

const pad = {
  tight: "py-[var(--section-tight)]",
  default: "py-[var(--section-default)]",
  generous: "py-[var(--section-generous)]",
};

export function Section({ id, rhythm = "default", labelledBy, children }: SectionProps) {
  return (
    <section id={id} aria-labelledby={labelledBy} className={pad[rhythm]}>
      <div className="mx-auto grid w-full max-w-content grid-cols-4 gap-x-[var(--gutter)] px-4 sm:grid-cols-8 sm:px-8 lg:grid-cols-12 lg:px-12">
        {children}
      </div>
    </section>
  );
}
```

Children place themselves on the grid (`col-span-4 lg:col-start-2 lg:col-span-6`). The `py-[var(...)]` form references tokens, which is the one acceptable use of bracket syntax.

## 9. Button with all states

```tsx
// components/Button.tsx
import { forwardRef } from "react";

type Props = React.ButtonHTMLAttributes<HTMLButtonElement> & {
  variant?: "primary" | "secondary";
  size?: "md" | "lg";
  loading?: boolean;
};

export const Button = forwardRef<HTMLButtonElement, Props>(function Button(
  { variant = "primary", size = "md", loading = false, children, className = "", disabled, ...rest },
  ref
) {
  const base =
    "inline-flex items-center justify-center gap-2 rounded-md font-text font-semibold " +
    "transition-colors duration-[var(--dur-fast)] ease-[var(--ease-out)] " +
    "focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-[var(--color-focus)] " +
    "disabled:cursor-not-allowed disabled:opacity-60";
  const sizes = { md: "h-11 px-5 text-base", lg: "h-12 px-6 text-[length:var(--text-body)]" };
  const variants = {
    primary: "bg-accent text-on-accent hover:bg-accent-press active:translate-y-px",
    secondary: "border border-ink text-ink hover:bg-surface active:translate-y-px",
  };
  return (
    <button
      ref={ref}
      aria-busy={loading || undefined}
      disabled={disabled || loading}
      className={`${base} ${sizes[size]} ${variants[variant]} ${className}`}
      {...rest}
    >
      {loading ? <span className="size-4 animate-spin rounded-full border-2 border-current border-t-transparent" aria-hidden="true" /> : null}
      <span>{children}</span>
    </button>
  );
});
```

For links styled as buttons, use the same classes on `<a>` (or the framework `Link`); never a `div` with `onClick`.

## 10. Accessible email capture

```tsx
"use client";
import { useState } from "react";
import { Button } from "./Button";

export function WaitlistForm({ action }: { action: (email: string) => Promise<void> }) {
  const [state, setState] = useState<"idle" | "loading" | "error" | "done">("idle");
  const [email, setEmail] = useState("");

  async function onSubmit(e: React.FormEvent) {
    e.preventDefault();
    setState("loading");
    try { await action(email); setState("done"); } catch { setState("error"); }
  }

  if (state === "done") {
    return <p role="status" className="t-body">You are on the list. We sent a confirmation to {email}.</p>;
  }

  return (
    <form onSubmit={onSubmit} noValidate className="flex flex-col gap-3 sm:flex-row sm:items-end">
      <div className="flex flex-1 flex-col gap-1.5">
        <label htmlFor="email" className="t-caption text-ink">Work email</label>
        <input
          id="email" name="email" type="email" autoComplete="email" required
          value={email} onChange={(e) => setEmail(e.target.value)}
          aria-invalid={state === "error" || undefined}
          aria-describedby={state === "error" ? "email-error" : undefined}
          className="h-12 rounded-md border border-boundary bg-paper px-4 text-base text-ink"
        />
        {state === "error" ? (
          <p id="email-error" className="t-caption text-ink">That did not go through. Check the address and try again.</p>
        ) : null}
      </div>
      <Button type="submit" size="lg" loading={state === "loading"}>Join the waitlist</Button>
    </form>
  );
}
```

Validate the email server-side too, rate-limit the endpoint, and never echo raw input into HTML without escaping (React escapes by default). If the founder already has a waitlist tool, post to it so existing signups stay in one list.

## 11. Images and media

| Content | Format | Notes |
| --- | --- | --- |
| Photos, screenshots with gradients | AVIF, WebP fallback | `next/image` and `astro:assets` generate these; plain HTML uses `<picture>` |
| UI screenshots with flat colour and text | WebP or PNG; check AVIF for text blur | Capture at 2x |
| Logos, icons, diagrams | SVG, optimised (SVGO) | Inline only if styled by CSS |
| Hero loop | MP4 (H.264) + WebM, under about 3MB, with poster | Muted, `playsinline`, pause control if over 5s |

```tsx
import Image from "next/image";

<Image src="/product/schedule.png" alt="Weekly schedule with two double-booked slots flagged" width={1600} height={1000}
       sizes="(min-width: 1024px) 60vw, 100vw" priority className="rounded-md border border-line" />
```

```html
<picture>
  <source srcset="/img/close-800.avif 800w, /img/close-1600.avif 1600w" type="image/avif" sizes="(min-width: 1024px) 60vw, 100vw">
  <source srcset="/img/close-800.webp 800w, /img/close-1600.webp 1600w" type="image/webp" sizes="(min-width: 1024px) 60vw, 100vw">
  <img src="/img/close-1600.jpg" width="1600" height="1000" alt="..." loading="lazy" decoding="async">
</picture>
```

- Always `width` and `height` (or `aspect-ratio`) to reserve space (CLS).
- Only the LCP image is eager: `priority` in Next.js, `fetchpriority="high"` and no `loading="lazy"` in HTML. Everything below the fold is lazy.
- Hero image under about 200KB.
- Alt text describes what the image shows and why it matters; decorative images get `alt=""`.

## 12. SEO, meta, and social

Next.js App Router:

```tsx
// app/layout.tsx (site defaults) or app/page.tsx (page-specific)
import type { Metadata } from "next";

export const metadata: Metadata = {
  metadataBase: new URL("https://example.com"),
  title: "<What it is> for <who it is for> | <Brand>", // about 50 to 60 characters
  description: "One or two plain sentences that say who it is for and what it does, about 140 to 160 characters.",
  alternates: { canonical: "/" },
  openGraph: { type: "website", url: "/", title: "...", description: "...", images: [{ url: "/og.png", width: 1200, height: 630, alt: "..." }] },
  twitter: { card: "summary_large_image" },
};
```

An `app/opengraph-image.png` (or `.tsx`) file is picked up automatically as the OG image.

Plain HTML / Astro head:

```html
<title>...</title>
<meta name="description" content="...">
<link rel="canonical" href="https://example.com/">
<meta name="viewport" content="width=device-width, initial-scale=1">
<meta property="og:type" content="website">
<meta property="og:title" content="...">
<meta property="og:description" content="...">
<meta property="og:image" content="https://example.com/og.png">
<meta property="og:url" content="https://example.com/">
<meta name="twitter:card" content="summary_large_image">
<link rel="icon" href="/favicon.ico" sizes="32x32">
<link rel="icon" href="/icon.svg" type="image/svg+xml">
<link rel="apple-touch-icon" href="/apple-touch-icon.png"> <!-- 180x180 -->
<meta name="theme-color" content="#F9F6F3">
```

- Character counts for title and description are guidelines; search engines truncate by pixel width and may rewrite them.
- The OG image (1200x630) uses the page's real type and palette, not a stock graphic, and stays legible at small preview sizes.
- Preview and staging deployments: `noindex`. Never ship `noindex` to production.
- Never `user-scalable=no` or `maximum-scale=1` in the viewport tag; it blocks zoom.
- Organization JSON-LD is optional; only real facts (name, URL, logo).

## 13. Verify

- Run the project's build and lint.
- Run the tell scan in `anti-generic.md` over the changed files.
- Compute contrast for every token pair with the script in `color-and-motion.md`.
- Take screenshots at 375/768/1280/1440 if a browser tool is available, then run `review-checklist.md` and score it.
