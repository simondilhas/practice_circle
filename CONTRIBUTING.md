# Contributing to The Practice Circle

> **New to GitHub or not technical?**  
> See [**How to Contribute Changes**](docs/howto/organize/protocols/contribute_changes.md) for a beginner-friendly guide with screenshots.

This document covers the **technical Git/GitHub workflow** for developers and experienced contributors.

---

## Prerequisites

- Git installed and configured
- GitHub account with SSH keys configured (recommended) or HTTPS access
- Familiarity with Git branching, pull requests, and markdown
- Text editor or IDE (VS Code, Vim, etc.)

---

## Governance Context

**Before contributing**, understand the governance model:
- **[docs/howto/organize/lifecycle/evolve_the_circle.md](docs/howto/organize/lifecycle/evolve_the_circle.md)** - Change tiers, Quaker discernment process, experimental branches, formal meetings
- Changes are reviewed for alignment with core principles, not just technical correctness
- Significant changes require discussion in GitHub Issues before PR submission
- Experimental changes require testing in practice before adoption

---

## Quick Reference

| Type | Process | Approvals |
|------|---------|-----------|
| **Typos/clarity** | Submit PR | 1 |
| **Structural changes** | Issue first, then PR | 2 |
| **Experimental changes** | Test in branch, formal meeting, PR with notes | 2+ |
| **Core principles** | Multiple circles, extended testing | 3+ |

---

## Git Workflow

### Initial Setup

```bash
# Fork the repository on GitHub (click "Fork" button)

# Clone your fork (SSH recommended)
git clone git@github.com:YOUR_USERNAME/practice_circle.git
# OR with HTTPS:
git clone https://github.com/YOUR_USERNAME/practice_circle.git

cd practice_circle

# Add upstream remote to sync with main repository
git remote add upstream git@github.com:simondilhas/practice_circle.git
# OR with HTTPS:
git remote add upstream https://github.com/simondilhas/practice_circle.git

# Verify remotes
git remote -v
```

### Branch Naming Convention

Use semantic branch names with prefixes:

```bash
fix/*         # Bug fixes, typos, broken links
improve/*     # Structural improvements, clarity enhancements
experiment/*  # Experimental changes being tested
docs/*        # Documentation-only updates
refactor/*    # Restructuring without functional changes
feature/*     # New features or sections
```

**Examples**:
```bash
git checkout -b fix/typo-in-facilitator-guide
git checkout -b improve/decision-protocol-clarity
git checkout -b experiment/60min-session-format
git checkout -b docs/update-contributing-guide
git checkout -b refactor/reorganize-practice-files
```

### Standard Development Workflow

```bash
# 1. Sync with upstream before starting
git fetch upstream
git checkout main
git merge upstream/main
git push origin main  # Update your fork

# 2. Create feature branch from latest main
git checkout -b fix/issue-description

# 3. Make your changes
# Edit files...

# 4. Review changes
git status                    # See what's modified
git diff                      # See line-by-line changes
git diff --cached             # See staged changes

# 5. Stage selectively (prefer granular commits)
git add docs/specific/file.md
# OR stage all changes:
git add .

# 6. Commit with descriptive message
git commit -m "Fix: Correct typo in facilitation section"
# OR with multi-line message:
git commit -m "Improve: Clarify decision-making protocol

- Add examples of when to use formal meetings
- Restructure section for better flow
- Link to related conflict resolution docs"

# 7. Push to your fork
git push origin fix/issue-description

# 8. Create Pull Request on GitHub
# Navigate to: https://github.com/YOUR_USERNAME/practice_circle
# Click "Compare & pull request"
```

### Keeping Your Branch Updated

```bash
# If upstream/main has advanced while you're working:

# Option 1: Rebase (cleaner history, preferred for small changes)
git fetch upstream
git rebase upstream/main
# Resolve conflicts if any
git push origin your-branch --force-with-lease

# Option 2: Merge (preserves history, safer for complex changes)
git fetch upstream
git merge upstream/main
# Resolve conflicts if any
git push origin your-branch
```

### Handling Merge Conflicts

```bash
# When conflicts occur during rebase or merge:

# 1. See conflicted files
git status

# 2. Open conflicted files, look for conflict markers:
# <<<<<<< HEAD
# Your changes
# =======
# Upstream changes
# >>>>>>> upstream/main

# 3. Edit files to resolve conflicts

# 4. Stage resolved files
git add path/to/resolved/file.md

# 5. Complete the operation
git rebase --continue  # if rebasing
# OR
git commit             # if merging
```

