# 💊 DoseTrack — Your GLP-1 Companion

A private, single-file dashboard to track GLP-1 doses (semaglutide, tirzepatide…), body weight, side effects and mood. Built for **HealthHack 48**.

**▶ Live demo: https://candicewu0515.github.io/dosetrack/**

No login needed. Open the link, click **Load sample data**, and look around. Try logging today's entry; when you're done, click **Clear & start fresh**.

## Why

I'm on semaglutide myself. The health apps I tried upload medication and weight data to their own servers. I wanted a simple, private place to answer one question honestly: *is this actually working?*

## Features

- Log dose, weight, side effects, mood and notes in under 30 seconds
- Weight trend chart, scaled by date, with each dose step-up marked
- Logging streak, total weight change and latest dose at a glance
- Side-effect frequency summary (e.g. how often nausea really happened)
- kg / lb / 斤 units
- JSON export / import for backup or moving between devices
- Built-in sample data: 20 weeks following a standard 4-week step-up schedule (0.25 → 0.5 → 1.0 → 1.7 → 2.4 mg)

## Privacy

Everything is stored in your browser's `localStorage`. There is no account, no server, no analytics and no network requests. Your data never leaves your device. The public demo uses sample data for the same reason.

## Run it locally

Download `index.html` and open it in any modern browser. It works offline.

## How it's built

One HTML file: vanilla JavaScript, a hand-built SVG chart, and zero dependencies. No framework, no CDN and no build step, so the demo can't break on a judge's laptop.

## Disclaimer

DoseTrack is a personal log, not medical advice. Talk to your clinician about dosing and side effects.
