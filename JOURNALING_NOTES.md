# Journaling Notes — Munasinghe-Fernando Travel Magazine (handoff / continuity file)

> **Purpose:** A private working note so any Claude Code session can pick up the
> travel-journaling project instantly. NOT part of the published magazines.
> To resume in a new session, say: *"Read JOURNALING_NOTES.md and let's continue."*

_Last updated: **Austria (Issue 02) FINALIZED & merged to main — real photo album + real cover.** Family streamed their full Austria album (~35 photos, recovered via transcript-base64 method → `images/austria/`). DONE: gave Salzburg / First Night (Burg Altpernstein) / Hallstatt their real uncropped photo heroes (replaced TBD placeholders); **rebuilt the imagined "Tastes of Austria" food page** (fake Figlmüller/Sacher cards, which were also CLIPPING) into a real schnitzel-lunch feature; added two photo spreads — **"At the garden gate"** (Salzburg: Lana + kids at the Mirabell steps pointing to the fortress) and **"The most photographed village"** (Hallstatt railing); **rewrote the last imagined page "Habsburg Forever"** into the real Schönbrunn day (confirmed by user: only Schönbrunn — NO Hofburg; arrived 4pm, state rooms till 6; NO Gloriette/gardens/concert), hero = the private-salon shot with Franz Joseph & Sisi portraits; **Reflections** now truthful (real "if we come back" = the salt mine + panorama they missed as both were closed; removed the fabricated 60m-slide/funicular; favourite=Mirabell gate, hardest=liftless-castle first night — true placeholders, user may reword); **real COVER** = Stephansdom family selfie (`cover.jpg`, masthead moved to top, gradient so faces stay clear); fixed cover + welcome + back-cover blurbs to match reality. All 23 pages screenshot-verified non-clipping. Austria has NO imagined content left. HELD unplaced Austria photos for optional extra spreads: Salzburg Residenzbrunnen/Getreidegasse/Residenz-facade/Do-Re-Mi-avenue/horse-fountain/family-cathedral(tilted); Hallstatt boat/market-square/postcard-vs-real/street/viewpoint; castle exterior-selfie/breakfast/valley-view; autobahn._

_Earlier: Prague **food + late-album redesign**. Built a reusable magazine photo-collage layout (`.mag-collage` / `.cl-*`) and used it for a 2-page "Tastes of Bohemia" street-food feature (trdelník, tornado potato, family eating), a Mucha-window feature, an Old Jewish Cemetery page, and a Winged Lion (RAF) memorial page — all with rich historical captions. Filled the empty "Road to Prague" page with the trdelník-through-a-street photo. Uploads still preview-only → used transcript extraction again._

