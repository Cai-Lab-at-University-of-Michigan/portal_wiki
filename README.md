# Portal Wiki - Shared Documentation System

This repository provides **shared documentation** that is automatically customized and deployed to multiple portal sites.

---

## Architecture

### Source Repository (This Repo)
- Shared documentation templates in `docs/` folder
- Portal configurations in `portals.yml`
- Build infrastructure and workflows
- MkDocs configuration template

### Portal Repositories
Each portal has its own repository that:
- Receives automatically built documentation
- Publishes to its own GitHub Pages site
- Has portal-specific branding (name, URLs)

### Live Portal Sites

- **RE-JOIN Portal**: https://Cai-Lab-at-University-of-Michigan.github.io/RE_JOIN_PORTAL_WIKI/
- **Microendoscope Portal**: https://Cai-Lab-at-University-of-Michigan.github.io/MICROENDOSCOPE_PORTAL_WIKI/

---

## How It Works

### Deployment Flow

1. You edit shared documentation in this repo's `docs/` folder
2. Documentation uses template variables like `{{PORTAL_NAME}}`, `{{PORTAL_URL}}`
3. When you push to this source repo (or manually trigger):
   - Workflow reads `portals.yml`
   - For each portal:
     - Copies `docs/` folder
     - Substitutes portal-specific variables
     - Builds with portal-specific configuration
     - Deploys to that portal's GitHub Pages
4. Same documentation, customized for each portal

### Template Variables

Use these variables in documentation markdown files:
- `{{PORTAL_NAME}}` - Portal display name (e.g., "RE-JOIN Portal Wiki")
- `{{PORTAL_URL}}` - Portal application URL (e.g., "https://rejoin.cai-lab.org")
- `{{SITE_URL}}` - Documentation site URL

Example:
```markdown
# Welcome to {{PORTAL_NAME}}

Visit the portal at {{PORTAL_URL}}/login
```

---

## Adding a New Portal

It's fully automated! Just add the portal configuration and commit.

### 1. Add Portal Configuration

Edit `portals.yml` and add your portal:

```yaml
portals:
  - name: yourportal
    display_name: "Your Portal Wiki"
    repository: Cai-Lab-at-University-of-Michigan/YOUR_PORTAL_WIKI
    site_url: "https://Cai-Lab-at-University-of-Michigan.github.io/YOUR_PORTAL_WIKI/"
    repo_url: "https://github.com/Cai-Lab-at-University-of-Michigan/YOUR_PORTAL_WIKI"
```

### 2. Commit and Push

```bash
git add portals.yml
git commit -m "Add new portal: yourportal"
git push
```

That's it! The workflow will automatically:
- Create the portal repository if it doesn't exist
- Enable GitHub Pages
- Build and deploy the documentation with portal-specific customization
- Publish to GitHub Pages

The site will be live at the configured site URL within a few minutes.

### Optional: Trigger Deployment Manually

The deployment runs automatically when you push to this source repository. To manually trigger:

1. Go to this repository's Actions tab
2. Select "Deploy to All Portals"
3. Click "Run workflow"

---

## Contributing

To contribute documentation:
1. Fork this repository
2. Edit files in the `docs/` folder
3. Use template variables (`{{PORTAL_NAME}}`, `{{PORTAL_URL}}`) for portal-specific content
4. Submit a pull request
5. Once merged, changes automatically deploy to all portals

See [contributing guide](CONTRIBUTING.md) for detailed guidelines.

---

## Local Development & Preview

### Prerequisites

1. Set up Python virtual environment:

```bash
python3 -m venv .venv
source .venv/bin/activate    # macOS / Linux
# OR
.\.venv\Scripts\activate     # Windows PowerShell
```

2. Install dependencies:

```bash
pip install mkdocs-material \
            mkdocs-minify-plugin \
            mkdocs-redirects \
            mkdocs-git-revision-date-localized-plugin \
            mkdocs-glightbox
```

### Preview Portal Documentation Locally

```bash
# Set portal variables
export PORTAL_NAME="RE-JOIN Portal Wiki"
export SITE_URL="https://Cai-Lab-at-University-of-Michigan.github.io/RE_JOIN_PORTAL_WIKI/"
export REPO_URL="https://github.com/Cai-Lab-at-University-of-Michigan/RE_JOIN_PORTAL_WIKI"
export PORTAL_URL="https://rejoin.cai-lab.org"

# Substitute variables in docs
cp -r docs docs-preview
find docs-preview -type f -name "*.md" -exec sed -i '' "s|{{PORTAL_NAME}}|$PORTAL_NAME|g" {} +
find docs-preview -type f -name "*.md" -exec sed -i '' "s|{{PORTAL_URL}}|$PORTAL_URL|g" {} +
find docs-preview -type f -name "*.md" -exec sed -i '' "s|{{SITE_URL}}|$SITE_URL|g" {} +

# Generate mkdocs.yml
envsubst < mkdocs.yml.template > mkdocs.yml

# Move preview docs to docs and serve
rm -rf docs
mv docs-preview docs
mkdocs serve

# Clean up after: git checkout docs/
```

Visit http://127.0.0.1:8000 to preview.

---

## Configuration Files

- **`portals.yml`**: Portal configurations (names, URLs, repositories)
- **`mkdocs.yml.template`**: MkDocs configuration template with placeholders
- **`docs/`**: Shared documentation templates with template variables

---

## GitHub Actions Workflows

### In This Repository

- **`deploy-all-portals.yml`**: Deploys to all portals on push to main
- **`links.yml`**: Checks for broken links in portal repositories weekly

---

## Secrets Required

**`PORTAL_WIKI_DEPLOY_TOKEN`** (Required in this source repository)

A GitHub Personal Access Token with the following permissions:
- `repo` (Full control of private repositories)
- Allows the workflow to:
  - Create new portal repositories
  - Clone portal repositories to fetch docs
  - Push deployments to portal repositories
  - Enable GitHub Pages on portal repositories

To create:
1. Go to GitHub Settings → Developer settings → Personal access tokens → Tokens (classic)
2. Generate new token with `repo` scope
3. Add as secret in this repository: Settings → Secrets and variables → Actions → New repository secret

---

## Questions?

Open an issue or contact the repository maintainers.
