# Migration Complete: al-folio → academicpages

This site is a fully migrated copy of Himanshu Kumar's academic website, moved from the al-folio Jekyll theme to the [academicpages](https://github.com/academicpages/academicpages.github.io) template (Minimal Mistakes-based).

**New site directory:** `/Users/himanshukumar/Documents/My Website - Academicpages/`  
**Old site directory:** `/Users/himanshukumar/Documents/My Website/`  
**Target URL:** https://himsriv24.github.io  
**GitHub username:** himsriv24

---

## Migration Checklist — All Done ✓

| Item | Status |
|---|---|
| `_config.yml` — name, URL, author, social links | ✓ |
| `_data/navigation.yml` — Publications, Research, Teaching, Blog, CV | ✓ |
| `_pages/about.md` — bio + news section | ✓ |
| `_pages/cv.md` — education, experience, awards, skills, service | ✓ |
| `images/profile.jpg` — profile photo | ✓ |
| Publications (27 total: 13 journal, 14 conference) | ✓ |
| Portfolio / Research Projects (4) | ✓ |
| Blog posts (3) | ✓ |
| Teaching (2) | ✓ |
| Talk placeholders removed | ✓ |
| Project images copied to `images/projects/` | ✓ |

---

## What You May Want to Customize

### 1. Sidebar bio (`_config.yml`)
The `author.bio` field is currently a single short line. You can expand it:
```yaml
author:
  bio: "Postdoctoral Fellow, Neurological Institute, Cleveland Clinic. Neurotechnology & brain signal processing for epilepsy."
```

### 2. Teaching files
The two teaching files (`_teaching/`) contain placeholder descriptions. Update them with actual course details, dates, and any linked materials.

### 3. Talks (optional)
The `_talks/` directory is empty. If you want a Talks page, add entries using this template:
```markdown
---
title: "Talk Title"
collection: talks
type: "Conference presentation"
permalink: /talks/YYYY-MM-DD-slug
venue: "Conference Name"
date: YYYY-MM-DD
location: "City, Country"
---
Brief description of the talk.
```
Suggested entries: AES 2025 (December), OHBM 2022 (June), ASSFN 2026 (May).

### 4. Remove the Talks nav item
If you don't add any talks, remove the Talks link from the navbar by editing `_data/navigation.yml` (it's currently not shown, so this is already done).

### 5. PDF CV
To add a downloadable PDF CV, place the file at `files/cv.pdf` and add a link to `_pages/cv.md`:
```markdown
[Download PDF CV](/files/cv.pdf)
```

### 6. Google Scholar profile image
Your profile photo is at `images/profile.jpg`. The sidebar will display it automatically.

---

## Deploying to GitHub Pages

Once you're satisfied with the site locally, push it to replace your existing GitHub Pages site:

```bash
cd "/Users/himanshukumar/Documents/My Website - Academicpages"

# Remove the cloned academicpages git history, start fresh
rm -rf .git
git init
git add .
git commit -m "Initial commit: migrate to academicpages theme"

# Point to your existing GitHub repo
git remote add origin https://github.com/himsriv24/himsriv24.github.io.git
git branch -M main
git push --force origin main
```

> **Note:** This overwrites the existing repo. Your old al-folio site is preserved at `/Users/himanshukumar/Documents/My Website/`.

GitHub Pages will build and deploy automatically. The site will be live at https://himsriv24.github.io within a few minutes of the push.

---

## Local Preview

```bash
cd "/Users/himanshukumar/Documents/My Website - Academicpages"
docker compose up
# Visit http://localhost:4000
```

If you don't have Docker, install Ruby + Bundler and run:
```bash
bundle install
bundle exec jekyll serve
```
