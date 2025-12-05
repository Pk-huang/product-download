<!-- Guidance for AI coding agents working in this repo (product-download) -->
# Copilot instructions — product-download

Overview
- This repository is a small static frontend for "product download" pages. It contains plain HTML pages, a single stylesheet at `css/download.css`, and assets in `img/`.
- There is no backend or build system in the repo. Changes should be limited to static assets unless the user explicitly asks to add a server.

Key files and patterns
- `index.html`, `ProductList.html`, `group.html`, `AddNew.html`, `Update.html`, `edit.html`, `login.html` — main views. Follow their structure when adding pages.
- `css/download.css` — central place for styling and project-specific class names (examples: `bg-F7F9FC`, `border-bule`). Update CSS here rather than scattering inline styles.
- `img/` — store images and SVG assets. Many SVGs are inlined directly in the HTML; prefer keeping small icons inline but put larger assets in `img/`.
- Bootstrap is included via CDN (Bootstrap 5.3.3). Use Bootstrap classes for layout and components to stay consistent.

Project-specific conventions
- Static-first: edit HTML and CSS directly — no JS frameworks present. There are no separate JS files; small interactive bits use Bootstrap's JS via CDN.
- Reusable row patterns: product list rows use the same markup block. When adding rows, copy the existing row structure (see `#list` in `ProductList.html`).
- Class name typos are intentional/established: e.g. `border-bule` (used for borders) and `bg-F7F9FC` (custom background color). Do not rename them without updating `css/download.css` and other pages together.
- Filenames use mixed capitalization (e.g., `ProductList.html`); preserve casing when referencing files.

Developer workflow (quick commands)
- Local preview (simple and reliable):
  - `python3 -m http.server 8000` from the repo root, then open `http://localhost:8000/ProductList.html` (or any page)
  - macOS alternative (Live Server extension) is fine for rapid edits.
- No build, dependency install, or test commands are present.

How to make safe changes
- When changing layout or colors: update `css/download.css` and then update all pages that rely on the same classes. Search for class names across the repo when modifying them.
- When adding new HTML views: replicate the header/nav/footer blocks from `ProductList.html` to keep consistent structure.
- Avoid adding server-side code unless the user requests it; if needed, propose a small Node/Python server and get approval first.

Examples (concrete edits)
- To add a new product row in `ProductList.html`:
  - Copy a `<div class="row align-items-center border-bottom bg-white py-4">...</div>` block from the existing `#list` and update inner columns.
- To change a color token `bg-F7F9FC` to a new hex value: update `css/download.css` and run a quick browser preview across main pages to confirm.

Integration notes
- External dependencies: Bootstrap CSS/JS via CDN. Network access required for CDN assets when previewing.
- No APIs or cross-component services to call out in the current codebase.

When in doubt
- Ask the repo owner before introducing new technologies (build systems, frameworks, or backends).
- Keep changes minimal and consistent with existing HTML structure and naming conventions.

If something isn't discoverable here (for example: real deployment steps, private APIs, or expected CSV/FTP sources), call out the missing information and ask the user for credentials or instructions.

-- End of instructions --
