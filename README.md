# Cell to Boardroom

Interactive console for **Session 18 — Industry 4.0, MES & AI/Data Analytics** (trainer: Lathieswar), used to run the two Practical Demo modules live in front of a class:

- **Part 1 — Live MES Walkthrough**: Station Login → Work Order → Batch Tracking → Genealogy Trace → Andon Trigger (with a live MTTR clock and escalation ladder).
- **Part 2 — AI/Analytics & SOC-SOH Exercise**: Predictive Quality dashboard, Predictive Maintenance signal (with Remaining-Useful-Life projection), a SOC/SOH hands-on calculator (manual Coulomb counting vs. an AI-model estimate), and a Digital Twin duty-cycle simulation.

It's a single self-contained static page — no build step, no dependencies to install, no backend. Everything (state, charts, calculations) runs client-side in the browser.

## Run it locally

Just open the file directly:

```bash
open index.html          # macOS
xdg-open index.html      # Linux
start index.html         # Windows
```

Or serve it (recommended, avoids any browser file:// quirks):

```bash
python3 -m http.server 8000
# then visit http://localhost:8000
```

## Run it on GitHub Pages

This repo is ready to publish as-is. Pick either option:

**Option A — Deploy from a branch (simplest, no Actions run needed)**
1. Push this repo to GitHub.
2. Go to **Settings → Pages**.
3. Under **Build and deployment → Source**, choose **Deploy from a branch**.
4. Branch: `main`, folder: `/ (root)`. Save.
5. Your site will be live at `https://<your-username>.github.io/<repo-name>/` within a minute or two.

**Option B — GitHub Actions (auto-deploys on every push)**
1. Push this repo to GitHub — it already includes `.github/workflows/pages.yml`.
2. Go to **Settings → Pages** and set **Source** to **GitHub Actions**.
3. Push to `main` (or re-run the workflow from the **Actions** tab) — it builds and deploys automatically from then on.

Either option works with zero code changes; the page has no build step and no external services other than a Google Fonts stylesheet loaded at runtime.

## Notes for the trainer

- Use the **Reset demo** button (top right) between class runs to clear all logged-in state, readings, alerts, and calculator inputs.
- Every step is reachable directly from the left-hand step list — you don't have to move through it in order live, but the numbered flow matches the deck's Demo Plan slides.
- The page has no backend and stores nothing outside the browser tab, so refreshing the page resets everything — there's no session to lose track of between machines.
- Works in both light and dark mode (follows the browser/OS setting).

## File structure

```
.
├── index.html                       # the entire application (HTML + CSS + JS)
├── .nojekyll                        # tells GitHub Pages to skip Jekyll processing
├── .gitignore
└── .github/workflows/pages.yml      # optional Actions-based Pages deploy
```
