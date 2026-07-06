# AGENTS.md — homepage-vshell

## Identity
Personal homepage / digital business card for **Luiz Paes** — a fast-loading static page with social links and contact info.

## Core directive
- **Speed is the #1 priority.** Every byte, font, script, and image must be justified. No unnecessary dependencies.
- Use the design prototypes in `/stitch-design` as the visual reference. The "Terminal Monolith" aesthetic: dark theme, cyan accent, Geist font, terminal-window card motif.

## Design system (from `stitch-design/terminal_monolith/DESIGN.md`)
- **Colors:** `#131313` (bg), `#111827` (surface), `#06b6d4` (cyan accent), `#e5e2e1` (headlines), `#bcc9cd` (body)
- **Typography:** Geist font — 32px headlines (desktop), 24px (mobile), 14px body, 12px labels, 13px code
- **Layout:** Max 640px container, tight spacing, 4px baseline grid
- **Shapes:** 4px radius small elements, 8px containers, no pills
- **Elevation:** Flat 2D — no shadows, no glass. Surface separation via tonal layers and 1px borders.

## Current state (pre-build)
No `index.html`, no `package.json`, no build tools yet. Prototypes use Tailwind via CDN. Final build should eliminate CDN dependencies for speed — inline critical CSS, self-host fonts, minimal JS.

## Stitch design screens
- `stitch-design/luiz_paes_personal_homepage_terminal_desktop/code.html` — desktop homepage
- `stitch-design/luiz_paes_personal_homepage_terminal_mobile/code.html` — mobile homepage
- `stitch-design/luiz_paes_contact_desktop/code.html` — desktop contact page
- `stitch-design/luiz_paes_contact_mobile/code.html` — mobile contact page
- `stitch-design/terminal_monolith/DESIGN.md` — full design token reference

## Notes
- `/stitch-design` is gitignored (design artifacts, not source code).
- No commits yet on `main`.
