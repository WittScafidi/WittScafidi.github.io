# Witt Scafidi — Digital Resume

A personal portfolio/resume website built with Jekyll, deployable to GitHub Pages.

---

## Local Development

### Prerequisites
- Ruby 3.x
- Bundler (`gem install bundler`)

### Setup & Run

```bash
cd witt-resume
bundle install
bundle exec jekyll serve
```

Then open [http://localhost:4000](http://localhost:4000) in your browser.

---

## Deploying to GitHub Pages

### Option A — User/Organization site (recommended)

1. Create a GitHub repo named **`<your-github-username>.github.io`**
2. Push all files in this folder to the `main` branch:
   ```bash
   git init
   git add .
   git commit -m "Initial commit"
   git remote add origin https://github.com/<username>/<username>.github.io.git
   git push -u origin main
   ```
3. Go to **Settings → Pages** and set source to `main` branch, root folder.
4. Your site will be live at `https://<username>.github.io` within a few minutes.

### Option B — Project site

1. Create a repo with any name (e.g., `resume`)
2. In `_config.yml`, update `baseurl` to `"/resume"` (your repo name)
3. Push and enable GitHub Pages from Settings.
4. Site will be at `https://<username>.github.io/resume`

---

## Updating the Resume PDF

Replace `assets/files/witt-scafidi-resume.pdf` with the new file (keep the same filename), then commit and push.

---

## Project Structure

```
witt-resume/
├── _config.yml          # Site configuration
├── Gemfile              # Ruby dependencies
├── index.html           # Main single-page content
├── _layouts/
│   └── default.html     # Base HTML layout
└── assets/
    ├── css/
    │   └── main.css     # All styles
    └── files/
        └── witt-scafidi-resume.pdf
```
