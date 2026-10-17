# 💊 DoseTrack — Your GLP-1 Companion

A private, single-file dashboard to track GLP-1 doses (semaglutide, tirzepatide…), body weight, side effects and mood. Built for **HealthHack 48**.

**▶ Live demo: https://candicewu0515.github.io/dosetrack/**

No login needed. Open the link, click **Load sample data**, and look around. Try logging today's entry; when you're done, click **Clear & start fresh**.

To try the Apple Health import without an iPhone, download [`sample-apple-health-export.zip`](sample-apple-health-export.zip) and choose it under **Import from Apple Health**.

## Why

I'm on semaglutide myself. The health apps I tried upload medication and weight data to their own servers. I wanted a simple, private place to answer one question honestly: *is this actually working?*

## Features

- Log dose, weight, side effects, mood and notes in under 30 seconds
- **You vs. clinical trials**: your % weight change by week since your first dose, plotted against the published trial averages and placebo (Wegovy STEP 1 / Zepbound SURMOUNT-1), with a one-line "how am I doing" summary and a hover tooltip
- **Side effects vs. FDA data**: each side effect you log next to its incidence in the trials (drug vs placebo, from the FDA label), plus a **live** ranking of real-world adverse-event reports from openFDA FAERS
- **Doctor summary**: a one-page report (dose history, weight change, trial comparison, side effects, recent notes) to print or save as PDF before an appointment
- **Next-dose countdown** with the standard Wegovy / Zepbound step-up schedule, and a weekly reminder you can add to any calendar (`.ics`)
- Semaglutide or tirzepatide: pick your medication and every comparison switches to that drug's data
- **Import from Apple Health**: choose the iPhone's `export.zip` (or the `export.xml` inside it) and the last 12 months of weigh-ins are merged into your log. The file is parsed in the browser, streamed so multi-GB exports work. kg/lb are converted, the morning reading wins on multi-weigh-in days, and weights you logged yourself are never overwritten
- Weight trend chart, scaled by date, with each dose step-up marked
- Logging streak, total weight change and latest dose at a glance
- kg / lb / 斤 units
- JSON export / import for backup or moving between devices
- Built-in sample data: 20 weeks following a standard 4-week step-up schedule (0.25 → 0.5 → 1.0 → 1.7 → 2.4 mg)

## Privacy

Everything is stored in your browser's `localStorage`. There is no account, no server and no analytics. Your data never leaves your device, and that includes your Apple Health export. The only network request is to openFDA for public adverse-event statistics, and it sends just the drug name (`semaglutide` or `tirzepatide`). If openFDA can't be reached, a saved snapshot is shown instead. **Delete all data** wipes everything in one click. The public demo uses sample data for the same reason.

## Public data sources

| What | Source |
|---|---|
| Trial weight curves | FDA prescribing information via [openFDA drug labels](https://open.fda.gov/apis/drug/label/). Wegovy: Study 2 (STEP 1) week 68, −14.9% vs placebo −2.4%; week 20 from the Study 5 run-in (mean 107.2 → 96.1 kg). Zepbound: Study 1 (SURMOUNT-1) week 72, 5/10/15 mg −15.0/−19.5/−20.9% vs placebo −3.1%; week 36 from the Study 4 lead-in (mean 107.3 → 85.2 kg). The dashed lines connect these published points. |
| Side-effect incidence | Wegovy label Table 3 (2.4 mg vs placebo); Zepbound label Table 1 (5–15 mg vs placebo) |
| Real-world reports | [openFDA FAERS](https://open.fda.gov/apis/drug/event/), queried live from the browser. These are voluntary reports, so counts show what people report, not how often it happens |

## Run it locally

Download `index.html` and open it in any modern browser. Everything works offline except the live openFDA ranking, which falls back to a saved snapshot.

## How it's built

One HTML file: vanilla JavaScript, hand-built SVG charts (sized to the screen, with hover tooltips), and zero dependencies. No framework, no CDN and no build step, so the demo can't break on a judge's laptop.

The Apple Health importer reads the zip's central directory itself (zip64 included), inflates the export with the browser's native `DecompressionStream`, and scans the XML as a text stream for `HKQuantityTypeIdentifierBodyMass` records. There's no XML DOM, so memory stays flat no matter how large the export is.

`sample-apple-health-export.zip` is synthetic data in the real export format, made for testing.

## Disclaimer

DoseTrack is a personal log, not medical advice. Talk to your clinician about dosing and side effects.
