# Slide Prompts — Item Cards (Slides 2–10)

Working prompts for the 10-slide character-sheet carousel using Google AI Studio (Gemini 3 Pro Image / Nano Banana Pro).

## How to use this file

For each item slide:

1. Open a **fresh AI Studio chat** at `aistudio.google.com`. Select model **Gemini 3 Pro Image** (Nano Banana Pro). Fall back to **Gemini 2.5 Flash Image** only if Pro is unavailable.
2. **Attach two images** (in this order):
   - `slides/template-item-empty-clean.png` — label: **MASTER TEMPLATE — fill the empty zones with the content below. Do NOT change the frame, corner ornaments, art slot, title ribbon, divider, palette, or pixel chunkiness.**
   - The slide's item PNG from `assets/` (per-slide list below) — label: **TRUE ITEM ART — preserve byte-identical, embed AS-IS on white inside the art slot, do not redraw**
3. **Paste the prompt** for that slide from below.
4. **Sanity-check the output** in this order:
   1. Item preserved (most likely failure point — compare to the source PNG in `assets/`)
   2. Text correct (typos, em-dashes, accents)
   3. Chrome unchanged from the master template
5. **Clean the watermark.** Gemini bakes a small sparkle / diamond glyph into the bottom-right corner. Open the result in Photopea, press `I` (eyedropper) and click on a parchment area, press `B` (brush, ~30px hardness 100%), brush over the watermark. Export as PNG.
6. **Save** as `slides/slide-NN-name.png`.

If a slide goes sideways, **reroll fresh** with the same prompt — don't iterate, fresh attempts usually win.

---

## Slide 2 — DJ CONTROLLER (already done — kept here for reference)

**Status:** ✅ Generated, saved as `slides/slide-02-cdj.png`

**Attach:** MASTER TEMPLATE + `assets/01-cdj.png`

**Paste:**

```
Fill in the attached MASTER TEMPLATE with the content below to produce
slide 2 of a 10-slide character-sheet carousel. The MASTER TEMPLATE
defines the entire visual system — frame, corner ornaments, art slot,
title ribbon, divider, palette, pixel chunkiness, parchment texture.
Do NOT change any of that. Only ADD the content described below in the
appropriate zones.

ITEM ART PRESERVATION: The attached TRUE ITEM ART is pixel-art.
Composite into the art slot byte-identical — do NOT redraw, smooth,
anti-alias, restyle, re-render, or upscale. Treat as a placed sticker.
The art slot interior stays WHITE. If you cannot preserve the item
byte-identically, leave the slot empty and say so.

CONTENT — slide 2: DJ CONTROLLER

ZONE 1 — ART SLOT: Place TRUE ITEM ART per preservation rule.

ZONE 2 — TITLE RIBBON (chunky pixel display, dark brown, centered):
  DJ CONTROLLER

ZONE 3 — RARITY LINE (small pixel-bitmap, centered, the word LEGENDARY
colored WARM ORANGE / OXBLOOD, the rest dark brown):
  LEGENDARY · WEAPON · TWO-HANDED

ZONE 4 — QUOTE LINE (pixel-bitmap italic, dark brown, in quote marks,
centered):
  "Where the set actually happens."

ZONE 5 — STATS BLOCK (centered, pixel-bitmap, "+6" and "+9" colored
amber/gold, labels and rest dark brown):
  +6 Rhythm · +9 Crowd Control
  Passive: Beatmatch
  Active: COKI — Goblin

ZONE 6 — FAVORITES BLOCK (centered, pixel-bitmap, label dark brown,
the number 140 and the artist names amber/gold for emphasis):
  Favorite BPM: 140
  Favorite Artists: Skee Mask · Djrum · Boards of Canada

ZONE 7 — DIVIDER: Already in MASTER TEMPLATE. Do NOT redraw.

ZONE 8 — DESCRIPTION BLOCK (below divider, two lines, centered, pixel-
bitmap, dark brown, NOT in quote marks, em-dash prefix on first line):
  — Pioneer CDJ-2000 Nexus.
    The hours nobody schedules meetings in.

DO NOT CHANGE: outer frame, corner ornaments, art slot sub-frame,
title ribbon shape, divider, parchment palette, aspect ratio (4:5,
1200 × 1500). Single image.
```

---

## Slide 3 — COFFEE DRIPPER

**Attach:** MASTER TEMPLATE + `assets/02-v60.png`

**Paste:**

