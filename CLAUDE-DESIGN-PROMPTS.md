# Claude Design — Prompts for the Character Sheet Carousel

Two prompts only. The first one establishes the visual system + produces the hero slide. The second is a tiny template you reuse for slides 2–10. Claude Design retains design context within a single project, so don't restate the system on every message — that wastes weekly quota.

Open Claude Design ([claude.ai/design](https://claude.ai/design)). Create a new project named **Character Sheet Carousel**. All prompts below go into that one project.

---

## Section A — Setup + Hero variants (1 message)

**Attach before sending:**
1. `reference/maplestory-reference.jpeg` — labelled "AESTHETIC LOCK — match this rendering language and palette family"
2. `reference/octopath-reference.jpeg` — labelled "AESTHETIC LOCK — match this character-screen layout pattern and atmospheric warmth"
3. `assets/portrait.png` — labelled "HERO ART"

Do NOT attach `reference/style-exemplar.png` — that previous output and an earlier loose prompt produced three off-target variants ("Parchment Grimoire", "Arcade CRT", "JRPG Status Screen"); keeping it in the chat invites the same drift.

**Paste this prompt:**

```
I'm building a 10-slide LinkedIn carousel — a "character sheet"
presenting me as an RPG profile. This is slide 1 of 10 (the hero /
profile page). Whatever visual system you commit to here will be
reused across the other 9 slides — pick a system that scales. Slides
2–10 each have an item art slot, a title banner, a small
"rarity · type" tag, an italic quote, a short stats list, and a
1–2-line description.

═══════════════════════════════════════════════════════════════════════
THE AESTHETIC LANE — LOCKED, NARROW
═══════════════════════════════════════════════════════════════════════

This is a classic 2D RPG / MMORPG character screen in the language of
MapleStory and Octopath Traveler — see the two attached reference
screenshots. They are aesthetic LOCKS, not vibe suggestions.

- Era reference: late-90s through HD-2D — MapleStory, Octopath
  Traveler, Stardew Valley, Disgaea, classic SNES/PSX JRPG menus
  (Final Fantasy VI, Chrono Trigger). NOT 8-bit arcade. NOT modern
  game UI. NOT illuminated manuscript / book design.

- Rendering: chunky pixel-art GUI. Frames, banners, dividers, icons,
  and stat-bar segments are all PIXEL-RENDERED with hard edges and
  visible pixel chunks at 1200×1500. No vector hairlines. No
  anti-aliased rounded corners on UI elements. The portrait's pixel
  grid sets the rendering scale — UI chrome must match it, not float
  above it as clean vector.

- Frame: chunky pixel panel border with depth — outer dark line plus
  inner highlight line, suggesting carved wood / parchment / forged
  metal. See the MapleStory reference for the panel-within-panel
  treatment and the bevel feel; nested mini-panels are encouraged.

- Palette: warm classic-RPG. Cream / parchment / aged-paper base, warm
  browns, with a limited accent palette (forest green, ocean blue,
  gold, oxblood / warm orange for emphasis). Atmospheric, not flat.
  NO neon, NO synthwave magenta or cyan, NO modern dark-navy card UI.

- Typography: pixel-bitmap or pixel-friendly typefaces. Small-caps
  pixel sans for labels and body, chunky pixel display for the title
  banner. Octopath-style refined typography is acceptable for the
  title only if it reads pixel-rendered (NOT Cinzel, NOT modern
  serif, NOT hairline). NO Press Start 2P (reads as 8-bit arcade,
  wrong era). NO modern sans like Inter or Pixelify Sans.

- Stat viz: either chunky 10-segment pixel bars (MapleStory style)
  OR slim pixel HP-bar with icon + numeral (Octopath style). Either
  works — but rendered in the warm RPG palette, not neon, and the
  bar segments themselves must be pixel-chunky.

═══════════════════════════════════════════════════════════════════════
HARD EXCLUSIONS — directions you returned previously that all missed
═══════════════════════════════════════════════════════════════════════

In the previous round you returned three variants that were all
off-target. Do not return any variant in these directions:

- "Parchment Grimoire" — illuminated-manuscript book design with
  Cinzel serif, fleurons, hairline rules, Roman numerals. Wrong era,
  wrong rendering language (vector book design, not pixel RPG).
- "Arcade Cartridge / CRT" — neon magenta/cyan synthwave with
  scanlines and "PLAYER 1 SELECT" chrome. Wrong palette, wrong era
  (8-bit arcade, not 16-bit RPG).
- "JRPG Status Screen" (modern) — dark navy card UI with vector
  rounded panels, Inter-ish typography, gold accents. Wrong
  rendering language (clean vector card, not pixel RPG).

═══════════════════════════════════════════════════════════════════════
WHAT'S LOCKED (do not change)
═══════════════════════════════════════════════════════════════════════
- Aspect: portrait 4:5, 1200 × 1500 px (LinkedIn document carousel)
- The portrait PNG (HERO ART) is rendered AS-IS — never redraw or
  restyle the pixel art itself
- The text content below — every word, exactly as written
- The aesthetic lane above

═══════════════════════════════════════════════════════════════════════
WHAT'S OPEN — vary on these axes only, all WITHIN the locked lane
═══════════════════════════════════════════════════════════════════════
- Palette mood within the warm RPG family — e.g., MapleStory
  cream-and-wood vs. Octopath atmospheric cream-on-dark-teal vs. a
  third take of your choice within the warm RPG palette family
- Frame ornament density — clean pixel panel vs. heavily ornate
  pixel-scroll borders with corner pieces
- Stats-viz approach — chunky MapleStory pixel segment bars vs.
  slim Octopath icon+bar+numeral
- Layout rhythm — tight nested mini-panels (MapleStory) vs. open
  single-frame composition (Octopath)

All three variants must read unmistakably as "classic 2D pixel-RPG
character screen." Not three eras. Not three art-direction abstractions.

═══════════════════════════════════════════════════════════════════════
THE BRIEF — HERO SLIDE (slide 1 of 10)
═══════════════════════════════════════════════════════════════════════

Layout flow, top → bottom:

1. Portrait art slot — HERO ART rendered as-is, inside a chunky pixel
   panel frame.

2. Name banner — two lines, exact text:
     OGUZ ORAL
     LV. 30 · PROJECT MANAGER
   The second line is a subtitle / class line, visually subordinate
   to the name, neutral in color (NOT styled as a rarity tag — rarity
   coding becomes meaningful on slides 2–10).

3. Six character stats — render these exact values:
     STR 68
     DEX 78
     INT 82
     WIS 74
     CHA 77
     LUK 63
   If you use 10-segment bars, filled counts are
   STR=6 · DEX=7 · INT=8 · WIS=7 · CHA=7 · LUK=6 (floor of value/10).

4. A chunky pixel-rendered divider (this divider will recur on slides
   2–10).

5. Italic quote line, in quote marks, exact text:
     "Side-quests > main story."

6. NO description block. The slide ends on the quote.

═══════════════════════════════════════════════════════════════════════
WHAT I WANT BACK
═══════════════════════════════════════════════════════════════════════

Three distinct hero variants, ALL within the locked aesthetic lane.
Give each variant a short name and 1–2 sentences explaining the
art-direction choices (palette mood, frame treatment, stats viz).
The three should differ on the open axes above — but all three must
unmistakably belong to the MapleStory / Octopath / classic-2D-RPG
family per the attached references.

After I pick one, that variant becomes the locked visual system and
I'll send the remaining 9 slides as short content blocks against it.
```

---

## Section B — Per-slide template (1 message per slide, slides 2–10)

**Attach before sending:**
- The matching pixel-art PNG from `assets/` (e.g. `assets/01-cdj.png` for slide 2).

**Paste this template, filling in the bracketed parts from `CONTENT.md`:**

```
Next slide. Reuse the locked visual system from the hero variant I
chose — same frame, palette, typography, divider, layout rhythm.
Item art is attached, render it AS-IS in the framed slot at the top.

SLIDE [N] — [SLIDE NAME]

Title:        [TITLE]
Rarity line:  [RARITY · TYPE · etc]    (color the rarity word per the key)
Quote:        "[punchline]"
Stats:
  [stat line 1]
  [stat line 2]
  ...
Favorites:                              (omit this whole block if not used)
  [favorites line 1]
  [favorites line 2]
Description:
  — [description starting with em-dash, NOT in quote marks]

Render at 1200 × 1500.
```

For the SLIDE 7 — LANGUAGE TOME case (no description), drop the entire
Description block from the template.

---

## Workflow

1. Open [claude.ai/design](https://claude.ai/design). Create a new project named **Character Sheet Carousel**.
2. Send Section A — attach `reference/style-exemplar.png` + `assets/portrait.png`. Claude Design returns three hero variants. Pick one. If none land, ask for a fourth round or request specific adjustments to your favourite — **do not move on until the hero is right**, every issue you fix here saves quota on the remaining 9 slides.
3. For each of slides 2 → 10, paste Section B with the slide's content block from `CONTENT.md` and attach the matching `assets/NN-*.png`. One message per slide. The chosen hero variant — not the original style-exemplar — is the lock.
4. The previously-generated COMPUTER exemplar (`reference/style-exemplar.png`) is now obsolete; regenerate slide 5 in the chosen hero's style as part of the slide 2–10 pass.
5. Export the project: PNG zip (or PDF). Save the PNGs into `slides/` as `slide-01-hero.png` … `slide-10-watch.png`.
5. Combine into a single PDF (macOS Preview: select all PNGs in order → drag into a new Preview window → File → Export as PDF).
6. Upload to LinkedIn as a document post.

## Final checks before posting
- LinkedIn broadcasts the post to your network and your current employer's Recruiter seats. This is a personality post (not job-seeking) — confirm comfort before posting.
- Crop any Claude Design watermark if one slipped through.
- Proofread every slide one last time against `CONTENT.md`.
