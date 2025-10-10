# Deployment Guide

This site uses MkDocs with the Material theme and is automatically deployed to GitHub Pages.

## Automatic Deployment

Every time you push to the `main` branch, GitHub Actions will automatically:
1. Build the MkDocs site
2. Deploy it to GitHub Pages

## Setup Required (One-time)

Go to your GitHub repository settings:
1. Navigate to **Settings** → **Pages**
2. Under "Build and deployment":
   - **Source**: Select "GitHub Actions"
3. Save the settings

## Local Development

```bash
# Activate virtual environment
source .venv/bin/activate

# Start development server
mkdocs serve

# View at http://localhost:8000
```

## Manual Deployment (Alternative)

If you prefer to deploy manually from your local machine:

```bash
source .venv/bin/activate
mkdocs gh-deploy
```

## Project Structure

```
practice_circle/
├── docs/              # Markdown content
│   ├── index.md       # Homepage
│   ├── manifesto/     # Manifesto documents
│   ├── framework/     # Framework documents
│   ├── practice/      # Practice guides
│   └── facilitator/   # Facilitator guides
├── mkdocs.yml         # MkDocs configuration
├── .venv/             # Python virtual environment
└── site/              # Generated HTML (auto-built, not committed)
```

## Adding Content

1. Add or edit markdown files in the `docs/` directory
2. Update `mkdocs.yml` navigation if adding new pages
3. Commit and push to main branch
4. GitHub Actions will automatically deploy

## Theme Customization

The site uses Material for MkDocs. To customize:
- Edit `mkdocs.yml` for theme settings
- See: https://squidfunk.github.io/mkdocs-material/

## Requirements

Python dependencies (already in `.venv/`):
- mkdocs
- mkdocs-material

