# luisrodcast.github.io

Portfolio site for Luis Rodriguez-Castellano, PhD — sport scientist.

Live at: https://luisrodcast.github.io/

## Structure

```
.
├── index.html                 # Landing page
├── performance/
│   ├── index.html             # Story page for the 2026 performance report
│   └── report.html            # The full report (anonymized)
├── srpe/
│   ├── index.html             # Story page for the 2026–27 sRPE report
│   └── report.html            # The full report (anonymized)
└── assets/
    └── css/
        └── portfolio.css      # Shared styles for story + landing pages
```

## Local preview

Open `index.html` directly in a browser, or run a quick static server:

```bash
python3 -m http.server 8000
# visit http://localhost:8000
```

## Deployment

GitHub Pages serves this repo automatically on push to `main`.
No build step. Updates go live within ~1 minute of `git push`.
