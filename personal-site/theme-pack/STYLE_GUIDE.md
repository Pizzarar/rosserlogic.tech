# Hypnospace / VIBE OS

A website theme packet for a Hypnospace Outlaw / Windows 95 "VIBE OS" desktop look — pixel windows with pastel
title bars, hard Win95 bevels, Bayer-dithered panels, and a calm synthwave sky. This is the single source of
truth: hand it (or the paste-ready brief below) to any AI builder, designer or image generator so every page
stays on-theme.

Built for a personal site (job networking + personal work + the Idle Minds studio and Escape From Idle),
hand-coded in HTML5 + Tailwind v4. Other sections: **Build** (stack, Tailwind theme, hosting), **Asset
pipeline** (placeholders → artist → swap), **Site plan** (pages and audiences).

> Industry names for this kind of document: **brand style guide**, **design system**, or, in game studios, an
> **art bible**. Same job: lock the palette, type, shapes, imagery and voice so nobody (human or AI) drifts.

## 1. Decode the reference

"Hypnospace / VIBE OS" is a specific slice of the retro-computer aesthetic. Name the slice precisely — vague
prompts produce generic "retro website" output.

| Ingredient | What it means visually | Prompt keywords that work |
|---|---|---|
| **Hypnospace desktop** | A fake operating system: windows, title bars, bevels, taskbars, dithering, square UI, hard shadows | `Hypnospace Outlaw style`, `fake OS`, `desktop window UI` |
| **Windows 95 chrome** | 1px inset bevel highlights/shadows, pastel gradient title bars, hard 2px offset shadows | `Win95 bevel`, `retro window chrome`, `title bar gradient` |
| **PC-98 pixel art** | Low-res pixel art, limited palettes, dithering, hard edges, square windows | `PC-98 style`, `16-color pixel art`, `dithered` |
| **Synthwave sky** | Violet → pink → coral → amber sky ramps, pastel-and-hot-pink, sky-CRTs in the clouds | `synthwave sky`, `vaporwave sunset`, `neon dusk` |
| **Bayer dither** | 4x4 ordered-dither texture overlay, faint, crisp | `Bayer matrix`, `ordered dither`, `pixelated texture` |

**Positioning in one line:** *A calm Hypnospace desktop at dusk — pastel gradient title bars, pixel windows,
dithered panels, and a violet-to-pink synthwave sky.*

## 2. Visual foundations

### Color
Two themes, same roles (P0 palette: `Midnight Mall` dark + `Pastel Morning` light). **Night (dark)** is the hero
theme — a dark mall at dusk. **Day (light)** is a softened mauve for long reading.

- `surface` is the page; `surface-raised` is window/panel bodies; `panel-hi` is raised rows and the panel-gradient end;
  `crt` is the dark terminal/ticker panel in **both** themes.
- `ink` for all body text and the 2px window borders; `ink-muted` for captions and metadata.
- `sunset-pink` is the brand color: primary buttons, needs-you badges, the one thing per screen that should be
  clicked. Never body text in Day.
- `sunset-orange` (amber) is the warm accent: the sun motif, highlights, waiting states.
- `dusk-violet` is the deep accent: section bands, footers, and the first stop of the title bar.
- `cel-teal` is the cool accent: links in Night, tags, secondary badges. Use it at most once per section.
- `phosphor` (mint) is CRT text, **only** on `crt` panels (tickers, "terminal" readouts).
- `gain` / `loss` (mint / coral or red) are for numbers that go up/down, always with ▲ / ▼.
- `line` is the divider/border colour (slot 03); the hard 2px outlines use `ink`.
- Title bars use the pastel gradient `violet → pink → skin` with `on-pastel` text; panels use a subtle vertical
  `panel-grad` and a faint Bayer dither.
- Ratio rule: ~70% surfaces, ~20% ink, ~10% accents. Never more than two accent colors in one block.

### Type
- **Display — Pixelify Sans (500, 700):** chunky pixel-display face. Headlines and title cards only, 28px+.
- **Body — JetBrains Mono (400, 700):** a coding mono that reads well as prose. All paragraphs and UI.
- **Pixel — Silkscreen (400):** bitmap-style face for data: prices, tickers, timestamps, labels, small badges.
  Never for paragraphs.
- All three are free Google Fonts, loaded with one `<link>` in the `<head>`.

