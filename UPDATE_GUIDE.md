# 📘 Trip Guide — Update Reference

> **When the trip plan changes, this is the master checklist of every place that needs updating.**
> Read top-to-bottom before editing. Numbering is **NOT consistent across files** — see ⚠️ warnings.
> Last major change logged at the bottom.

---

## 📦 Complete file inventory

### A. Master planning files (edit these FIRST — they're the source of truth)
| File | Purpose | Day numbering |
|---|---|---|
| `guide.html` | Main A4 printable trip guide (cover + all 31 days + 22 history pages) | **Day 1–31 = actual trip days** ✅ |
| `index.html` | Landing page · interactive map · day cards · **REMINDERS/TODO banner** | 3 JS arrays (see §C) |
| `Munasinghe-Fernando_Family_Europe_Trip_2026.xlsx` | Day-by-Day / Calendar / Transit / TODO sheets | Col A = trip day ✅ |

### B. Printable booklets (A4)
| File | Who | Pages per day | Day numbering |
|---|---|---|---|
| `booklet.html` | **Parents** (full detail) | pgA + pgB | Day 1–31 ✅ |
| `booklet-avin.html` | **Avin** (4yo) | **4: pgA + pgB + pgC + pgD** | Day 1–31 ✅ |
| `booklet-aviann.html` | **Aviann** (8yo) | pgA + pgB + history pages | Day 1–31 ✅ |
| `booklet-avisha.html` | **Avisha** (11yo) | pgA + pgB + history pages | Day 1–31 ✅ |
| `kids.html` | Kids-zone landing page (links to kid booklets) | — |

### C. Per-day detail pages
| File | Purpose | ⚠️ Day numbering |
|---|---|---|
| Individual day detail pages — NOW RENUMBERED to current 31-day plan (see mapping below) | ⚠️ **FILENAME ≠ TRIP DAY.** Read the `<title>` for the real day. Full mapping: day_1→D1, day_2→D2, day_3→D3, day_4→D4, day_5→D5, **day_6b→D6 (Prague full)**, day_6→D7, day_7→D8, day_8→D9, day_9→D10, day_10→D11, day_11→D12(Pisa), day_12→D12(Rome), day_13→D13, day_14→D14, day_15→D15, day_16→D16, day_17→D17, day_17b→D18(Geneva), day_18→D19, day_19→D20, **day_20→D21(Paris)**, day_22→D22, **day_21→D23(Brussels)**, day_23→D24, day_24→D25, day_25→D26, day_26→D27, day_27→D28, **day_29→D29, day_30→D30, day_31→D31**. |

### D. Magazines (A4 keepsake, one PDF per country — built from history pages + food cards)
| File | Country | Notes |
|---|---|---|
| `magazines/01-china-2026.html` … `magazines/13-sweden-2026.html` | 13 country issues, numbered in travel order (China · Germany · Austria · Czechia · Hungary · Italy · Vatican · Switzerland · France · Netherlands · Belgium · Denmark · Sweden) | 7 pages each: Cover · Welcome/TOC · Feature 1 · Duo-photo · Feature 2 · Tastes · Reflections/back-cover |
| Generator: `C:/Source/Trip2026/generate_magazines.py` | rebuilds magazines 02–14 | 01-china is hand-maintained separately |
| Self-contained exports | Denmark, Sweden | `Denmark-Copenhagen-magazine-2026.html`, `Sweden-Gothenburg-magazine-2026.html` (repo root, photos embedded as base64) |

> **Naming convention — `NN-country-YYYY.html`.** The `-YYYY` year suffix marks the *edition*. Every file above is the **2026** trip. If a country is revisited, its new issue gets the visit year (e.g. `china-2030.html`) and sits beside the 2026 one — never overwrite or renumber an existing year's issue. The `NN-` prefix orders that trip's issues; a later trip starts its own sequence.

### E. Data / image files (rarely need itinerary edits)
| File / folder | Purpose |
|---|---|
| `map-data.js` | Country boundary geo data (Natural Earth). **Static.** |
| `Munasinghe-Fernando_Family_Europe_Trip_2026_LATEST_FROM_GSHEET.xlsx` | Google-Sheets sync copy. ⚠️ **Overwrites local edits — edit GSheet directly or re-export.** |
| `images/day-01/` … `images/day-31/` | Day maps + visit-card photos (folder № = trip day ✅) |
| `images/flags/` | Country flags — `DE.jpg`, `DE-outline.png` etc. **Any format works** (jpg/jpeg/png/webp/avif/svg/gif) via `imgFallback()` |
| `images/food/` | Food card images (`08b-france-croissant.jpg` etc.) |
| `images/<country>/` | Magazine photos (`images/china/cover.jpg`, `images/austria/...`, etc.) |

---