```
Fill in the attached MASTER TEMPLATE with the content below to produce
slide 3 of a 10-slide character-sheet carousel. Do NOT change any
chrome — only ADD content into the empty zones.

ITEM ART PRESERVATION: The attached TRUE ITEM ART is pixel-art.
Composite into the art slot byte-identical — do NOT redraw, smooth,
anti-alias, restyle, re-render, or upscale. Treat as a placed sticker.
The art slot interior stays WHITE. If you cannot preserve the item
byte-identically, leave the slot empty and say so.

CONTENT — slide 3: COFFEE DRIPPER

ZONE 1 — ART SLOT: Place TRUE ITEM ART per preservation rule.

ZONE 2 — TITLE RIBBON (chunky pixel display, dark brown, centered):
  COFFEE DRIPPER

ZONE 3 — RARITY LINE (small pixel-bitmap, centered, the word UNCOMMON
colored FOREST GREEN, the rest dark brown):
  UNCOMMON · ARTEFACT

ZONE 4 — QUOTE LINE (pixel-bitmap italic, dark brown, in quote marks,
centered):
  "Patience in ceramic form. The brew rewards precision."

ZONE 5 — STATS BLOCK (centered, pixel-bitmap, "+4" colored amber/gold,
labels and rest dark brown):
  +4 INT (mornings only)
  Active: Removes [Grogginess] status

(NO favorites block on this slide.)

ZONE 7 — DIVIDER: Already in MASTER TEMPLATE. Do NOT redraw.

ZONE 8 — DESCRIPTION BLOCK (below divider, two lines, centered, pixel-
bitmap, dark brown, NOT in quote marks, em-dash prefix on first line):
  — Pour-over daily ritual. 1:16 ratio, specialty beans, gooseneck kettle.
    The ceremony matters more than the caffeine.

DO NOT CHANGE: outer frame, corner ornaments, art slot sub-frame,
title ribbon shape, divider, parchment palette, aspect ratio (4:5,
1200 × 1500). Single image.
```

---

## Slide 4 — MTG TOME

**Attach:** MASTER TEMPLATE + `assets/03-mtg-tome.png`

**Paste:**

```
Fill in the attached MASTER TEMPLATE with the content below to produce
slide 4 of a 10-slide character-sheet carousel. Do NOT change any
chrome — only ADD content into the empty zones.

ITEM ART PRESERVATION: The attached TRUE ITEM ART is pixel-art.
Composite into the art slot byte-identical — do NOT redraw, smooth,
anti-alias, restyle, re-render, or upscale. Treat as a placed sticker.
The art slot interior stays WHITE. If you cannot preserve the item
byte-identically, leave the slot empty and say so.

CONTENT — slide 4: MTG TOME

ZONE 1 — ART SLOT: Place TRUE ITEM ART per preservation rule.

ZONE 2 — TITLE RIBBON (chunky pixel display, dark brown, centered):
  MTG TOME

ZONE 3 — RARITY LINE (small pixel-bitmap, centered, the word EPIC
colored ROYAL PURPLE muted, the rest dark brown):
  EPIC · TOME

ZONE 4 — QUOTE LINE (pixel-bitmap italic, dark brown, in quote marks,
centered):
  "99 cards. One general. Infinite politics."

ZONE 5 — STATS BLOCK (centered, pixel-bitmap, "+6" colored amber/gold,
labels and rest dark brown):
  +6 CHA in multiplayer encounters
  Summons: [Casual Chaos]

ZONE 6 — FAVORITES BLOCK (centered, pixel-bitmap, label dark brown,
the commander names amber/gold for emphasis, with bullet markers):
  Favorite Commanders:
    · Iroh, Grand Lotus
    · Go-Shintai of Life's Origin

ZONE 7 — DIVIDER: Already in MASTER TEMPLATE. Do NOT redraw.

ZONE 8 — DESCRIPTION BLOCK (below divider, one line, centered, pixel-
bitmap, dark brown, NOT in quote marks, em-dash prefix):
  — Magic: The Gathering, Commander format.

DO NOT CHANGE: outer frame, corner ornaments, art slot sub-frame,
title ribbon shape, divider, parchment palette, aspect ratio (4:5,
1200 × 1500). Single image.
```

---

## Slide 5 — COMPUTER

**Attach:** MASTER TEMPLATE + `assets/04-computer.png`

**Paste:**

