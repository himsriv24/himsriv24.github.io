# Himanshu Kumar, Ph.D. — Personal Academic Website

[![Live Site](https://img.shields.io/badge/Live_Site-himsriv24.github.io-blue?style=flat&logo=github)](https://himsriv24.github.io)
[![Lab](https://img.shields.io/badge/Lab-AI--NE_Lab-teal)](https://ainelab.github.io)
[![Affiliation](https://img.shields.io/badge/Affiliation-IIT_Indore-darkgreen)](https://www.iiti.ac.in)
[![Deployment Status](https://github.com/himsriv24/himsriv24.github.io/actions/workflows/pages.yml/badge.svg)](https://github.com/himsriv24/himsriv24.github.io/actions)

Source code for the personal academic website of **Dr. Himanshu Kumar**, Assistant Professor at the Mehta Family School of Biosciences and Biomedical Engineering, [IIT Indore](https://www.iiti.ac.in).

* **Live URL:** [https://himsriv24.github.io](https://himsriv24.github.io)
* **Built With:** [Academic Pages](https://academicpages.github.io/) / [Jekyll](https://jekyllrb.com/)
* **Hosted On:** GitHub Pages

---

## 🧭 Directory Structure

```text
.
├── _config.yml              # Site configuration, author bio, social handles, affiliations
├── _data/
│   └── navigation.yml       # Header menu items (Publications, Research, Blog, CV)
├── _pages/
│   ├── about.md             # Homepage content, bio, and news announcements
│   ├── cv.md                # Curriculum Vitae markdown page
│   └── publications.html    # Publications archive page layout
├── _publications/           # Markdown records for journal and conference papers
├── _portfolio/              # Research project descriptions (seizure segmentation, SOZ, etc.)
├── _posts/                  # Technical blog posts and research insights
├── _teaching/               # Course and teaching records
├── _talks/                  # Conference talks and invited presentations
├── files/
│   └── CV_Himanshu_Kumar.pdf# Downloadable PDF CV
├── images/
│   ├── profile.jpg          # Author avatar
│   └── projects/            # Figures and illustrations for research projects
└── .github/workflows/
    └── pages.yml            # Automated GitHub Pages build & deploy pipeline
```

---

## ⚡ Local Development & Preview

### Option A: Using Docker (Recommended)
```bash
docker compose up
```
Open **[http://localhost:4000](http://localhost:4000)** in your browser.

### Option B: Using Jekyll & Bundler Natively
Ensure Ruby (>= 3.0) and Bundler are installed:
```bash
bundle install
bundle exec jekyll serve
```
Open **[http://localhost:4000](http://localhost:4000)** in your browser.

---

## ✍️ Updating Content

* **Add a Publication:** Add a new Markdown file inside `_publications/` following the existing format (specify `category: manuscripts` for journal papers or `category: conferences` for conference papers).
* **Add News / Announcement:** Update the `News` section inside [`_pages/about.md`](_pages/about.md).
* **Add a Research Project:** Add a new Markdown file inside `_portfolio/`.
* **Add a Blog Post:** Add a new Markdown file to `_posts/` titled `YYYY-MM-DD-title.md`.
* **Update CV:** Update [`_pages/cv.md`](_pages/cv.md) and replace [`files/CV_Himanshu_Kumar.pdf`](files/CV_Himanshu_Kumar.pdf) with the newest version.
* **Update Profile / Links:** Modify `author` fields in [`_config.yml`](_config.yml).

---

## 🚀 Deployment

The site automatically builds and deploys to GitHub Pages via GitHub Actions whenever changes are pushed to the `gh-pages` branch:

```bash
git add .
git commit -m "Update site content"
git push origin gh-pages
```

---

## 📜 License & Acknowledgments

This website is built upon the open-source [Academic Pages](https://github.com/academicpages/academicpages.github.io) template, derived from the [Minimal Mistakes](https://mademistakes.com/work/minimal-mistakes-jekyll-theme/) Jekyll theme by Michael Rose.
