# Hang Nguyen — Data Analyst Portfolio

Personal portfolio website for **Nguyễn Ngọc Thanh Hằng**, Data Analyst at Wolffun Game.

🌐 **Live site:** https://hangvt2003-hue.github.io  
📧 **Contact:** hangvt2003@gmail.com

---

## Tech Stack

- **Main page** (`index.html`) — React 18 (via CDN) + custom CSS, single-file no-build-step
- **Project case-study pages** (`projects/*.html`) — Standalone HTML using shared `assets/case-study.css`
- **Blog posts** — External links (e.g., LinkedIn, Medium); URLs configured in the `BLOG_POSTS` array inside `index.html`
- **Embedded reports** — Original HTML reports in repo root (Game_Metrics_Brief.html, Engagement_Drop_Doc.html, Ad_Quality_Report.html)
- **Fonts** — Fraunces (display serif) + Geist (body) + JetBrains Mono (code/labels)

No build pipeline. Just push and GitHub Pages serves it.

---

## File Structure

```
.
├── index.html                       # Main React single-page app
├── README.md                        # This file
├── Game_Metrics_Brief.html          # Embedded in projects/game-metrics-framework.html
├── Engagement_Drop_Doc.html         # Embedded in projects/engagement-drop-analysis.html
├── Ad_Quality_Report.html           # Embedded in projects/ad-quality-monitoring.html
├── assets/
│   ├── case-study.css               # Shared CSS for all sub-pages
│   ├── img/
│   │   └── profile.jpg              # ⚠️ ADD YOUR NEU GRADUATION PHOTO HERE
│   ├── cv/
│   │   ├── Hang_Nguyen_DA_CV.pdf    # Generated CV (linked from header)
│   │   └── Hang_Nguyen_DA_CV.docx   # Source CV
│   ├── customer-behavior-supermarket.pdf  # ⚠️ ADD THE PDF REPORT HERE
│   └── certificates/                # (optional) certificate scans
├── projects/
│   ├── game-metrics-framework.html
│   ├── engagement-drop-analysis.html
│   ├── ad-quality-monitoring.html
│   ├── max-force-ad-daily.html
│   ├── user-cohort-profiling.html
│   ├── iap-price-localization.html
│   ├── hr-power-bi-dashboard.html        # ⚠️ NEEDS POWER BI EMBED URL
│   ├── customer-behavior-supermarket.html # ⚠️ NEEDS PDF
│   └── suicide-rates-analysis.html       # ⚠️ NEEDS COLAB URL
```

---

## ⚠️ Setup Steps Before Deploying

There are 4 things you need to add or update before the site is fully complete:

### 1. Profile photo

Add your NEU graduation photo (or any professional headshot) as:
```
assets/img/profile.jpg
```
Recommended: portrait orientation, ~600×800px or larger, JPG format.

### 2. HR Power BI Dashboard — embed URL

Open `projects/hr-power-bi-dashboard.html`. Find the `<iframe>` whose `src="about:blank"` and replace it with your published Power BI URL:

1. In Power BI Service, open your HR dashboard.
2. **File → Embed report → Publish to web (public)**.
3. Copy the iframe `src` URL (looks like `https://app.powerbi.com/view?r=…`).
4. Paste it into the `src` attribute. Remove the `data-pbi-placeholder` and `onload` attributes.

### 3. Customer Behavior Supermarket — PDF file

Add the report PDF as:
```
assets/customer-behavior-supermarket.pdf
```
The page `projects/customer-behavior-supermarket.html` already references this path — once the file is there, the iframe will render it.

### 4. Suicide Rates Analysis — Google Colab link

1. Open your Colab notebook.
2. Click **Share → Anyone with the link → Viewer**.
3. Copy the URL.
4. Open `projects/suicide-rates-analysis.html` and search for `REPLACE_WITH_COLAB_URL`. Replace with your URL.

---

## Deploying to GitHub Pages

1. Push this folder to your GitHub repository (`hangvt2003-hue/hangnnt.github.io` per the convention you set, OR rename the repo to `hangvt2003-hue.github.io` for an auto-deploy at the root domain).
2. Go to **Settings → Pages**.
3. Under **Source**, select **Deploy from a branch**, choose `main` (or `master`), folder `/ (root)`.
4. Save. GitHub will give you the live URL within a minute.

For a project repo (not username repo), the URL will be `https://hangvt2003-hue.github.io/hangnnt.github.io/`. For a username repo (renamed to `hangvt2003-hue.github.io`), it will be at the root: `https://hangvt2003-hue.github.io/`.

---

## Local Preview

The simplest way to preview locally — any static-file server works:

```bash
# Python 3
python3 -m http.server 8000

# Node.js (npx)
npx serve .

# Then open http://localhost:8000
```

---

## Updating the CV

The CV `.docx` is the source of truth. To regenerate the PDF after editing:

```bash
# Convert docx to pdf using LibreOffice
libreoffice --headless --convert-to pdf assets/cv/Hang_Nguyen_DA_CV.docx --outdir assets/cv/
```

---

## Customization Notes

- **Color theme** — All colors are CSS variables defined at the top of `index.html` (`<style>` block) and `assets/case-study.css`. Change `--accent`, `--paper`, etc. in both files to retheme.
- **Fonts** — Loaded from Google Fonts at the top of each HTML file. Swap the link URL to change fonts.
- **Hero stats** — Edit the `Hero` component in `index.html` (search for "GPA" or "Industry experience").
- **Adding a new project** — Add an entry to the `WORK_PROJECTS` array near the top of `index.html`'s React block, then create a new file under `projects/` based on any existing one as a template.
- **Adding a new blog post** — Add an entry to `BLOG_POSTS` and create a new file in `blog/` based on any existing one.

---

## Anonymization Note

Project case studies referencing my work at Wolffun Game describe the methodology, structure, and analytical mindset — but specific game names, internal account IDs, absolute revenue numbers, and proprietary tooling have been anonymized. Game names appear as "Puzzle Game A," "Puzzle Game B," etc. The studio is referred to as "Mobile Gaming Studio." This protects employer confidentiality while accurately representing the technical and analytical work.

---

© 2026 Nguyễn Ngọc Thanh Hằng · Built in HCMC