```
Fill in the attached MASTER TEMPLATE with the content below to produce
slide 5 of a 10-slide character-sheet carousel. Do NOT change any
chrome — only ADD content into the empty zones.

ITEM ART PRESERVATION: The attached TRUE ITEM ART is pixel-art.
Composite into the art slot byte-identical — do NOT redraw, smooth,
anti-alias, restyle, re-render, or upscale. Treat as a placed sticker.
The art slot interior stays WHITE. If you cannot preserve the item
byte-identically, leave the slot empty and say so.

CONTENT — slide 5: COMPUTER

ZONE 1 — ART SLOT: Place TRUE ITEM ART per preservation rule.

ZONE 2 — TITLE RIBBON (chunky pixel display, dark brown, centered):
  COMPUTER

ZONE 3 — RARITY LINE (small pixel-bitmap, centered, the word RARE
colored OCEAN BLUE, the rest dark brown):
  RARE · WEAPON · TWO-HANDED

ZONE 4 — QUOTE LINE (pixel-bitmap italic, dark brown, in quote marks,
centered):
  "Type. Commit. Repeat."

ZONE 5 — STATS BLOCK (centered, pixel-bitmap, "+9" and "+7" colored
amber/gold, labels and rest dark brown):
  +9 Build Speed · +7 Problem-Solving
  Skill: Agentic Workflows

(NO favorites block on this slide.)

ZONE 7 — DIVIDER: Already in MASTER TEMPLATE. Do NOT redraw.

ZONE 8 — DESCRIPTION BLOCK (below divider, two lines, centered, pixel-
bitmap, dark brown, NOT in quote marks, em-dash prefix on first line):
  — By day: tickets, roadmaps, 1-on-1s.
    By night: this thing builds whatever I can describe.

DO NOT CHANGE: outer frame, corner ornaments, art slot sub-frame,
title ribbon shape, divider, parchment palette, aspect ratio (4:5,
1200 × 1500). Single image.
```

---

## Slide 6 — 3D PRINTER

**Attach:** MASTER TEMPLATE + `assets/05-printer.png`

**Paste:**

```
Fill in the attached MASTER TEMPLATE with the content below to produce
slide 6 of a 10-slide character-sheet carousel. Do NOT change any
chrome — only ADD content into the empty zones.

ITEM ART PRESERVATION: The attached TRUE ITEM ART is pixel-art.
Composite into the art slot byte-identical — do NOT redraw, smooth,
anti-alias, restyle, re-render, or upscale. Treat as a placed sticker.
The art slot interior stays WHITE. If you cannot preserve the item
byte-identically, leave the slot empty and say so.

CONTENT — slide 6: 3D PRINTER

ZONE 1 — ART SLOT: Place TRUE ITEM ART per preservation rule.

ZONE 2 — TITLE RIBBON (chunky pixel display, dark brown, centered):
  3D PRINTER

ZONE 3 — RARITY LINE (small pixel-bitmap, centered, the word RARE
colored OCEAN BLUE, the rest dark brown):
  RARE · CRAFTING STATION

ZONE 4 — QUOTE LINE (pixel-bitmap italic, dark brown, in quote marks,
centered):
  "If the part doesn't exist, print it."

ZONE 5 — STATS BLOCK (centered, pixel-bitmap, "+3" colored amber/gold,
labels and rest dark brown):
  +3 DEX · Enables: .STL Crafting
  Cooldown: 4 hours per object

(NO favorites block on this slide.)

ZONE 7 — DIVIDER: Already in MASTER TEMPLATE. Do NOT redraw.

ZONE 8 — DESCRIPTION BLOCK (below divider, two lines, centered, pixel-
bitmap, dark brown, NOT in quote marks, em-dash prefix on first line):
  — Bambu P1S. Cable holders, desk mounts, weird brackets.
    The junk drawer became a feature.

DO NOT CHANGE: outer frame, corner ornaments, art slot sub-frame,
title ribbon shape, divider, parchment palette, aspect ratio (4:5,
1200 × 1500). Single image.
```

---

## Slide 7 — LANGUAGE TOME ⚠️ (special — flags + no description)

**Heads-up:** the flag emojis 🇬🇧🇹🇷🇩🇪 may not render correctly in a pixel-bitmap font. Try with flags first; if they render badly, reroll with text labels (`[GB]` `[TR]` `[DE]` or `EN` / `TR` / `DE`).

**Attach:** MASTER TEMPLATE + `assets/06-language.png`

**Paste:**

