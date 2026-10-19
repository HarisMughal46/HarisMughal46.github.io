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

## Content
All content is real and lives in `index.html`: LinkedIn (`linkedin.com/in/harismughal-hm4646`), GitHub, email (`CONTACT_EMAIL` in the script too), About, quick facts, skills, certifications, six project cards (each linked to its GitHub repo; Projexa is private, so it shows a "Private repo" label), and the experience/education timeline.

There is no `og-image.png` yet, so the `og:image`/`twitter:image` tags are left out and the Twitter card uses `summary`. To add a preview image, upload a 1200×630 `og-image.png`, add both tags back with its absolute URL, and switch the card to `summary_large_image`.

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
