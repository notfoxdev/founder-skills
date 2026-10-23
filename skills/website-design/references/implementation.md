# Implementation

Read this when writing the code. Adapt to the detected stack; these examples assume a React/Next.js app with Tailwind, with plain-CSS equivalents where it matters.

## 1. Tokens as CSS custom properties

Every value in components comes from a token. Replace names and values with the design plan.

```css
/* app/globals.css or styles/tokens.css */
:root {
  /* colour: named by role in the brief */
  --color-paper: #F4F2EC;
  --color-ink: #1B1A17;
  --color-muted: #5C5A52;
  --color-line: #D9D5C9;
  --color-accent: #E2541B;
  --color-accent-ink: #1B1A17; /* text on accent, verified 4.5:1 */
  --color-focus: #1B1A17;

  /* type */
  --font-display: "Display Family", ui-serif, Georgia, serif;
  --font-text: "Text Family", ui-sans-serif, system-ui, sans-serif;
  --font-mono: "Mono Family", ui-monospace, SFMono-Regular, monospace;

  --text-display: clamp(2.5rem, 1.6rem + 4.5vw, 4.75rem);
  --text-headline: clamp(1.95rem, 1.4rem + 2.4vw, 3.05rem);
  --text-title: clamp(1.25rem, 1.1rem + 0.6vw, 1.5625rem);
  --text-body-lg: 1.25rem;
  --text-body: 1.0625rem;
  --text-caption: 0.8125rem;

  --leading-display: 1.02;
  --leading-headline: 1.1;
  --leading-title: 1.28;
  --leading-body: 1.6;

  --tracking-display: -0.025em;
  --tracking-headline: -0.02em;
  --tracking-caps: 0.07em;

  /* spacing on a 4px base */
  --space-1: 4px;  --space-2: 8px;  --space-3: 12px; --space-4: 16px;
  --space-6: 24px; --space-8: 32px; --space-12: 48px; --space-16: 64px;
  --space-24: 96px; --space-32: 128px;

  --section-tight: var(--space-12);
  --section-default: var(--space-16);
  --section-generous: var(--space-24);

  --measure: 65ch;
  --content-max: 1200px;

  /* shape and depth */
  --radius-sm: 4px;
  --radius-md: 8px;
  --shadow-1: 0 1px 2px rgb(27 26 23 / 0.06), 0 2px 8px rgb(27 26 23 / 0.06);

  /* motion */
  --ease-standard: cubic-bezier(0.2, 0, 0, 1);
  --ease-emphasized: cubic-bezier(0.16, 1, 0.3, 1);
  --dur-fast: 120ms;
  --dur-base: 220ms;
  --dur-slow: 560ms;
}

@media (min-width: 768px) {
  :root {
    --section-default: var(--space-24);
    --section-generous: var(--space-32);
  }
}
```

## 2. Map tokens into Tailwind

Tailwind v4 (CSS-first): move the colour, font, radius, and width tokens from `:root` into `@theme`. Tailwind emits them as CSS variables and generates utilities (`bg-paper`, `text-ink`, `font-display`, `rounded-md`, `max-w-content`). Keep spacing-section and motion tokens in `:root`. Do not redeclare a token as `var()` of itself; that creates a cycle.

```css
@import "tailwindcss";

@theme {
  --color-paper: #F4F2EC;
  --color-ink: #1B1A17;
  --color-muted: #5C5A52;
  --color-line: #D9D5C9;
  --color-accent: #E2541B;
  --color-accent-ink: #1B1A17;
  --color-focus: #1B1A17;

  --font-display: "Display Family", ui-serif, Georgia, serif;
  --font-text: "Text Family", ui-sans-serif, system-ui, sans-serif;
  --font-mono: "Mono Family", ui-monospace, SFMono-Regular, monospace;

  --radius-sm: 4px;
  --radius-md: 8px;

  --container-content: 1200px;
  --container-measure: 65ch;
}
```

If fonts come from `next/font` variables, use `@theme inline { --font-display: var(--font-newsreader); }` where the right-hand variable has a different name from the theme token.

Tailwind v3 (`tailwind.config.ts`):

