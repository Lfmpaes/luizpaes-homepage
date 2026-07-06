# Luiz Paes Static Homepage Plan

## Summary

Build a two-page static personal site for Luiz Paes:

- `index.html`: terminal-style personal homepage / digital business card.
- `contact.html`: terminal-style contact page using direct `mailto:` and social links, no backend form service.
- No framework, no Tailwind runtime, no CDN scripts, no JavaScript required.
- Self-host one Geist Latin variable WOFF2 font file from `@fontsource-variable/geist@5.2.9`.
- Replace Material Symbols with small inline SVG icons to avoid loading an icon font.

No repo files should be changed until Plan Mode is exited.

## Stack

Use:

- Plain HTML5
- Inline critical CSS in each HTML file
- One self-hosted font asset:
  - `assets/fonts/geist-latin-wght-normal.woff2`
  - Source package: `@fontsource-variable/geist@5.2.9`
  - Source path inside tarball: `package/files/geist-latin-wght-normal.woff2`
- Inline SVG icons for:
  - terminal
  - code/GitHub
  - LinkedIn/person/contact
  - X
  - Instagram/camera
  - email
  - send/external-link where needed

Do not add:

- `package.json`
- build tools
- Tailwind
- Google Fonts runtime links
- Material Symbols
- third-party JavaScript
- analytics
- images unless Luiz provides a real profile image later

## Files To Add

### `index.html`

Purpose: primary landing page.

Content:

- Header:
  - terminal icon
  - `Luiz Paes`
  - nav links: `Home`, `Contact`
  - active state on `Home`
- Main:
  - centered terminal card
  - terminal title: `home.sh` on desktop, `profile.sh` acceptable on mobile only if matching prototype is easier; prefer `home.sh` consistently
  - avatar placeholder using CSS + inline SVG person icon, not an image
  - heading: `Luiz Paes`
  - role: `Software Developer`
  - specialty row:
    - `Backend`
    - `Microservices`
    - `DevOps`
    - `AI-Agent Integration`
  - intro:
    - `I build reliable web applications, backend services, and developer-focused solutions with a focus on scalability and technical precision.`
  - skill badges:
    - `ORACLE SQL`
    - `NODE.JS`
    - `NESTJS`
    - `MICROSERVICES`
    - `DEVOPS`
    - `DOCKER`
    - `LINUX`
    - `AI AGENTS`
  - social/contact icon links:
    - GitHub: `https://github.com/username`
    - LinkedIn: `https://linkedin.com/in/Lfmpaes`
    - X: `https://x.com/username`
    - Instagram: `https://instagram.com/username`
    - Email: `mailto:your.email@example.com`
- Footer:
  - `© 2026 Luiz Paes`
  - text links: `GitHub`, `LinkedIn`, `Email`

### `contact.html`

Purpose: contact page, based on the contact prototypes but optimized for zero JS and no service dependency.

Content:

- Header:
  - same brand as homepage: `Luiz Paes`
  - nav links: `Home`, `Contact`
  - active state on `Contact`
- Main:
  - title: `Get in Touch`
  - subtitle: `System ready. Awaiting user input.`
  - terminal card titled `contact.sh`
  - direct contact rows/buttons:
    - Email: `your.email@example.com`
    - LinkedIn: `linkedin.com/in/Lfmpaes`
    - GitHub: `github.com/username`
  - primary CTA:
    - label: `Send Email`
    - href: `mailto:your.email@example.com?subject=Hello%20Luiz`
- Footer:
  - same as homepage

Avoid a visible form because the selected contact behavior is mail links only.

### `assets/fonts/geist-latin-wght-normal.woff2`

Vendor the Latin variable font only.

CSS:

```css
@font-face {
  font-family: "Geist";
  src: url("./assets/fonts/geist-latin-wght-normal.woff2") format("woff2");
  font-weight: 100 900;
  font-style: normal;
  font-display: swap;
}
```

## Design Implementation

Use these tokens directly in CSS custom properties:

```css
:root {
  --bg: #131313;
  --canvas: #0e0e0e;
  --surface: #111827;
  --surface-2: #201f1f;
  --surface-3: #2a2a2a;
  --accent: #06b6d4;
  --accent-bright: #4cd7f6;
  --headline: #e5e2e1;
  --body: #bcc9cd;
  --border: #3d494c;
  --border-muted: #1f2937;
}
```

