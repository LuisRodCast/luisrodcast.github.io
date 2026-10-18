# Portfolio setup — step by step

**Target**: a public GitHub Pages site at `https://luisrodcast.github.io/`
**Time**: ~15 minutes end-to-end
**You end up with**: a professional portfolio landing page with two
project write-ups and the actual reports embedded one click away.

---

## 1. Create the GitHub repo

The repo must be named **exactly** `luisrodcast.github.io` — that exact
name is what makes GitHub Pages serve it at `https://luisrodcast.github.io/`
instead of a subpath.

1. On [github.com](https://github.com), click **+** → **New repository**
2. Repository name: `luisrodcast.github.io`
3. Visibility: **Public** (required for free GitHub Pages hosting)
4. Don't check any of the "Add README/gitignore/license" boxes
5. Click **Create repository**

Keep the setup page open.

---

## 2. Clone it locally

Open **Git Bash** (not R) and run:

```bash
cd "C:/Users/El_ca/OneDrive - New Mexico State University"
git clone https://github.com/LuisRodCast/luisrodcast.github.io.git
cd luisrodcast.github.io
```

You're now in an empty repo folder.

---

## 3. Drop in the portfolio files

Copy everything from the delivered `portfolio/` folder I just gave you
into this directory. Final layout should be:

```
luisrodcast.github.io/
├── index.html
├── README.md
├── SETUP.md               (this file -- can delete after you're set up)
├── performance/
│   └── index.html
├── srpe/
│   └── index.html
└── assets/
    └── css/
        └── portfolio.css
```

---

## 4. Add the report files

Copy your two existing HTML reports into their project folders, renaming
them so each is `report.html`:

```bash
# From the luisrodcast.github.io/ root in Git Bash:
cp "../aggie_db_project/reports/anonymous_performance_report.html" performance/report.html
cp "../aggie_db_project/reports/nmsu_srpe_report_2026_2027.html"   srpe/report.html
```

(Adjust the source paths to wherever those reports actually live on your
machine. If they're in a different folder, use the actual path.)

Verify both ended up where expected:

```bash
ls -la performance/report.html srpe/report.html
```

Both files should exist and be their original sizes (~1.5 MB and ~3 MB).

---

## 5. Local preview before pushing

Confirm everything renders correctly before putting it on the public
internet. The simplest way:

**In R:**

```r
# From the repo root
servr::httd(".")
```

That opens http://127.0.0.1:4321 (or similar). Click through the
landing page, into each project page, click the "View full report"
button — the report should open in a new tab and look identical to the
original.

**Or from Git Bash:**

```bash
python -m http.server 8000
# visit http://localhost:8000
```

**Check:**
- Landing page shows your name, role, hero statement, and four project cards
- Clicking "Open the project →" on Performance opens the story page
- The big orange "View full report" button opens the actual report in a new tab
- Same for the sRPE project
- No broken images, no missing styles, nothing looks half-rendered

If anything's off, fix locally before pushing.

---

## 6. Push to GitHub

```bash
git add .
git commit -m "Initial portfolio release"
git push -u origin main
```

GitHub Pages picks it up automatically within ~1 minute.

---

## 7. Visit your live site

Go to **https://luisrodcast.github.io/**

- If the page loads correctly: done
- If you get a 404: wait 2 more minutes (first deployment can take a
  little longer) and try again
- If you get 404 after 5 minutes: on GitHub, go to the repo → Settings
  → Pages → make sure "Source" is set to "Deploy from a branch" and
  branch is `main`

---

## 8. Share the URL

Add `https://luisrodcast.github.io/` to:
- Your résumé / CV
- LinkedIn profile → Contact Info / Websites
- ResearchGate profile → Personal Website
- Your Wix bio page

The URL is permanent as long as the repo stays public.

---

## Making updates later

Any time you want to change copy, add a project, or swap in a new report:

1. Edit the files locally
2. Preview with `servr::httd(".")` or `python -m http.server 8000`
3. `git add . && git commit -m "describe change" && git push`
4. Live within ~1 minute

To add a new project:
- Create a new folder like `my-new-project/`
- Copy `performance/index.html` as a template
- Rewrite the eyebrow, headline, four body sections, and CTA
- Add a new `<article class="project">` block to the landing `index.html`
- Push

---

## Adding a professional headshot (optional, later)

If you decide to add a photo:

1. Save a square JPG (~400×400px minimum) as `assets/img/headshot.jpg`
2. In `index.html`, inside the About section, add:

```html
<img src="assets/img/headshot.jpg" alt="Luis Rodriguez-Castellano"
     style="width:120px; height:120px; border-radius:50%; margin-bottom:24px;">
```

Push and the photo appears in the About section.