## 🔧 CHECKLIST — when a day plan changes, touch ALL of these

### 1. `guide.html` — the day page (primary)
Inside the affected `<div class="page day-page">`:
- `<h2>` route title (e.g. `🇫🇷 Versailles + Paris → 🇳🇱 Amsterdam`)
- `<div class="route">` date
- `<div class="meta">` start time + transit summary
- `<div class="map-block">` → `images/day-XX/map.jpg`
- `<div class="day-food-wrap">` food card
- `<div class="info-strip">` → sleep-block + wear + safety
- `<div class="visits">` → numbered visit cards 1..N + **`VISITING (N stops)` count must match**
- `<div class="box notes">` important notes
- `<div class="footer">Day X of 31 · Date · ...`
- **History pages** (`.china-history`, `.paris-history`, etc.) sit BEFORE the relevant day

### 2. `booklet.html` (parents) — matching day block (pgA + pgB)

### 3. `booklet-avin.html` (4yo) — **ALL 4 pages** for the day
- `pgA` (map + flags + food + mood) · `pgB` (draw) · `pgC` (colour + count) · `pgD` (mission + mood + sticker)
- ⚠️ **All 4 must share identical `data-country` / `data-flag` / `data-color`** (edge-tab consistency)

### 4. `booklet-aviann.html` (8yo) + 5. `booklet-avisha.html` (11yo)
- `pgA` (map-info-row + food + moment + plan) · `pgB` (safety + spots + journal)
- History page order per country: **pgA → combined-hist → kids-hist → pgB**
- ⚠️ `<h2 class="loc">` is the day title · `.mt`/`.md` = moment · `<ol class="plan">` = the plan list

### 6. `index.html` — THREE arrays must stay in sync
- **`stops[]`** (route data): `{day,date,name,country,lat,lon,type,file,hotel,desc}` — `file:` must match the right `day_X.html`
- **`legs[]`** (inside `buildDayCards()`): `range:[startIdx,endIdx]` are **indices into `stops[]`, NOT day numbers** — ⚠️ adding/removing a stop shifts ALL later ranges
- **`REMINDERS[]`** (ticket TODOs): `{id,icon,title,deadline,deadlineLabel,detail,actionLabel,actionUrl}` · `done:true` marks complete

### 7. `day_X.html` — the matching detail page
- ⚠️ Confirm which trip day it is via its `<title>` first
- Update title, h1, banner, timeline

### 8. Excel `Munasinghe-Fernando_Family_Europe_Trip_2026.xlsx`
- **Day-by-Day**: col A=day, B=date, E=hotel (+hyperlink), I=notes/desc
- **Calendar**: daily summary line
- **Transit**: train/flight bookings

### 9. Magazines (only if the change affects a country's content/photos)
- Edit the relevant `magazines/NN-country-2026.html` OR re-run `generate_magazines.py`

---

## 🚨 KNOWN TRAPS (learned the hard way)

1. **`day_X.html` filename ≠ trip day.** Always read the `<title>`. Filenames are sequential IDs, not trip-day numbers.
2. **Booklet version-drift.** The booklets can lag the guide by an entire itinerary version. When making a plan change, **verify the booklets actually show the current plan first** (e.g. they once still showed a single "Lourdes → Amsterdam train day" long after the guide had a 2-day Paris stay). Don't assume — grep the `<h2 class="loc">` for each affected day.
3. **`index.html` `legs[]` ranges break on `stops[]` reorder.** One added/removed stop shifts every later leg `range:[a,b]`.
4. **Country edge-tab attrs** (`data-country/flag/color`) must be identical across ALL page-types of the same day (pgA/B/C/D in Avin).
5. **Day swaps require image-folder + night-count + path updates.** e.g. swapping Day 23↔24 means `images/day-23/` ↔ `images/day-24/` and "(2nd of 3 nights)" ↔ "(3rd of 3 nights)".
6. **History pages are positioned, not standalone.** In guide.html they sit BEFORE the day; in kids' booklets they sit INSIDE the day block (pgA → hist → pgB). Re-ordering days breaks this.
7. **A4 everywhere.** All booklets are A4 (`@page { size:A4 portrait }`). Don't revert to A5.
8. **`imgFallback()` extension order:** jpg → jpeg → png → webp → avif → svg → gif. Drop any format in the right folder — no HTML change needed.
9. **PDF colours:** every file has `print-color-adjust:exact` in `@media print` so backgrounds/gradients survive "Save as PDF". Keep it.
10. **GSheet Excel copy overwrites.** Manual Excel edits to the `_LATEST_FROM_GSHEET.xlsx` get wiped on next sync — edit the main xlsx or the GSheet source.
11. **Reminder deadlines must be real.** Don't invent a "60-day release" rule unless the venue actually has one (Eiffel does; Versailles does NOT — it books months ahead).

