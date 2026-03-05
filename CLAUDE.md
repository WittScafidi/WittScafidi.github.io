# CLAUDE.md — Witt Scafidi Jekyll Resume Site

## Project Overview
- **Local path:** `/Users/wittscafidi/Desktop/Gen AI/witt-resume/`
- **Live site:** `https://wittscafidi.github.io`
- **Platform:** Jekyll static site, hosted on GitHub Pages
- **Repo:** `github.com/WittScafidi/WittScafidi.github.io`

---

## Deployment Workflow (Important)
- There is **no git push** — a 403 auth error blocks it
- All deploys are done via **manual drag-and-drop upload** through the GitHub web UI
- GitHub Pages auto-rebuilds after each upload (takes 1–3 minutes)
- After uploading, do a **hard refresh** (`Cmd+Shift+R`) to bypass browser cache
- To check build status: GitHub repo → **Settings → Pages**

### Upload locations
| File type | Where to upload on GitHub |
|-----------|--------------------------|
| Root HTML files | Repo root |
| `_layouts/*.html` | `_layouts/` folder |
| `assets/css/main.css` | `assets/css/` folder |
| Images | `assets/images/` folder |
| Resume PDF | `assets/files/` folder |
| Blog posts | `_posts/` folder |

### GitHub folder creation trick
GitHub won't create empty folders. To create one via web UI:
1. "Add file" → "Create new file"
2. Type `foldername/placeholder.txt` in the filename field
3. Commit, then upload real files, then delete placeholder

---

## Site Architecture

### Pages
| File | URL | Layout |
|------|-----|--------|
| `index.html` | `/` | `default` |
| `experience.html` | `/experience` | `page` |
| `education.html` | `/education` | `page` |
| `skills.html` | `/skills` | `page` |
| `athletics.html` | `/athletics` | `page` |
| `blog.html` | `/blog` | `page` |
| `resume.html` | `/resume` | `page` |

### Layout chain
- `layout: page` → `_layouts/page.html` → `_layouts/default.html`
- `layout: default` → `_layouts/default.html`
- `layout: post` → `_layouts/post.html` → `_layouts/default.html`

### Blog posts
- Stored in `_posts/` as markdown files
- Filename format: `YYYY-MM-DD-title.md`
- Current post: `_posts/2026-03-04-presence-in-an-artificial-world.md`

---

## Key Files
```
witt-resume/
├── index.html               # Homepage (hero, about, experience teaser, Spotify, photos, contact)
├── experience.html          # Full work history
├── education.html           # W&M degree, coursework
├── skills.html              # Skills grid (Languages, Data, Operations, Leadership)
├── athletics.html           # D1 baseball
├── blog.html                # Writing/blog index
├── resume.html              # Inline resume view + PDF download
├── _config.yml              # Site config (title, description, baseurl, plugins)
├── _layouts/
│   ├── default.html         # Master layout: navbar + content + footer
│   ├── page.html            # Sub-layout: page-banner header + content
│   └── post.html            # Blog post layout
├── _posts/
│   └── 2026-03-04-presence-in-an-artificial-world.md
├── assets/
│   ├── css/main.css         # All site styles (single stylesheet)
│   ├── files/witt-scafidi-resume.pdf
│   └── images/
│       ├── headshot.jpg     # Circular headshot in navbar
│       ├── baseball.jpg     # Baseball action photo
│       ├── IMG_4662.jpg     # Off the Clock gallery photo
│       ├── IMG_4838_2.jpg   # Target team photo (Experience page)
│       ├── IMG_6094.jpg     # Off the Clock gallery photo
│       ├── IMG_6558.JPG     # Off the Clock gallery photo
│       └── IMG_7149.JPG     # Off the Clock gallery photo
```

---

## Design System

### Theme
- **Style:** Film grain, warm/dark navy — "Option B" styling
- **Background:** Dark navy (`--navy`)
- **Font:** Inter (sans) + Playfair Display (headings)
- **Single CSS file:** `assets/css/main.css`

### Key CSS classes
| Class | Purpose |
|-------|---------|
| `.section` | Standard content section |
| `.section-dark` | Dark navy background section |
| `.page-banner` | Dark header on sub-pages (title + subtitle) |
| `.fade-in` / `.fade-in.visible` | Scroll-reveal animation |
| `.photo-grid` | Mosaic photo gallery (column-count: 2) |
| `.photo-tile` | Individual photo in gallery |
| `.exp-photo` | Experience page photo block |
| `.skill-group` / `.skill-tag` | Skills page cards and pills |
| `.page-content` | Flex wrapper for sticky footer |

### Sticky footer
`body` uses `display: flex; flex-direction: column; min-height: 100vh` and `.page-content { flex: 1 }` to push the footer to the bottom on short pages.

---

## Academic Info (Witt)
- **Degree:** Bachelor of Business Administration
- **Concentration:** Business Analytics with Data Science
- **Minor:** Data Science
- **School:** Raymond A. Mason School of Business, William & Mary
- **Display format:** `BBA in Business Analytics & Data Science · Data Science Minor · Raymond A. Mason School of Business, William & Mary`

---

## Content Notes

### Navbar
- Logo: circular headshot (`/assets/images/headshot.jpg`)
- Links: About · Experience · Education · Skills · Athletics · Writing · Resume

### Homepage sections (in order)
1. Hero (name, subtitle with degree/minor, CTA buttons)
2. About
3. Experience teaser
4. Spotify (static, no API)
5. Off the Clock (photo gallery — 4 personal photos, mosaic layout)
6. Contact

### Experience page
- Timeline of work history
- Target section includes a photo (`IMG_4838_2.jpg`) of team-gifted W&M baseball shirt

### Em dashes
- **Keep:** Location separators (`Target Distribution Center &mdash; Stuarts Draft, VA`) and date ranges (`&ndash;`)
- **Removed:** All Claude-written prose em dashes in copy

---

## macOS Sandbox Note
The macOS sandbox **blocks terminal access to the Downloads folder**. `cp` and file commands will return "Operation not permitted" for files in `/Users/wittscafidi/Downloads/`. Workaround: ask user to manually drag files from Downloads into the project folder via Finder.

---

## Local Dev Server
- Config: `.claude/launch.json`
- Start via `preview_start` tool (name: "jekyll")
- Runs at `http://localhost:4000`
- Note: `.fade-in` elements start at `opacity: 0` — run `document.querySelectorAll('.fade-in').forEach(el => el.classList.add('visible'))` in preview_eval before screenshotting