Typography:

- Body: `14px`, line-height `1.6`
- Desktop H1: `32px`, weight `700` or `800`
- Mobile H1: `24px`
- Section/card title: `18px`, weight `600`
- Labels: `12px`, uppercase, `0.05em` letter spacing
- Code/meta: `13px`

Layout:

- Max content width: `640px`
- Header/footer inner width: `640px`
- Desktop:
  - full viewport layout
  - header top, footer bottom
  - main card centered vertically
- Mobile:
  - natural scrolling
  - `16px` page padding
  - card starts below header
  - footer after content
- Card:
  - 1px border
  - 8px max radius only if needed; prototypes mostly square, so use `0` or `4px` for terminal card
  - no shadow
  - no glass/blur
- Badges:
  - 1px border
  - `#111827` background
  - cyan text
  - 4px radius, no pills
- Hover/focus:
  - border or text color changes only
  - no transform, no shadow

## Public Interfaces

No runtime APIs.

External user-facing URLs/constants must be centralized near the top of each HTML page as obvious editable link values in markup:

- `https://github.com/username`
- `https://linkedin.com/in/Lfmpaes`
- `https://x.com/username`
- `https://instagram.com/username`
- `mailto:your.email@example.com`

Use `target="_blank"` plus `rel="noopener noreferrer"` for external links.

## Performance Requirements

Acceptance targets:

- No render-blocking external CSS.
- No external font/CDN requests.
- No JavaScript on initial version.
- Total authored HTML + CSS should stay small enough to inspect manually.
- Only one font file request.
- Icon SVGs inline, reused with compact markup.
- No profile image placeholder network request.
- Lighthouse Performance should be effectively 100 for local/static serving.

## Accessibility And Metadata

Add to each page:

- `lang="en"`
- responsive viewport meta
- descriptive `<title>`
  - homepage: `Luiz Paes | Software Developer`
  - contact: `Contact | Luiz Paes`
- meta description
- visible focus states with cyan outline/border
- `aria-label` on icon-only links
- meaningful link text in footer
- semantic structure: `header`, `nav`, `main`, `section`, `footer`
- current nav item with `aria-current="page"`

## Test Cases

Run after implementation:

1. Static file presence:
   - `index.html` exists
   - `contact.html` exists
   - `assets/fonts/geist-latin-wght-normal.woff2` exists

2. No unwanted dependencies:
   - Search output must show no:
     - `cdn.tailwindcss.com`
     - `fonts.googleapis.com`
     - `fonts.gstatic.com`
     - `Material Symbols`
     - `<script`

3. Local render:
   - Serve with `python3 -m http.server 4173`
   - Open:
     - `http://localhost:4173/`
     - `http://localhost:4173/contact.html`

4. Responsive checks:
   - Desktop viewport around `1600x1280`
   - Mobile viewport around `390x884`
   - Header, card, badges, icons, and footer must not overlap.
   - Mobile page must scroll naturally if needed.
   - Text must not overflow buttons/badges.

5. Link checks:
   - `Home` goes to `./`
   - `Contact` goes to `contact.html`
   - Footer links match the icon links
   - Email opens a `mailto:` URL
   - External links use `rel="noopener noreferrer"`

6. Visual checks:
   - Match Terminal Monolith aesthetic:
     - dark charcoal background
     - cyan accent
     - terminal-window card motif
     - flat borders
     - no shadows
     - no rounded pills
   - Homepage closely follows the provided desktop and mobile screenshots.
   - Contact page keeps the contact prototype mood while using direct mail/contact links instead of a form service.

## Assumptions And Defaults

- Build includes both `index.html` and `contact.html`, per selected scope.
- Contact uses direct mail/social links only, no form backend and no JavaScript.
- Use prototype-derived identity data:
  - LinkedIn is `https://linkedin.com/in/Lfmpaes`
  - unknown GitHub, X, Instagram, and email values remain explicit placeholders from the prototypes.
- Copyright year should be updated from prototype `2024` to current year `2026`.
- No real profile image is available, so use the prototype’s icon/avatar placeholder.
- `/stitch-design` remains ignored and is not copied into source.
