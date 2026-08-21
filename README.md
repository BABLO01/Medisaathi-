# MediSaathi — Personal Health & Medicine Companion (v2, single-file build)

This version has everything the app needs — all styling and all app logic —
built directly into **one file: `index.html`**. There are no `css/` or `js/`
subfolders to worry about, which makes it very hard to break when uploading
to GitHub.

## Files in this folder (all flat, no subfolders)

- `index.html` — the entire app (required)
- `manifest.json` — makes the app installable (optional, but recommended)
- `service-worker.js` — makes the app work offline (optional, but recommended)
- `icon-192.png`, `icon-512.png`, `icon-maskable-192.png`, `icon-maskable-512.png` — app icons (optional)
- `MEDISAATHI_PROGRESS.md` — current status, what's done, what's deferred, next steps
- `CHANGELOG.md` — history of major changes

**Only `index.html` is required.** Even if you upload just that one file, the
full app works. The other files just add offline support, an installable
icon, and a proper home-screen icon.

## What's new in v2

Medicines, vitals, family profiles, timeline, calendar, notes, vault, reports,
insights, search, English/Urdu, themes and PWA install — everything from v1 —
plus:

- **Activity (walking)** — live start/pause/stop timer or manual entry
- **Water tracker** — quick-add buttons, daily target, progress bar
- **Sleep tracker** — bedtime/wake entries with a trend chart
- **Custom trackers** — log anything your doctor recommends
- **Doctor questions** — save questions for your next visit
- **Doctor visit summary** — 7/30/90-day printable report
- **Emergency health card** — key details kept private on your device
- **Food & natural guidelines** — general educational nutrition info
- **Today's Health Tip** and a daily **"How I feel today"** check-in
- **Informational feedback** on readings (e.g. "within typical range") —
  general reference-range guidance only, never a diagnosis
- **First-launch welcome screen** (once, replayable from About)

See `MEDISAATHI_PROGRESS.md` for exactly what's included, what was
deliberately left out (and why), and suggested next steps.

## How to upload to GitHub (step by step)

1. Go to your repository on github.com (e.g. `github.com/bablo01/Medisaathi`).
2. **If you previously uploaded an older version**, delete the old
   `index.html` and any `js`/`css` folders first, so nothing conflicts.
3. Click **Add file → Upload files**.
4. Drag the files from this folder directly into the upload box — **do
   not** drag a folder, and don't drag the zip file itself. Select the
   individual files.
5. Scroll down and click **Commit changes**.
6. Go to **Settings → Pages**, and make sure the source branch is set to the
   branch you just uploaded to (usually `main`), with the folder set to
   `/ (root)`.
7. Wait a minute or two, then open your `https://<username>.github.io/<repo>/`
   link. If it still looks like an old version, do a hard refresh or open it
   in a private/incognito tab once.

## Privacy

All health data stays on your own device, in your browser's private storage
(IndexedDB). Nothing is uploaded anywhere unless you choose to export or
share it yourself. The Emergency Health Card is private too — it is not
shared automatically with anyone.

## Medical safety

MediSaathi organizes and displays your own recorded information. It does
not diagnose conditions, prescribe or adjust medication, or replace a
doctor. Any "feedback" on a reading (like "above typical range") is based on
commonly published general reference ranges, shown for information only —
always talk to a healthcare professional about what your numbers mean for
you.

## Developer

Developed by **Muhammad Usman Channa** (محمد عثمان چنّا).
