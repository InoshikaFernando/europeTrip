# Munasinghe-Fernando Travel Magazine — Runbook

> The single source of truth for how every issue is written and built.
> New issues and rewrites MUST follow this. Issue **03 · Austria (v3, the memoir)**
> — `magazines/03-austria-2026-v3.html` — is the reference implementation; when in
> doubt, copy it.

---

## 0. The family (get these right — always)

| Role | Name | Notes |
|------|------|-------|
| Dad | **Avinesh** ("Avi") | Full legal name *Navin Avinesh Welikala Munasinghe* — used ONLY on `day_*.html` booking/logistics pages (tickets, licence, hotel). Magazines use **Avinesh**. |
| Mum | **Inoshi** | Inoshi Fernando. **Never "Lana"** (an old placeholder — fully removed). |
| Child | **Avisha** | 11, **boy** |
| Child | **Aviann** | 8, **girl** |
| Child | **Avin** | 4, **boy** (the youngest; often in the stroller) |

- Brand / masthead: **"Munasinghe-Fernando Travel"**. Family sign-off: **"Avinesh, Inoshi, Avisha, Aviann & Avin Munasinghe-Fernando"**.
- Spelling: **NZ/British** (colour, favourite, honour, metre…).

---

## 1. The one rule that beats every other rule

**Never invent.** No events, dialogue, reactions, emotions, weather, food, places or
thoughts that the family didn't actually report. You may *describe and connect* real
details beautifully, but you may not fabricate a memory. If a sensory or emotional
detail is missing, **leave it out or ask** — do not fill the gap with fiction.

This is why most issues can't be written yet: they need the family's real material first.

---

## 2. Voice (the Austria v3 standard)

Write it as a **first-person family memoir, narrated by Inoshi (the mum)** — carry a
small **"told in Inoshi's words"** byline on the opener. She speaks as **"I"**; the
family is **"we"**; Avinesh and the children are named. It stays a *shared* story (the
"we" keeps the children inside it, so reading it in 25 years they feel it is their own
memory), but the telling voice is one person — intimate, not a detached report.

- **"I / my"** for Inoshi herself and her own back-story (e.g. the *Sound of Music*
  childhood: *"When I was six or seven, my sister and I used to perform…"*).
- **"We / our"** for everything the family did together ("our children", "the two of
  us") — never "the children" from a distance.
- Name **Avinesh** and the kids; quote them in their own words when real.
- If a different issue is genuinely better told by someone else, keep the same
  first-person-narrator principle and state whose voice it is in the byline — but default
  to Inoshi for consistency across the series.

**Attributed child points of view.** A moment that truly belongs to a child may be told
in *that child's own* first person — clearly labelled so the reader knows the voice has
handed over (a small kicker/mini-heading like *Avisha · 11* or *In Aviann's words*, or a
boxed aside). Switch the "I" to the child for that block, then return to Inoshi. Use it
**only for a moment the child actually lived or said** — never invent a child's words,
thoughts or feelings. If you don't have the child's real line for a moment, leave it out
or ask. These asides are precious precisely because they're real: one true line from a
4-, 8- or 11-year-old is worth more than a paragraph written *for* them.
- Preserve each child **as they are at this age** — real words, jokes, complaints,
  boredom, what they noticed. A child's one true line can carry a whole page.
- Keep the **imperfect moments** (closed attractions, shut shops, tired legs, the
  liftless castle). They are the stories the family will retell.
- Warm, literary, specific. **Beauty comes from precise detail, not adjectives.** Avoid
  "magical / amazing / breathtaking / unforgettable" and tourism-brochure copy.
- Weave history in *lightly* and accurately, tied to what the family was standing in
  front of — never a Wikipedia paragraph.
- **Don't write an itinerary.** Open each chapter *inside a moment*; give big moments a
  paragraph and small ones a sentence; end on something specific (an image, a line),
  never "a day we'll cherish forever".
- Real quotes only. Austria's, as recorded: Inoshi — *"Every time, I was in Austria in my
  mind"*; Avinesh at the Stephansdom — *"Honestly, I had no words."*; Aviann (8), on the
  fiaker horses on the Graben — *"What is that disgusting smell?"*. Inoshi's own felt lines
  carry the same weight as spoken quotes: her *confidence* at the Residenzbrunnen
  (confident to see the trip through with her "three little musketeers") and her
  *thanksgiving* at the Pestsäule ("a chance to say thank you, God, for the experience").
- **History is allowed — facts are not invention.** You MAY state accurate, verifiable
  history/geography tied to what the family stood in front of, even when they didn't
  remark on it (why Salzburg's lanes are narrow — pinched between the Mönchsberg and the
  Salzach; Maria Theresa built Schönbrunn; the Pestsäule was Leopold I's thanks-offering
  after the 1679 plague). Keep it light, one or two sentences, tied to the photo/moment —
  never a Wikipedia block. The #1 rule bans inventing the *family's* experience, not
  stating true context. If unsure a fact is right, leave it out or flag it.
- **Don't guess which place a photo shows.** If an interior/landmark is ambiguous (e.g.
  Schönbrunn vs the Belvedere), confirm with the family before captioning — a confident
  wrong label is worse than asking.