### Amending Commits

```bash
# Fix the last commit (message or files)
git add forgotten-file.md
git commit --amend -m "Updated commit message"
git push origin your-branch --force-with-lease

# Interactive rebase for older commits (advanced)
git rebase -i HEAD~3  # Edit last 3 commits
# Follow interactive prompts to edit, squash, or reorder
```

---

## Pull Request Template

When submitting a PR, please include:

```markdown
## Type of Change
- [ ] Typo/grammar fix
- [ ] Clarity improvement
- [ ] Structural change
- [ ] Experimental change (tested in practice)
- [ ] Core principle modification

## Description
[Explain what changed and why]

## Alignment with Core Principles
[How does this support attention, honesty, and compassion?]

## Testing (if applicable)
- Who tested: [people/circles]
- Duration: [timeframe]
- What we learned: [brief summary or link to meeting notes]

## Impact
- Who is affected by this change?
- Does this remove any existing flexibility?
- Has this been discussed in an issue first? [link]

## Related
- Related issue: #[number]
- Related experiment: [branch name if applicable]
```

---

## For Reviewers

### Review with Quaker Discernment

See **[docs/framework/HOW_WE_CHANGE.md](docs/framework/HOW_WE_CHANGE.md)** for full principles.

**Quick guide**:
1. Read carefully with open attention
2. Speak from experience, not theory
3. Seek to understand before judging
4. Choose response mindfully:
   - **Approve**: "I sense this serves the intention"
   - **Comment**: Questions or suggestions (doesn't block)
   - **Request changes**: Needs specific work
   - **Block** (rare): Core principles threatened

### Review Checklist

- [ ] Changes are clear and well-explained
- [ ] Aligns with core principles (attention, honesty, compassion)
- [ ] Doesn't introduce hierarchy, dogma, or barriers
- [ ] Improves accessibility or clarity
- [ ] For structural changes: Has this been discussed?
- [ ] For experimental changes: Are testing notes included?
- [ ] Documentation style is consistent
- [ ] No broken links or formatting errors

---

## Style Guide

### Markdown Standards

**Headers**:
```markdown
# H1 - Page Title (one per page)
## H2 - Major Section
### H3 - Subsection
#### H4 - Minor Subsection (use sparingly)
```

- Use ATX-style headers (`#`) not setext-style (underlines)
- One H1 per page (the page title)
- Hierarchical structure (don't skip levels: H1 → H3)
- Leave blank line before and after headers

**Lists**:
```markdown
- Use hyphens for unordered lists
  - Indent with 2 spaces for nesting
  - Consistent spacing

1. Use numbers for ordered lists
2. Auto-numbering is fine (1., 1., 1.)
3. Or use sequential numbers (1., 2., 3.)
```

**Emphasis**:
```markdown
**Bold** for strong emphasis, key concepts
*Italic* for subtle emphasis, quotes, terms
`Code` for inline code, commands, file paths
```

**Links**:
```markdown
[Link text](relative/path/to/file.md)  - Relative links preferred
[External link](https://example.com)   - External links
[Link with title](file.md "Hover title")
```

**Code Blocks**:
````markdown
```bash
# Bash commands
git commit -m "Message"
```

```python
# Python code
def example():
    pass
```

```yaml
# YAML configuration
key: value
```
````

**Horizontal Rules**:
```markdown
---
```
Use `---` (three hyphens) for thematic breaks

**Blockquotes**:
```markdown
> **Note**: Important callout
> Continues on next line

> *Provisional notice*
> Multi-line quote
```

**Tables**:
```markdown
| Column 1 | Column 2 | Column 3 |
|----------|----------|----------|
| Data     | Data     | Data     |
| Data     | Data     | Data     |
```

**Images**:
```markdown
![Alt text](assets/images/filename.png)
![Alt with title](assets/images/filename.png "Image title")
```

### Language Style

**Tone and Voice**:
- Direct, clear, conversational
- Non-dogmatic, open, inviting
- Avoid absolutist language ("always", "never", "must")
- Prefer "we suggest" over "you must"
- Present tense for current state
- Avoid passive voice where possible

**Formatting**:
- Use **bold** for key concepts, emphasis
- Use *italics* for quotes, reflective notes, terms
- Use `code formatting` for:
  - File paths: `docs/path/to/file.md`
  - Commands: `git commit`
  - Code snippets
  - Configuration values

**Accessibility**:
- Write for global audience (avoid idioms, slang)
- Define jargon on first use
- Use simple, clear language
- Avoid unnecessarily complex words
- Short sentences (15-20 words average)
- Short paragraphs (3-5 sentences)

**Inclusive Language**:
- Gender-neutral pronouns (they/them/their)
- Avoid ableist language
- Avoid culturally specific references unless explained
- Focus on actions, not identities

**Technical Writing**:
- Be specific: "2-3 weeks" not "a while"
- Be concrete: Examples over abstractions
- Be actionable: Clear next steps
- Be scannable: Headings, lists, short paragraphs

### File Naming

**Conventions**:
```
lowercase_with_underscores.md  # For most files
UPPERCASE.md                    # For important root docs
kebab-case-acceptable.md        # Also acceptable
```

**Best Practices**:
- Descriptive names
- No spaces (use `_` or `-`)
- Keep reasonably short (< 50 chars)
- Avoid special characters
- Use `.md` extension

### Directory Structure

```
docs/
├── assets/              # Static files (images, PDFs)
│   └── images/         # Image files
├── howto/              # How-to guides
│   ├── practice/       # Practice instructions
│   └── organize/       # Organizational guides
│       ├── roles/      # Circle roles
│       ├── lifecycle/  # Circle lifecycle
│       ├── protocols/  # Standard protocols
│       └── finances/   # Financial management
├── research/           # Research and background
└── index.md           # Landing page
```

### Commit Message Format

**Structure**:
```
Type: Brief summary (50 chars or less)

Optional longer description after blank line.
- Can use bullet points
- To explain what and why
- Keep lines to 72 characters

Closes #123
```

**Types**:
- `Fix:` Bug fixes, typo corrections
- `Add:` New content, new features
- `Improve:` Enhancements to existing content
- `Refactor:` Restructuring without content changes
- `Docs:` Documentation meta changes
- `Experiment:` Experimental changes

**Examples**:
```
Fix: Correct typo in facilitator guide

Add: New protocol for conflict resolution

- Create comprehensive conflict resolution guide
- Add to navigation under Protocols
- Link from related documents

Closes #45

Improve: Clarify decision-making protocol

Restructure section for better flow, add concrete
examples of when to use formal meetings vs. async
discussion.
```

### Link Conventions

**Internal Links**:
- Use relative paths from current file
- Include `.md` extension
- Link to other docs files (not site/ files)

```markdown
[Link to sibling](./sibling_file.md)
[Link to child](subdir/child_file.md)
[Link to parent](../parent_file.md)
[Link to section](./file.md#section-heading)
```

**External Links**:
- Use full URLs
- Include `https://`
- Open in new tab functionality handled by theme

### Front Matter

Material theme doesn't require front matter for most pages, but you can optionally add:

```yaml
---
# Optional page description for SEO
description: Brief page description here

# Optional: hide table of contents
toc_depth: 2
---
```

Navigation is controlled in `mkdocs.yml`, not in front matter.

---

## Experimental Branches

For detailed governance process, see **[Evolve the Circle](docs/howto/organize/lifecycle/evolve_the_circle.md)**.

### Technical Workflow

Experimental branches allow testing significant changes in practice before merging to main.

**Process**:
1. Open GitHub issue with `experiment-proposal` label
2. Create branch: `git checkout -b experiment/description`
3. Add documentation marked as experimental
4. Update `EXPERIMENTS.md` tracking file
5. Push branch (don't create PR yet)
6. Test in practice for defined period
7. Hold formal review meeting
8. Create PR with:
   - Meeting notes
   - Participant count and contexts
   - Consensus statement
   - Testing outcomes

**Key Points**:
- Experimental branches stay open during testing
- Don't merge until after formal review
- Keep experiment documentation updated
- Archive branch even if declined (preserve learnings)

**Example**:
```bash
# 1. Create and push experimental branch
git checkout -b experiment/60min-sessions
# Add docs marked as experimental
git add docs/experiments/60min_sessions.md EXPERIMENTS.md
git commit -m "Experiment: 60-minute session format"
git push origin experiment/60min-sessions

# 2. Test in practice (4-6 weeks)

# 3. After review meeting, create PR
# Include all testing outcomes and meeting notes
```

---

## Local Development

### Environment Setup

**Recommended: Use virtual environment**

```bash
# Create virtual environment
python3 -m venv venv

# Activate virtual environment
source venv/bin/activate  # On Linux/Mac
# OR
venv\Scripts\activate     # On Windows

# Install dependencies
pip install -r requirements.txt

# Verify installation
mkdocs --version
```

### Development Server

```bash
# Start local dev server with live reload
mkdocs serve

# Or specify host/port
mkdocs serve --dev-addr=0.0.0.0:8080

# Server runs at: http://localhost:8000
# Auto-reloads on file changes
```

**Features**:
- Live reload on save
- Search functionality
- Full theme preview
- Warning messages for broken links

### Build and Validate

```bash
# Build static site
mkdocs build

# Build with strict mode (fail on warnings)
mkdocs build --strict

# Output directory: site/
# Index file: site/index.html
```

### Testing Your Changes

Before submitting PR:

```bash
# 1. Check for markdown linting issues
# Install markdownlint-cli if needed:
npm install -g markdownlint-cli

# Run linter
markdownlint 'docs/**/*.md'

# 2. Check for broken links (local build)
mkdocs build --strict

# 3. Verify navigation structure
mkdocs serve
# Manually check: all pages accessible, nav makes sense

# 4. Check for YAML syntax errors in mkdocs.yml
python -c "import yaml; yaml.safe_load(open('mkdocs.yml'))"
```

### File Structure

```
practice_circle/
├── docs/                     # All markdown source files
│   ├── assets/              # Images, PDFs, etc.
│   │   └── images/
│   ├── howto/               # How-to guides
│   │   ├── practice/        # Practice instructions
│   │   └── organize/        # Organizational guides
│   ├── research/            # Research materials
│   ├── index.md             # Homepage
│   ├── manifesto.md         # Core manifesto
│   └── ...
├── site/                    # Generated static site (gitignored)
├── mkdocs.yml               # MkDocs configuration
├── requirements.txt         # Python dependencies
└── CONTRIBUTING.md          # This file
```

### MkDocs Configuration

Key sections in `mkdocs.yml`:

```yaml
site_name: Project title
theme:
  name: material          # Material theme
  features:              # Enabled features
    - navigation.tabs
    - search.suggest
    - ...

nav:                     # Navigation structure
  - Home: index.md       # Defines menu order
  - Section:
    - Page: path/to/file.md

markdown_extensions:     # Enabled markdown features
  - admonition          # Info boxes
  - pymdownx.tabbed     # Tabs
  - ...
```

### Deployment (Maintainers Only)

Site deploys automatically via GitHub Actions on merge to `main`.

**Manual deployment** (if needed):
```bash
# Build and deploy to GitHub Pages
mkdocs gh-deploy

# With custom message
mkdocs gh-deploy -m "Deploy custom message"
```

**Note**: GitHub Actions workflow in `.github/workflows/` handles automatic deployment.

---

## Common Tasks

### Fix a Typo (Quick PR)

```bash
# 1. Sync and branch
git fetch upstream
git checkout main
git merge upstream/main
git checkout -b fix/typo-in-facilitator-guide

# 2. Edit file
vim docs/howto/organize/roles/facilitator.md

# 3. Commit and push
git add docs/howto/organize/roles/facilitator.md
git commit -m "Fix: Correct typo in facilitation checklist"
git push origin fix/typo-in-facilitator-guide

# 4. Create PR on GitHub
# Go to your fork, click "Compare & pull request"
```

### Propose Structural Change (With Discussion)

```bash
# 1. Open GitHub issue FIRST
# Navigate to: https://github.com/simondilhas/practice_circle/issues/new
# Discuss proposed changes with community

# 2. After discussion support, create branch
git fetch upstream
git checkout main
git merge upstream/main
git checkout -b improve/decision-protocol-examples

# 3. Make changes
vim docs/howto/organize/protocols/make_decisions.md

# 4. Test locally
mkdocs serve
# Preview at http://localhost:8000

# 5. Commit with reference to issue
git add docs/howto/organize/protocols/make_decisions.md
git commit -m "Improve: Add examples to decision protocol

- Add concrete examples of when to use formal meetings
- Restructure for better flow
- Link to conflict resolution protocol

Closes #123"

# 6. Push and create PR
git push origin improve/decision-protocol-examples
# Create PR on GitHub, link to issue
```

### Start Experimental Branch

```bash
# 1. Open issue with experiment proposal
# Label: "experiment-proposal"
# Describe: what, why, testing plan, success criteria

# 2. Create experimental branch
git fetch upstream
git checkout main
git merge upstream/main
git checkout -b experiment/60min-session-format

# 3. Add experimental documentation
mkdir -p docs/experiments
vim docs/experiments/60min_sessions.md
# Mark clearly as "⚠️ EXPERIMENTAL"

# 4. Update experiments tracking
vim EXPERIMENTS.md
# Add entry with status, testers, timeline

# 5. Commit
git add docs/experiments/60min_sessions.md EXPERIMENTS.md
git commit -m "Experiment: 60-minute session format

- Add initial documentation
- Mark as experimental
- Define testing criteria: 3+ circles, 6 weeks
- Track in EXPERIMENTS.md"

# 6. Push (but DON'T create PR yet)
git push origin experiment/60min-session-format

# 7. Test in practice for defined period
# ...testing happens...

# 8. Hold formal review meeting
# Document outcomes, consensus, learnings

# 9. After testing complete, create PR
# Include: meeting notes, participant count, consensus statement
# PR description explains testing outcomes
```

### Add New Page to Navigation

```bash
# 1. Create the markdown file
vim docs/howto/organize/protocols/new_protocol.md

# 2. Add front matter (optional for Material theme)
# But ensure content follows standard format

# 3. Update mkdocs.yml navigation
vim mkdocs.yml
# Add entry under appropriate section:
# - Protocols:
#   - New Protocol: howto/organize/protocols/new_protocol.md

# 4. Test navigation locally
mkdocs serve
# Verify page appears in menu and loads correctly

# 5. Commit both files
git add docs/howto/organize/protocols/new_protocol.md mkdocs.yml
git commit -m "Add: New protocol documentation

- Create new protocol guide
- Add to navigation under Protocols section"

git push origin your-branch
```

### Update File Organization

```bash
# When reorganizing files (BE CAREFUL - breaks links)

# 1. Move/rename files using git mv (preserves history)
git mv docs/old/path/file.md docs/new/path/file.md

# 2. Update mkdocs.yml navigation
vim mkdocs.yml

# 3. Find and update all internal links
grep -r "old/path/file" docs/
# Update all references

# 4. Test thoroughly
mkdocs serve
# Click through all navigation
# Test search functionality

mkdocs build --strict
# Check for broken links

# 5. Commit with clear description
git add -A
git commit -m "Refactor: Reorganize protocol documentation

- Move protocols to new structure
- Update navigation in mkdocs.yml
- Fix all internal links
- Verify no broken references"
```

---

## Advanced Topics

### Working with Multiple Branches

```bash
# List all branches (local and remote)
git branch -a

# Switch between branches
git checkout branch-name
# OR newer syntax:
git switch branch-name

# Work on multiple features simultaneously
git checkout -b feature/first-feature
# ... work ...
git checkout -b feature/second-feature
# ... work ...

# Keep branches updated independently
git checkout feature/first-feature
git fetch upstream
git rebase upstream/main

git checkout feature/second-feature
git fetch upstream
git rebase upstream/main
```

### Cherry-Picking Commits

```bash
# Apply a specific commit from another branch
git checkout target-branch
git cherry-pick <commit-hash>

# Cherry-pick multiple commits
git cherry-pick <commit1> <commit2> <commit3>

# Cherry-pick with no commit (stage only)
git cherry-pick -n <commit-hash>
```

### Stashing Work in Progress

```bash
# Save uncommitted changes temporarily
git stash save "Work in progress on feature X"

# List stashes
git stash list

# Apply most recent stash
git stash apply

# Apply specific stash
git stash apply stash@{2}

# Apply and remove stash
git stash pop

# Clear all stashes
git stash clear
```

### Cleaning Up History

```bash
# Squash last 3 commits into one
git rebase -i HEAD~3
# In editor, change 'pick' to 'squash' for commits to combine

# Split a commit into multiple
git rebase -i HEAD~1
# Mark commit as 'edit'
git reset HEAD^
# Stage and commit changes separately
git commit -m "First part"
git commit -m "Second part"
git rebase --continue

# Remove a commit from history
git rebase -i HEAD~5
# Delete the line with unwanted commit
```

### Searching and Debugging

```bash
# Search for text in files
git grep "search term"

# Search in specific file types
git grep "search term" -- "*.md"

# Find when a line was changed
git blame docs/path/to/file.md

# Find which commit introduced a bug (binary search)
git bisect start
git bisect bad                 # Current commit is bad
git bisect good <commit-hash>  # Known good commit
# Git will checkout commits; test each:
git bisect good  # or 'git bisect bad'
git bisect reset  # When done

# View file at specific commit
git show <commit-hash>:path/to/file.md

# View all changes to a file
git log --follow -p -- docs/path/to/file.md
```

### Advanced Diffing

```bash
# Compare branches
git diff main..your-branch

# Compare specific files between branches
git diff main..your-branch -- docs/specific/file.md

# Compare working directory to specific commit
git diff <commit-hash>

# Word-level diff (not line-level)
git diff --word-diff

# Statistics only
git diff --stat

# Show what would be merged
git diff main...your-branch  # Note: three dots
```

### Undoing Things

```bash
# Undo unstaged changes to a file
git checkout -- path/to/file.md
# OR newer syntax:
git restore path/to/file.md

# Unstage a file (keep changes)
git reset HEAD path/to/file.md
# OR newer syntax:
git restore --staged path/to/file.md

# Undo last commit (keep changes)
git reset --soft HEAD^

# Undo last commit (discard changes)
git reset --hard HEAD^

# Revert a published commit (creates new commit)
git revert <commit-hash>
```

### Useful Git Aliases

Add to `~/.gitconfig`:

```ini
[alias]
    st = status -sb
    co = checkout
    br = branch
    cm = commit -m
    ca = commit --amend
    df = diff
    lg = log --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit
    unstage = reset HEAD --
    last = log -1 HEAD
    visual = log --graph --oneline --all
```

Then use:
```bash
git st           # Instead of git status
git lg           # Pretty log
git visual       # Branch visualization
```

### Performance and Maintenance

```bash
# Clean up unnecessary files and optimize
git gc

# Verify repository integrity
git fsck

# Show repository size
git count-objects -vH

# Prune remote tracking branches that no longer exist
git fetch --prune

# Remove branches that have been merged
git branch --merged | grep -v "\*" | xargs -n 1 git branch -d
```

---

## Troubleshooting

### "Detached HEAD" State

```bash
# You're in detached HEAD if you checked out a specific commit

# To save your work:
git checkout -b new-branch-name
# OR attach to existing branch:
git checkout main
git merge <commit-hash>
```

### Accidentally Committed to Wrong Branch

```bash
# If you committed to main instead of feature branch:

# 1. Create branch from current state
git branch feature/my-work

# 2. Reset main to upstream
git reset --hard upstream/main

# 3. Switch to your feature branch
git checkout feature/my-work
```

### Push Rejected (Non-Fast-Forward)

```bash
# Someone else pushed to the branch

# Option 1: Pull and merge
git pull origin your-branch
# Resolve conflicts if any
git push origin your-branch

# Option 2: Pull and rebase (cleaner)
git pull --rebase origin your-branch
git push origin your-branch

# Option 3: Force push (CAREFUL - only if you're sure)
git push origin your-branch --force-with-lease
```

### Large Files Accidentally Committed

```bash
# If you committed large files (>50MB):

# Remove from last commit
git rm --cached path/to/large/file
git commit --amend -m "Remove large file"

# Remove from history (if already pushed)
# Use BFG Repo-Cleaner or git-filter-branch
# See: https://rtyley.github.io/bfg-repo-cleaner/
```

### Recover Deleted Branch

```bash
# Find the commit hash
git reflog

# Recreate branch
git checkout -b recovered-branch <commit-hash>
```

---

## Getting Help

### Documentation
- **Beginner's guide**: [How to Contribute Changes](docs/howto/organize/protocols/contribute_changes.md)
- **Governance model**: [Evolve the Circle](docs/howto/organize/lifecycle/evolve_the_circle.md)
- **Git documentation**: [git-scm.com/doc](https://git-scm.com/doc)
- **MkDocs documentation**: [mkdocs.org](https://www.mkdocs.org/)
- **Material theme**: [squidfunk.github.io/mkdocs-material](https://squidfunk.github.io/mkdocs-material/)

### Getting Support
- **GitHub Issues**: Open an issue for discussions, questions, or bug reports
- **Pull Request Comments**: Ask questions directly on PRs
- **Community Discussion**: Use issue comments for longer discussions

---

## License

By contributing, you agree that your contributions will be licensed under the same license as the project [LICENSE](LICENSE.md)

---

> *These technical guidelines can be updated through the standard review process (Tier 2: Structural Changes).*