```
Fill in the attached MASTER TEMPLATE with the content below to produce
slide 7 of a 10-slide character-sheet carousel. Do NOT change any
chrome — only ADD content into the empty zones.

ITEM ART PRESERVATION: The attached TRUE ITEM ART is pixel-art.
Composite into the art slot byte-identical — do NOT redraw, smooth,
anti-alias, restyle, re-render, or upscale. Treat as a placed sticker.
The art slot interior stays WHITE. If you cannot preserve the item
byte-identically, leave the slot empty and say so.

CONTENT — slide 7: LANGUAGE TOME

ZONE 1 — ART SLOT: Place TRUE ITEM ART per preservation rule.

ZONE 2 — TITLE RIBBON (chunky pixel display, dark brown, centered):
  LANGUAGE TOME

ZONE 3 — RARITY LINE (small pixel-bitmap, centered, the word UNCOMMON
colored FOREST GREEN, the rest of the line — including [QUEST ACTIVE]
— dark brown):
  UNCOMMON · TOME · [QUEST ACTIVE]

ZONE 4 — QUOTE LINE (pixel-bitmap italic, dark brown, in quote marks,
centered):
  "Two fluent. One grinding."

ZONE 5 — STATS BLOCK (centered, pixel-bitmap, three lines, with flag
emojis at the start of each line; level numbers "99" and "35" colored
amber/gold, labels dark brown; preserve the arrow → and the
parenthetical "(native)" exactly):
  🇬🇧 English   Lv. 99
  🇹🇷 Turkish   Lv. 99 (native)
  🇩🇪 German    Lv. 35  →  telc B1 quest in progress

(NO favorites block on this slide.)
(NO description block on this slide. The slide ends after the divider —
leave the area below the divider as empty parchment.)

ZONE 7 — DIVIDER: Already in MASTER TEMPLATE. Do NOT redraw.

DO NOT CHANGE: outer frame, corner ornaments, art slot sub-frame,
title ribbon shape, divider, parchment palette, aspect ratio (4:5,
1200 × 1500). Single image.
```

---

## Slide 8 — CONTROLLER

**Attach:** MASTER TEMPLATE + `assets/07-controller.png`

**Paste:**

```
Fill in the attached MASTER TEMPLATE with the content below to produce
slide 8 of a 10-slide character-sheet carousel. Do NOT change any
chrome — only ADD content into the empty zones.

ITEM ART PRESERVATION: The attached TRUE ITEM ART is pixel-art.
Composite into the art slot byte-identical — do NOT redraw, smooth,
anti-alias, restyle, re-render, or upscale. Treat as a placed sticker.
The art slot interior stays WHITE. If you cannot preserve the item
byte-identically, leave the slot empty and say so.

CONTENT — slide 8: CONTROLLER

ZONE 1 — ART SLOT: Place TRUE ITEM ART per preservation rule.

ZONE 2 — TITLE RIBBON (chunky pixel display, dark brown, centered):
  CONTROLLER

ZONE 3 — RARITY LINE (small pixel-bitmap, centered, the word EPIC
colored ROYAL PURPLE muted, the rest dark brown):
  EPIC · RELIC

ZONE 4 — QUOTE LINE (pixel-bitmap italic, dark brown, in quote marks,
centered):
  "One more turn."

ZONE 5 — STATS BLOCK (centered, pixel-bitmap, "+5" values colored
amber/gold, labels and rest dark brown):
  +5 Strategy · +5 Grind Tolerance
  Passive: Min-Max Instinct
  Passive: Meta Awareness

ZONE 6 — FAVORITES BLOCK (centered, pixel-bitmap, labels dark brown,
the genre and game names amber/gold for emphasis):
  Favorite Genres: Card · Strategy · RPG
  Favorite Games: Persona 5 · MapleStory · Hearthstone

ZONE 7 — DIVIDER: Already in MASTER TEMPLATE. Do NOT redraw.

ZONE 8 — DESCRIPTION BLOCK (below divider, one line, centered, pixel-
bitmap, dark brown, NOT in quote marks, em-dash prefix):
  — Been a gamer as long as I can remember.

DO NOT CHANGE: outer frame, corner ornaments, art slot sub-frame,
title ribbon shape, divider, parchment palette, aspect ratio (4:5,
1200 × 1500). Single image.
```

---

## Slide 9 — MALTIPOO

**Attach:** MASTER TEMPLATE + `assets/08-maltipoo.png`

**Paste:**

