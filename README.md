# 💊 DoseTrack — Your GLP-1 Companion

A private, single-file dashboard to track GLP-1 doses (semaglutide, tirzepatide…), body weight, side effects and mood. Built for **HealthHack 48**.

**▶ Live demo: https://candicewu0515.github.io/dosetrack/**

No login needed. Open the link, click **Load sample data**, and look around. Try logging today's entry; when you're done, click **Clear & start fresh**.

To try the Apple Health import without an iPhone, download [`sample-apple-health-export.zip`](sample-apple-health-export.zip) and choose it under **Import from Apple Health**.

## Why

I'm on semaglutide myself. The health apps I tried upload medication and weight data to their own servers. I wanted a simple, private place to answer one question honestly: *is this actually working?*

## Features

- Log dose, weight, side effects, mood and notes in under 30 seconds
- **Import from Apple Health**: choose the iPhone's `export.zip` (or the `export.xml` inside it) and the last 12 months of weigh-ins are merged into your log. The file is parsed in the browser, streamed so multi-GB exports work. kg/lb are converted, the morning reading wins on multi-weigh-in days, and weights you logged yourself are never overwritten
- Weight trend chart, scaled by date, with each dose step-up marked
- Logging streak, total weight change and latest dose at a glance
- Side-effect frequency summary (e.g. how often nausea really happened)
- kg / lb / 斤 units
- JSON export / import for backup or moving between devices
- Built-in sample data: 20 weeks following a standard 4-week step-up schedule (0.25 → 0.5 → 1.0 → 1.7 → 2.4 mg)

## Privacy

Everything is stored in your browser's `localStorage`. There is no account, no server, no analytics and no network requests. Your data never leaves your device, and that includes your Apple Health export. **Delete all data** wipes everything in one click. The public demo uses sample data for the same reason.

## Run it locally

Download `index.html` and open it in any modern browser. It works offline.

## How it's built

One HTML file: vanilla JavaScript, a hand-built SVG chart, and zero dependencies. No framework, no CDN and no build step, so the demo can't break on a judge's laptop.

The Apple Health importer reads the zip's central directory itself (zip64 included), inflates the export with the browser's native `DecompressionStream`, and scans the XML as a text stream for `HKQuantityTypeIdentifierBodyMass` records. There's no XML DOM, so memory stays flat no matter how large the export is.

`sample-apple-health-export.zip` is synthetic data in the real export format, made for testing.

## Disclaimer

DoseTrack is a personal log, not medical advice. Talk to your clinician about dosing and side effects.
