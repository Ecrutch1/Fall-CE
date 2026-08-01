# WCCCD Continuing Education — Shopping Cart Registration Prototype

An interactive prototype of a modern shopping-cart registration experience for
Wayne County Community College District Continuing Education, built from the
real Fall 2026 course and schedule data.

**Everything is a single self-contained file: [`index.html`](index.html).**
Open it in any browser — no server, build step, or dependencies required.

## What it does

- **Browse** 478 real class sections across 6 campuses + online, by category
  tile, campus, or search (title / course number / CRN / instructor)
- **Real schedules** — meeting days, times, start/end dates, instructor, and
  max enrollment for every section (from the Crystal Reports export)
- **Multi-class cart** — register for any number of classes in one checkout,
  with automatic **schedule-conflict warnings** when two classes overlap
- **Registration form** that mirrors the current WCCCD Cognito Forms
  registration form field-for-field (name, A-Number, DOB, new/returning,
  address, phones, Wayne County residency, semester, signature, optional
  federal reporting section)
- **Static fallback** — the full catalog is baked in as plain HTML, so the
  page is browsable even in viewers that block JavaScript; scripting
  progressively enhances it into the full cart experience

## Placeholders / known gaps

- **Pricing is a flat $25 placeholder** — real fees are not in the source data
- Seats shown are max enrollment; no seats-remaining feed yet
- Checkout is a demo — no payment is processed, nothing is submitted anywhere

## Repo layout

| Path | Purpose |
|---|---|
| `index.html` | The prototype (fully self-contained) |
| `data/courses.csv` | Source course list (title, CRN, course number, campus) |
| `data/schedule.xls` | Source schedule export (days, times, dates, instructor, max enrollment) |
| `build/parse-courses.js` | Parses `courses.csv` → `courses.json` |
| `build/build.js` | Merges data + template → `index.html` |
| `build/wcccd-template3.html` | Page template (HTML/CSS/JS with data placeholders) |
| `tests/` | Playwright smoke tests (JS-on and JS-off modes) |

## Rebuilding after a data update

```bash
node build/parse-courses.js   # if the CSV changed
node build/build.js           # regenerates index.html
```

---
Prototype built with Claude. Placeholder pricing; not an official WCCCD site.