---

## ✅ Copy-paste checklist for each plan change

```
[ ] guide.html — day page (header, meta, map, food, info-strip, visits + stop count, notes, footer)
[ ] guide.html — history pages adjusted if country/city changed
[ ] booklet.html (parents) — day block
[ ] booklet-avin.html — pgA + pgB + pgC + pgD (matching country attrs)
[ ] booklet-aviann.html — pgA + pgB (+ history order: pgA→combined→kids→pgB)
[ ] booklet-avisha.html — pgA + pgB (+ history order)
[ ] index.html — stops[] entry (incl. file: ref)
[ ] index.html — legs[] ranges checked
[ ] index.html — REMINDERS[] dates/day refs (+ deadline is real)
[ ] day_X.html — matching file (confirm via <title>)
[ ] Excel — Day-by-Day + Calendar + Transit (+ hyperlinks)
[ ] images/day-XX/ — new/swapped images
[ ] magazines/NN-country-2026.html — if country content changed
[ ] Hard-refresh ALL + verify visually + check div balance
```

---

## 🔑 Quick-find: key locations in `index.html`
- `const stops = [` — route data (~line 830)
- `function buildDayCards()` → `const legs = [` — day-card grouping (~line 62000)
- `const REMINDERS = [` — ticket TODOs (~line 16250)

---

