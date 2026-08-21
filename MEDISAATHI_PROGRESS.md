# MediSaathi — Progress

## Current version
v2 (single-file build)

## Features completed
- Dashboard: today's medicines, adherence ring, latest readings, quick-add,
  "How I feel today", Today's Health Tip, recent activity, install banner
- Medicine manager: photo, dosage, schedule, instructions, refill, pause/edit/delete
- Family / caregiver mode (multiple person profiles, per-person data)
- Blood pressure, blood sugar, weight, and other vitals (heart rate, SpO₂,
  temperature, sleep, steps, custom) — each with charts and history
- Informational clinical-range feedback pills (within range / above / below /
  needs attention) for BP, blood sugar, heart rate, SpO₂, temperature —
  general reference ranges only, never a diagnosis, always paired with a
  disclaimer
- Health timeline (unified, filterable by category)
- Calendar view
- Notes (title, content, category, date)
- Health vault (photos/documents, camera or file upload)
- Monthly report + printable "Doctor view"
- Health insights (rule-based, data-only, never diagnostic)
- Global search across medicines, notes, vault, vitals, doctor questions,
  custom trackers
- English + Urdu with full RTL layout
- Light / Dark / Medical themes
- Installable PWA with offline caching (service worker)
- Export / import / clear data, with confirmation before destructive actions
- Accessibility basics: skip link, focus states, aria labels, reduced-motion support
- First-launch welcome screen (shown once, replayable from About)
- Activity (walking): start/pause/resume/stop timer + manual entry fallback
- Water tracker: quick-add buttons, daily target, progress bar
- Sleep tracker: bedtime/wake entries with duration chart
- Custom trackers: log any doctor-recommended measurement (name + unit + value)
- Doctor questions: save, mark answered, delete
- Doctor visit summary: 7/30/90-day range report, printable
- Emergency health card: name, blood group, allergies, medicines, contact
  (private, local-only, shown/shared only if the user chooses to)
- Food & natural guidelines: static, evidence-based-style educational content
  (vegetables, fruits, whole foods, hydration, lower-sodium choices), with a
  daily rotating "Today's Healthy Choice" tip and a clear non-medical disclaimer
- Developer attribution updated to "Muhammad Usman Channa" / محمد عثمان چنّا
- "More" menu added so secondary features don't clutter the dashboard

## Known limitations (by design, not hidden from the user)
- **No OCR for BP/sugar photos.** True on-device OCR (e.g. a Tesseract.js
  integration) was not implemented in this pass — it's a meaningfully large
  addition (large WASM/model download, accuracy tuning, a confirm/edit/retry
  flow) and was deprioritized in favour of finishing the rest of the v2
  feature set reliably. Users can still attach a photo of the reading; they
  just enter the numbers manually. This is called out honestly rather than
  faking OCR.
- **No background push notifications.** Medicine reminders only fire while
  the app is open in a tab, because there is no backend server to deliver
  push notifications when the browser is fully closed (this is a GitHub
  Pages / no-backend constraint, explained in the README).
- **Water/food daily targets are not personalized** by age/weight/condition —
  they're simple user-set numbers with general educational framing, per the
  "individual needs vary" requirement.

## Files
Single-file build (recommended for GitHub Pages — see README):
- `index.html` — everything inlined (HTML + CSS + JS)
- `manifest.json`, `service-worker.js`
- `icon-192.png`, `icon-512.png`, `icon-maskable-192.png`, `icon-maskable-512.png`

Modular source (for future development — not what gets deployed):
- `index.html`, `css/style.css`
- `js/db.js`, `js/i18n.js`, `js/utils.js`, `js/charts.js`, `js/app.js`

The single-file build is generated from the modular source by inlining
`css/style.css` and concatenating `js/db.js` + `js/i18n.js` + `js/utils.js` +
`js/charts.js` + `js/app.js` (with `import`/`export` keywords stripped) into
one `<script>` tag. **Important:** this merge puts every module's top-level
functions into one shared scope, so function names must stay unique across
all five JS files — a name collision between `js/db.js` and `js/app.js`
(`clearAllData` defined in both) caused a real shipped bug (infinite
recursion) that was found and fixed in this pass. Always re-check for
duplicate top-level function names after editing the modular source and
before regenerating the single-file build.

## Next recommended step
If continuing this project in a future session:
1. Read this file and `CHANGELOG.md` first.
2. Inspect `js/app.js`, `js/db.js`, `js/i18n.js`, `css/style.css` (modular
   source) — treat these as the source of truth, not the generated
   `index.html`.
3. Likely next additions, roughly in priority order:
   - Client-side OCR for BP/blood sugar photo readings (with a mandatory
     confirm/edit step — never auto-save an OCR guess)
   - Per-tracker custom units/icons and simple sparkline charts on the
     Trackers list
   - A proper "replace/remove photo" control in the medicine and vault forms
     (currently: uploading a new photo replaces it, but there's no explicit
     remove button)
   - Export/share a single day's or week's data as an image (not just print)
4. Regenerate the single-file `index.html` bundle from modular source after
   any change, and re-run the duplicate-function-name check before shipping.
