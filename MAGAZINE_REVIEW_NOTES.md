# Magazine Review Notes — editorial checklist

Standing rules distilled from the Austria (Issue 02) review. When the user asks me
to review a magazine (`magazines/NN-country-2026.html`), go through **every** item below,
fix what applies, publish to `main`, then report so the user can manually verify.

## 1. No repeated / duplicated storytelling
- Each spread must **advance** the narrative. Never re-tell the same day, scene, or
  moment on the next page.
- If two spreads cover the same place, give them **distinct angles** and let the day
  **conclude only once** — at the end of the last spread, not the first.
- Watch for repeated phrases/quotes across consecutive pages (e.g. Salzburg told the
  Sound-of-Music story twice; Hallstatt put everyone to bed on page 1 then reopened
  the day on page 2). Split arrival/setup vs. the main events + the day's close.

## 2. History first, then the personal story
- A city's **opening** spread should lead with the historical/context feature
  ("what this place is"), then flow into the family's personal experience.
- Do **not** put the personal story first with the history tacked on at the bottom.
- Add a **bridge sentence** from the history into the personal story.

## 3. Map ALL photos into the issue
- Every photo the user has for that country must appear, **unless it is a literal
  duplicate** of one already shown (same subject/shot). If dropping any, say which
  and why.
- Personal/family shots → woven into story spreads as heroes.
- Everything else → captioned **album pages that follow the narrative** (city by
  city, moment by moment). Never a random dump.
- Check the image folder(s) for orphans: any `images/<country>/*.jpg` (and
  sub-folders) not referenced in the HTML.

## 4. Photos live next to their story
- Iconic personal shots belong **with the relevant story spread**, not buried in a
  generic later album (e.g. the Do-Re-Mi gate photo moved up next to the story).

## 5. Accurate identification & captions
- Verify what's actually in a photo before captioning/placing it. (Onion domes =
  Baroque church, not a fortress. Confirm landmarks.)
- When unsure of a specific room/building name, use a **safe descriptive caption**
  rather than asserting a wrong name. Don't over-assert IDs.

## 6. Rotation, cropping, framing
- Bake EXIF rotation so nothing displays sideways (`ImageOps.exif_transpose`;
  phone photos often have orientation flag 6 = rotate 90° CW).
- Crop letterbox / black bars.
- Portrait photos must not be cropped awkwardly — use `background-size:contain` or a
  correct `aspect-ratio`, dark backdrop behind.

## 7. Page boundaries — no overflow
- Content must stay inside the page margin. Use `min-height` (not fixed `height`) on
  `.mag-page`. When adding text to a spread, shrink the photo `max-height` so nothing
  spills past the folio.
- **GOTCHA:** because pages use `min-height`, a too-tall page silently *grows* instead of
  clipping — so a `scrollHeight − clientHeight` check reads 0 (no overflow) even when the
  page has spilled onto a 2nd printed sheet. Verify by measuring each page's `offsetHeight`
  against A4 (295mm ≈ **1115px** at 96dpi) and flag anything taller. (Caught the Glockenspiel
  page at 1320px after adding a photo.)

