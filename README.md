# Hardware-tools

A tiny, **single-file** static web project (`index.html`) intended to act as a **hardware tools hub** (a lightweight page you can open locally or host on GitHub Pages). :contentReference[oaicite:0]{index=0}

At the moment the repository is deliberately minimal: **1 commit**, **HTML 100%**, and only **`index.html`** is present. :contentReference[oaicite:1]{index=1}

---

## What this repo is for

Use this project as a simple, fast way to keep hardware-related information in one place, for example:

- A **tool inventory** (hand tools, electronics tools, measuring gear)
- Quick links to **datasheets**, manuals, and reference docs
- A “bench setup” checklist (ESD, soldering, calibration reminders)
- A parts/consumables list (tips, flux, solder, heatshrink, wire gauges, etc.)

> GitHub currently shows no description/topics for this repo, so this README defines the intended scope. :contentReference[oaicite:2]{index=2}

---

## Repo contents

- `index.html` — the full page/app (HTML/CSS/JS in one file) :contentReference[oaicite:3]{index=3}

---

## Run locally

### Option A — open directly
You can usually run it by double-clicking `index.html`.

### Option B — serve with a tiny local server (recommended)
This avoids `file://` restrictions and behaves more like real hosting.

**Python**
```bash
python -m http.server 8080