_Then (St Vitus interior pass): swapped the "Inside St. Vitus" hero to the wide **nave-vault** shot (`day-06/39`), and added two `.mag-spread` pages — **"The Silver Saint"** (Nepomuk's silver tomb `day-06/40`) and **"In Bronze"** (bronze memorial group `day-06/41`). Old `31-st-vitus-interior.jpg` now unused. **NOTE:** headless check flagged the **"Tastes of Bohemia"** collage page as overflowing ~208px — worth a re-check._

_Then "≥1 photo per attraction" pass DONE (added 6 `.mag-spread` pages, Chromium-verified, photos already in repo): Kohl Fountain → detail `11`; St George's → nave `24`; Old Royal Palace → heraldic ceiling `29`; Throne → Crown Jewels `33`; Týn → towers `21`; St Nicholas → exterior `19`. Prague issue ~33 pages, and a Prague "second photo for six attractions" pass also landed on main._
>
> _Then: **fixed the "Tastes of Bohemia" collage overflow** — root cause was `.cl-grid` being a flex child without `min-height:0`, so its `height:100%` images ballooned to intrinsic height; added `min-height:0` to `.cl-grid` (safe for all collage pages). **Added the Astronomical Clock's 2nd photo:** the all-five family selfie under the Old Town Hall tower → `day-06/42-clock-family-selfie.jpg`, new page "All Five of Us". Whole issue re-verified 0 clipping. **Brno:** user asked to add Brno photos but NONE are in the transcript yet — awaiting upload (each alone). Held-but-unused Prague photos: `25/26/28/30/31` + St Vitus extras (mucha-selfie/apse/saints/flame/royal-tomb/chapel) in transcript._

---

## The project

The family is travelling China → Europe → home (10 Jul – 7 Aug 2026, ~30 nights,
billed as "15 countries, 33 cities"). There are 14 per-country magazine issues in
`magazines/NN-country-2026.html`, static HTML published via GitHub Pages. As the family
tells us what really happened, we replace the pre-trip **imagined placeholder** text
with **real experiences**, keeping each issue's exact HTML structure, classes, and
warm magazine-editorial tone.

## The family (the Munasinghe-Fernandos)

- **Avinesh** ("Avi") — dad · **Lana** — mum (parents; magazine sign-offs read "Avinesh, Lana, Avisha, Aviann & Avin Munasinghe-Fernando").
  - NOTE: his **full legal name is "Navin Avinesh Welikala Munasinghe-Fernando"** — he *goes by* Avinesh/Avi (the kids' names all echo it: Avinesh → Avisha, Aviann, Avin). Magazines use **Avinesh** (family voice); the **`day_*.html` booking/logistics pages keep the legal "Navin …"** on tickets/licence/hotel so they match his documents — do NOT change those. (Corrected across all 14 issues this session per Lana's confirmation.)
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
- **Slovenia (Issue 05) was a DRIVE-THROUGH, NOT a stop (user-confirmed).** Coming
  **Hungary → Italy** the family passed **through Slovenia with no stop — they SKIPPED Lake Bled.**
  So Issue 05 has **no real content** and should NOT imply a Bled/Ljubljana visit; keep it a
  transit note (the Italy welcome line "we crossed the Alps from Slovenia" is fine as-is). Do not
  invent a Slovenia day. If it becomes a real issue later it's a "the country we only drove across"
  page, not a sightseeing one.

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
  `<div class="sp-photo"><img src="../images/day-XX/<file>.jpg" alt="…"><div class="ph-info">Photo · Munasinghe-Fernando</div></div>`
  with CSS `.sp-photo img { max-width:100%; max-height:150mm; }` (shows whole frame). Add that CSS
  per issue file. DELETE leftover striped `ph-name` placeholder boxes on pages with no photo.
- **LAYOUT CONSTRAINT (important):** every `.mag-page` is a FIXED `210mm × 295mm` with
  `overflow:hidden`, so anything past the bottom is silently CLIPPED. Budget ≈ **one 150mm `.sp-photo`
  per page** + eyebrow/headline/deck/meta + a compact 2-col text block (≈2 short paras + a quote).
  For lots of photos, make **more pages** (each a `.mag-spread` with a descriptive folio), don't stack.
- **VERIFY BEFORE PUSHING:** render the file with headless Chromium and screenshot each `.mag-page`
  to catch clipping. Playwright lives at `/opt/node22/lib/node_modules/playwright`; chrome at
  `/opt/pw-browsers/chromium-1194/chrome-linux/chrome`. Screenshot per `.mag-page` element, eyeball each.
- **Style = Option A:** clean photo, NO watermark. Rich `sp-caption` + discreet `Photo · Munasinghe-Fernando` chip.
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
- Live URL pattern: `https://inoshikafernando.github.io/europeTrip/magazines/NN-country-2026.html`
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
  (black/gold + sand/mud) the kids loved. Touch 2 (Ottobeuren 27 Jul) still imagined
  placeholder. **Touch 3 (Full Circle, the way home) now REAL:** flew Gothenburg → Munich,
  landed ~8:30pm; stashed the bulk of the luggage in an **airport locker**, carried out only
  night + next-day clothes so the hop was light; taxi to a **Mercure at Aufkirchen** (village
  near MUC) for the last European night; **bus** back to the terminal next morning, T2 check-in
  ~10:30, China Air → Beijing (Great Wall stopover) → home. Replaced the old "Novotel by the
  terminal" fiction; added the Mercure reference photo. **Real arrival photos wired in (this
  session):** the €25 **airport shower** family shot (day-03/02) on the "First hours" page, and
  the **REWE street-picnic** family shot (day-03/03) as a two-up beside the Marienplatz selfie on
  "City on Foot." Both baked for EXIF rotation (were orientation 6). Wove in the family's own
  reflection that **Marienplatz "holds both old and modern"** (grand stone/spires vs. modern
  shopfronts). Open thread: replacement backpack.
  **16 Marienplatz photos now placed (this session):** two new album spreads after "City on
  Foot" — **"The Living Statues"** (the gold plinth performer + the sand/mud reclining performer,
  the kids' favourite, + three family/kids shots at the Mariensäule) and **"Old & New"** (Neues
  Rathaus facade, a Baroque church interior [captioned safely, not asserting St Peter's],
  Kaufingerstraße shopping street tying to the old/modern reflection, market tents, an old-town
  church, the family walking the back lanes). Frauenkirche onion-dome **family selfie** added to
  the Glockenspiel page. All EXIF-baked (orientation 6). TOC + page numbers resynced (issue now
  15 pages). HELD in repo as near-dup swaps: 18-marienplatz-wide, 20-marienplatz-panorama,
  21-oldtown-church-street. Every page verified non-clipping via headless Chromium.
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
  Ludmila, The Old Royal Palace (Land Rolls), Inside St. Vitus (rose window), The Throne of
  Bohemia** + real family photos onto the Castle & Clock pages +
  a "Just Before Leaving" closing portrait. Issue is now **24 pages, all live on `main`**; every page verified
  non-clipped via headless-Chromium screenshots. TOC updated (grouped entries so the Welcome page
  doesn't overflow). ~10 extra/near-dup photos HELD in repo as possible swaps (St Nicholas exterior,
  Týn closeup, 2nd Kohl, bridge walk/tower/crucifix, clock tower, St George nave/apse/relief, palace
  heraldic wall/ceiling, castle model). **PUBLISH MODE:** user said "publish as you go / no need to
  create branches" — so commits now fast-forward straight into **main** (live) each turn.
  **PENDING (re-send in the fresh session, each ALONE):** the family had just started sending **St.
  Vitus cathedral interior** photos when this session got too big — a wide **nave-vault** shot, the
  **stained-glass apse windows** (world-famous, incl. a Mucha window; some scaffolding visible from
  restoration), and a **bronze memorial group** under a Gothic arch. One attachment was **"too large"**
  and didn't upload — ask them to resend a smaller version. Good next move: a **"Windows of St. Vitus"**
  stained-glass page, and optionally swap the interior hero to the nave-vault shot. (Current interior
  page uses the rose-window shot `day-06/31-st-vitus-interior.jpg`.)
  **NEW magazine-collage layout (this session):** added `.mag-collage` page type + `.cl-*` classes — an
  asymmetric 12-col grid (`grid-template-rows:repeat(4,1fr)` fills the fixed page exactly → no clipping),
  photo `figure.cl-fig` with `.cl-over` gradient caption, boxed `.cl-note` text tiles, and (for
  single-photo feature pages) an unboxed `.cl-side` editorial sidebar with a `.cl-accent` callout pinned
  to the bottom (`margin-top:auto`) so whitespace reads as intentional, not an empty box. Rich
  descriptive/historical captions per the user's brief ("what is it, why important, history").
  Rotation gotcha: the family selfie had NO EXIF tag but a tilted candid composition — do NOT rotate it;
  give it a wide-ish cell so all five stay in frame.
