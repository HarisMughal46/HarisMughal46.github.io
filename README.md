# Haris Mughal — Portfolio

A responsive, single-page portfolio hosted on GitHub Pages. The site uses semantic HTML, inline CSS/JavaScript, and static SVG project previews; no build step is required.

## Highlights

- Professional profile focused on software engineering, .NET, SAP Business One, and software quality assurance.
- Responsive layout, keyboard-visible focus states, skip link, mobile navigation, light/dark theme, and reduced-motion support.
- Project cards with individual **conceptual UI mockups**. These are illustrative designs, not screenshots of deployed product interfaces.
- Evidence-led KPI cards for Crystal Reports support and documented automated test counts.
- SEO title/description, canonical URL, Open Graph/Twitter metadata, inline SVG favicon, and Person structured data.
- CV at `assets/Haris_Mughal_CV.pdf`.
- Existing profile image assets `assets/haris.jpg` and `assets/haris.webp` are retained unchanged.
- Contact form validates fields and opens a pre-filled `mailto:` link; it does not submit to a server.

## Structure

```
.
├── index.html
├── 404.html
├── og-image.png
├── robots.txt
├── sitemap.xml
└── assets/
    ├── Haris_Mughal_CV.pdf
    ├── haris.jpg
    ├── haris.webp
    └── project-ui/       # Individual conceptual project previews (SVG)
```

## Preview locally

From the repository root:

```bash
python -m http.server 8000
```

Then open `http://localhost:8000`.

## Deployment

GitHub Pages is configured for a static site: keep `index.html`, `404.html`, `robots.txt`, `sitemap.xml`, `og-image.png`, and `assets/` at the repository root. No npm install or build command is needed.

## Content accuracy

Project feature summaries and test counts reflect the portfolio's documented project descriptions. KPI values should be updated if the underlying project/report counts change. Project UI mockups are labelled conceptual to avoid presenting them as real product screenshots.

## Maintenance

- Update links and experience details in `index.html`.
- Add project previews in `assets/project-ui/` and reference them with responsive `img` elements.
- Re-check keyboard navigation, mobile layout, contrast, external links, and image loading after significant changes.
