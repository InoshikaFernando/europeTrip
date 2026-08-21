# Prompt — NZ car rental kids' activity workbooks (paste into the car-rental session)

This is a hand-off prompt. Copy everything inside the fenced block below and paste it
as the first message in the car-rental repo's Claude Code session.

Background: it is modelled on what worked for the Munasinghe-Fernando Europe 2026 kids'
booklets in this repo (`booklet-avin.html` 4yo, `booklet-aviann.html` 8yo,
`booklet-avisha.html` 11yo, `kids.html` landing page) — per-age files, fixed-height A4
pages, print-to-PDF, activity blocks like COLOUR ME / MY MISSION / sticker + tally /
journal prompts / A LITTLE HISTORY. The prompt below re-states those patterns in full
so the other session does not need access to this repo.

```
We run a car rental company in New Zealand. Lots of our customers are families doing
road trips, and the kids get bored in the car. I want to give every booking a free
printable activity workbook, personalised to the region they're driving through and to
their kids' ages.

Build me a static, self-contained "Workbook Builder" — a customer-facing web page where
a parent picks their region, their child's age group, and which kinds of activities they
want, and gets a print-ready A4 workbook (print to PDF from the browser).

## 1. What the customer chooses

**a) Region / district they're travelling.** Use New Zealand's 16 regions as the top
level, and let the customer drill into a district/area within it:

  North Island: Northland · Auckland · Waikato · Bay of Plenty · Gisborne ·
  Hawke's Bay · Taranaki · Manawatū-Whanganui · Wellington
  South Island: Tasman · Nelson · Marlborough · West Coast · Canterbury ·
  Otago · Southland

Allow multi-select — a customer doing Christchurch → Queenstown wants Canterbury AND
Otago in one workbook, with the pages in travel order.

**b) Age group.** Four bands, each with its own page templates, reading level and
handwriting-line spacing:
  - 3–5 (pre-reader)  — big shapes, colouring, tracing, counting, stickers, faces to circle
  - 6–8 (early reader) — short sentences, simple word searches, dot-to-dot, mazes, drawing boxes
  - 9–12 (confident reader) — crosswords, quizzes, real history/nature reading, journalling
  - 13+ (teen) — photo challenges, longer reads, log/notes pages, harder puzzles, playlists

**c) Activity modules — tick what you want.** The workbook is assembled only from the
ticked modules, so two families in the same region get different books:
  - 🎨 Colour me (region landmark / native bird / road scene line art)
  - 📖 Read (a short true story about the place — history, Māori history, geology, wildlife)
  - ✏️ My notes / journal (dated prompt + ruled lines sized to the age band)
  - 🧩 Crossword (region-specific clues)
  - 🔤 Word search (place names, native species)
  - 🚗 Road bingo / I-spy (things you'll actually see on that stretch of road)
  - 🗺️ Map page (route with towns to tick off as you pass them)
  - 🐦 Wildlife spotter (species genuinely found in that region, with tick boxes)
  - 🧠 Quiz / did-you-know
  - 🌀 Maze + dot-to-dot
  - 🔍 Spot the difference
  - 📷 Photo challenge (a list of shots to take)
  - 🗣️ Te reo Māori word of the day (with the correct macrons and meaning)
  - ⭐ Sticker / star chart + tally counters (sheep counted, bridges crossed, etc.)
  - 😂 Jokes & riddles page

**d) Trip length** — how many days of pages to generate (1–14). Each day gets its own
spread, so the book paces itself across the trip.

## 2. How to build it

- **Static HTML/CSS/JS only.** No build step, no server, no external API calls at
  render time. It must work opened straight from a file and hosted on our site.
- **Content lives in a data file**, not hard-coded in the page — e.g. `content/regions.js`
  (or one JSON file per region: `content/canterbury.json`). Each region holds its own
  landmarks, stories, wildlife list, crossword clues, word-search banks, te reo words,
  road-bingo items and colouring-page references. Adding a region must mean adding a
  data file, never touching the layout code.
- **Print-first page model** (this is the part that matters most — it's what made our
  earlier booklets work):
  - `@page { size: A4 portrait; margin: 0; }`
  - every page is a fixed-size `.page { width:210mm; height:295mm; padding:14mm 16mm;
    overflow:hidden; break-after:page; display:flex; flex-direction:column; }`
  - screen preview shows the pages stacked on a grey background with a drop shadow;
    `@media print` strips the background, toolbar and shadows.
  - Content must be **checked to fit** each fixed-height page — nothing may overflow or
    be clipped. If a section doesn't fit, let it run onto a second page rather than
    shrinking type below the age band's minimum.
  - A small fixed toolbar with a "🖨️ Print / Save PDF" button, hidden in print.
- **Line art must be printer-friendly**: pure black strokes on white, no fills, no
  gradients, no photographic backgrounds — parents print these on cheap home printers
  and in motels. Draw the colouring/maze/dot-to-dot art as **inline SVG**, so it stays
  crisp and the file stays self-contained.
- **Generated puzzles must actually be solvable.** Build the crossword and word-search
  generators properly and verify every grid: real intersections, no duplicate or
  unplaceable words, answer keys on a final page. Do not ship a grid you haven't
  verified programmatically.

## 3. Style and voice

- **NZ/British spelling throughout** — colour, favourite, neighbour, realise, metre.
- **Te reo Māori must be correct**, with macrons (Manawatū, Whanganui, kākāpō, tūī,
  Aoraki). If you are not certain of a word, a meaning or a place name's macron, leave
  it out rather than guess. Same for iwi/hapū references — respectful, accurate, or absent.
- **No invented facts.** Every "did you know", history note, distance and species claim
  must be one you're confident is true. Flag anything uncertain in a `TODO-VERIFY`
  comment in the data file instead of publishing it.
- Warm, friendly, kid-facing voice. Speak to the child, not to the parent.
- Age-appropriate line spacing: 3–5 gets ~12mm ruled lines, 6–8 ~9mm, 9–12 ~7mm, 13+ ~6mm.
- Leave our branding as a placeholder: a `--brand` colour variable, a logo slot on the
  cover and a small footer line on each page. I'll drop in the real logo and colours.

## 4. Deliverables

1. `index.html` — the builder: region picker, age band, activity checkboxes, trip
   length, live page-count estimate, and a "Build my workbook" button.
2. `workbook.html` (or a rendered view in the same page) — the generated printable book:
   cover (child's name field, region, dates) → contents → per-day activity pages →
   answer keys → back page.
3. `content/` — the region data files.
4. `README.md` — how to add a new region, how to add a new activity module, and the
   fixed-page/print rules above, so a non-developer on our team can extend it.

## 5. How to start — do this first

Don't build all 16 regions at once. Work in this order and stop for my review between
steps:

**Step 1.** Ask me any questions you need answered first (brand colours, business name,
whether kids' names should be typed in or handwritten, print size preference).
**Step 2.** Build the full engine plus **one pilot region — Canterbury** — with **all**
activity modules and **all four** age bands, so I can see every combination working and
printing correctly. Show me the print output before going further.
**Step 3.** Once I sign off on the pilot, roll the remaining 15 regions out from the
same templates.

Confirm the plan back to me before you start writing code.
```