## 8. Factual accuracy & the user's real experience
- Honor what actually happened; never contradict established facts.
- Known trip facts: skipped **Bled/Slovenia** entirely (drove through — write nothing
  about it); **did** finish the **Vatican** (write it); **3 nights** in Switzerland
  (all alpine villages); visited **La Maison du Gruyère**; the route rail reads
  **30 nights** (don't contradict with a different day count).

## 9. Personal voice
- Weave in the user's own reflections/quotes where offered (e.g. the "I have
  confidence" note on the Austria reflections page).

## 10. Housekeeping
- Keep the **table of contents and page folios in sync** whenever pages are
  added/removed or reordered.
- Publish flow: commit on branch → push → merge to `main` → push `main`.

## 11. No grid / tile photos — everything is a photo-story
- **Never** lay photos out as cropped square tiles or fixed grids (no 4-column
  galleries, no `ed-grid`/`cl-grid`/`essay-item` masonry, no `fd-img` tile grids).
- Convert every such page into a **photo-story** in the house style of **France
  (Issue 08)**: a scene `op-title` + a narrative `op-lead`, then rows (`prow`) of
  **uncropped** photos whose widths are computed from each image's aspect ratio so
  the row shares one height and fills the column — each photo with its own italic
  caption (`cap`). Photos flow in the order the day happened.
- Uncropped is the rule: `width` varies per photo, `height:auto` — never
  `object-fit:cover` into a fixed tile. Let a story run onto extra pages rather
  than cram or crop; keep folios/TOC in sync (rule 10).
- The reusable CSS (`.mag-story/.op-*/.prow/.ph/.cap`) and the justified-row
  width maths live in France (Issue 08); copy them into each issue as it's converted.

## 12. No empty space — every page must FILL (as well as not overflow)
- A page with a big blank band at the foot is a defect, just like an overflow.
  Target: content reaches near the folio; no more than a small margin of blank.
- **Text/history pages:** fill with a fitting element — a **stat row**, a **dates
  timeline**, a **"Next time" wish-list**, this-issue **highlights**, or an
  enlarged supporting photo. Never pad with filler prose.
- **Photo/gallery pages:** enlarge the photos so they fill. A sparse grid of small
  tiles is worse than fewer, larger photos.
- **Portrait photos are height-capped in a row:** 3 portrait shots across (≈56mm)
  are short and leave blank. Use **2 big photos side-by-side (≈87mm)** to fill, or
  a 1-big + 2-stacked collage. (Fixed the Schönbrunn story pages this way.)
- Always re-run the height check after enlarging (rule 7): fill to the folio,
  **never past it**.

## 13. Never cover faces — or key scenery — with text or cards
- Titles, coverlines and labels must sit in a **face-free zone** (open sky, plain
  ground), never on a family face. On a face-heavy hero, lift the title to the top
  over the sky.
- City cards / tiles must not cover the hero's **faces** OR its **key scenery**
  (e.g. the Hallstatt hills). If they'd cover either, move them off the photo.
- **Card labels go BELOW the photo**, never as text baked over a face.

## 14. Multi-city covers — the split layout
- For issues covering several cities (Austria, Italy, Switzerland, France…), use the
  **split layout**: full hero on the LEFT (scenery + family visible), and a clean
  dark **city-column on the RIGHT** — one card per city, photo with the label
  beneath. Do **not** scatter cards over the hero scene.
- Build the cards from real family/landmark photos (label beneath), not baked-in
  text tiles. Switzerland (Issue 08) and Austria (03) covers are the reference.
- Italy's variant (many cities): an **L-frame** of cards along top+right, hero held
  in the open lower-left corner. Same rule — cards in their own band, off the faces.

## 15. Journey route rail — must match ISSUE order everywhere
- The rail lists countries in issue/travel order:
  **01 China · 02 Germany · 03 Austria · 04 Czechia · 05 Hungary · 06 Italy ·
  07 Vatican · 08 Switzerland · 09 France · 10 Netherlands · 11 Belgium ·
  12 Denmark · 13 Sweden · ⌂ Home.**
- **Chapter number = the issue number.** ✓/`done` on every EARLIER issue, ★/`here`
  on the current one, plain for the ones ahead.
- Country count is **13** (not 14). Keep it consistent with the rail and any deck.
- Fill the journey page (rule 12) with a "what's ahead" line + this-issue highlights.
- ⚠️ This rail is stale (old order, Germany at 07) in the issues not yet reviewed —
  fix it in each as you go.

## 16. Back cover teases the NEXT issue with the NEXT country's landmark
- The "★ NEXT ISSUE · [country] ★" back cover must show a **landmark photo of that
  next country**, not the current one. (Germany→Hallstatt, Austria→Prague Castle,
  Czechia→Budapest night, Hungary→Colosseum, Vatican→Matterhorn, Switzerland→Eiffel,
  France→Amsterdam, Netherlands→Atomium, Belgium→Nyhavn, Denmark→Gothenburg.)
- The chain follows issue order (02→03 … 13→Home). Sweden (13) teases Home · NZ.
- Back-cover issue label is **trip-scoped**: **"No. NN of 14 · Europe 2026"** (see
  rule 25). Keep the format identical across every issue in the trip.

## 17. History as a story, with 2–3 matched photos per page
- When asked to explain a place's history (palace, cathedral, etc.): **write it as a
  narrative story** and add **2–3 matching photos per page** to illustrate it.
  Story is primary; photos are the graphics. (Schönbrunn: Maria Theresa → the Great
  Gallery/Mozart → the imperial apartments → treasures & the end.) Never a photo grid.

## 18. Only the family's own photos — no stock, no photo-less filler
- Use only real **"Photo · Munasinghe-Fernando"** shots. **Never** stock images
  (e.g. the unused `images/food/` reference set).
- If a page has no usable own photos and is generic filler (e.g. a food page for a
  country they only passed through), **remove it** and fix the TOC/folios — don't pad
  it with stock.

## 19. Numbering & facts consistent everywhere
- Issue numbers, "No. X in this series", "Chapter X", "One of Fourteen", country
  counts must agree across cover, journey rail, back cover and cross-references
  (a Prague/Czechia mention is **No. 04**, not 03).
- Honour the real itinerary/accommodation (e.g. Germany's 2nd night = the Novotel by
  Munich Airport, **not** Ottobeuren — plans changed).

## 20. "Next time" framing
- Frame anything missed as **"Next time"** and **name the specific places**
  (Neuschwanstein, the Romantic Road, the Ottobeuren basilica…), never "what we missed".

## 21. Add history wherever it fits — the reader loves history
- The user **loves history**: wherever a page has room or touches a place with a
  story (a palace, a square, a bridge, a cathedral, a castle, a whole city),
  **weave in the historical context** — who built it and when, why it looks the
  way it does, what happened there. Add it as narrative prose, a **"story in N
  dates" timeline**, a short **history sidebar/feature**, or a captioned fact —
  whatever fills the page best (rule 12) without crowding the family story.
- History is a first-class way to fill a light page: prefer a real history
  feature over generic filler prose. Keep it **accurate** (rule 5/8) — hedge or
  use a safe descriptive line when unsure, never assert a wrong fact.
- Blend, don't bury: the family's personal moment stays the heart of the spread;
  history frames it (rule 2). Aim for at least one genuine historical note per
  city/landmark spread across every issue.

## Publish / preview flow
- Commit on branch → push → ff-merge to `main` → push `main`.
- **raw.githack caches per-URL.** When giving the user a preview link, add a
  `?v=N` cache-buster and bump N so they see the fresh version (not a stale cache).

## 22. The mother's name is Inoshi (never "Lana")
- The family is **Avinesh, Inoshi, Avisha, Aviann & Avin Munasinghe-Fernando**. The
  mother/author is **Inoshi**. Earlier drafts wrongly called her "Lana" — never use
  that name anywhere (signoffs, captions, alt text). (Watch base64 image blobs — a
  literal "Lana" inside a data-URI is coincidental; never edit those.)

## 23. No standalone food page — weave food into the day it happened
- The magazine must read as **one continuous story**. Never give food its own
  "★ TASTES OF…" / `mag-food` page.
- Put each dish into the **narrative of the day it was eaten** (a sentence or two in
  that day's spread) and place any real food photo as a captioned shot on that day's
  spread or nearest album page. Then delete the standalone page and **renumber** the
  TOC + any sequential folios (rule 10).
- Keep only the family's own food photos (rule 18); drop CSS-emoji placeholder cards.

## 24. Architecture as inheritance — say where the style came from
- The reader loves knowing **what tradition a building belongs to and who it was
  inherited/copied from**, not just what it is. On any architecture note, name the
  lineage: classical dome/arch/column = **Roman**, revived in the **Renaissance**;
  Gothic (pointed arch, rib vault) = **invented in France**; painted ceilings =
  **Italy's** supreme art, exported across Europe; carved/ornamented walls =
  **Prague's** glory; **alpine timber chalets** (Hallstatt ≈ Zermatt) vs **lowland
  stone burgher towns** (Bern/Zürich arcades); tax-shaped **Dutch canal houses**;
  civic **guild/belfry** wealth in Belgium; **beyond Rome's reach** in Scandinavia
  (classical arrived late as an import); **Dutch-engineered** Gothenburg canals.
- Blend it into the family story (rule 2/21); keep it accurate (rule 5/8).

## 25. Collection naming & numbering — number WITHIN a trip, not globally
- The magazines are a growing shelf of **trips**, written in any order but sorted by
  travel date. Each trip is its own series identified by a **name + year**
  (e.g. *Europe 2026*; a future *Singapore 2016* — Batam, Bintan, etc.).
- **Issue numbers restart at 01 inside each trip.** Never use one global running
  number — that way adding an older trip later never forces a renumber.
- Back-cover / masthead label is trip-scoped: **"No. NN of 14 · Europe 2026"**
  (a future set reads e.g. "No. 01 of 3 · Singapore 2016"). Applied to all 13
  current issues (2026-08). The "14" counts the 13 countries + the Home finale.
- **Filenames / folders:** current issues stay flat as `NN-country-2026.html` (so
  existing raw.githack links keep working). **New trips go in their own folder** —
  `magazines/2016-singapore/01-….html` etc. — numbered from 01 within that folder.
- **Revisiting a country:** a second visit is just a new issue in a new trip folder
  (no collision with the 2026 one). **Link them** with a "We've been here before"
  cross-reference line pointing to the earlier issue, and list everything on a
  top-level **`magazines/index.html`** (build it when the 2nd trip starts).
