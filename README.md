# CMA Practice — Section A

A mobile-first web app for practicing CMA US questions with full answer
explanations and a 20-question mock-exam mode. Built as a single static
`index.html` — no build step, no backend, no dependencies.

- **129 questions** across 7 topics (Section A · The Financial Statements)
- **Practice mode** — one question at a time, tap an option, tap **Check
  answer** to reveal the correct answer plus the full explanation for every
  option. Filter by topic from the home screen.
- **Mock exam** — a random 20-question set. Answer them all, submit, and get a
  scored report (with the ~72% ICMA-style pass benchmark) plus a per-question
  review.
- Works offline once loaded, and can be added to a phone home screen.

## Deploy to Vercel

**Option A — drag & drop (fastest)**
1. Go to [vercel.com/new](https://vercel.com/new).
2. Drag this whole `cma-practice` folder onto the page (or the `index.html`).
3. Deploy. That's it — it's a static site, zero config needed.

**Option B — Git**
1. Push this folder to a GitHub repo.
2. In Vercel, **New Project → Import** the repo.
3. Framework preset: **Other**. Leave build & output settings empty.
4. Deploy.

**Option C — Vercel CLI**
```bash
npm i -g vercel
cd cma-practice
vercel        # preview
vercel --prod # production
```

## Files
- `index.html` — the entire app (UI + all questions embedded).
- `vercel.json` — clean URLs + cache headers (optional).

## Adding more question sets (e.g. Section B, C…)
All questions live in one array near the top of `index.html`:
```js
const QUESTIONS = [ { num, id, topic, question, intro, table, tail,
                      options:{A,B,C,D}, correct, correctExplanation,
                      explanations:{...}, studyUnit, pctCorrect }, ... ];
```
Append new objects in the same shape and redeploy. If you have more source
PDFs, send them over and they can be parsed into this exact format
automatically.
