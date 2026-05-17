# Xinyu Wang — Personal Academic Homepage

A single-file static homepage. No build tools, no dependencies. Just open `index.html` in a browser, or push to GitHub Pages.

## What's in here

```
site/
├── index.html              ← the entire homepage
├── assets/
│   ├── headshot.jpg        ← your portrait (400×400)
│   └── CV-XinyuWang.pdf    ← put your CV here (see below)
└── README.md               ← this file
```

## Quick preview

Just double-click `index.html` to open it locally. Everything works offline.

## How to deploy to GitHub Pages (one-time setup, ~10 min)

### Step 1 — Create the repository

Go to https://github.com/new and create a **new repository** with this exact name:

```
Echo-wxy.github.io
```

The name must match your GitHub username (`Echo-wxy`) followed by `.github.io`. This tells GitHub: "treat this as my personal site." Set it to **Public**. Don't add a README, .gitignore, or license at this step.

### Step 2 — Upload the files

The easiest way (no command line):

1. On the new repo page, click **"uploading an existing file"**
2. Drag the entire contents of the `site/` folder (the `index.html` file and the `assets/` folder) into the upload area
3. Scroll down and click **"Commit changes"**

If you prefer the terminal:

```bash
cd site
git init
git add .
git commit -m "Initial homepage"
git branch -M main
git remote add origin https://github.com/Echo-wxy/Echo-wxy.github.io.git
git push -u origin main
```

### Step 3 — Enable Pages (usually automatic)

Go to your repo → **Settings** → **Pages** (left sidebar). You should see:

> Your site is live at https://echo-wxy.github.io/

If you don't see that, under "Build and deployment" pick **Deploy from branch**, branch = `main`, folder = `/ (root)`, then click Save. Give it 1–2 minutes.

### Step 4 — Visit your site

Open https://echo-wxy.github.io/ — that's it. The existing `SCAF-analysis-tool` project page is unaffected; it still lives at https://echo-wxy.github.io/SCAF-analysis-tool/.

## How to update content later

Editing the page = editing `index.html`. Some common edits:

### Replace the headshot
Drop a new `headshot.jpg` (square, ~400×400 px) into `assets/`. Same filename, no other change needed.

### Add a CV PDF
Save your CV as `assets/CV-XinyuWang.pdf`. The "CV (PDF)" button already links to it. If you don't have one yet, you can either delete the button (search `CV (PDF)` in index.html) or leave it — the link will just 404 until you add the file.

### Add a new publication
Find the `<!-- ===== PUBLICATIONS ===== -->` section. Each paper is one `<article class="pub">…</article>` block. Copy any existing one and edit the fields. The `<span class="me">…</span>` wrapper bolds your name in the author list.

### Update venues / links to OpenReview
The OpenReview links in the publications section are placeholders (`https://openreview.net/forum?id=`). When you have the final URLs, paste them in. Same for any future DOIs.

### Change colors or fonts
Top of `index.html`, look for the `:root { … }` block. The accent color (the warm rust orange) is `--accent: #b8451f`. Change it to any hex and the whole page updates. Fonts are loaded from Google Fonts in the `<link>` tag near the top of `<head>`.

## Design notes

- **Typography**: Display headings use *Fraunces* (a contemporary serif with a slightly editorial feel). Italic accents use *Instrument Serif* for a hand-drawn-headline look. Code-like labels use *JetBrains Mono*.
- **Palette**: Warm off-white background (`#f5f3ee`), deep ink (`#1a1a1a`), warm rust accent (`#b8451f`). Chosen to feel like an editorial / scholarly publication rather than a generic tech site.
- **Layout**: Single page, anchored navigation, side-labelled sections with numbered prefixes. The portrait has an offset accent block behind it as a visual anchor.

## Custom domain (optional, later)

If you ever want `xinyuwang.com` or similar, buy the domain, add a `CNAME` file to the repo containing just the domain name, and configure DNS at your registrar to point to GitHub Pages. GitHub has a guide here: https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site

## Issues you might hit

- **Page doesn't update after I push?** GitHub caches aggressively. Try a hard refresh (Ctrl+Shift+R / Cmd+Shift+R) or wait 2–3 minutes.
- **Fonts look weird?** Make sure your browser can reach `fonts.googleapis.com`. In some networks (e.g. inside mainland China), this can be slow. If you experience this, the page still works — it just falls back to system serif/mono fonts.
- **OpenReview links 404?** The placeholder URLs need to be replaced with the real forum IDs. Search for `openreview.net/forum?id=` in `index.html` and update each one.
