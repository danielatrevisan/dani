## Copilot instructions — catálogo Marrocos & Grécia

Context: este repositório contém um site estático (arquivo principal: `catalogo_marrocos_grecia.html`) com imagens remotas (Unsplash) e CSS inline. Use este guia para edições seguras e PRs claros.

- Key file: `catalogo_marrocos_grecia.html` — única entrada principal. Edite conteúdo, imagens e classes diretamente aqui.
- Typical assets: imagens referenciadas via URLs (Unsplash); se adicionar imagens locais, coloque em `images/` ou `assets/images/` e atualize `src` para caminho relativo.

Run & review locally
- Quick local server (preview):
```bash
python3 -m http.server 8000
# open http://localhost:8000/catalogo_marrocos_grecia.html
```
- Alternatively use VS Code Live Server for auto-reload.

Project-specific conventions
- Keep `utf-8` charset and Portuguese `lang="pt-BR"` in `<html>`.
- Prefer relative paths for local assets (no spaces, use hyphens). Example: `images/capa.jpg`.
- When adding CSS, prefer `css/styles.css` and add a single `<link>` in the `<head>` rather than many inline styles.

Structure & patterns an agent should know (examples from the file)
- Navigation: anchors in the sticky nav map to section ids (timeline, casablanca, mykonos, contatos) — keep anchors intact when renaming sections.
- Timeline component: classes `.timeline`, `.tl-item`, `.country-vert`, and modifier `.no-dots` control vertical layout and dots. If changing heights/top offsets, adjust both `.country-vert` inline `style="top:Xpx;height:Ypx"` and sibling `.tl-item` positions.
- Cards: `.card` wraps content; images are in `<figure>` with `<figcaption>` — preserve caption text when swapping images.
- Print rules exist (`@media print`) — prints hide nav.sticky and remove shadows; test printing after major layout edits.

Assets & external deps
- Fonts loaded from Google Fonts (`Poppins`, `Playfair Display`). If you need offline builds, vendor fonts locally into `assets/fonts/` and update `<link>`.
- Images currently use Unsplash query URLs. If you replace with local files, optimize (JPEG/WEBP, max-width ~2000px, 70–85% quality) and mention size in PR.

Editing guidance for agents
- When editing copy: include the changed snippet in the PR description and mention the section id (e.g. marakech).
- When replacing images: note filename, dimensions and compression settings in PR. Example: "replace `img/capa.jpg` with 3000×2000 px, JPEG quality 85%".
- For layout changes (grid columns, timeline offsets): provide screenshots or a short note how to reproduce locally (server + browser + viewport size).

Testing & verification
- Visual check: open in Chrome/Firefox, inspect Console/Network for 404s or JS errors (there's no heavy JS but check network for images/CSP issues).
- Printing: use browser Print preview to confirm `@media print` output.
- PDF export example (optional): `wkhtmltopdf catalogo_marrocos_grecia.html catalogo.pdf` (install wkhtmltopdf first).

PR / commit conventions
- Commit messages: prefix with scope and short intent: `feat(catalog): atualizar capa` or `fix(a11y): alt text missing`.
- PR description should contain:
  1. short summary (1–2 lines),
  2. list of changed files, anchors/sections impacted (e.g. timeline, dicas),
  3. steps to review locally (server command + URL),
  4. notes on assets (sizes, origins) and accessibility checks.

What to avoid
- Do not run unknown scripts in the repo. This is a static site — avoid introducing build tools without maintainer consent.
- Avoid large binary changes (mass image replacements) without prior note; prefer separate PR for assets.

If you want this file placed at the repository root under `.github/`, tell me the repo root path (or open the project folder) and I will move it and/or open a PR.

Request feedback: review these sections and tell me if you want more examples (commit messages, PR templates, or automated checks like an image-size linter).
