# Bubble Era Anime

A website theme packet for an early-90s anime / Japanese bubble-era look — the vibe of STONKS-9800, city pop record sleeves and PC-98 computer screens. This is the single source of truth: hand it (or the paste-ready brief below) to any AI builder, designer or image generator so every page stays on-theme.

Built for a personal site (job networking + personal work + the Idle Minds studio and Escape From Idle), hand-coded in HTML5 + Tailwind v4 by Gemini in Antigravity. Other sections: **Build** (stack, Tailwind theme, hosting), **Asset pipeline** (placeholders → artist → swap), **Site plan** (pages and audiences).

> Industry names for this kind of document: **brand style guide**, **design system**, or, in game studios, an **art bible**. Same job: lock the palette, type, shapes, imagery and voice so nobody (human or AI) drifts.

## 1. Decode the reference

"Early 90s anime" is broad; STONKS-9800 is a specific slice of it. Name the slice precisely — vague prompts produce generic "anime website" output.

| Ingredient | What it means visually | Prompt keywords that work |
|---|---|---|
| **PC-98 aesthetic** (the "9800" in the title is a nod to NEC's PC-9801 line) | Low-res pixel art, limited palettes, dithering, square UI windows with title bars, hard edges | `PC-98 style`, `16-color pixel art`, `dithered`, `retro Japanese computer UI` |
| **City pop** | Sunset gradients, neon on night skylines, pastel-and-hot-pink, sleeve-art illustration | `city pop album cover`, `1980s Tokyo night`, `neon sunset` |
| **Bubble-era Japan (1986–1991)** | Salarymen, stock tickers, pachinko, sports cars, skyscrapers, money excess | `Japanese bubble economy`, `Showa era office`, `Tokyo 1989` |
| **Early-90s cel anime** | Hand-painted cels, flat shading with one hard shadow, film grain, big expressive eyes, VHS softness | `90s cel-shaded anime`, `hand-painted cel`, `VHS film grain` |
| **Vaporwave** (overlay, use lightly) | Retro-computer chrome, pastel glitches | `vaporwave` — **use sparingly**; it pulls toward meme aesthetics fast |

**Positioning in one line:** *A calm, nostalgic 1989 Tokyo office screen at sunset — pixel windows, city pop colors, cel-anime illustration.*

## 2. Visual foundations

### Color
Two themes, same roles. **Night (dark)** is the hero theme — PC-98 screens and city pop skylines both live at night. **Day (light)** is the cream-paper variant for readable content pages.

- `surface` is the page; `surface-raised` is window/panel bodies; `crt` is the dark terminal/ticker panel in **both** themes.
- `ink` for all body text; `ink-muted` for captions and metadata.
- `sunset-pink` is the brand color: primary buttons, the active tab, the one thing per screen that should be clicked. Never body text in Day (fails contrast, 3.1:1).
- `sunset-orange` is the warm accent: highlights, the sun motif, hover states.
- `dusk-violet` is the deep accent: section bands, title bars, footers.
- `cel-teal` is the cool accent: links in Night, tags, secondary badges. Use it at most once per section.
- `phosphor` is green CRT text, **only** on `crt` panels (tickers, "terminal" readouts).
- `gain` / `loss` are for numbers that go up/down. Western convention (green up, red down) — note that Japanese markets traditionally show *red* for rising prices; pick one and stay consistent. On `crt` panels use `crt-gain` / `crt-loss` instead.
- Ratio rule: ~70% surfaces, ~20% ink, ~10% accents. Never more than two accent colors in one block.

### Type
- **Display — Dela Gothic One:** heavy, Japanese-gothic poster face. Headlines and title cards only, 28px+.
- **Body — M PLUS 1p:** clean Japanese-designed sans with excellent Latin. All paragraphs and UI.
- **Pixel — DotGothic16:** bitmap-style font for data: prices, tickers, timestamps, labels, small badges. Never for paragraphs.
- All three are free Google Fonts, loaded with one `<link>` in each page's `<head>`.
- Optional flourish: a small Japanese subtitle under major headings (e.g. `市場` "market", `お知らせ` "news"). Only if you can verify the translation — wrong Japanese is worse than none.

### Shape & layout
- **Square corners everywhere** (`radius-none`; `radius-sm` 2px max for small chips). PC-98 UI had no rounded corners.
- **Window panels:** content sits in boxes with a 2px `ink` border, a `dusk-violet` title bar, and a hard offset shadow (`shadow-window`: violet in Night, ink in Day) — no blur.
- Spacing on an 8px grid (`space-1` … `space-6`).
- One accent pattern allowed per page: scanlines, a dither band, or the striped sunset disc. Not all three.

### Imagery
- **Illustration > photography.** If photos are needed, treat them: posterize, add a duotone in `dusk-violet` + `sunset-pink`, add light grain.
- Subjects: Tokyo skyline at dusk, office desks with beige PCs, CRT monitors, stock boards, trains, convertibles, rain on neon, a single anime-style protagonist.
- Style: flat cel shading, one hard shadow, limited palette, slight grain. Pixel-art versions for small spots (icons, headers).
- **Do not use** screenshots or art from STONKS-9800 or any real anime — that's someone else's copyrighted work. Generate or commission original art in this style.

## 3. Voice & copy
- Calm, slightly wry, nostalgic. Think "late-night city pop radio DJ who also reads the Nikkei."
- Short sentences. Occasional retro-computer framing: `> LOADING…`, `[ OK ]`, `SYSTEM READY`.
- Avoid: meme-speak ("stonks", "to the moon"), overused vaporwave text (`Ａｅｓｔｈｅｔｉｃ` full-width text), fake Japanese.

## 4. Guardrails for AI tools

**Always**
- Square corners, hard shadows, window-panel framing.
- Night theme as default hero; Day theme for long reading.
- Pixel font only for data/labels.
- Original illustration in 90s cel / PC-98 style.

**Never**
- Rounded "SaaS" cards, soft blurred shadows, glassmorphism.
- Blue-purple tech gradients, stock-photo people, emoji.
- Generic "anime" (modern moe style, 2010s+ digital anime look).
- Copyrighted characters, logos, or game assets.
- More than two accent colors in one section.

## 5. Paste-ready brief (for any AI builder or image tool)

```
STYLE BRIEF — "Bubble Era Anime"
Aesthetic: early-1990s Japanese anime meets PC-98 computer UI and city pop album art; 1989 Tokyo bubble-economy mood; calm, nostalgic, slightly wry.
Colors (dark/hero): background #12112A, panels #1E1C40, text #F3ECDF, muted #B8B2D6, brand hot pink #FF6FA5, orange #FFA552, violet #9A7BFF, teal #45D6CF, CRT green #7CFF9B.
Colors (light): background #F4EEE2, panels #E8DFCC, text #1B1A33, muted #4E4A6B, pink #E8508A, orange #F28C38, violet #5B3F9E, teal #2FB5B0.
Fonts: Dela Gothic One (headlines), M PLUS 1p (body), DotGothic16 (numbers, labels).
Layout: square corners only; content in bordered "window" panels with a violet title bar and a hard 4px offset shadow (no blur); 8px spacing grid.
Imagery: original flat cel-shaded 90s anime illustration or 16-color dithered pixel art — Tokyo skyline at sunset, beige office PCs, CRT monitors, stock boards. No photos unless duotoned violet+pink with grain.
Avoid: rounded cards, blurred shadows, gradients outside sunset art, emoji, modern anime style, real anime/game characters or logos.
```

For image generators, append the subject, e.g.: `…, a salaryman at a beige PC-98 computer watching a stock chart, Tokyo skyline at sunset through the window, 90s cel anime, limited palette, film grain`.


---

## 4. Pixel art (common gotcha)

Pixel art must be drawn small and scaled up by **whole numbers** (×2, ×3, ×4). Scaling by ×2.5 makes uneven, smeared pixels.

- Artist delivers at native size (e.g. 480×270 for a 16:9 scene, 16×16 for icons) as **PNG only**. JPEG/WebP-lossy wrecks pixel edges.
- Site displays it in a fixed-size box at an integer multiple, with:
  ```css
  .pixelated { image-rendering: pixelated; }
  ```
- In `ASSETS.md`, Type = `pixel`, and "Shown at" must be an exact multiple of "Deliver at".