### Shape & layout
- **Square corners everywhere** (`radius-none`; `radius-sm` 2px max for small chips). PC-98 UI had no rounded corners.
- **Window panels:** content sits in boxes with a 2px `ink` border, a pastel gradient title bar, a 1px Win95 bevel
  (inset highlight + shadow), and a hard offset shadow (`shadow-window`: ink in Night, softened ink in Day) — no blur.
- Spacing on an 8px grid (`space-1` … `space-6`).
- One texture allowed per page: the Bayer dither, a scanline strip, or the striped sunset disc. Not all three.

### Imagery
- **Illustration > photography.** If photos are needed, treat them: posterize, add a duotone in `dusk-violet` +
  `sunset-pink`, add light grain.
- Subjects: a Hypnospace desktop at dusk, office desks with beige PCs, CRT monitors, sky-CRTs in the clouds,
  synthwave skylines, a single PC-98 caricature protagonist.
- Style: flat cel shading, one hard shadow, limited P0 palette, slight grain. Pixel-art versions for small spots
  (icons, headers, cast portraits).
- **Do not use** screenshots or art from Hypnospace Outlaw or any real game — that's someone else's copyrighted
  work. Generate or commission original art in this style.

## 3. Voice & copy
- Calm, slightly wry, nostalgic. Think "late-night mall security guard narrating a desktop OS."
- Short sentences. Occasional retro-computer framing: `> LOADING…`, `[ OK ]`, `SYSTEM READY`.
- Avoid: meme-speak, overused vaporwave text (`Ａｅｓｔｈｅｔｉｃ` full-width text), fake Japanese.

## 4. Guardrails for AI tools

**Always**
- Square corners, hard offset shadows, Win95 bevels, window-panel framing.
- Night theme as default hero; Day theme for long reading.
- Pixel font only for data/labels.
- Original illustration in the Hypnospace / PC-98 style.

**Never**
- Rounded "SaaS" cards, soft blurred shadows, glassmorphism.
- Neon glow (`box-shadow: 0 0 …`, `text-shadow: 0 0 …`) — crisp hard pixel lines/shadows only.
- Blue-purple tech gradients outside the sky ramp, stock-photo people, emoji.
- Generic "anime" (modern moe style, 2010s+ digital anime look).
- Copyrighted characters, logos, or game assets.
- More than two accent colors in one section.

## 5. Paste-ready brief (for any AI builder or image tool)

```
STYLE BRIEF — "Hypnospace / VIBE OS"
Aesthetic: Hypnospace Outlaw / Windows 95 fake desktop meets PC-98 pixel art and a synthwave dusk sky; calm, slightly wry.
Colors (dark "Midnight Mall"): background #140C26, panels #21163D, raised #33255C, text #F7F0FF, muted #B5A5D8,
brand hot pink #FF68A8, amber #FFC46C, violet #9B72E8, teal #4FD6CF, mint #79DFA8, coral #FF8E78, ink #07040F.
Colors (light "Pastel Morning"): background #E0D1DC, panels #EBE0E8, raised #D6C2D0, text #2B1840, muted #574268,
pink #A8236A, amber #F7BF5C, violet #5D40B5, teal #1D5F61, mint #2E9462, shadow rgba(43,24,64,0.38).
Fonts: Pixelify Sans (headlines), JetBrains Mono (body), Silkscreen (numbers, labels).
Layout: square corners only; content in bordered "window" panels with a pastel violet->pink->peach gradient title
bar, a 1px Win95 bevel and a hard 4px offset shadow (no blur); faint Bayer dither on panels; 8px spacing grid.
Imagery: original flat PC-98 pixel art or dithered illustration — Hypnospace desktop at dusk, sky-CRTs, synthwave
skyline. No photos unless duotoned violet+pink with grain.
Avoid: rounded cards, blurred/glow shadows, gradients outside the sky ramp, emoji, real game characters or logos.
```

For image generators, append the subject, e.g.: `…, a PC-98 caricature bust in a desktop window at dusk, 16-color
dithered pixel art, limited palette, hard shadow`.

---

## 6. Pixel art (common gotcha)

Pixel art must be drawn small and scaled up by **whole numbers** (×2, ×3, ×4). Scaling by ×2.5 makes uneven,
smeared pixels.

- Artist delivers at native size (e.g. 480×270 for a 16:9 scene, 16×16 for icons) as **PNG only**. JPEG/WebP-lossy wrecks pixel edges.
- Site displays it in a fixed-size box at an integer multiple, with:
  ```css
  .pixelated { image-rendering: pixelated; }
  ```
- In `ASSETS.md`, Type = `pixel`, and "Shown at" must be an exact multiple of "Deliver at".
