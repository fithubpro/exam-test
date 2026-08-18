# CMA Practice — Part 1

A mobile-first web app for practicing CMA US questions with full answer
explanations and a 20-question mock-exam mode. Built as a single static
`index.html` — no build step, no backend, no dependencies. Open it directly in
a browser or deploy the folder to any static host.

- **2,067 questions** from three question banks (HOCK, Gleim, Wiley), across
  64 topics and three exam sections:
  - Section A · The Financial Statements — 267 questions
  - Section B · Planning, Budgeting & Forecasting — 1,473 questions
  - Section C · Performance Management — 327 questions
  - Each question card is tagged with its source bank (HOCK / Gleim / Wiley).
  - Duplicate questions are removed automatically on import (exact-match).
- **Section focus** — practice or take a mock exam across all sections, or
  narrow to Section A, B, or C.
- **Practice mode** — one question at a time; tap an option, tap **Check
  answer** for the correct answer and full explanation. Jump to any topic
  (grouped by bank/study unit) from the home screen.
- **Mock exam** — a random 20-question set (respecting your focus), scored with
  the ~72% ICMA-style pass benchmark and a per-question review.
- Multi-column calculation tables render cleanly.

## Deploy to Vercel
Drag the `cma-practice` folder onto https://vercel.com/new, or push to a repo
and import it (framework preset: Other; no build settings needed).

## Note on size
At ~2,000 questions the questions are embedded in `index.html` (~3.2 MB). This
keeps it a single portable file, but it's the point where moving questions to a
database (with login + per-student history) becomes the better architecture.


## File structure (updated)
The questions now live in **`questions.json`** (loaded at startup) instead of being
embedded in the HTML, so `index.html` is small (~34 KB) and easy to edit/diff.

Deploy both files together (they must sit side by side). On Vercel or any http
server this works out of the box. **Note:** opening `index.html` directly from
your computer (`file://`) will not load the questions, because browsers block
`fetch()` of local files — serve it over http (deploy it, or run a local server)
and it works.

## SEO
`index.html` now ships with a keyword-focused title/description, Open Graph +
Twitter cards, JSON-LD (WebApplication + FAQ), and crawlable content in the
initial HTML (so search engines see real text even before the app's JavaScript
runs). `robots.txt` and `sitemap.xml` are included.

**Before it can rank, replace the placeholder domain** `https://cmalearn.com/`
with your real (ideally custom) domain in: the `<link rel="canonical">`, the
`og:`/`twitter:` URLs, the JSON-LD `url`, `robots.txt`, and `sitemap.xml`.
Then add the site to Google Search Console and submit the sitemap. Optionally add
a 1200×630 `og-image.png` for social share previews.
