# Journaling Notes — Munasinghe Travel Magazine (handoff / continuity file)

> **Purpose:** A private working note so any Claude Code session can pick up the
> travel-journaling project instantly. NOT part of the published magazines.
> To resume in a new session, say: *"Read JOURNALING_NOTES.md and let's continue."*

_Last updated: Prague photo album fully wired in — 13 real photos placed across the issue (incl. St Vitus family cover + 6 new pages). See "Photo workflow" for the transcript-extraction recovery method (uploads stopped persisting to disk again)._

---

## The project

The family is travelling China → Europe → home (10 Jul – 7 Aug 2026, ~30 nights,
billed as "15 countries, 33 cities"). There are 14 per-country magazine issues in
`magazines/NN-country.html`, static HTML published via GitHub Pages. As the family
tells us what really happened, we replace the pre-trip **imagined placeholder** text
with **real experiences**, keeping each issue's exact HTML structure, classes, and
warm magazine-editorial tone.

## The family (the Munasinghes)

- **Navin** — dad · **Lana** — mum (parents; sign-offs read "Navin, Lana, Avisha, Aviann & Avin Munasinghe")
- **Avisha** — 11, **boy**
- **Aviann** — 8, **girl**
- **Avin** — 4, **boy**

## House style

- Warm, literary, magazine-editorial. Match each issue's existing voice.
- **NZ/British spelling** (colour, favourite, honour, etc.).
- Reuse each issue's own CSS classes & accent colours — don't invent new looks.
  - China: red `#8b1a1a` + gold `#c89b3c`
  - Germany: blue `#1b4f8e` + green `#0a7a3a`
  - (Each issue has its own palette; check the file's `<style>`.)
- New pages use existing page classes (`mag-spread`, `mag-duo`, `mag-food`, etc.).
- Give inserted pages **descriptive non-numeric folios** (e.g. `— Issue 01 · China · Arrival —`)
  so existing numbered folios/TOC don't need renumbering.

## Recurring series elements (the "book series" feel)

- **"The Journey / Story So Far"** front page with a **route rail**
  (issue order 01→14 + ⌂ Home; `★` = you are here, done = ticked, upcoming = muted).
  Built in China (Ch.1), Austria (Ch.2), Czechia (Ch.3). **TODO: roll out to the remaining 11 issues.**
  CSS (`.mag-journey`, `.jr-*`) is added per-file with that issue's accent colour
  (China red #8b1a1a/#c89b3c; Austria blue #28508c/#c89b3c; Czech red #6e1313/green #325437).
- **"Where We Head Next"** = the existing back-cover NEXT ISSUE teaser (already in each issue).

## Route (issue order) & multi-touch countries

01 China · 02 Austria · 03 Czechia · 04 Hungary · 05 Slovenia · 06 Italy ·
07 Switzerland · 08 Germany · 09 France · 10 Netherlands · 11 Belgium ·
12 Denmark · 13 Sweden · 14 Vatican · ⌂ Home (NZ)

- **China = 2 touches (bookends):** outbound 10 Jul (Forbidden City), homebound 7 Aug (Great Wall).
- **Germany = 3 touches:** (1) ~11 Jul Munich arrival/walk [being added], (2) 27 Jul Ottobeuren, (3) 5 Aug Aufkirchen + Munich.
- Numbering is **not strictly chronological**: Czech overlaps Austria; Belgium is a
  day-trip inside the Netherlands stay; **Vatican (Issue 14) is really 22 Jul** during the
  Rome/Italy leg — kept as a special *finale* issue that springboards to Home.

## Photo workflow (IMPORTANT — established mid-trip)

- **Real trip photos live in `images/day-01/` … `images/day-31/`** (by trip day, matching the
  itinerary: day-02 Beijing, day-03 Munich+Salzburg, day-04 Hallstatt, day-05 Prague arrival,
  day-06 Prague full day, day-07 Vienna, …). NOTE: many pre-existing files there are **reference/
  stock images from planning** (some of skipped spots, e.g. day-04 bone-house), NOT the family's
  own photos — don't trust them as "what they did."
- **The user sends real photos in chat**; they arrive as real files at
  `/root/.claude/uploads/<session>/<name>.jpg` (Read + copy). **CRITICAL: the user must send the
  image ALONE — no caption text in the same message — or it arrives as a preview only and NO file
  is saved.** Image alone = file; image + text = preview. Ask for captions in a separate message.
- **KNOWN ISSUE:** the upload pipeline sometimes stops persisting files to
  `/root/.claude/uploads/…` — every photo comes as preview-only (I can *see* it but there's no file
  on disk). **RECOVERY METHOD THAT WORKS (use this, don't wait for a fresh session):** the images
  ARE stored as base64 inside the session transcript at
  `/root/.claude/projects/-home-user-europeTrip/<SESSION-ID>.jsonl`. Extract them with a small
  Python script: walk each JSON line, find `{"type":"image","source":{"type":"base64","data":…}}`
  blocks, `base64.b64decode`, **dedupe by md5** (your own Read-tool image views get re-embedded as
  dupes), write in order → you get every photo the user sent, full quality. Re-run the script as
  more photos arrive (it's idempotent). This session recovered all 19 photos this way.
- **Process each photo** (needs `pip install Pillow`): EXIF-straighten, resize long edge ~2000px,
  save JPEG q82 → ~300–600 KB. `ImageOps.exif_transpose(im); resize; im.save(dst,'JPEG',quality=82,optimize=True)`.
  Phone photos often have EXIF orientation 6/8 and MUST be transposed or they show sideways.
  Save into the matching `images/day-XX/` with a descriptive name.
- **Wire in as a FULL, UNCROPPED photo** (user insisted — NO cropping): use a `.sp-photo` block,
  NOT the cropping `background-size:cover` hero:
  `<div class="sp-photo"><img src="../images/day-XX/<file>.jpg" alt="…"><div class="ph-info">Photo · Munasinghe</div></div>`
  with CSS `.sp-photo img { max-width:100%; max-height:150mm; }` (shows whole frame). Add that CSS
  per issue file. DELETE leftover striped `ph-name` placeholder boxes on pages with no photo.
- **LAYOUT CONSTRAINT (important):** every `.mag-page` is a FIXED `210mm × 295mm` with
  `overflow:hidden`, so anything past the bottom is silently CLIPPED. Budget ≈ **one 150mm `.sp-photo`
  per page** + eyebrow/headline/deck/meta + a compact 2-col text block (≈2 short paras + a quote).
  For lots of photos, make **more pages** (each a `.mag-spread` with a descriptive folio), don't stack.
- **VERIFY BEFORE PUSHING:** render the file with headless Chromium and screenshot each `.mag-page`
  to catch clipping. Playwright lives at `/opt/node22/lib/node_modules/playwright`; chrome at
  `/opt/pw-browsers/chromium-1194/chrome-linux/chrome`. Screenshot per `.mag-page` element, eyeball each.
- **Style = Option A:** clean photo, NO watermark. Rich `sp-caption` + discreet `Photo · Munasinghe` chip.
- **Prague photos placed (all real, uncropped):** Old Town → St Nicholas (`day-06/09`), Charles
  Bridge → family@tower (`day-05/06`), Astronomical Clock → orloj (`day-05/07`), Josefov → yellow
  Široká street (`day-06/08`).
- **Cover = A (family photo, full cover). DONE:** now the **St Vitus cathedral family photo**
  (`day-06/12-st-vitus-family.jpg`) — the family across the bottom, cathedral soaring above.
  Masthead/title at TOP (`.mag-cover` inline `justify-content:flex-start`); gradient dark-at-top for
  the title, light at the bottom so faces stay clear. Image ratio ≈ page ratio, so `center 42%/cover`
  shows nearly the whole frame.
- **OPEN user feedback — BOTH ACTIONED:** (1) "wrong picture in wrong place" → the **red-rooftop
  panorama** (`day-06/13`) is now the **Old Town / King's Landing** hero; the old stock St-Nicholas
  exterior was removed from that page. (2) "add more content" → wrote **6 new pages** from the album
  (Kohl Fountain, Bridge Saints/St-John-of-Nepomuk, Old-Town Streets, Týn Church, St Nicholas Church,
  Jewish Town Hall) + real family photos onto the Castle & Clock pages.
- **PHOTOS THE USER SENT — ALL RECEIVED & PLACED (this session, via transcript extraction).** Final
  homes (Issue 03):
  1. St Vitus cathedral family (`day-06/12`) → **COVER**. ✓
  2. Family close-up, mountain bg → new **"Just Before Leaving"** closing page (`day-06/16`),
     captioned "just before leaving" (per user; deck kept location-neutral since it's not Prague). ✓
  3. Kohl Fountain (`day-06/10`) → new **Kohl Fountain** page. ✓ (2nd near-dup `day-06/11` HELD.)
  4. Red-rooftop panorama (`day-06/13`) → **Old Town** hero. ✓
  5. Jewish Town Hall (`day-06/15`) → new **Jewish Town Hall** page. ✓
  6. Family at castle viewpoint (`day-06/14`) → **Castle** page hero. ✓
  Plus more they streamed in: Charles-Bridge **St-John-of-Nepomuk** cross+locks (`day-05/10`) → new
  Bridge-Saints page; **family at the Astronomical Clock** (`day-05/12`) → swapped onto Clock page;
  **Old-Town street** candid (`day-06/17`) → new Streets page; **Týn Church** (`day-06/20`) + **St
  Nicholas interior** (`day-06/18`) → two new church pages.
- **HELD (processed & in repo, NOT placed — offer as swaps):** `day-06/11` kohl-detail,
  `day-06/19` st-nicholas-exterior, `day-06/21` tyn-closeup, `day-05/08` charles-bridge-walk,
  `day-05/09` old-town-bridge-tower-arch, `day-05/11` bridge-crucifix-calvary, `day-05/13`
  astronomical-clock-tower. (One near-duplicate clock shot the user flagged "same" was skipped.)

## Publish workflow

- Develop on the session's designated branch (this session: **`claude/prague-photos-journaling-l70djc`**).
- Commit → push branch → fast-forward merge into **`main`** → Pages rebuilds.
- Live URL pattern: `https://inoshikafernando.github.io/europeTrip/magazines/NN-country.html`
- The **user also edits `index.html`, `guide.html`, `schedule.html`, `day_*.html` directly on `main`.**
  If a push to main is rejected, re-sync: `git fetch origin main` → merge `origin/main`
  into the branch → `git reset --hard origin/main` on main → `git merge --ff-only <branch>` → push.
- User has approved publishing straight to the live site (all reversible).

## Progress log

- **Issue 01 China — outbound DONE & live.** Added: The Journey (recap+rail),
  Before We Left (packing), Arrival in Beijing, The Palace Day, The Long Day's End
  (+ Avin fever postscript). **Pending:** homebound Great Wall (7 Aug) → then rewrite
  China's Reflections page to cover all of China.
- **Issue 08 Germany — IN PROGRESS.** **Visit 1 arrival page DONE & live** (Munich
  landing ~11 Jul: torn backpack, stroller kept separately, €25 airport shower, car
  pickup, driving on the right). Welcome updated "two doses" → three; cover dates now
  11 Jul · 27 Jul · 5 Aug. **Visit 1b (Munich on foot) DONE & live:** REWE picnic lunch
  (salads, hot dogs, Brezel), Marienplatz, St. Peter's Church, two living-statue performers
  (black/gold + sand/mud) the kids loved. Touches 2 & 3 (Ottobeuren 27 Jul, Aufkirchen/Munich
  5 Aug) still imagined placeholder. NOTE: placeholder "Munich in Three Squares" duo (Marienplatz
  etc.) is for the 5 Aug visit — reconcile if they revisit. Open thread: replacement backpack.
- **Issue 02 Austria — IN PROGRESS.** Added "The Journey" recap page (Ch.2, route rail) +
  a real, deeply personal Salzburg spread. **Lana's Sound of Music story** is the heart of it:
  favourite childhood film, played Maria (sister as Liesl, dolls for the other kids), watched
  it 100+ times ("every time I was in Austria in my mind"), and after 30 years did the fountain
  splash + stood at the garden gate for real with her own kids watching. Real visit was a rushed
  noon–afternoon (11 Jul): Mirabell Gardens, streets, ice-cream, **fortress seen only from afar,
  Mozart's birthplace skipped, running 2 hrs behind to reach church.** The imagined "Salzburg in
  Three Squares" duo was **DELETED** (Mozart birthplace/fortress not really visited). Hallstatt &
  Vienna pages still imagined placeholder (Austria block 11–15 Jul; confirm if/when they do them).
  Added "The First Night" page (Sat 11 Jul eve): Saturday Mass finished 7:45pm; **Austria shops
  shut at 6pm Sat** so missed grocery dinner; grabbed pizza/pasta at a restaurant just before it
  closed (unexpected cost); stayed at **Burg Altpernstein castle — no lift, hauled heavy bags to
  3rd floor** (historical castle); bath, bed, exhausted. NOTE: file page order is Hallstatt →
  Salzburg → First Night → Vienna (Hallstatt/Vienna still placeholder) — reorder to chronological
  when those two are made real.
- **Hallstatt (Sun 12 Jul) now REAL & reordered** into date order (Salzburg → First Night →
  Hallstatt → Vienna). Real visit: woke 5am fresh (bath fixed the jet-lag), castle breakfast
  buffet 7:15/7:30 (cheese, ham, salads, dips, juice, cereal); drove to Hallstatt, arrived
  ~10:30 (not yet hot); **salt mine was CLOSED**; very crowded; did a village walk + a boat
  ride on the Hallstättersee; didn't eat there (full from breakfast) but **tried Wiener
  Schnitzel on the drive back**. Imagined Hallstatt (funicular/mining tunnel/60m slide) removed.
  Only Vienna (Wed 15 Jul, Schönbrunn/Hofburg) left as imagined placeholder in Austria.
- **Issue 03 Czechia/Prague — NEARLY DONE.** Real pages now: The Journey (Ch.3 rail) · Road to
  Prague (Mon 13, dawn castle departure) · Arrival in Prague (first laundry at Andy's Laundromat
  Vinohrady, torn-backpack replacement not found nearby → drive needed, supermarket donuts) ·
  Prague Castle (Mon 13 pm: castle + St Vitus Cathedral + St George's Basilica; **cathedrals felt
  grander than the castle**; kids tired → mini tourist train w/ English commentary; tram tip =
  **buy tickets on board, kids ride free**; on way down sat in park w/ Girl-and-Dove statue for a
  **spiral "tornado" potato + trdelník ice-cream/Nutella**) · Charles Bridge & the Clock (Tue 14:
  left apartment 8am, on bridge ~8:15, **almost empty**; then Astronomical Clock show) · Old Town
  (**"looks like King's Landing" (GOT)**, majestic/un-photographable, luxury-brand shops match the
  grandeur). Removed imagined pages: old Charles Bridge (5:30 dawn fiction), Old-Town clock page,
  duplicate Prague Castle duo (Golden Lane/Kafka/guard). **They SKIPPED the river cruise.**
  **PHOTO ALBUM NOW FULLY WIRED IN (this session):** the family streamed their whole Prague album;
  ~16 placed, incl. St Vitus family COVER + many new pages: Kohl Fountain, Bridge Saints, Old-Town
  Streets, Týn Church, St Nicholas Church, Jewish Town Hall, **St George's Basilica, Tomb of St
  Ludmila, The Old Royal Palace (Land Rolls)** + real family photos onto the Castle & Clock pages +
  a "Just Before Leaving" closing portrait. Issue is now **22 pages**; every page verified
  non-clipped via headless-Chromium screenshots. TOC updated (grouped entries so the Welcome page
  doesn't overflow). ~10 extra/near-dup photos HELD in repo as possible swaps (St Nicholas exterior,
  Týn closeup, 2nd Kohl, bridge walk/tower/crucifix, clock tower, St George nave/apse/relief, palace
  heraldic wall/ceiling, castle model). **PUBLISH MODE:** user said "publish as you go / no need to
  create branches" — so commits now fast-forward straight into **main** (live) each turn.
  **STILL TODO for Prague:** Tastes of Bohemia food page still has striped placeholders (real so far:
  trdelník + tornado potato — the two food photos `images/czech/food-*` don't exist yet). Reflections
  page is written but could gain the family's own favourite/hardest/if-we-come-back words. Then
  Austria's Vienna (Wed 15 Jul) is next chronologically. Open thread: still need to buy the
  replacement backpack.
- **Issues 04–07, 09–14 — untouched** (imagined placeholder). Real reflections to come as they travel.
- **Austria still open:** Vienna page (Wed 15 Jul — comes AFTER Prague chronologically), Tastes
  of Austria food page, and Reflections all still imagined placeholder.

## Real details captured so far (facts to reuse — keep consistent)

**China arrival (10 Jul):** landed ~4:30am; hand-luggage only (skipped baggage claim);
WeChat message → hotel shuttle; guide said bring raincoats but they were in the checked
bag → bought ponchos; WeChat Pay rejected some cards → paid via AliPay (cards deliberately
split across apps as backup); Google Maps said 30 min, real trip 90 min → **use Didi, not Google**.

**Forbidden City (10 Jul):** arrived 4 min early, guide waited ~5 min in the rain; saw every
room / whole bucket list; rain kept the heat down but sweaty; forgot Avin's stroller → the
4-year-old walked it all; parent's lifelong dream (loves Chinese & Korean historical dramas).
Return: Didi to a wrong same-named hotel; no-English driver kindly phoned the hotel, drove
them there, refused extra fare.

**Departure (10→11 Jul):** wandered near hotel, found a small restaurant, great cheap lunch;
bath + quick nap; flight 02:50am, hotel shuttle ran until 21:30, up at 20:30; at airport Avin
felt cold → jumper → thermal scanner flagged a **minor fever**; it was just exhaustion — slept
on the flight, lots of water (no Panadol, it was in the checked bag), recovered by Germany.

**Packing (China "Before We Left" page):** two seasons (NZ winter → Europe summer);
clothes light with backups (boys shorts + 1 trouser; Aviann dresses + spares; hair bands/oil/gel);
shoes + walking slippers each; sun kit (sunscreen, 5 sunglasses, bucket hats, bottles, aloe);
medicine bag (Panadol/ibuprofen/cetirizine in tablets + syrup, lozenges, Quick-Eze, nasal
spray, plasters, wound cream); school (journals ×5, Avisha Narnia ×2, Aviann Charlotte's Web,
online homework, Avin colouring + activity book); 3 Shein kids' cameras + 32GB micro-SD cards;
clever finds (2.5 kg Kmart folding car seats ×3, eye masks with built-in pillow, EU adapters,
noodles/soup/mac&cheese/3-in-1 coffee from home); bags = 2 big + 4 small backpacks, 1 China
hand-luggage, Avin's strap harness-backpack, a stroller, 3 car seats.

**Germany Visit 1 (11 Jul) — arrival page done:** flight from Beijing landed on time;
immigration + bags; Avin fully recovered; **one big backpack torn** on the carousel (need to
buy a replacement); waited long for the stroller then learned Munich keeps strollers at a
**separate oversized-items point**, not the belt; **Munich Airport public shower** — €25 per
cubicle for 2 hrs, took 1 cubicle, ~45 min to wash all five; **car pickup smooth, kids loved
their car seats**; drove into Munich; **driving on the right** (opposite NZ) felt crazy at
first but adapted within ~30 min. _Awaiting: the 2+ hr Munich city wander (Visit 1b)._