```ts
import type { Config } from "tailwindcss";

export default {
  content: ["./src/**/*.{ts,tsx,mdx}"],
  theme: {
    extend: {
      colors: {
        paper: "var(--color-paper)",
        ink: "var(--color-ink)",
        muted: "var(--color-muted)",
        line: "var(--color-line)",
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

Rules: no arbitrary values like `text-[37px]` or `bg-[#7c3aed]` in components. If you need a new value, add a token and say why.

## 3. Type utilities

Define the scale once so components use roles, not sizes:

```css
@layer components {
  .t-display  { font-family: var(--font-display); font-size: var(--text-display);  line-height: var(--leading-display);  letter-spacing: var(--tracking-display);  text-wrap: balance; }
  .t-headline { font-family: var(--font-display); font-size: var(--text-headline); line-height: var(--leading-headline); letter-spacing: var(--tracking-headline); text-wrap: balance; }
  .t-title    { font-family: var(--font-text);    font-size: var(--text-title);    line-height: var(--leading-title);    letter-spacing: -0.01em; font-weight: 600; }
  .t-body-lg  { font-family: var(--font-text);    font-size: var(--text-body-lg);  line-height: 1.5; max-width: 55ch; text-wrap: pretty; }
  .t-body     { font-family: var(--font-text);    font-size: var(--text-body);     line-height: var(--leading-body); max-width: var(--measure); text-wrap: pretty; }
  .t-caption  { font-family: var(--font-text);    font-size: var(--text-caption);  line-height: 1.45; letter-spacing: 0.01em; color: var(--color-muted); }
}
```

## 4. Font loading

Next.js (`next/font` self-hosts, subsets, and sets fallback metrics to avoid layout shift):

```tsx
// app/fonts.ts
import { Newsreader, Public_Sans } from "next/font/google";
import localFont from "next/font/local";

export const display = Newsreader({ subsets: ["latin"], weight: ["500"], variable: "--font-newsreader", display: "swap" });
export const text = Public_Sans({ subsets: ["latin"], weight: ["400", "600"], variable: "--font-public-sans", display: "swap" });

// Fontshare or other downloaded fonts: place .woff2 files in the repo
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

Then point the role tokens at the generated variables: `--font-display: var(--font-newsreader), Georgia, serif;` (in `:root` for v3, in `@theme inline` for v4). Use distinct names for the generated variable and the role token.

Plain HTML/CSS:

```html
<link rel="preload" href="/fonts/display-500.woff2" as="font" type="font/woff2" crossorigin>
```

```css
@font-face {
  font-family: "Display Family";
  src: url("/fonts/display-500.woff2") format("woff2");
  font-weight: 500;
  font-display: swap;
}
```

## 5. Base styles

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
:where(a, button, input, select, textarea, summary):focus-visible {
  outline: 2px solid var(--color-focus);
  outline-offset: 2px;
  border-radius: var(--radius-sm);
}
img, video { max-width: 100%; height: auto; display: block; }
.tabular { font-variant-numeric: tabular-nums; }
.skip-link { position: absolute; left: var(--space-4); top: -100px; }
.skip-link:focus { top: var(--space-4); }
```

## 6. Layout primitives

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
      <div className="mx-auto w-full max-w-content px-4 md:px-6 lg:px-8">{children}</div>
    </section>
  );
}
```

The `py-[var(...)]` form references tokens, which is the one acceptable use of bracket syntax.

## 7. Button with all states

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
    "transition-colors duration-[var(--dur-fast)] ease-[var(--ease-standard)] " +
    "focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-[var(--color-focus)] " +
    "disabled:cursor-not-allowed disabled:opacity-60";
  const sizes = { md: "h-11 px-5 text-base", lg: "h-12 px-6 text-[1.0625rem]" };
  const variants = {
    primary: "bg-accent text-[var(--color-accent-ink)] hover:brightness-95 active:brightness-90",
    secondary: "border border-ink/80 text-ink hover:bg-ink/5 active:bg-ink/10",
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

## 8. Accessible email capture

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
          className="h-12 rounded-md border border-line bg-paper px-4 text-base text-ink"
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

Validate the email server-side too, rate-limit the endpoint, and never echo raw input into HTML without escaping (React does this by default).

## 9. Images and media

```tsx
import Image from "next/image";

<Image src="/product/schedule.png" alt="Weekly schedule with two double-booked slots flagged" width={1600} height={1000}
       sizes="(min-width: 1024px) 60vw, 100vw" priority className="rounded-md border border-line" />
```

- `priority` (or `fetchpriority="high"`) only on the LCP image.
- Hero loops: `<video autoplay muted loop playsinline poster="/hero-poster.avif">` with MP4 (H.264) and WebM sources, plus a pause button. Under reduced motion, show the poster.

## 10. Verify

- Run the project's build and lint.
- Check computed contrast for every token pair with the script in `color-and-motion.md`.
- Take screenshots at 375/768/1280/1440 if a browser tool is available, then run `review-checklist.md`.
