# Contributing to The Practice Circle

Thank you for your interest in improving these documents. All contributions go through a transparent review process using pull requests.

---

## Governance First

**Before contributing**, please read:
- **[docs/framework/HOW_WE_CHANGE.md](docs/framework/HOW_WE_CHANGE.md)** - How documents evolve, Quaker discernment process, experimental branches, formal meetings
- **[docs/framework/CHARTA.md](docs/framework/CHARTA.md)** - Section 10: Document Governance

This file focuses on the **technical Git/GitHub workflow**. The governance principles are part of the framework.

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

### Fork and Branch

```bash
# Fork the repository on GitHub first

# Clone your fork
git clone https://github.com/YOUR_USERNAME/practice_circle.git
cd practice_circle

# Add upstream remote
git remote add upstream https://github.com/ORIGINAL_OWNER/practice_circle.git

# Create a branch
git checkout -b fix/typo-in-charta
# or
git checkout -b improve/session-structure
# or
git checkout -b experiment/60min-sessions
```

### Make Changes

Edit the relevant markdown files in `docs/`. Use clear, simple language.

```bash
# Check what changed
git status
git diff

# Stage your changes
git add docs/framework/CHARTA.md

# Commit with clear message
git commit -m "Fix typo in daily practice section"
# or
git commit -m "Clarify online ad hoc format structure"
```

### Submit Pull Request

```bash
# Push to your fork
git push origin fix/typo-in-charta

# Then go to GitHub and create a Pull Request
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
- Use ATX-style headers (`#` not underlines)
- Use `-` for unordered lists
- Use `---` for horizontal rules
- Include front matter for MkDocs navigation

### Language Style
- Use **bold** for emphasis on key concepts
- Use *italics* for quotes or reflective notes
- Use `>` blockquotes for provisional notices or important callouts
- Keep language simple, direct, and non-dogmatic
- Avoid jargon unless necessary (define when used)
- Write in present tense
- Use inclusive, accessible language

### Front Matter (for docs/)

```yaml
---
title: Page Title
parent: Section Name
nav_order: 1
---
```

---

## File Organization

```
docs/
├── manifesto/          # Why we exist
├── framework/          # How circles operate
│   ├── CHARTA.md
│   ├── HOW_WE_CHANGE.md
│   ├── DECISION_MEETING_PROTOCOL.md
│   └── ...
├── facilitator/        # Guidance for facilitators
├── practice/           # Practice stages and appendices
├── federation/         # (future) Inter-circle coordination
└── research/           # (future) Documentation and learning

CONTRIBUTING.md         # This file (technical workflow)
EXPERIMENTS.md          # Active and archived experiments
README.md               # Project overview
```

---

## Experimental Branches

See **[docs/framework/HOW_WE_CHANGE.md](docs/framework/HOW_WE_CHANGE.md)** for full process.

### Quick Steps:

1. **Propose**: Open issue with `experiment-proposal` label
2. **Create branch**: `git checkout -b experiment/description`
3. **Add to EXPERIMENTS.md**: List your experiment
4. **Test in practice**: Defined duration with minimum participants
5. **Hold review meeting**: Document using template in HOW_WE_CHANGE.md
6. **Submit PR**: Include meeting notes and participant count
7. **Update EXPERIMENTS.md**: Mark outcome

### Branch Naming

- `fix/*` - Small fixes (typos, formatting)
- `improve/*` - Structural improvements
- `experiment/*` - New approaches being tested
- `docs/*` - Documentation updates

---

## Building Locally

### Install Dependencies

```bash
pip install -r requirements.txt
```

### Preview Site

```bash
mkdocs serve
```

Then open http://localhost:8000

### Build Site

```bash
mkdocs build
```

Output goes to `site/` directory.

---

## Common Tasks

### Fix a Typo

```bash
git checkout -b fix/typo-location
# Edit file
git add docs/framework/CHARTA.md
git commit -m "Fix typo in Section 3"
git push origin fix/typo-location
# Create PR on GitHub
```

### Propose Structural Change

```bash
# 1. Open GitHub issue first, discuss
# 2. If there's support:
git checkout -b improve/online-format-details
# Edit files
git add docs/framework/CHARTA.md
git commit -m "Add more detail to online ad hoc format"
git push origin improve/online-format-details
# Create PR linking to issue
```

### Start Experiment

```bash
# 1. Open issue with experiment-proposal label
# 2. Create branch
git checkout -b experiment/walking-circles
# 3. Add documentation
# Edit docs, mark as experimental
# 4. Update EXPERIMENTS.md
git add docs/practice/WALKING_CIRCLES.md EXPERIMENTS.md
git commit -m "Experiment: Walking circle format"
git push origin experiment/walking-circles
# 5. Test in practice (don't create PR yet!)
# 6. After testing + meeting, create PR with notes
```

---

## Getting Help

- **Questions about how we change**: Read [docs/framework/HOW_WE_CHANGE.md](docs/framework/HOW_WE_CHANGE.md)
- **Questions about practice**: Read [docs/framework/CHARTA.md](docs/framework/CHARTA.md)
- **Technical issues**: Open a GitHub issue
- **Want to discuss an idea**: Open a GitHub issue before creating PR

---

## License

By contributing, you agree that your contributions will be licensed under the same license as the project (see LICENSE file).

---

> *These technical guidelines can be updated through the standard review process (Tier 2: Structural Changes).*
