# AI Output Quality Evaluation Dashboard

A single-page web app for evaluating AI-generated responses on four quality dimensions and tracking results over time.

**Live demo:** `https://YOUR-USERNAME.github.io/ai-eval-dashboard/` (replace after enabling GitHub Pages)

## Quality dimensions

Each response is scored from 0 to 10 on:

| Dimension | What it measures |
|---|---|
| Relevance | Alignment with the user's question |
| Completeness | Coverage of the requested information |
| Clarity | Readability, structure and simplicity |
| Factual Support | Accuracy and evidence behind the claims |

**Overall score** = (Relevance + Completeness + Clarity + Factual Support) / 4, shown as a percentage out of 100.

| Score | Status |
|---|---|
| 90–100 | Excellent |
| 75–89 | Good |
| 60–74 | Average |
| 0–59 | Needs Improvement |

## Features

- **Overview:** KPI cards (total evaluations, average score, % excellent, % needs improvement) with change versus the previous 30 days, a weekly trend, a status breakdown, and a selector to inspect any recent evaluation.
- **New Evaluation:** form with name, prompt, AI response, optional expected answer and optional reference sources. Includes input validation, loading state and edit support.
- **Results:** overall score, per-dimension progress bars, status badge, radar chart, a reason for each score, strengths, weaknesses and recommendations.
- **Evaluation History:** search, status and date filters. Click any row to open that evaluation. View, edit, delete and export actions.
- **Analytics:** score distribution, average by dimension, radar, status donut, monthly trend and volume, with 7 / 30 / 90 day and all-time filters.
- **Compare Responses:** enter a prompt with two responses, or pick two saved evaluations, and compare side by side.
- **Reports:** summary statistics, CSV export and print-to-PDF.
- **Settings:** reset to sample data or clear everything.
- Responsive layout and automatic light/dark theme.

## Demo evaluation mode (important)

No AI API key is configured. Scores come from a **deterministic text heuristic** (keyword overlap, response length, sentence structure), **not from a real AI judge**.

- Factual Support stays low and is flagged as *unverified* unless reference sources or an expected answer are supplied.
- The app never claims that a response is factually verified.
- The 30 pre-loaded evaluations are labelled "(sample)" and contain placeholder text.

To use real AI scoring, add a backend that calls a model API and keeps the key server-side. A static GitHub Pages site cannot store an API key safely.

## Run locally

No build step or dependencies. Open `index.html` in any modern browser.

## Deploy on GitHub Pages

1. Create a public repository and upload `index.html` (and this README).
2. Go to **Settings → Pages**.
3. Under **Build and deployment**, choose **Deploy from a branch**, select `main` and `/ (root)`, then **Save**.
4. Visit `https://YOUR-USERNAME.github.io/REPO-NAME/` after a minute or two.

## Data and privacy

- Everything runs in the browser. No data is sent to any server.
- Evaluations are saved in the browser's `localStorage`, so they are private to each browser and device and are lost if site data is cleared.
- CSV export opens a copy-to-clipboard box. Paste the text into a `.csv` file.
- PDF export uses the browser's print dialog (**Save as PDF**).

## Project structure

```
index.html   # the entire app: HTML, CSS and JavaScript
README.md
```

## Tech notes

- Plain HTML, CSS and JavaScript. Charts (line, bar, donut, radar) are inline SVG.
- No external scripts, fonts or images are loaded.

## Roadmap ideas

- Backend (Node.js + Express) with SQLite or PostgreSQL for shared persistence
- Real AI-judge scoring through a server-side API key
- Native CSV and PDF file downloads
- Saved prompt library
