# Fadi Al Machot — Academic Website

Professional academic website built with [Quarto](https://quarto.org/) and deployed to GitHub Pages.

---

## 🚀 Quick Start: Deploy to GitHub Pages

### Step 1 — Install Quarto
Download from [quarto.org/docs/get-started](https://quarto.org/docs/get-started/) and install.

### Step 2 — Create a GitHub repository
1. Go to [github.com/new](https://github.com/new)
2. Name it (e.g. `academic-website` or your username + `.github.io`)
3. Set it to **Public**
4. Don't initialize with a README (you'll push this folder)

### Step 3 — Configure your site URL
Open `_quarto.yml` and update:
```yaml
site-url: "https://YOUR-USERNAME.github.io/YOUR-REPO"
```
Also update the GitHub link in the navbar.

### Step 4 — Add your profile photo
Place a file named `profile.png` in the `assets/` folder.
Recommended: square image, at least 400×400px.

### Step 5 — Push to GitHub
```bash
cd fadi-almachot-site
git init
git add .
git commit -m "Initial site"
git remote add origin https://github.com/YOUR-USERNAME/YOUR-REPO.git
git branch -M main
git push -u origin main
```

### Step 6 — Enable GitHub Pages
1. Go to your repo → **Settings** → **Pages**
2. Under **Source**, select **GitHub Actions**
3. The site will build and deploy automatically on every push to `main`
4. Your site will be live at `https://YOUR-USERNAME.github.io/YOUR-REPO`

---

## 📁 File Structure

```
fadi-almachot-site/
├── _quarto.yml          # Site config — navigation, theme, URL
├── index.qmd            # Home page — bio, timeline, news
├── publications.qmd     # All publications with filters
├── research.qmd         # Research projects
├── teaching.qmd         # Courses
├── supervision.qmd      # PhD & Master students
├── service.qmd          # Service, committees, review roles
├── media.qmd            # YouTube, talks
├── contact.qmd          # Contact info
├── assets/
│   ├── custom.scss      # All styling
│   └── profile.png      # ← ADD YOUR PHOTO HERE
└── .github/
    └── workflows/
        └── deploy.yml   # Auto-deploy on push
```

---

## ✏️ How to Update Content

### Add a news item
Open `index.qmd` and paste at the TOP of the `#news-recent` block:
```markdown
::: {.news-item}
::: {.news-date}DD.MM.YYYY:::
[[NEW]{.news-badge}] Your news text here, with [links](https://...) if needed.
:::
```
Move it to `#news-more` once it's older than ~6 months.

### Add a publication
Open `publications.qmd`. Find the right year heading and paste:
```markdown
::: {.pub-entry data-theme="THEMES" data-type="TYPE"}
::: {.pub-title}
[Paper Title](https://doi-or-url)
:::
::: {.pub-authors}
Author A., Author B., **Al Machot F.**, Author C.
:::
::: {.pub-venue}
[Journal/Conference Name]{.venue-name} · Publisher · Year
:::
:::
```
**Available themes** (space-separated in data-theme):
`zsl` · `neural-symbolic` · `activity` · `timeseries` · `healthcare` · `adas` · `agriculture`

**Types:** `journal` · `conference` · `book` · `chapter`

### Add a research project
Open `research.qmd` and copy a `.project-card` block.

### Add a student
Open `supervision.qmd` and copy a `.student-entry` block.

### Add a YouTube video
Open `media.qmd`. Replace the iframe `src` with an embed URL:
`https://www.youtube.com/embed/VIDEO_ID`

### Change the colour scheme
Open `assets/custom.scss`. The main variables are at the top:
```scss
$primary:    #1a3a5c;  // dark navy — navbar, headings
$accent:     #2d7dd2;  // blue — links, tags, highlights
```

---

## 🔧 Local Preview

```bash
# Install Quarto first, then:
quarto preview
```
Opens the site at `http://localhost:4532` with live reload.

To do a full build:
```bash
quarto render
```
Output goes to the `docs/` folder (used by GitHub Pages).

---

## 📝 Notes

- The `docs/` folder is in `.gitignore` and built by GitHub Actions — don't commit it manually.
- The site uses the `cosmo` Quarto theme with custom SCSS overrides.
- Publication filters are pure JavaScript — no external libraries needed.
- Font: [Inter](https://fonts.google.com/specimen/Inter) (body) + [Lora](https://fonts.google.com/specimen/Lora) (headings), loaded from Google Fonts.
