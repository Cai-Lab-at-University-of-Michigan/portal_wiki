# Contributing to RE-JOIN Docs

## Quick start
1. Fork this repo and create a branch: `git checkout -b docs/my-change`
2. Install MkDocs: `pip install mkdocs-material`
3. Preview locally: `mkdocs serve` (open http://127.0.0.1:8000/)
4. Commit + push, then open a Pull Request.

## Writing rules
- Use Markdown only; headings start with a single `## Title`.
- Use **relative links** to other pages (e.g., `file-conversion.md`).
- Put images in `docs/assets/` and link `./assets/<name>.png`.
- Put pdfs in `docs/tutorials/` and link `./tutorials/<name>.pdf`.
- Use template variables for portal-specific content:
  - `{{PORTAL_NAME}}` for portal display name
  - `{{PORTAL_URL}}` for portal application URL
  - `{{SITE_URL}}` for documentation site URL
- Keep sections: *Aim*, *Steps*, *Troubleshooting*, *Links/Next*.


## Style tips
- Use imperative steps (1., 2., 3.).
- Prefer code ticks for UI labels: `Upload Files`, `Convert to SISF`.
- No inline HTML unless necessary.

## PR review checklist
- Builds locally (`mkdocs build`) without warnings.
- No broken links; images load.
- Page fits within nav in `mkdocs.yml`.
