# Haris Mughal — Portfolio

A fast, accessible, single-file personal portfolio. Everything (HTML, CSS, JS, icons, placeholder art) lives in **`index.html`**; the only external request is Google Fonts (Space Grotesk + Inter), with system-font fallbacks if it's blocked.

```
portfolio/
├── index.html        # the whole site
├── README.md
└── screenshots/      # QA screenshots (not needed for deployment)
```

## Features
- Mobile-first, responsive (checked at 360 / 768 / 1280 px)
- Light and dark themes follow `prefers-color-scheme` by default; the toggle's choice is saved in `localStorage` (`theme` key)
- Sticky navbar with mobile menu (Esc / outside-click closes it), smooth scrolling, active-section highlighting
- Entrance animations via `IntersectionObserver`, turned off under `prefers-reduced-motion`
- Accessibility: semantic landmarks, skip link, visible focus rings, ARIA labels, keyboard navigation, WCAG AA contrast in both themes (axe-core: 0 violations)
- SEO: title, description, canonical, Open Graph and Twitter cards, inline SVG favicon
- Contact form with client-side validation that opens a pre-filled `mailto:` link (no backend)

## Personalize
Search `index.html` for **`PERSONALIZE`**. Every value you should check or replace has that comment next to it.

| What | Where / current value |
|---|---|
| Canonical + `og:url` | `https://your-domain.example/` → your deployed URL |
| `og:image` / `twitter:image` | `https://your-domain.example/og-image.png` → absolute URL to a 1200×630 image |
| Meta description | `<head>` |
| LinkedIn | `https://www.linkedin.com/in/your-linkedin-handle` (hero, contact, footer: 3 places + visible label) |
| GitHub | `https://github.com/HarisMughal46` (real) |
| Email | `harismughalhm092@gmail.com` (real; also `CONTACT_EMAIL` in the script) |
| Availability pill | "Open to new opportunities" |
| Hero tagline | hero section |
| Avatar | gradient "HM" tile; swap for `<img src="me.jpg" alt="Portrait of Haris Mughal" width="400" height="400">` |
| About bio + quick facts | `[Placeholder]` paragraphs, `X+`, `XX`, `City` |
| Project descriptions | TaskManagerApp, Projexa |
| Project repo links | currently the GitHub profile, so switch them to each repo |
| Live demo links | currently `#` |
| "Coming soon" cards | 2 slots; replace them with real projects or delete them |
| Timeline | 2 experience + 1 education entries, all placeholders |

**Colors and fonts:** edit the CSS variables at the top of `<style>` (`--c-primary`, `--c-secondary`, `--c-accent`, neutrals, `--font-heading`, `--font-body`). The dark theme overrides appear twice (the `prefers-color-scheme` block and `[data-theme="dark"]`), so keep both in sync. Re-check contrast after you change colors.

**Adding a project:** copy one `<article class="project-card">` block. Each inline SVG thumbnail needs a unique gradient `id`.

## Preview locally
```bash
cd portfolio && python3 -m http.server 8000   # then open http://localhost:8000
```
(You can also open `index.html` directly in a browser.)

## Deploy

### GitHub Pages
1. Create a repo: `HarisMughal46.github.io` for a user site, or any name for a project site.
2. Commit `index.html` (and `README.md`) to the repo root:
   ```bash
   git init && git add index.html README.md && git commit -m "Portfolio"
   git branch -M main
   git remote add origin https://github.com/HarisMughal46/HarisMughal46.github.io.git
   git push -u origin main
   ```
3. Go to **Settings → Pages → Build and deployment**, set Source: *Deploy from a branch*, then pick `main` / `(root)`.
4. The site goes live at `https://harismughal46.github.io/`. Update the canonical/OG URLs to match.

### Netlify
- **Drag and drop:** at app.netlify.com go to *Add new site → Deploy manually* and drop the `portfolio` folder.
- **Git:** import the repo. Leave the build command empty and set the publish directory to `.`
- **CLI:** `npx netlify-cli deploy --dir . --prod`

### Vercel
- Import the repo at vercel.com/new. Choose Framework preset **Other**, no build command, output directory `.`
- **CLI:** `npx vercel --prod` from inside `portfolio/`

Custom domain: add it in the host's dashboard, then update `canonical`, `og:url` and `og:image`.

## Notes
- The contact form uses `mailto:`, so visitors need an email client configured. For a real inbox-backed form, point the form at a service such as Formspree or Netlify Forms.
- `screenshots/` is for QA only. You can leave it out of the deployment.
