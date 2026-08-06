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

---
_Add new review notes here as the user raises them._