**Prague food/late-album DONE:** Tastes of Bohemia is now a 2-page collage feature (trdelník ice-cream,
  tornado potatoes, kids + Aviann + all-five selfie) with a trdelník/tornado history note. New pages:
  **The Mucha Window** (after Inside St. Vitus), **The Old Jewish Cemetery** (in Josefov, after the intro
  street page), **The Winged Lion** RAF memorial (after St. Nicholas). Road-to-Prague page now carries the
  trdelník-ring-through-a-street photo. Photos live in `images/czech/food-*`, `images/czech/trdelnik-*`,
  `images/czech/tornado-potato-kids.jpg`, `images/czech/food-family-selfie.jpg`, and
  `images/day-06/34..37`. **HELD (not placed, no dup):** Jewish Town Hall clock-tower shot (`img_007`) —
  the Town Hall already has its own page.
**(historical note) earlier STILL TODO — now resolved:** Tastes of Bohemia food page had striped placeholders.
**Post-redesign corrections (user review pass):** (1) The "just before leaving" portrait
  (`day-06/16-family-portrait-mountain`, mountain bg) is actually the **Austria→Prague departure**, not a
  Prague finale — moved it to the **Road page** hero and DELETED the old "One Last Picture" closing page.
  (2) Castle page hero was a city-overlook shot (no castle/cathedral visible) — swapped in a real
  **St. Vitus from the Third Courtyard** photo (`day-06/38-st-vitus-courtyard.jpg`, family crossing below).
  **HELD/unused now:** `day-06/14-family-castle-viewpoint.jpg` (the overlook family shot) — free to place
  if wanted (King's Landing page already has the `day-06/13` panorama). Interim route-map idea
  (`day-05/map.jpeg`) was tried on the Road page then replaced by the portrait. Issue now **27 pages**. Reflections
  page is written but could gain the family's own favourite/hardest/if-we-come-back words. Then
  Austria's Vienna (Wed 15 Jul) is next chronologically. Open thread: still need to buy the
  replacement backpack.
- **Issue 04 Hungary — DONE & LIVE** (Budapest, 16 Jul; see section below). **Issues 05, 07, 09–13 — untouched** (imagined placeholder). Real reflections to come as they travel.
- **Issue 14 Vatican — REAL BUILD STARTED (Wed 22 Jul).** User confirmed Vatican = its own issue (separate country). DONE so far: cover set to the family's St Peter's Square selfie (`images/vatican/cover.jpg` = copy of `day-14/vatican-st-peters-family.jpg`); Welcome rewritten to the user's own reflection — **"a whole new world, crossing from Rome into the Vatican"** (their words, the issue's opening theme). ⚠️ Placeholder differs from the REAL day: **NO Castel Sant'Angelo** (dropped) — actual day = St Peter's (interior + Confessio/tomb) → Vatican Museums → Sistine → back into Rome for **San Giovanni in Laterano + Scala Santa** → **Colosseum at dusk**. Placeholder's Castel Sant'Angelo page (p05), the fabricated kid quotes (Reflections: "Avin shouted We were INSIDE that", "Avisha: I want to learn to draw like that" — INVENTED), and the imagined food page all TO BE REPLACED. **16 St Peter's photos saved** `images/vatican/vday-01..16.jpg` (EXIF-fixed, q82): 01 Baldacchino/Confessio, 02 Bernini Tomb of Alexander VII (winged skeleton+hourglass), 03 Baroque altar relief, 04 Baldacchino+altar, 05 side altar, 06 carved tomb relief, 07 papal statue in pier, 08 evangelist mosaic+bronze crucifix, 09 **PIETÀ**, 10 gilded dome, 11 nave barrel vault, 12 nave interior w/people, 13 hand+Roma postcard vs St Peter's Sq, 14 Bernini colonnade, 15 St Peter's Sq at dawn+obelisk, 16 facade+steps. **TODO (tonight, full build):** uncropped **.sp-photo** pages (NOT the placeholder's cropping .sp-hero/.duo-photo) — "A whole new world" square opener (13/14/15/16), St Peter's vastness (11/12), the tomb/Baldacchino/Confessio (01/04), the Pietà (09), Bernini's Alexander VII tomb (02); Sistine = text page (no photos allowed inside); then Scala Santa + Colosseum pages (photos pending this afternoon). Reconcile TOC, remove Castel Sant'Angelo + invented quotes, screenshot-verify no clipping. Branch = `claude/rome-pompeii-travel-2i8mo6`.
- **Issue 06 Italy — Pompeii feature ADDED (Day 13, Tue 21 Jul).** Built **6** new `.mag-spread` pages inserted after the Rome page (folio "ITALY · 05"), before the food page, all screenshot-verified 0px clip. 6th page = **"The Littlest Explorer — Fifteen thousand steps. Age four."** (`day-13/photo-08-avin-explorer.jpg`): Avin (4) walked all of Pompeii, no stroller, in 40°C heat — callback to the China/Forbidden-City note. The first five: (1) **"Frozen at 79 AD"** — Temple of Apollo + Vesuvius hero (`day-13/photo-02`), eruption/burial/1748-rediscovery story + quote; (2) **"The Forum"** — pair Jupiter+colonnade (`03`+`04`); (3) **"The Antiquarium — What the ash kept safe"** — marble goddess (`05`, compact); (4) **"The People of the Ash"** — plaster cast (`06`) + Fiorelli story + quote; (5) **"Our Day — A missed train, and a day worth it"** — family-on-Frecciarossa + Pompeian street pair (`01`+`07`), the real day (missed the booked FR, rebooked 09:25, da Michele pizza, Circumvesuviana, 40°C heat, dinner at cousin's in Naples). Also fixed the Rome page's outdated "drive from Rome takes 2.5 hours" → Frecciarossa + Circumvesuviana. Photos: family sent them mid-visit, saved raw to `images/day-13/photo-01..07`, EXIF-transposed (orient 6 on most) + resized long-edge 2000 + q82 (300–670 KB), contact-sheet-verified upright. NOTE: they travelled Rome→Pompeii **by train**, not the car day the `day_13.html` logistics page originally assumed (that page was reworked separately this session). **HELD:** none — all 7 sent photos placed. This session's branch = `claude/rome-pompeii-travel-2i8mo6` (NOT main — per session instructions).
- **Issue 04 Hungary — DONE & LIVE** (Budapest, 16 Jul; see section below).
- **Issue 06 Italy — LARGELY REAL** (Venice/Padua/Rosa Mistica/Florence pages built from real photos in `images/italy/`; the earlier "untouched" note was stale). **Rome+Vatican page (folio 05) + the "Tastes of Italy" food grid are still IMAGINED/TBD placeholders** (Rome hero `day-12-colosseum-interior.jpg` and `food-01..06` don't exist as real photos yet). **MILAN SECTION ADDED (23–24 Jul, this session `claude/milano-journal-notes-ucgtyw`):** 7 new pages inserted after the Rome+Vatican page, before the food page — a full-bleed **"Milano" section cover** (all-five family selfie at the Duomo façade, `milan-duomo-family.jpg`), **Piazza del Duomo** (Vittorio Emanuele II equestrian), **the Duomo nave**, **the Windows** (sp-pair: apse + stained-glass rays), **Marble & Sky** (funerary monument + rooftop/Madonnina text), **the Galleria** (sp-pair: arcade + entrance), **"Three under the glass dome"** (the 3 kids). All 9 photos processed to `images/italy/milan-*` (orient-6 phone, exif_transpose; uncropped `.sp-photo`, long-edge 2000px q82). All 7 pages screenshot-verified non-clipping. TOC got a "Milan" entry (page nums bumped 06→07→08); cover cv-meta + reflection sign-off dates extended to 24 Jul. **OPEN Qs for user:** (1) did they actually do the **Duomo rooftop** (I wrote it as "we booked the early lift" per the itinerary — no rooftop photo yet)? (2) did they see **Leonardo's Last Supper**? The cover "INSIDE" features line still promises it but the schedule doesn't include it — reconcile. (3) friends' names / what they ate / the Castello Sforzesco evening — not yet written (no photos). (4) welcome-page prose still says "left Naples on the following Wednesday" — stale now that Milan is the last stop; optional fix.
- **Issues 05, 07, 09–14 — untouched** (imagined placeholder). Real reflections to come as they travel.
- **Austria still open:** Vienna page (Wed 15 Jul — comes AFTER Prague chronologically), Tastes
  of Austria food page, and Reflections all still imagined placeholder.

## Issue 04 Hungary (Budapest, Thu 16 Jul) — DONE & LIVE

**18 pages, all real, published to `main`.** Built live from the family's own photos as they toured.
Pages: real **cover** (all five on Fisherman's Bastion terrace, Danube behind; masthead moved to TOP,
gradient reworked so faces stay clear) · Welcome + TOC rewritten to the real day (drove in, parked Pest →
Basilica → Chain Bridge on foot → funicular up → Buda hill → river; TOC tagged Pest/Buda/River) ·
**Chapter 4 Journey** route rail · **St. Stephen's Basilica ×3** (facade, dome — *Avin (4) climbed to the
top*, Szent Jobb Holy-Right relic) · **Fisherman's Bastion ×2** (white towers; "Under the Arches" 3 kids) ·
**The King in Bronze** (St. Stephen equestrian statue) · **Matthias Church ×4** (family exterior selfie,
painted nave, Béla III tomb, **Treasury collage**: Holy Crown/Sisi/altar cross) · **Buda Castle** (family +
green dome + Prince Eugene statue) · **Danube sunset cruise** finale (family on glass-roofed boat, golden
hour) · **Tastes of Hungary = Lángos** collage (board of three + family dinner + Nutella). Deleted the
imagined **Széchenyi baths** page (they didn't go). Reflections rewritten from the real day.
- **LAYOUT GOTCHAS (this file):** (1) `.mag-collage` grid captions on the BOTTOM-row cell clip — keep photo
  captions out of the last row (put the text `.cl-note` there). (2) Line-based `grid-column:a / b` inline
  placement did NOT render reliably here — use the `.col-N .row-N` **span classes** (all uniform span) OR a
  plain **flexbox** layout (the final food page uses flex: full-width figure on top, inner flex row of two
  below, note last). (3) Several phone photos had **NO EXIF orientation tag** but were 90° off — exif_transpose
  won't fix those; rotate manually and ALWAYS view the saved file.
- **HELD (in repo, not placed):** matthias-church-exterior/apse, matthias interior altar/sanctuary/side-altar/
  laszlo-chapel, fishermans-bastion terrace-parliament-view/towers-close/stairs, bastion-arch-kids-alt,
  panorama-* (chain-bridge/elisabeth/margaret/parliament-dome/parliament-clear), sandor-palace-guard,
  buda-castle-family-alt, langos-classic-pizza/pizza-closeup, basilica-dome-top-kids. Also main's
  `road-to-budapest-family-car.jpg` (a "Road to Budapest" opener was suggested but NOT built — Journey page
  used instead). Vienna **Votivkirche** held at `images/austria/vienna-votivkirche.jpg` for the Austria issue.
- **STILL OPEN:** **back cover** bg image missing (`images/hungary/back-cover.jpg` → use a Parliament-lit /
  Chain-Bridge-at-night cruise shot when sent); optional 2nd cruise "city at night" page.
- **Publishing:** developed on branch `claude/budapest-issue-04-hungary-ij6ich`, fast-forward-merged to `main`
  each turn (live). Dad's sign-off name is **Avinesh** (main corrected Navin→Avinesh across all 14 issues).

### (original plan, kept for reference)

Family's own plan for the Budapest day: **St. Stephen's Basilica** (9–5) · **Matthias Church** (9–5)
· **Fisherman's Bastion** · **Castle Hill funicular** (Budavári Sikló, ~8am–10pm) · **Danube sunset
cruise** (~8:30pm). Buda-side cluster = Castle Hill (Matthias Church + Fisherman's Bastion + Buda
Castle, reached by the funicular); Pest-side = Basilica + (suggested) Parliament, Shoes on the
Danube, Chain Bridge, Great Market Hall. NB timing: the funicular "8–10pm" and the 8:30 cruise
overlap — do Castle Hill late-afternoon or after the cruise. Build Issue 04 from real photos/details
as they arrive, same rich-history treatment as Vienna. (This is the leg being handed to a fresh
session — see the resume prompt given 15 Jul evening.)
**Parking chosen:** **Central Passage Parkoló** (Király utca 8–10, District VI, by Deák Ferenc tér)
— central Pest, ~6 min walk to St. Stephen's Basilica; park once, whole day on foot/tram-2/funicular,
return here after the cruise. **Route given (min-stairs, funicular):** Central Passage → Basilica →
Parliament + Shoes on the Danube → tram 2 / Chain Bridge → funicular UP → Castle Hill (Buda Castle,
Matthias, Fisherman's Bastion main terrace, skip paid turrets) → down → dinner → 8:30 sunset cruise.
**Set off 7:30am Thu 16 Jul** — `images/hungary/road-to-budapest-family-car.jpg` (all five in the car,
happy) = natural **"Road to Budapest" opener** for Issue 04.

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

**Brno → Vienna travel day (Wed 15 Jul) — CAPTURED, page not built yet:** again woke early;
packed; walked to fetch the vehicle from the (car) park. Planned to leave Prague at 10am but
**left at 8am** — so decided to spend a bit of time in **Brno** on the way. At 8:30am they were
on the road. **Route now confirmed: Prague → Brno → Vienna** (so Brno is a stop en route, and
**Vienna is still the next issue-02 Austria destination**, reached 15 Jul via Brno — this
reconciles the earlier "Vienna = Wed 15 Jul" note). **The Brno reason = nostalgia:** ~12 years
ago **Avinesh ("Avi", the dad — CONFIRMED)** came to Brno on an **office/work tour**, and the family
wanted to bring back those old memories. Awaiting: what they did/saw in Brno, the company/place
Avi visited, whether they went back to that actual building, and photos (send ALONE, no caption
in same message). Good page idea: a warm **"Return to Brno"** memory-lane feature for Issue 02
(Austria) or Issue 03 (Czechia).
**PHOTOS RECEIVED (last morning in Prague → setting off) — processed & in repo at `images/day-07/`,
NOT yet placed on a page:** (1) `leaving-prague-family-apartment.jpg` — all five outside their
Prague stay, the **"Gold Art Apartments"** door (had NO EXIF tag + stored sideways → fixed with a
manual ROTATE_90; note this gotcha). (2) `leaving-prague-kafka-monument.jpg` — Avisha at the
**Franz Kafka Monument** (Jaroslav Róna's bronze, man on an empty suit, Jewish Quarter). (3)
`leaving-prague-street-aviann.jpg` — Aviann on a sunlit cobbled Old-Town street. (4)
`leaving-prague-powder-tower.jpg` — the **Powder Tower / Prašná brána** Gothic gate, near-empty
early street. (5) `leaving-prague-powder-tower-family.jpg` — all-five selfie under the Powder
Tower. (6) `road-to-brno-in-car-family.jpg` — all-five in-car selfie setting off (EXIF orient 6,
auto-transposed to portrait). All uncropped, long-edge ~2000px, q82. Awaiting per-photo captions.
Natural home: a new **"The Last Morning in Prague / Road to Brno"** travel-day opener for the
15 Jul leg (day-07).
**VIENNA (Wed 15 Jul) — ARRIVED, real content starting:** after the Brno detour they reached
**Vienna**. First thing captured: they're **hearing the love story of Emperor Franz Joseph I &
Empress Elisabeth ("Sisi")** — the classic Habsburg romance (Franz Joseph was meant to marry
Sisi's elder sister Helene but chose 15-yr-old Sisi at Bad Ischl in 1853; her free-spirited,
melancholy life at court; assassinated in Geneva 1898). This is the storyline of **Schönbrunn
Palace** and the **Hofburg / Sisi Museum** audio tours — CONFIRM which venue they heard it at.
This makes the **Vienna page (Issue 02 Austria) REAL at last** — replace the imagined placeholder
with the Sisi story as its heart (echoes Lana's Sound-of-Music thread: another woman's story that
Austria makes vivid). NB spelling: "Sisi" (Austrian) not "Sissi" (the films).
**VENUE CONFIRMED = Schönbrunn Palace** (they photographed the palace's history boards).
**DONE THIS SESSION — 3 new history pages added to Issue 02 (magazines/02-austria-2026.html),
after the existing imagined "Habsburg Forever" Vienna page (folio 05), all screenshot-verified
non-clipping:** (1) **"The emperor who chose the wrong sister"** — the Franz Joseph & Sisi love
story (Bad Ischl 1853, the rigid court, Hungary/1867 Compromise, Mayerling 1889, Geneva 1898,
68-yr reign; ties to Lana's Sound-of-Music thread). (2) **"Echoes of a Monarchy"** — a photo
page showing their own (uncropped) shot of the Schönbrunn timeline/empire-map board
(`images/austria/schoenbrunn-panel-echoes-map.jpg`); added a new `.sp-photo` CSS class to this
issue for uncropped `<img>` photos. (3) **"The autumn Vienna stopped an empire"** — the 1529
First Siege (Suleiman the Magnificent, Mohács 1526, Count Niklas von Salm, the rain + mining war,
withdrawal; nods to the 1683 second siege / Sobieski). All use descriptive folios (no TOC
renumber). Text-forward pages sit ~55–60% filled (clean essay look) — could grow if they send a
real family-at-Schönbrunn photo (would headline the Sisi page).
**HELD panels (processed, in `images/austria/`, NOT placed — offer as swaps/extra pages):**
`schoenbrunn-panel-genealogy.jpg` (Habsburg family tree 1740–1918) and
`schoenbrunn-panel-monarchy-end.jpg` (Leopold II → end of monarchy 1918).
**SCHÖNBRUNN STATE-ROOMS PHOTOS (15 Jul) — 39 sent, all saved & EXIF-oriented at
`images/austria/schoenbrunn/NN.jpg`** (NN = 01..39 by capture order; stable semantic copies made
for the placed ones: `great-gallery.jpg`=23, `great-gallery-ceiling.jpg`=24,
`immersive-projection.jpg`=04, `maria-theresa.jpg`=06, `emperor-court-dress.jpg`=05,
`rococo-clock.jpg`=13, `imperial-table.jpg`=18, `private-salon.jpg`=11). Orientation gotcha:
this phone tagged ALL of them EXIF-orientation 6 → `ImageOps.exif_transpose` fixes every one
(the Read/preview tool shows RAW pixels so they LOOK sideways in preview — trust exif_transpose,
verified via a contact-sheet montage; script in scratchpad).
**DONE — new 4-page "Inside Schönbrunn" feature added to Issue 02**, inserted right after the
imagined "Habsburg Forever" page (folio 05), all screenshot-verified non-clipping:
(1) **The Great Gallery** (`great-gallery.jpg`, kids gazing up at the Guglielmi ceiling; history:
Maria Theresa's ballroom, 1760 fresco bombed 1945 & restored, Congress of Vienna balls 1814,
JFK–Khrushchev 1961). (2) **A History in Light** (the immersive projection room; palace history:
hunting lodge→1441 rooms, "Schönbrunn yellow", Mozart 1762, Napoleon HQ 1805/09 & his son d.1832).
(3) **Maria Theresa** (portrait, uncropped; 40-yr reign, 16 children incl. Marie Antoinette).
(4) **How They Lived** (mag-duo: rococo clock + laid imperial table; Spanish court ceremonial +
family warmth). Added `.sp-photo.compact` CSS (max-height 116mm) for photo+text pages. Descriptive
folios (no TOC renumber). NB: for the `.mag-duo` page, fixed photo `height:104mm` + `aspect-ratio:auto`
(a percentage/flex height chain collapsed the fixed mag-page box — avoid).
**HELD (saved, unplaced — offer as more pages/swaps):** ~31 other Schönbrunn interiors incl. the
Bergl garden-landscape rooms (#33/38/39), more state salons (#08/09/11/12/22/29/32), Franz-Joseph/
Sisi-era private rooms (#10/14/15), archduchess portrait pairs (#16/17), ceiling-fresco details
(#24/26/27/28), the emperor-in-court-dress portrait (#05), gilt wall details (#25/30/31). Could
become an "Imperial Portraits" page and a "State Rooms" collage page.
**Evening (Wed 15 Jul) — DONE: 4-page evening feature built** (Issue 02, inserted after "The Siege
of 1529", before the food page; all screenshot-verified non-clipping):
(1) **Stephansdom (exterior)** — `stephansdom-tower-roof.jpg` + cathedral history (1147 origin, 136m
"Steffl" south tower, ~230k-tile roof w/ Habsburg double-eagle, catacombs, 1945 fire → rebuilt 1952).
(2) **Inside Stephansdom — "Honestly, I had no words"** (user's own words) — mag-duo, nave + Baroque
altar photos + the speechless-interior moment + Gothic interior notes (pulpit c.1500, Wiener Neustädter
altar, Frederick III tomb). (3) **An Evening Walk — "One walk, four Viennas"** — 2×2 photo grid:
State Opera+Lorelei fountain (music), Marc-Anton/Secession (Jugendstil/Klimt), fiaker (old town),
Capistran monument (the Ottoman-frontier tie). (4) **"Prague or Vienna?"** reflection — the user's
recurring dilemma in their own voice ("majesty that suits the castle"; "found" vs "commissioned"
beauty; heart big enough for both), weaving real Prague (King's Landing, empty Charles Bridge,
trdelník) + Vienna (Schönbrunn, Sisi, the wordless cathedral) moments. Uses existing classes +
inline grid; no new CSS beyond earlier `.sp-photo.compact`.
**Evening photos saved in `images/austria/`:** stephansdom-tower-roof, -capistran-pulpit,
-interior-nave, -interior-nave-windows (held), -interior-side-altar (held), -interior-baroque-altar,
vienna-fiaker, vienna-fountain-facade (=State Opera/Karajan-Platz), vienna-marc-anton-secession.
HELD/unused: interior-nave-windows, interior-side-altar (offer as swaps/extra interior page).
**(earlier context) Evening (Wed 15 Jul):** after Schönbrunn, into central Vienna; walked the old
town to Stephansdom. Sightseeing/tower hours were
done for the day (closed 16:30/17:30) so this is the free interior + exterior + old-town wander,
possibly the ~6pm Mass; **Naschmarkt** flagged as the market/dinner option (stalls closing, but its
restaurants open till 23:00). Awaiting: how the cathedral + evening went, and photos (Stephansdom
interior/roof, the walk) — a **"An Evening in Vienna / Stephansdom"** page would close the Vienna
day nicely. NB Stephansdom = Vienna's Gothic cathedral (South Tower 343 steps; famous zig-zag
tiled roof; a different building from the Habsburg palaces).
**STILL OPEN for Vienna:** the existing "Habsburg Forever" page (folio 05) is still IMAGINED
(Orangery concert, Avin asleep — fiction); rewrite when they share their real Schönbrunn day
(what the kids made of the Sisi story, gardens/Gloriette, etc.). Awaiting more Vienna photos.

**Germany Visit 1 (11 Jul) — arrival page done:** flight from Beijing landed on time;
immigration + bags; Avin fully recovered; **one big backpack torn** on the carousel (need to
buy a replacement); waited long for the stroller then learned Munich keeps strollers at a
**separate oversized-items point**, not the belt; **Munich Airport public shower** — €25 per
cubicle for 2 hrs, took 1 cubicle, ~45 min to wash all five; **car pickup smooth, kids loved
their car seats**; drove into Munich; **driving on the right** (opposite NZ) felt crazy at
first but adapted within ~30 min. _Awaiting: the 2+ hr Munich city wander (Visit 1b)._

**Switzerland — Maison Cailler + lunch (Sat 25 Jul, Day 16 / halfway point):** after the
Gornergrat morning, drove down to **Broc** for the **Maison Cailler** chocolate factory
(free visitor parking; self-guided history + tasting). The exhibit's chocolate-history thread
(Aztecs → **Emperor Charles V's** Spanish court → refined in the French court → Swiss milk
chocolate) sparked the kids' question of whether this was the same Charles as **Prague** — it's
not: **Charles V** (Habsburg, Spain, 1500s, the chocolate one) vs **Charles IV** (Bohemia, 1300s,
the Charles Bridge one). **Lunch = galette** (savoury **buckwheat** crêpe, French-Swiss).
**Family observation to use:** the galette *looked AND tasted* similar to **thosai/dosa** — but
they're different ingredients: **buckwheat is a seed/pseudo-cereal** (cousin of rhubarb/sorrel),
whereas **undu (උඳු / ulundu / urad dal) is a legume/black gram**. Nice "tastes like home, made
from something totally different" bridge for a food page. _Story angles: "A Sweet Empire" chocolate
spread (built into Issue 07); a food note pairing galette ↔ thosai._
