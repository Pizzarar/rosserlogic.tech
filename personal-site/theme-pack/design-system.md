---
trigger: always_on
---

# Design system: Bubble Era Anime

Full rationale: `docs/STYLE_GUIDE.md`. Values: `docs/design-tokens.json` (mirrored in `src/theme.css`). This file holds what you need while writing markup.

## Themes

- **Night** (default, `data-theme="night"`): hero theme for most pages.
- **Day** (`data-theme="day"`): cream paper, for long reading and the résumé. Can go on `<html>` or on a single `<section>`; utilities recolor automatically.
- Never use Tailwind's `dark:` variant. Theming is `data-theme` only.

## Color utilities (the ONLY colors that exist)

`bg-`, `text-`, `border-` + one of:

| Token | Role |
|---|---|
| `surface` | Page background |
| `surface-raised` | Window bodies, cards, inputs |
| `crt` | Dark terminal panel (both themes). Only place `phosphor` text appears. |
| `ink` / `line` | Body text / 2px borders |
| `ink-muted` | Captions, dates, metadata |
| `sunset-pink` | Brand: primary button, active nav, ONE call to action per screen. In Day: fills only, never text. |
| `sunset-orange` | Warm accent: highlights, sun motif, hover |
| `dusk-violet` | Title bars, section bands, footer |
| `cel-teal` | Tags, secondary badges, Night links. Max once per section. |
| `on-accent` | Text on pink / orange / teal fills |
| `on-violet` | Text on dusk-violet |
| `phosphor` | Green CRT text, on `crt` only |
| `gain` / `loss` | Up / down numbers, always with ▲ / ▼ |
| `crt-gain` / `crt-loss` | Same, on `crt` panels |

Tailwind's default palette is removed. `bg-blue-500`, `text-slate-300`, `bg-white`, `bg-[#070a12]` and other arbitrary hex values are **banned**. If a needed color is missing, ask; don't invent one.

Ratio per screen: ~70% surfaces, ~20% ink, ~10% accents. Max two accent colors in one section.

## Type

| Class | Font | Use |
|---|---|---|
| `font-display` | Dela Gothic One | h1/h2, title cards. 28px (`text-[28px]`/`text-3xl`) minimum. |
| `font-sans` | M PLUS 1p | Default. All paragraphs and UI. |
| `font-pixel` | DotGothic16 | Numbers, prices, dates, labels, buttons, badges, window titles. Never paragraphs. |

Scale: title-card 64px/0.95 · h1 40px · h2 28px · lead 20px/30px · body 16px/26px · small 14px/22px · ticker 18px · label 14px +0.06em tracking.

Optional small Japanese subtitle under major headings **only** if the translation is supplied in `docs/CONTENT_FACTS.md`. Never machine-guess Japanese.

## Shape, spacing, depth

- Square corners. `rounded-sm` (2px) is the max and only for tiny chips. No `rounded-full` except circular avatars.
- Spacing on the 8px grid: prefer `1 2 4 6 10 16` (4/8/16/24/40/64px).
- Depth = `shadow-window` (hard offset, no blur). Hover/press = `shadow-pressed` + translate 2px.
- **Banned:** `blur-*`, `backdrop-blur`, glow shadows, glassmorphism, gradients (except inside sunset artwork), `opacity` fades used for decoration, parallax, cursor effects, page-load animations.
- One texture per page max: `.scanlines` OR a dither band OR the sunset disc.

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

**Nav**: `surface-raised` bar, 2px `line` bottom border, `font-pixel` links, active page gets `bg-sunset-pink text-on-accent`. Mobile: simple toggle, no slide-out drawers with blur.

**Footer**: `bg-dusk-violet text-on-violet`, `font-pixel` small text.

## Voice in UI copy

Calm, slightly wry, nostalgic. Short sentences. Light retro-computer framing in labels only (`> LOADING…`, `[ OK ]`, `SYSTEM READY`). Never in résumé facts.
Avoid meme speak ("stonks", "to the moon"), full-width ａｅｓｔｈｅｔｉｃ text, emoji, fake Japanese, and buzzword stacks ("enterprise-grade fault-tolerant mission-critical").

## Imagery

Original flat cel-shaded 90s anime illustration or 16-color dithered pixel art. Never use STONKS-9800 assets, real anime screenshots, or copyrighted characters. Until art exists, use placeholders per `assets.md`.