## 📋 Current confirmed bookings (as of last edit)
- ✈ Air China CA784 (AKL→PEK out) + CA962 (return) — booked
- 🚄 TGV 8508 — Toulouse→Paris, Wed 29 Jul 10:20, Coach 12, Seats 224-229, Booking **Z272DK**
- 🚄 Eurostar 9387 — Paris→Amsterdam, Thu 30 Jul 20:22→23:33, Coach 13, Seats 72-76
- 🗼 Eiffel Tower summit — Wed 29 Jul 22:30, 5 tickets (2A+3C), €65, Purchase **#262010328650**
- ⛪ Vatican Museums "Open Bus Gardens" — Wed 22 Jul **10:30** (Day 14), 5 pax (2 full + 3 reduced, incl. Avin — bus needs a seat per head, no free under-7), €170 VISA, **NON-REFUNDABLE**, Order **2L2NF52D19XTF1U5O1** (Txn SIV001-20260623-101417-40378620), paid via official Vatican EPay (net.va). Pkg = 45-min open-bus Gardens ride (audio incl.) + self-guided Museums + Sistine Chapel (no audio inside). E-ticket PDF (QR) arrives separately → print + save to Day 14 Drive folder.
- ⛪ St Peter's Basilica reserved entry — Wed 22 Jul **08:00** (Day 14, do FIRST before 10:30 museums), 5 pax (2 Intero + 2 Ridotto + Avin free Gratuito 0–6), reserved time + self-guided route + digital audioguide, **NON-REFUNDABLE**, **Voucher 681056**, paid via Stripe (pi_3TlRDeB18mH0F3Ta0vfAU9iB). ⚠ Dome climb NOT included (separate ~€10 ticket if wanted).
- 🚂 Gornergrat Railway — Sat 25 Jul, Zermatt–Gornergrat **return, 2nd class**, 4 tickets (2 adult CHF 132 + 2 child 6–16 CHF 66), Avin (4) FREE no ticket, **CHF 398 total** (incl CHF 2 myClimate, VAT 29.67), Visa, **Order 2600101379** · reservation codes: Adult 12B9TS2Z · Adult WPDQD5ZR · Child V1RD37Z3 · Child TB7WQ9ZF · ✅ all 4 PDFs saved to Drive: https://drive.google.com/drive/folders/1D2cgrT5x2QLoqYbZ_4tPMgu5pEhHZeds?usp=drive_link. SBB Stalden→Zermatt train NOT included — ✅ just buy on the day (SBB app/station, no pre-booking; regional train, fixed fare).
- ⛪ Florence GIOTTO PASS ×5 — Sun 19 Jul (Day 11), 🔔 **Bell Tower climb-up 14:15 SHARP** + Baptistery + Museum + Santa Reparata (dome DROPPED — too much for Avin after Mestre drive), 5 passes (2 adult + 2 reduced 7-14 + Avin free under-6), 5 PDFs in Day 11 Drive folder (1xxzV_PDpe...). ⚠ **14:15 slot forced a Day 11 replan**: the old 10:00 Padua Mass + 15:00 Florence arrival would MISS the Bell Tower — so Padua is now a quick ~45-min prayer stop (NO Mass), leave Mestre ~07:00, arrive Florence ~11:45. Mass must be the Sat 18 Jul Vigil (St Mark's Venice) OR Sun evening in Florence (SS. Annunziata / Duomo 18:00), NOT the Padua morning Mass. NB: Uffizi still to book (free child timed tickets).
- 🏨 Hotels: Eklo Paris Porte de Versailles (Conf #5763500807, PIN 1117) + all others (see Excel)
- 🏨 ALT-PLAN hotel: ibis budget Le Kremlin-Bicêtre (non-refundable backup, only if Brussels+Caen detour)

## 🎫 Key pending pre-trip TODOs (see index.html REMINDERS banner for full list + deadlines)
- 👑 Versailles palace ticket €21, 09:30 slot (Day 22) — by 5 Jul
- 🎒 Confirm luggage storage: Gare du Nord lockers (primary) + Eklo (backup) — by 20 Jul
- 📔 Anne Frank House, Uffizi, Florence Duomo dome, etc. — see banner (⛪ Vatican Museums ✅ BOOKED — see confirmed bookings above)

---

## 📅 Current Paris plan (2-day, Versailles included)
**Day 21 (Wed 29 Jul) — Lourdes → Paris:** TGV arrive 14:55 · Eiffel & Champ de Mars · Notre-Dame · Saint-Germain dinner · 22:00 Eiffel sparkle · 22:30 Eiffel summit ✅
**Day 22 (Thu 30 Jul) — Versailles + Paris → Amsterdam:** 08:00 checkout (bags→Gare du Nord lockers) · 10:00 Versailles palace + Hall of Mirrors · Sainte-Chapelle · Luxembourg toy boats · Sacré-Cœur (last stop) · 20:22 Eurostar 9387 → AMS 23:33
**Day 23 (Fri 31 Jul) — Brussels day trip** (cousin drives)
**Day 24 (Sat 1 Aug) — Amsterdam rest day** (Anne Frank, Sat Vigil)

---
*Change log: Versailles added to Day 22 (palace-only €21) · Sacré-Cœur kept as Day 22 last stop · sunrise Eiffel dropped · all 7 files + Excel synced · booklets resynced from stale "Lourdes→AMS train day" to current 2-day Paris plan.*
*Change log (24 Jun 2026): LOUVRE moved to Day 21 (Wed 29 Jul) evening — Wed late opening till 21:45 makes it fit the Paris-arrival evening; Day 22 (Thu) won't work (Louvre shuts 18:00 + Versailles/Eurostar overload). Swapped Day 21 daytime "Eiffel & Champ de Mars" card for the Louvre (Eiffel/Trocadéro still happen at night for the 22:00 sparkle). STILL TO BOOK: ~16:30 timed slot, 2 adults €22 + 3 free kids, louvre.fr (30-day release opens ~29 Jun). Updated guide.html, day_20.html, day_19.html (stale next-day note), index.html (Louvre reminder + Day 21 card). Optional/skippable if kids wiped. Also: Shehani dinner added to Day 23 evening (Amsterdam, TBC).*
*Change log (23 Jun 2026): Florence GIOTTO PASS ×5 BOOKED — Day 11 (19 Jul), Bell Tower instead of dome (dome dropped for Avin), 5 PDFs saved. Updated index.html REMINDERS (done), guide.html Day 11 cards (dome→Bell Tower), UPDATE_GUIDE.md. Uffizi still pending.*
*Change log (23 Jun 2026): Gornergrat Railway BOOKED — Sat 25 Jul, 4 tix (2A+2C) CHF 396, Avin free, Order 2600101379, Print@home. Updated index.html REMINDERS (done), day_17.html, day_16.html, UPDATE_GUIDE.md. NB: SBB Stalden→Zermatt train still to buy separately.*
*Change log (23 Jun 2026): St Peter's Basilica BOOKED — reserved entry Day 14 (22 Jul) 08:00, 5 pax, Voucher 681056, NON-REFUNDABLE (dome NOT included). Slotted FIRST before the 10:30 museums. Updated guide.html, day_14.html, 3 booklets, index.html REMINDERS (st-peters-basilica, done). Note: no Wednesday Papal Audience in July (Leo XIV summer break) + no Sunday in Rome → no Pope sighting expected on these dates.*
*Change log (23 Jun 2026): Vatican Museums BOOKED — "Open Bus Gardens" pkg, Day 14 (22 Jul) 10:30, 5 pax €170 NON-REFUNDABLE, Order 2L2NF52D19XTF1U5O1. Self-guided admission was sold out, so booked the Gardens-bus bundle (which includes museum entry). Day 14 morning re-timed: St Peter's FIRST (07:30, beat queue), then 10:30 Gardens bus + Museums, ~12:30 Sistine — because the chapel→basilica shortcut is guided-tour-only. Updated: guide.html, day_14.html, booklet.html, booklet-aviann.html, booklet-avisha.html, index.html REMINDERS (marked done).*
