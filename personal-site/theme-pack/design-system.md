---
trigger: always_on
---

# Design system: Hypnospace / VIBE OS

Full rationale: `docs/STYLE_GUIDE.md`. Values: `docs/design-tokens.json` (mirrored in `src/theme.css` and `personal-site/theme-pack/theme.css`). This file holds what you need while writing markup.

## Themes

- **Night** (default, `data-theme="night"`): "Midnight Mall" hero theme for most pages.
- **Day** (`data-theme="day"`): "Pastel Morning", for long reading and the résumé. Can go on `<html>` or on a single `<section>`; utilities recolor automatically.
- Never use Tailwind's `dark:` variant. Theming is `data-theme` only.

## Color utilities (the ONLY colors that exist)

`bg-`, `text-`, `border-` + one of:

| Token | Role |
|---|---|
| `surface` | Page background |
| `surface-raised` | Window bodies, cards, inputs |
| `panel-hi` | Raised rows, secondary buttons, panel-gradient end |
| `crt` | Dark terminal panel (both themes). Only place `phosphor` text appears. |
| `ink` | Body text / 2px borders |
| `ink-muted` | Captions, dates, metadata |
| `line` | Dividers, secondary borders (P0 slot 03) |
| `sunset-pink` | Brand: primary button, needs-you badge, ONE call to action per screen. In Day: fills only, never text. |
| `sunset-orange` | Warm amber accent: sun motif, highlights, waiting |
| `dusk-violet` | Section bands, footer, first stop of the title-bar gradient |
| `cel-teal` | Tags, secondary badges, Night links. Max once per section. |
| `on-accent` | Text on pink / teal fills |
| `on-violet` | Text on dusk-violet bars |
| `phosphor` | Mint CRT text, on `crt` only |
| `gain` / `loss` | Up / down numbers, always with ▲ / ▼ |
| `crt-gain` / `crt-loss` | Same, on `crt` panels |

Tailwind's default palette is removed. `bg-blue-500`, `text-slate-300`, `bg-white`, `bg-[#070a12]` and other arbitrary hex values are **banned**. If a needed color is missing, ask; don't invent one.

Ratio per screen: ~70% surfaces, ~20% ink, ~10% accents. Max two accent colors in one section.

## Chrome (Hypnospace / VIBE OS)

- **Win95 bevel:** windows, cards and buttons carry a 1px inset bevel — `inset 1px 1px 0 var(--bevel-hi), inset -1px -1px 0 var(--bevel-lo)` — plus a hard offset shadow (`shadow-window` / `shadow-pressed`).
- **Title bar:** `.window-bar` is a pastel gradient `linear-gradient(90deg, var(--tb-1), var(--tb-2) 62%, var(--tb-3))` with `--on-pastel` text.
- **Panels:** `.window`, `.card`, `.btn` use `var(--panel-grad)` (subtle vertical panel gradient).
- **Bayer dither:** `.window-body` / `.body-crt` get a faint `var(--bayer)` overlay (`image-rendering: pixelated`). Never dither over body copy.

## Type

| Class | Font | Use |
|---|---|---|
| `font-display` | Pixelify Sans (500, 700) | h1/h2, title cards. 28px minimum. |
| `font-sans` | JetBrains Mono (400, 700) | Default. All paragraphs and UI. |
| `font-pixel` | Silkscreen (400) | Numbers, prices, dates, labels, buttons, badges, window titles. Never paragraphs. |

Scale: title-card 64px/0.95 · h1 40px · h2 28px · lead 20px/30px · body 16px/26px · small 14px/22px · ticker 18px · label 14px +0.06em tracking.

## Shape, spacing, depth

- Square corners. `rounded-sm` (2px) is the max and only for tiny chips. No `rounded-full` except circular avatars.
- Spacing on the 8px grid: prefer `1 2 4 6 10 16` (4/8/16/24/40/64px).
- Depth = hard offset shadow + Win95 bevel. Hover/press = `shadow-pressed` + translate 2px.
- **Banned:** `blur-*`, `backdrop-blur`, glow shadows (`box-shadow: 0 0 …`, `text-shadow: 0 0 …`), glassmorphism, gradients (except inside sunset artwork and the title-bar gradient), `opacity` fades used for decoration, parallax, cursor effects, page-load animations.
- One texture per page max: the Bayer dither, `.scanlines`, or the sunset disc.

## Components (use these classes; don't rebuild them from utilities)

**Window**: the only content container.
```html
<section class="window" aria-labelledby="memo-title">
  <div class="window-bar"><span id="memo-title">MEMO.TXT</span><span class="controls" aria-hidden="true"></span></div>
  <div class="window-body">…</div>
</section>
```
Variant `window window-crt` = terminal readout (phosphor text on crt). Don't nest windows more than one level.

**Buttons**: `<a class="btn btn-primary">&gt; VIEW RÉSUMÉ</a>` (one per screen) · `<a class="btn btn-secondary">PROJECTS</a>`. Labels are uppercase or `>`-prefixed.

**Ticker**: `<div class="ticker">LABEL 123 <span class="up">▲1.2%</span> | …</div>`. Only real numbers from `docs/CONTENT_FACTS.md`. Static unless asked; any motion respects `prefers-reduced-motion`.

**Tag**: `<span class="tag">SERVICENOW</span>`.

**Nav**: `surface-raised` bar, 2px `ink` bottom border, `font-pixel` links, active page gets `bg-sunset-pink text-on-accent`. Mobile: simple toggle, no slide-out drawers with blur.

**Footer**: `bg-dusk-violet text-on-violet`, `font-pixel` small text.

## Voice in UI copy

Calm, slightly wry, nostalgic. Short sentences. Light retro-computer framing in labels only (`> LOADING…`, `[ OK ]`, `SYSTEM READY`). Never in résumé facts.
Avoid meme speak ("stonks", "to the moon"), full-width ａｅｓｔｈｅｔｉｃ text, emoji, fake Japanese, and buzzword stacks ("enterprise-grade fault-tolerant mission-critical").

## Imagery

Original flat PC-98 pixel art or dithered illustration. Never use Hypnospace Outlaw assets, real game screenshots, or copyrighted characters. Until art exists, use placeholders per `assets.md`.
