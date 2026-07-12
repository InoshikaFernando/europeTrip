# Journaling Notes — Munasinghe Travel Magazine (handoff / continuity file)

> **Purpose:** A private working note so any Claude Code session can pick up the
> travel-journaling project instantly. NOT part of the published magazines.
> To resume in a new session, say: *"Read JOURNALING_NOTES.md and let's continue."*

_Last updated: China outbound fully journaled; adding Germany Visit 1 (Munich arrival)._

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
  Built in China as "Chapter One". **TODO: roll out to the other 13 issues.**
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

## Publish workflow

- Develop on branch **`claude/travel-magazine-reflections-gkh8wt`**.
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
- **Issues 02–07, 09–14 — untouched** (imagined placeholder). Real reflections to come as they travel.

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
