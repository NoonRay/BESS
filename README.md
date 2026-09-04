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

- Use the **Reset demo** button (top right) between class runs to clear all logged-in state, readings, alerts, and calculator inputs — it does not change your theme choice.
- Every step is reachable directly from the left-hand step list — you don't have to move through it in order live, but the numbered flow matches the deck's Demo Plan slides.
- A progress bar under the header tracks how many of the 9 steps have real input recorded, so you can see at a glance what's left to demo.
- Each step ends with a collapsible **Instructor talking point** — a ready-made question to put to the room without breaking flow to think one up.
- **Station Login** and **Andon Trigger** both have quick-fill buttons that jump straight to the interesting failure paths (an uncertified operator, a station that isn't released, a missed MTTR target) instead of typing them out live.
- **Batch Tracking** readings that fall out of spec can **Flag Andon** directly from the table row — it jumps to Part 1's Andon step and raises a live alert with the right trigger type pre-selected, demonstrating the loop Module C describes.
- **Andon Trigger** now has five trigger types (quality, machine, material, safety, data) each with its own target MTTR and escalation path, matching the deck's escalation matrix; resolved alerts accumulate in a session incident log.
- **Genealogy Trace** can trace backward (to the electrode lot and supplier batch) or forward (to module/pack assembly and shipment) from the same cell ID.
- **Predictive Maintenance** lets you switch between three machines with different vibration trends (healthy, mid-drift, urgent) to show how the RUL estimate changes.
- **SOC / SOH Calculator** has one-click preset scenarios and flags when a raw (pre-clamp) calculation would have gone outside 0–100%.
- **Digital Twin** uses a continuous C-rate slider (rather than two fixed toggles) against dashed gentle/fast reference lines, so you can dial in any duty cycle live.
- The header icons toggle **theme** (system → light → dark), **fullscreen**, and a **help** dialog listing all of the above plus keyboard shortcuts (← / → move between steps, Esc closes the dialog).
- The page has no backend and stores nothing outside the browser tab except your theme preference, so refreshing resets the demo — there's no session to lose track of between machines.
- Works in both light and dark mode (follows the browser/OS setting by default, or your explicit choice from the theme toggle).

## File structure

```
.
├── index.html                       # the entire application (HTML + CSS + JS)
├── .nojekyll                        # tells GitHub Pages to skip Jekyll processing
├── .gitignore
└── .github/workflows/pages.yml      # optional Actions-based Pages deploy
```
