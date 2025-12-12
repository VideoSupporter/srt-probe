# Repository Guidelines

## Project Structure & Module Organization
- Primary content lives in `docs/`; GitHub Pages builds from here using the minimal Jekyll theme configured in `docs/_config.yml`.
- `docs/index.md` is the entry page; localized copies (e.g., `README.ja.md`, `README.zh.md`, `README.ko.md`, `README.es.md`) sit alongside it.
- Reference material lives under `docs/guides/` (detailed guides and troubleshooting), long-form drafts in `docs/article/`, shared layout in `docs/_layouts/`, and assets in `docs/images/`.
- Keep new images under `docs/images/` and link with relative paths so `jekyll-relative-links` resolves them.

## Build, Test, and Development Commands
- `bundle exec jekyll serve --source docs --livereload --host 0.0.0.0 --port 4000`: run the site locally with live reload for doc edits.
- `bundle exec jekyll build --source docs --destination _site`: validate the site compiles; fails on missing front matter or bad Markdown.
- `bundle exec jekyll doctor`: optional sanity check for common configuration issues.

## Coding Style & Naming Conventions
- Markdown: use GitHub Flavored Markdown; start pages with front matter `---`, `layout: default`, `---` when a layout is required.
- Language suffixes: follow the existing pattern (`.ja.md`, `.zh.md`, `.ko.md`, `.es.md`) and keep English as the source of truth.
- Links: prefer relative links within `docs/`; keep anchor text concise. Use code fences with info strings (e.g., ```bash) for commands.
- Formatting: keep line wrapping readable (~100 characters) and avoid trailing whitespace.

## Testing Guidelines
- Run `bundle exec jekyll build --source docs` before pushing to ensure pages render and Mermaid blocks remain intact.
- Manually verify new/updated links and images from the local serve output; check that translations still point to the same targets.
- For new assets, confirm file names are lowercase with hyphens and referenced from the correct locale page.

## Commit & Pull Request Guidelines
- Follow the existing short, conventional-style prefixes seen in history (`docs: ...`, `feat: ...`). Use imperative mood and keep subjects under ~72 characters.
- Each PR should summarize scope, list affected locales, and include screenshots or GIFs for visual changes.
- Link related issues or forms, note any build/test commands run, and mention known follow-ups when deferring translation updates.

## Localization Notes
- When adding English content, open follow-up tasks for missing translations; partial updates are acceptable if clearly noted in the PR.
- Keep terminology consistent across languages (e.g., “SRT Probe”, mode names, and button labels). Use existing files as the glossary.
