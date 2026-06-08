# Gemini — Prompts for the Character Sheet Carousel

Switching from Claude Design (vector HTML/CSS/SVG, wrong tool for pixel art) to Google's image-gen stack, which actually rasters pixels and accepts your existing PNGs as inputs to embed AS-IS.

---

## Decision: which model, which surface, which workflow

**Use Nano Banana Pro (Gemini 3 Pro Image), not 2.5 Flash Image.**
- Nano Banana Pro: ~94% text-rendering accuracy, native 4K output, best cross-edit coherence. Text accuracy is the make-or-break here — a stat line that misrenders "+9 Crowd Control" as "+9 Croud Conrtol" is a slide you throw away.
- Gemini 2.5 Flash Image (original Nano Banana): cheaper and faster, capped at 3 input images, weaker on small text. Use as the fallback only if Pro is rate-limited or gated.

**Use Google AI Studio (`aistudio.google.com`), not the consumer Gemini app or Vertex.**
- AI Studio: free-tier Pro access, multi-image attach via UI, persistent prompt history, can rerun a prompt with one input swapped (huge for slides 2–10). Web UI, no SDK setup.
- Gemini consumer app: works but no easy way to keep a stable system prompt while swapping item images per slide.
- Vertex AI / API: only worth it if you script a batch run; for ten one-off slides AI Studio is faster.

