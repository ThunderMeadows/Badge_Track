# Badge Track

Score instructor observations on TRADOC Form 600-21-1 and track Army Instructor Badge progress under TRADOC Regulation 600-21 (Faculty Development and Recognition Program).

A single HTML file. No build step, no server, no accounts.

## What it does

- **Score** an observation against TF 600-21-1, Version 3 (May 2023): ten items, four bands, 100 points, any Unacceptable is a no-go. Rate each criterion the way the form distinguishes them and the tool tells you which band the criteria point to; you confirm and set the point value.
- **Write the comments** from what you observed: short observer notes assembled from the criteria you answered, with the lesson's specifics filled in, editable before they go on the form.
- **Fill the official forms.** Downloads a completed TF 600-21-1 and a completed USAACE (DOTD) Form 2657-R (Academic Instructor Hours) with your data in the fields.
- **Track badge progress** for each instructor: hours, consecutive evaluations, self-assessments, developmental observations, courses, packet dates, and time-in-billet gates, each citing its paragraph of TR 600-21. A packet view mirrors table C-2 and writes the DA Form 4187 section IV remarks.
- **Log primary instructor hours** by lesson, in hours and minutes, with the 15M10 course map pre-loaded.

## Run it

Open `index.html` in a browser. That's it.

To host it, push this repository to GitHub and turn on GitHub Pages (Settings → Pages → Deploy from branch, `main`, root). The site is then at `https://<user>.github.io/<repo>/`. On a phone, open that address and use "Add to Home Screen"; the manifest and icons are included.

## Where the data lives

When hosted on its own, every record (instructors, observations, hours) is stored in the browser you use, in `localStorage`. Nothing leaves the device. That means:

- Use one browser on one device for the record, or move data with **Back up** / **Restore** on the Badge progress tab (a JSON file).
- Clearing site data in the browser deletes the record. Back up before you do.
- The in-progress observation and your defaults (observer name, unit, EIC status) are also kept in the browser.

The two blank forms are embedded in `index.html` so it works offline. Fonts and the PDF library load from public CDNs the first time and are cached by the browser.

## Files

```
index.html               the application
manifest.webmanifest     home-screen install metadata
assets/
  icon.svg               app icon, tile
  icon-*.png             raster icons (32, 64, 180, 192, 512)
  badge-track-mark.svg   the mark on light
  badge-track-mark-inverse.svg
  badge-track-lockup.svg mark plus wordmark
.nojekyll                keeps GitHub Pages from processing the site
```

## Adapting it to another course

Open `index.html` and find `const COURSE`. Course number, title, unit, locations, and the lesson list (code, module, title, allocated hours) are plain data. `LESSON_PREFIX` sets the lesson-number prefix (the training schedule and course map use 011-15M1; the ISAP uses 011-15M10). `SCHEDULES` holds the built-in class training schedule; more classes are imported from the training office PDF on the Hours tab (Log from the training schedule → Import) and kept with the records. `DEFAULT_OBSERVER` sets the name that opens on every new observation.

## Notes

- This is a working aid built by an instructor for scoring and record-keeping. It is not an official Army or TRADOC system and does not replace the signed forms, the FDRP manager's records, or the regulation.
- The criteria cues and comment phrasings are condensed prompts written for this tool. Score against the printed form; the rubric text itself belongs to its publishers.
- Requirements follow the Final Draft TR 600-21 placed in interim effect by TRADOC TASKORD 3G9B (27 June 2025), which sets the badge thresholds at 80, 85, and 90 on TF 600-21-1. The TASKORD is superseded when the reg is formally published; check the published version against the Badge progress tab when that happens.
- The embedded TF 600-21-1 blank was repaired before embedding: the published PDF reuses one field name for nine of the ten score boxes, and several fields on both forms carry default-appearance strings that PDF fillers cannot parse.