```
Fill in the attached MASTER TEMPLATE with the content below to produce
slide 9 of a 10-slide character-sheet carousel. Do NOT change any
chrome — only ADD content into the empty zones.

ITEM ART PRESERVATION: The attached TRUE ITEM ART is pixel-art.
Composite into the art slot byte-identical — do NOT redraw, smooth,
anti-alias, restyle, re-render, or upscale. Treat as a placed sticker.
The art slot interior stays WHITE. If you cannot preserve the item
byte-identically, leave the slot empty and say so.

CONTENT — slide 9: MALTIPOO — FAMILIAR

ZONE 1 — ART SLOT: Place TRUE ITEM ART per preservation rule.

ZONE 2 — TITLE RIBBON (chunky pixel display, dark brown, centered;
preserve the em-dash exactly):
  MALTIPOO — FAMILIAR

ZONE 3 — RARITY LINE (small pixel-bitmap, centered, the word LEGENDARY
colored WARM ORANGE / OXBLOOD, the rest of the line — including
[LOCKED] — dark brown):
  LEGENDARY COMPANION · [LOCKED]

ZONE 4 — QUOTE LINE (pixel-bitmap italic, dark brown, in quote marks,
centered):
  "Coming to a couch near you."

ZONE 5 — STATS BLOCK (centered, pixel-bitmap, "+5" and "+3" colored
amber/gold, labels and rest dark brown):
  +5 Morale · +3 Wholesome
  Unlock Condition: [Real life cooperates]

(NO favorites block on this slide.)

ZONE 7 — DIVIDER: Already in MASTER TEMPLATE. Do NOT redraw.

ZONE 8 — DESCRIPTION BLOCK (below divider, one line, centered, pixel-
bitmap, dark brown, NOT in quote marks, em-dash prefix):
  — Mocha the Maltipoo. Dream companion slot.

DO NOT CHANGE: outer frame, corner ornaments, art slot sub-frame,
title ribbon shape, divider, parchment palette, aspect ratio (4:5,
1200 × 1500). Single image.
```

---

## Slide 10 — WATCH

**Attach:** MASTER TEMPLATE + `assets/09-watch.png`

**Paste:**

```
Fill in the attached MASTER TEMPLATE with the content below to produce
slide 10 of a 10-slide character-sheet carousel. Do NOT change any
chrome — only ADD content into the empty zones.

ITEM ART PRESERVATION: The attached TRUE ITEM ART is pixel-art.
Composite into the art slot byte-identical — do NOT redraw, smooth,
anti-alias, restyle, re-render, or upscale. Treat as a placed sticker.
The art slot interior stays WHITE. If you cannot preserve the item
byte-identically, leave the slot empty and say so.

CONTENT — slide 10: WATCH

ZONE 1 — ART SLOT: Place TRUE ITEM ART per preservation rule.

ZONE 2 — TITLE RIBBON (chunky pixel display, dark brown, centered):
  WATCH

ZONE 3 — RARITY LINE (small pixel-bitmap, centered, the word EPIC
colored ROYAL PURPLE muted, the rest dark brown):
  EPIC · TIMEPIECE · STYLE

ZONE 4 — QUOTE LINE (pixel-bitmap italic, dark brown, in quote marks,
centered):
  "Form. Function. No clutter."

ZONE 5 — STATS BLOCK (centered, pixel-bitmap, "+2" colored amber/gold,
"Junghans Max Bill" can also be amber for emphasis, labels and rest
dark brown):
  +2 Presence
  Passive: Never late to things that matter
  Daily Driver: Junghans Max Bill

(NO favorites block on this slide.)

ZONE 7 — DIVIDER: Already in MASTER TEMPLATE. Do NOT redraw.

ZONE 8 — DESCRIPTION BLOCK (below divider, one line, centered, pixel-
bitmap, dark brown, NOT in quote marks, em-dash prefix):
  — Horology is the hobby. Collecting is the hazard.

DO NOT CHANGE: outer frame, corner ornaments, art slot sub-frame,
title ribbon shape, divider, parchment palette, aspect ratio (4:5,
1200 × 1500). Single image.
```

---

## Final assembly (after all 10 slides are in `slides/`)

1. **Watermark cleanup pass.** Open each `slides/slide-NN-*.png` in Photopea, eyedropper parchment, brush over the bottom-right Gemini watermark sparkle, **File → Export As → PNG**, overwrite. Skip slide 1 if it didn't have one.
2. **Assemble PDF.** Finder → select `slide-01-hero.png` through `slide-10-watch.png` in order → drag into a fresh Preview window → File → **Export as PDF** → name `character-sheet.pdf`.
3. **Upload to LinkedIn** as a document post.

## Color reference (hex)

If you need to specify exact colors in any reroll prompt:

| Element | Hex |
|---|---|
| Body brown (labels, text) | `#4A2E1F` |
| Amber/gold (values, emphasis) | `#C8862E` |
| LEGENDARY (warm orange/oxblood) | `#B8501E` |
| EPIC (royal purple, muted) | `#6B3D8A` |
| RARE (ocean blue) | `#2E5F8A` |
| UNCOMMON (forest green) | `#3F7A3F` |