**Run the HYBRID workflow, not the pure-generation workflow.**
- Why: Even Nano Banana Pro at 94% text accuracy will mangle ~6% of small text (stat labels, rarity tags, BPM numerals). Across ten slides with ~30 text fragments each, you'll hit visible errors. And cross-slide chrome consistency drifts even with a style-anchor image attached — bevel widths, divider segment counts, frame ornament density wander between generations.
- The fix: generate ONE empty template slide in Gemini (frame + banner zone + portrait/item slot + divider + stats-row template + footer zone — all pixel-rendered, no text). Then composite portrait/item PNGs and all text in Figma (or Photopea / Affinity / Pixelmator Pro), one frame, ten layered comps. Pixel-art assets stay untouched (non-negotiable #1). Chrome is byte-identical across all ten slides (non-negotiable #2). Text is correct because you typed it in a vector editor, not asked an image model to render it.
- Pure-generation path is documented as Section C in case you'd rather try it first; switch to hybrid the moment the second slide drifts.

The two non-negotiables (pixel-art preservation, cross-slide consistency) are baked into every prompt below as explicit clauses.

---

## Section A — Hero slide prompt (HYBRID-PRIMARY)

This generates slide 1 as the master template AND the visual exemplar for slides 2–10. Run this first. Keep iterating until it's right — every fix here saves work later.

### Attach checklist (in this order, with these labels)
1. `reference/maplestory-reference.jpeg` — label: **AESTHETIC LOCK A — match this rendering language, frame chunkiness, and palette family**
2. `reference/octopath-reference.jpeg` — label: **AESTHETIC LOCK B — match this character-screen layout pattern and HD-2D atmospheric warmth**
3. `assets/portrait.png` — label: **HERO ART — preserve EXACTLY, embed as-is, do not redraw**

(Three input images is the safe limit for any Gemini image model. Do not attach `reference/style-exemplar.png` — that was the previous off-target output, and including it invites the same drift.)

### Paste this prompt

```
I'm building a 10-slide LinkedIn document carousel — a "character sheet"
presenting me as an RPG profile. This is slide 1 of 10, the hero / profile
page. The visual system you commit to here is reused across the other 9
slides, so build a system that scales: a chunky pixel-rendered frame with
a clear title-banner zone, a clear art-slot zone, a horizontal pixel
divider, a stats zone, and a footer zone for a quote line. Slides 2–10
will reuse this exact frame with an item-art PNG in the art slot and
different text per slide.

═══════════════════════════════════════════════════════════════════════
THE AESTHETIC LANE — LOCKED, NARROW
═══════════════════════════════════════════════════════════════════════

Classic 2D RPG / MMORPG character screen, in the language of MapleStory
and Octopath Traveler — see the two attached reference screenshots. They
are aesthetic LOCKS, not vibe suggestions.

- Era reference: late-90s through HD-2D — MapleStory, Octopath Traveler,
  Stardew Valley, Disgaea, classic SNES/PSX JRPG menus (Final Fantasy VI,
  Chrono Trigger). NOT 8-bit arcade. NOT modern game UI. NOT illuminated
  manuscript / book design.

- Rendering: chunky pixel-art GUI. Frames, banners, dividers, icons, and
  stat-bar segments are PIXEL-RENDERED with hard edges and visible pixel
  chunks at 1200×1500. No vector hairlines. No anti-aliased rounded
  corners on UI elements. The attached portrait's pixel grid sets the
  rendering scale — UI chrome must match it, not float above it as clean
  vector.

- Frame: chunky pixel panel border with depth — outer dark line plus
  inner highlight line, suggesting carved wood / parchment / forged
  metal. Nested mini-panels are encouraged (see MapleStory reference for
  the panel-within-panel treatment and bevel feel).

- Palette: warm classic-RPG. Cream / parchment / aged-paper base, warm
  browns, with a limited accent palette (forest green, ocean blue, gold,
  oxblood / warm orange for emphasis). Atmospheric, not flat. NO neon.
  NO synthwave magenta or cyan. NO modern dark-navy card UI.

- Typography: pixel-bitmap or pixel-friendly typefaces. Small-caps pixel
  sans for labels and body, chunky pixel display for the title banner.
  Octopath-style refined pixel typography is acceptable for the title
  only if it reads pixel-rendered. NO Cinzel. NO modern serif. NO
  hairline. NO Press Start 2P (reads as 8-bit arcade, wrong era). NO
  modern sans like Inter or Pixelify Sans.

- Stat viz: chunky 10-segment pixel bars, MapleStory style. Each segment
  visibly pixel-chunky, warm RPG palette, not neon.

═══════════════════════════════════════════════════════════════════════
HARD EXCLUSIONS — directions to avoid (prior failed rounds)
═══════════════════════════════════════════════════════════════════════

- Illuminated-manuscript book design with Cinzel serif, fleurons,
  hairline rules, Roman numerals. Wrong era, wrong rendering language.
- Neon synthwave / arcade CRT — magenta/cyan, scanlines, "PLAYER 1
  SELECT" chrome. Wrong palette, wrong era.
- Modern dark-navy card UI — vector rounded panels, Inter-ish
  typography, gold accents. Wrong rendering language entirely.

═══════════════════════════════════════════════════════════════════════
TWO HARD REQUIREMENTS
═══════════════════════════════════════════════════════════════════════

1. PORTRAIT PRESERVATION — The attached HERO ART (portrait.png) is
   pixel-art. Embed it AS-IS into the framed art slot. Do not restyle,
   smooth, anti-alias, redraw, upscale, or "improve" it. Treat it as a
   placed sticker. Generate the frame and chrome AROUND it. The portrait's
   pixel grid is sacred and sets the chunkiness scale for all UI chrome.

2. SYSTEM REUSABILITY — This frame will be reused for 9 more slides with
   different item art and different text in the same zones. Design clean
   slot boundaries — art slot, title banner, rarity-tag line, quote line,
   stats block, footer/description block — so an item PNG and new text
   can drop into the same frame without breaking. Do not paint art into
   the frame edges.

═══════════════════════════════════════════════════════════════════════
OUTPUT SPEC
═══════════════════════════════════════════════════════════════════════
- Aspect ratio: 4:5 portrait, 1200 × 1500 px (LinkedIn document carousel)
- Do not change the input aspect ratio while editing
- Single image, no caption, no watermark

═══════════════════════════════════════════════════════════════════════
HERO SLIDE LAYOUT (slide 1 of 10)
═══════════════════════════════════════════════════════════════════════

Top to bottom:

1. Chunky pixel frame around the entire 4:5 canvas (carved-wood / forged-
   metal / parchment-bevel feel — pick one and stay with it).

2. Title banner zone at top. Render this exact text inside it, pixel-
   rendered, two lines, the second line subordinate to the first:
       OGUZ ORAL
       LV. 30 · PROJECT MANAGER
   The subtitle is neutral brown — NOT a rarity color. Rarity coloring
   becomes meaningful on slides 2–10, not here.

3. Portrait art slot — HERO ART rendered AS-IS inside a chunky pixel
   sub-frame. Centered horizontally.

4. Stats grid — six rows, each row: [pixel-bitmap label] · [10-segment
   chunky pixel bar] · [pixel-bitmap numeric value]. Render exactly:
       STR  ██████░░░░  68
       DEX  ███████░░░  78
       INT  ████████░░  82
       WIS  ███████░░░  74
       CHA  ███████░░░  77
       LUK  ██████░░░░  63
   Bar fill = floor(value / 10). Filled segments warm-amber/gold. Empty
   segments dark-brown well/parchment.

5. Chunky pixel-rendered horizontal divider (this exact divider will
   recur on slides 2–10).

6. Footer zone with italic quote line in quote marks, exact text:
       "Side-quests > main story."
   Dark-brown, pixel-italic, small.

NO description block on this slide. The slide ends on the quote.

═══════════════════════════════════════════════════════════════════════
DELIVERABLES
═══════════════════════════════════════════════════════════════════════

Generate the slide. If you offer variants, all must stay inside the
locked aesthetic lane above (warm classic 2D pixel-RPG character screen,
MapleStory / Octopath family). Do not return modern card UI, illuminated
manuscript, or arcade CRT directions — those have been tried and rejected.
```

### After you have a good slide 1
- **Save it** as `slides/slide-01-hero.png`. Keep it in AI Studio's history too — you'll attach it to every subsequent prompt as the style anchor.
- **Hybrid path users**: also ask Gemini to regenerate the same slide WITHOUT the portrait, WITHOUT any text, WITHOUT the stat-bar fills — just the empty frame, banner zone, sub-frame for art, divider, six empty stat rows, and footer zone. Save as `slides/template-empty.png`. This is your master template for compositing slides 2–10 in Figma. (See Section D for the empty-template prompt.)

---

## Section B — Per-slide prompt (slides 2–10), pure-generation path

Use this only if you're committing to the pure-Gemini path (Section C below explains the tradeoff). Otherwise skip to Section D for the hybrid workflow.

### Attach checklist (per slide)
1. `slides/slide-01-hero.png` — label: **STYLE ANCHOR — match this exact frame, palette, typography, divider, layout rhythm**
2. The slide's item PNG from `assets/` (e.g. `assets/01-cdj.png` for slide 2) — label: **ITEM ART — preserve EXACTLY, embed as-is in the art slot, do not redraw**

(Two input images, well within the 3-image cap.)

### Paste this template, filling the bracketed fields from CONTENT.md

```
Next slide in the same 10-slide character-sheet carousel. Reuse the
EXACT visual system from the attached STYLE ANCHOR (slide 1) — same
frame, same palette, same typography, same divider, same layout rhythm,
same pixel chunkiness. Do not redesign. Do not drift the bevel, the
divider segment count, the corner ornament, or the palette.

The attached ITEM ART is pixel-art. Embed it AS-IS in the art slot at
the top of the frame. Do not redraw, restyle, smooth, anti-alias, or
upscale it. Treat as a placed sticker. Generate the frame and chrome
around it.

Output: 4:5 portrait, 1200 × 1500 px. Do not change the aspect ratio.

═══════════════════════════════════════════════════════════════════════
SLIDE [N] — [SLIDE NAME]
═══════════════════════════════════════════════════════════════════════

Title banner (chunky pixel display, top-aligned in banner zone):
  [TITLE]

Rarity / type line (small pixel-bitmap, immediately under banner):
  [RARITY · TYPE · etc — color the rarity word per the key below]

Item art slot:
  [ITEM ART rendered as-is from the attachment]

Italic quote line, in quote marks (dark brown, pixel-italic):
  "[quote]"

Stats block (pixel-bitmap, amber values, brown labels — same numeric
typography and bar treatment as slide 1):
  [stat line 1]
  [stat line 2]
  [stat line 3]
  ...

Favorites block (same styling as Stats — OMIT THIS WHOLE BLOCK if not
listed in the slide content below):
  [favorites line 1]
  [favorites line 2]

Pixel divider (same as slide 1).

Description block (pixel-bitmap, em-dash prefix, NOT in quote marks,
1–2 lines):
  — [description]

═══════════════════════════════════════════════════════════════════════
RARITY COLOR KEY (for the rarity word in the rarity line)
═══════════════════════════════════════════════════════════════════════
  LEGENDARY  — warm orange / oxblood
  EPIC       — royal purple, muted
  RARE       — ocean blue
  UNCOMMON   — forest green
  COMMON     — neutral brown (no slide uses this)
```

For **slide 7 (LANGUAGE TOME)** which has no description block, drop the entire Description block from the template before sending.

### Per-slide content (paste verbatim from CONTENT.md, slot into the template above)

Slide 2 — DJ CONTROLLER · attach `assets/01-cdj.png`
Slide 3 — COFFEE DRIPPER · attach `assets/02-v60.png`
Slide 4 — MTG TOME · attach `assets/03-mtg-tome.png`
Slide 5 — COMPUTER · attach `assets/04-computer.png`
Slide 6 — 3D PRINTER · attach `assets/05-printer.png`
Slide 7 — LANGUAGE TOME · attach `assets/06-language.png` (no description)
Slide 8 — CONTROLLER · attach `assets/07-controller.png`
Slide 9 — MALTIPOO · attach `assets/08-maltipoo.png`
Slide 10 — WATCH · attach `assets/09-watch.png`

(Open `CONTENT.md`, copy the slide's content block, replace the bracketed fields in the prompt above. One message per slide.)

---

## Section C — Pure-generation tradeoff (read before choosing)

The pure-Gemini path (Sections A + B as written) generates each finished slide complete with item, text, stats. Tradeoffs:

**Risks**
- Text errors. Even Nano Banana Pro at ~94% text accuracy will misrender characters across ten slides × ~30 text fragments each = expect 5–15 visible errors total. Each error = a regenerate.
- Chrome drift. Style-anchor attachment helps but doesn't fully pin: bevel thickness, divider pixel count, frame ornament density wander 5–10% between generations. Side-by-side on LinkedIn, that drift reads as "ten different slides," not "one carousel."
- Aspect-ratio adherence. Most generations land at 4:5 when asked, but ~10% of the time you get 1:1 or a near-miss; you'll re-roll those.
- Quota burn. You'll spend more tries than expected.

**When pure-generation is fine**
- If you only need 2–3 slides.
- If you're OK with the "handmade artisan variation" reading on chrome.
- If you don't mind regenerating 1-in-10 for text errors.

**Why hybrid (Section D) is recommended for ten slides**
- Pixel-perfect chrome consistency across all ten (literally the same PNG pixels).
- Zero text errors (you type the text in Figma).
- Pixel-art assets fully untouched.
- One Gemini generation (the empty template), nine Figma duplicates with swapped layers.

---

## Section D — Hybrid workflow (recommended primary path)

### D1. Generate the empty master template in Gemini

After Section A's hero slide is dialed in, send this follow-up to Gemini in the same chat (Gemini 2.5 Flash Image and Pro both retain context within a session):

#### Attach checklist
1. `slides/slide-01-hero.png` — label: **REFERENCE — use the same frame, palette, divider, typography style, but produce the EMPTY version described below**

#### Paste this prompt

```
Now produce the same slide as an EMPTY master template. Same 4:5
portrait 1200×1500 canvas. Same chunky pixel frame, same banner zone,
same sub-frame for art, same divider, same six-row stats zone, same
footer zone. But:

- NO portrait or item art. The art slot is empty (cream/parchment fill,
  same as the slide background).
- NO text in the title banner. The banner zone is rendered (the chunky
  banner ribbon / cartouche) but contains no letters.
- NO text in the rarity/type line. Empty space below the banner.
- NO text in the stats rows. The stat rows show empty 10-segment bars
  (all dark-brown wells, zero amber fill) and no labels or numerals.
- NO quote, NO description text. Footer zone is rendered but empty.

Everything else identical to slide 1: pixel-rendered chrome, exact same
divider, same frame ornament. This is the master template I'll composite
portraits, items, and text into per-slide.

Single image, 4:5, 1200×1500. Do not change the aspect ratio.
```

Save the result as `slides/template-empty.png`.

If Gemini gives you an empty template that doesn't match slide 1's chrome exactly (this is the most likely failure), iterate: ask it to "regenerate using slide 1's exact frame, same divider, same banner shape, just with no text or art inside." Worst case, you can edit slide 1 in Figma directly — paint over the portrait/text zones with the cream background — to manufacture the empty template by hand.

### D2. Composite each slide in Figma (or equivalent)

Tool options in order of suitability:
- **Figma** (free) — vector + raster layer comp, easy duplication, frame-as-component pattern.
- **Photopea** (free, browser) — Photoshop clone, good for raster pixel work.
- **Affinity Photo / Pixelmator Pro** — paid, pro raster.

Per-slide steps (Figma):
1. Place `slides/template-empty.png` as the background layer of a new 1200×1500 frame.
2. Drop the slide's pixel-art PNG (`assets/portrait.png` for slide 1, `assets/01-cdj.png` for slide 2, etc.) into the art slot. Use **Image → Resampling: Nearest Neighbor** (Figma: right-click image → Render Settings → Pixelated; in Photopea: Image → Image Size → Resample: Nearest Neighbor) so resizing doesn't anti-alias the pixel art.
3. Type the title, rarity line, quote, stats, favorites, description into the matching zones. Use a real pixel-bitmap font, not a fake-pixel rendering — install one of: **Pixel Operator, Determination Mono, Press Start 2P (avoid for body — it's 8-bit), Munro, m5x7, or VT323**. Pick one body and one display, use them across all ten slides.
4. For stat bars, build a 10-segment bar component once (10 squares, 6 amber, 4 dark-brown). Reuse and adjust amber count per stat. STR=6, DEX=7, INT=8, WIS=7, CHA=7, LUK=6 on the hero; for slides with stats like "+6 Rhythm," you can use the same bar pattern with 6/10 fill or skip bars and use only the text — match what slide 1 established.
5. Color the rarity word per the key: LEGENDARY=warm orange, EPIC=royal purple, RARE=ocean blue, UNCOMMON=forest green.
6. Export: PNG, 1× scale (1200×1500), nearest-neighbor / no smoothing. Save as `slides/slide-NN-name.png`.

### D3. Why hybrid wins on the two non-negotiables

| Requirement | Pure-generation | Hybrid |
|---|---|---|
| Pixel-art preserved AS-IS | Probabilistic (Gemini may resmooth at edges) | Guaranteed (Figma layer is byte-identical to source PNG) |
| Cross-slide chrome consistency | 90–95% similar across slides | 100% identical (same template PNG behind all 10) |
| Text correctness | 94% per fragment, ~15 errors over 10 slides | 100% (you type it) |
| Effort to iterate copy | Re-prompt + re-roll Gemini | Edit text layer in Figma |

---

## Workflow — end to end

1. **Open AI Studio.** `aistudio.google.com`. Sign in. Pick model **Gemini 3 Pro Image** (Nano Banana Pro). If it's not in the dropdown, fall back to **Gemini 2.5 Flash Image**.
2. **Send Section A.** Attach the three files exactly as listed (two references + portrait). Iterate until slide 1 lands. Do not move on with a half-right hero — every issue you fix here saves work on nine more slides.
3. **Save slide 1** as `slides/slide-01-hero.png`.
4. **Send Section D1** in the same AI Studio chat (it retains the slide-1 context). Attach slide 1. Get the empty template back. Save as `slides/template-empty.png`.
5. **Open Figma.** Build a 1200×1500 frame. Place `template-empty.png` as the background. Composite slide 1 (portrait + text) inside it as a sanity check — confirm it visually matches the slide 1 PNG you generated. If it does, your template is good.
6. **Composite slides 2–10** in Figma using D2 steps. One frame per slide, all ten in the same Figma file, all referencing the same template.
7. **Export all ten** as PNGs at 1× into `slides/`.
8. **Assemble PDF.** macOS Preview: select all ten PNGs in slide order in Finder → drag into a new Preview window → File → Export as PDF → name it `character-sheet.pdf`.
9. **Upload to LinkedIn** as a document post.

### If you go pure-generation instead (skip D, do B per-slide)
- Replace step 4–6 with: for each of slides 2–10, send Section B with the slide's content block and the slide's item PNG attached, plus slide 1 as the style anchor. Two attachments per call. Save each result.
- Expect to regenerate 1–2 slides for text errors, 1–2 for chrome drift, 0–1 for aspect-ratio misses.

---

## Limitations and gotchas (verified, April 2026)

- **Multi-image input**: Gemini 2.5 Flash Image accepts up to 3 input images. Pro accepts more but stay at 3 to be safe. Section A uses 3 (two refs + portrait). Section B uses 2 (anchor + item). D1 uses 1 (anchor).
- **Aspect ratio**: 4:5 is supported. State it in prose AND set it via AI Studio's image-config control if available. About 1-in-10 generations still land off-ratio; re-roll.
- **Text rendering at small sizes**: Even Pro's 94% accuracy compounds across ~30 text fragments per slide. This is the strongest argument for the hybrid path.
- **Cross-image consistency drift**: A style-anchor attachment helps but doesn't fully pin chrome. For a 10-slide carousel where viewers swipe through them sequentially, drift is visible. Hybrid eliminates this.
- **Pixel-art preservation**: "preserve exactly," "do not redraw," "embed as-is," "treat as a placed sticker" — repeat these phrases. They demonstrably reduce restyling. They do not eliminate it; expect a 10–20% chance Gemini smooths the portrait edges. Hybrid eliminates this.
- **Watermark**: Gemini-generated images carry an invisible SynthID watermark. No visible watermark by default in AI Studio for personal use. Confirm before posting.
- **Quota**: AI Studio's free tier on Pro is generous but not unlimited. If you exhaust it mid-carousel, fall back to 2.5 Flash Image (same prompts, expect more re-rolls), or to the hybrid path which only needs 1–2 generations total.

---

## File layout you'll end up with

```
character-sheet/
├── CONTENT.md                       (locked, source of truth)
├── CLAUDE-DESIGN-PROMPTS.md         (obsolete, kept for history)
├── GEMINI-PROMPTS.md                (this file)
├── assets/                          (source pixel art, untouched)
│   ├── portrait.png
│   ├── 01-cdj.png … 09-watch.png
├── reference/
│   ├── maplestory-reference.jpeg
│   ├── octopath-reference.jpeg
│   └── style-exemplar.png           (obsolete, do not attach)
├── slides/
│   ├── slide-01-hero.png            (Gemini output, also your style anchor)
│   ├── template-empty.png           (Gemini output, hybrid path)
│   ├── slide-02-cdj.png … slide-10-watch.png  (Figma comps if hybrid; Gemini outputs if pure)
│   └── character-sheet.pdf          (final, ready for LinkedIn)
└── figma/                           (optional, hybrid path only)
    └── character-sheet.fig
```