Full brief (the long version this distils) lives in the project history; this section is
the operative summary.

---

## 3. Structure of an issue

1. **Cover** (see §5).
2. **Opener** — kicker, a two-line headline, an italic lede framing the leg. No facts-dump.
3. **Chapters** — one per place / major experience. Each: `Chapter N · Place`,
   a title, an italic subtitle, the narrative, 1–3 photos, and an optional sidebar.
4. **Reflections** — what we carried out; a *Worth Remembering* box (favourite / hardest
   / if-we-come-back), family sign-off.

**Sidebars** (use only where they genuinely fit — don't force the same ones):
*Travel Reality*, *The Kids Said…*, *Worth Remembering*, *What Surprised Us*,
*Things Photos Can't Tell You*, *Our Favourite Moment*, *Would We Go Back?*

**Folios / numbering:** inserted pages get descriptive folios so the numbered TOC never
needs renumbering.

---

## 4. Layout = A4 "sheets" (reads on screen, exports as a clean PDF)

The memoir is laid out as **white A4 pages on a grey backdrop** — paginated on screen and
clean when saved as PDF. Copy the CSS from `03-austria-2026-v3.html`. Key points:

- `body{ background:#9a9fa5; padding:22px 0; }` — grey viewer backdrop.
- Each section (`.opener`, `.chapter`) is a **white sheet**: `width:210mm; margin:0 auto
  16px; padding:20mm 22mm; background:#fff; box-shadow:0 2px 16px rgba(0,0,0,.35);`.
- **Fonts:** `Fraunces` (display/headings + drop cap), `Spectral` (body, italic
  decks/captions), `JetBrains Mono` (kickers, labels, credit). **Self-host them**
  (`magazines/fonts/*.woff2`, inlined `@font-face`), do NOT rely on a Google Fonts
  `<link>` — the PDF generator can't fetch Google Fonts and will silently fall back to a
  Times clone ("Liberation Serif"), which looks wrong. Reuse the files already in
  `magazines/fonts/`. After generating a PDF, verify with
  `strings file.pdf | grep BaseFont` — you should see Fraunces/Spectral/JetBrains, never
  Liberation/DejaVu.
- **Accent palette** is per-country (Austria: blue `#28508c`, gold `#b1812c`, ink
  `#2c2522`). Each new issue sets its own `:root` palette; keep the structure identical.
- **Full-bleed photo** inside a sheet: `figure.photo.bleed{ margin-left:-22mm;
  margin-right:-22mm; }` (spans the page; never `vw`, which breaks in print).
- **Drop cap** on each chapter's lead paragraph; **pull-quote** `.pq`; **sidebar** `.side`.
- **Print block** (makes Save-as-PDF clean):
  ```css
  @page{ size:A4; margin:0; }
  @media print{
    body{ background:#fff; padding:0; }
    .cover{ height:297mm; page-break-after:always; }
    .opener,.chapter{ margin:0; box-shadow:none; padding:18mm 16mm; page-break-before:always; }
    .opener{ page-break-before:avoid; }
    figure.photo,.side,.pq,.duo,.endnote{ break-inside:avoid; }
    .chapter h2{ break-after:avoid; }
  }
  ```
- Mobile: a `@media (max-width:800px)` block drops the sheets to full width.
- **Pack the PDF — no half-empty pages.** On screen, photos can be tall (`max-height:138mm`).
  But in the *print* block that height + `break-inside:avoid` orphans each portrait onto its
  own near-empty A4 sheet. So the `@media print` block caps photos smaller so a photo and
  text share a page: `figure.photo img{max-height:92mm}`, `figure.photo.bleed img{104mm}`,
  `.duo img{85mm}`, with `figure.photo{margin:5mm 0}` and ~10.5px captions. Copy these from
  `03-austria-2026-v3.html`. (Austria went 36 → 23 pages with this; later grew to 27 as
  more real photos were added — that's fine.)
- **Verify page density before shipping.** Rasterise the PDF (PyMuPDF: `pymupdf.open(pdf)`,
  `page.get_pixmap(dpi=60)`) and measure ink-per-page / where the bottom content ends; flag
  any page under ~9% ink (empty) or ending above ~62% (big bottom gap), and build a contact
  sheet to eyeball it. Script pattern kept in the session scratchpad.

---

## 5. Cover = the V2 style (the family likes this one)

A **full-bleed family selfie** with the issue's three cities as **small cards floating on
the photo**, title at the foot. Copy from `03-austria-2026-v3.html` / `-v2.html`.

- Photo: `.bg{ background-size:100% auto; background-position:center top; }` — **full
  width, no side-crop**, so no one (especially Avin, who sits at the right edge) is ever
  cropped. Do **not** use `cover` on a narrowed panel; it slices the edges.
- A dark top-and-bottom `scrim` gradient for legibility.
- **City cards** `.citystrip`: a small column top-right (`width:37mm; top:13mm;
  right:8mm`), white-framed, **images uncropped** (`height:auto`), **no dark rail
  behind them**, placed over sky/scenery so they never cover a face. No "THE CITIES"
  header.
- Masthead centred at top; **country title** (`Fraunces`, ~92px) pinned to the bottom
  (`margin-top:auto`); italic deck; pill **teasers**; family + dates credit.

---

## 6. Photos

- Real photos only; the family's own. Process: EXIF-straighten (`ImageOps.exif_transpose`),
  resize long edge ~2000px, JPEG q82 (~300–600 KB). Watch phone EXIF orientation 6/8.
- **Never crop faces.** Wire photos in **uncropped** (`.photo` / `.bleed`, not a
  cover-cropped hero). Full frame always.
- Store under `images/<country>/…`; descriptive names.
- Captions **add to the memory** (what it felt like / what happened just after), they
  don't describe the pixels.
- **Uploads arriving preview-only?** Recover from the session transcript: base64 image
  blocks in `~/.claude/projects/-home-user-europeTrip/<SESSION>.jsonl`, decode, dedupe by
  md5. (`extract.py` kept in the session scratchpad.) Note the transcript also holds images
  you *viewed* with Read, so index order ≠ send order — identify by content (a montage
  helps), not position.
- **Curate — you are the editor, not a dumping ground.** When the family sends many photos
  (a whole city at once), use the genuinely new/better ones and **skip near-duplicates** of
  what a chapter already shows. One real *moment* = about one photo. A new scene, a face not
  yet shown, or a true story beat earns a place; a third gilded hall or fifth lake view does
  not. Say plainly which you used and which you held, and offer to swap — don't silently
  bloat the chapter. Prefer **upgrading** an existing weak photo over adding a duplicate.
- **`.duo` crops (`object-fit:cover`) — never put a face in one.** Face photos go in full,
  uncropped `figure.photo`; reserve `.duo` two-ups for scenics/architecture with no family
  faces.
- **Big folders (GBs): go local.** Don't upload multi-GB archives to a cloud session (disk +
  upload limits). Either the family sends per-city batches in chat (works well), or run a
  local Claude Code session pointed at the folder, following this runbook, committing only
  the resized copies — not the originals.

---

## 7. Build & publish

- **Start every new issue by copying `magazines/_TEMPLATE-issue.html`** — it carries the
  whole format (self-hosted fonts, cover, A4 sheets, print CSS) with `{{PLACEHOLDERS}}`
  and inline instructions. Fill it in; don't rebuild from scratch.
- Files: `magazines/NN-country-YYYY.html`. Austria memoir = `03-austria-2026-v3.html`
  (the worked reference example).
- **Verify before pushing:** render each page headless (Playwright at
  `/opt/node22/lib/node_modules/playwright`, Chromium at
  `/opt/pw-browsers/chromium-1194/chrome-linux/chrome`); screenshot every page/sheet and
  check nothing clips or crops a face.
- **PDF:** `page.pdf({ format:'A4', printBackground:true, preferCSSPageSize:true })`.
- Commit → push branch → fast-forward into **main** (GitHub Pages rebuilds). `main` is
  shared/edited by others, so always `git fetch origin main` and re-sync before pushing.
- Live URL: `https://inoshikafernando.github.io/europeTrip/magazines/NN-country-YYYY.html`.

---

## 8. Rollout status

- ✅ **03 · Austria** — complete memoir (v3), built from the family's real photos and words
  across all four chapters (Salzburg, Burg Altpernstein, Hallstatt, Vienna). **This is the
  reference implementation — when in doubt, copy it.**
- ▶️ **Next:** issues that already have real family material (China has the most) get
  converted to this memoir format one at a time. Each needs the family's real notes/
  photos before it can be written — see §1.
- ⏳ Remaining issues stay as-is until their real content arrives, then follow this runbook.
