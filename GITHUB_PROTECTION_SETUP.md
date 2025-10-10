# Setting Up Branch Protection for Document Governance

To enable the pull request governance model, configure GitHub branch protection for the `main` branch.

---

## Steps to Configure

### 1. Navigate to Repository Settings
```
GitHub Repository → Settings → Branches → Add branch protection rule
```

### 2. Branch Name Pattern
```
main
```

### 3. Protection Rules to Enable

#### ✅ Required Settings

**Require a pull request before merging**
- ✅ Enable this
- Set "Required number of approvals before merging": **2**
  - For small/forming circles, start with 1
  - Increase to 2-3 as the community grows

**Require status checks to pass before merging**
- ✅ Enable this
- Select: `build` (from your deploy-mkdocs workflow)
- This ensures the site builds successfully

**Do not allow bypassing the above settings**
- ✅ Enable this
- Applies to administrators too (important for accountability)

#### ⚠️ Optional but Recommended

**Require conversation resolution before merging**
- ✅ Enable this
- Ensures all discussion threads are addressed

**Require linear history**
- Consider enabling this to keep a clean history
- Prevents merge commits, requires rebase or squash

**Lock branch**
- ❌ Do not enable
- Would prevent all direct commits (too restrictive)

**Do not allow force pushes**
- ✅ Enable this
- Protects history from being rewritten

---

## Who Can Approve?

### Initial Phase (Pre-Circle Formation)
- Repository owner and trusted early contributors
- 1 approval sufficient for testing

### After First Circle Forms
- Any member of formed circles with repository access
- Rotate access quarterly (aligned with role rotation)
- 2 approvals from different people

### Federation Phase (Multiple Circles)
- Representatives from different circles
- Require approvals from different circles for core changes
- 3+ approvals for principle-level modifications

---

## Granting Repository Access

### Collaborator Access Levels:

**Write Access** (for active circle members):
```
Repository → Settings → Collaborators → Add people
```
- Can create branches
- Can submit PRs
- Can review and approve PRs
- **Cannot** merge to protected main (requires approval)

**Maintain Access** (for rotating facilitators):
- All Write permissions
- Can merge approved PRs
- Rotates every 3 months (aligned with role rotation)

### Best Practice
- Start conservative (fewer people with merge rights)
- Expand as trust and processes stabilize
- Always require at least 1 other approval (no self-merge)

---

## Pull Request Workflow

### For Contributors:

1. **Fork or create branch**
   ```bash
   git checkout -b improve/session-structure
   ```

2. **Make changes and commit**
   ```bash
   git add docs/framework/CHARTA.md
   git commit -m "Clarify daily practice requirements"
   ```

3. **Push and create PR**
   ```bash
   git push origin improve/session-structure
   ```
   Then create PR on GitHub

4. **Address review feedback**
   - Respond to comments
   - Make requested changes
   - Discuss disagreements openly

5. **Wait for approval and merge**
   - Required approvals obtained
   - Conflicts resolved
   - Maintainer merges

### For Reviewers:

**Use Quaker-inspired discernment** (see [docs/framework/HOW_WE_CHANGE.md](docs/framework/HOW_WE_CHANGE.md) for full details):

1. **Read carefully with open attention**
   - What changed and why?
   - Is the reasoning clear?
   - What's your felt sense of this?

2. **Speak from experience, not theory**
   - "This helped/harmed my circle" > "This seems wrong"
   - Has it been tested in practice?
   - Does it align with core principles?

3. **Seek to understand before judging**
   - Ask questions
   - Listen deeply to responses
   - Consider alternatives together

4. **Choose your response mindfully**
   - **Approve**: "I sense this serves the intention"
   - **Comment**: Questions or suggestions (doesn't block)
   - **Request changes**: Needs specific work before ready
   - **Block** (rare): Only when core principles threatened

**Remember**: You're seeking unity through discernment, not voting on preferences.

---

## Emergency Changes

### What if immediate change is needed?

For genuine emergencies (security issues, broken deployments, harmful content):

1. **Create the PR anyway** (maintains transparency)
2. **Mark as urgent** in the title and description
3. **One approval is sufficient** (from any maintainer)
4. **Document in PR why urgency was needed**
5. **Retrospective**: Discuss how to prevent similar emergencies

**Note**: "I want this now" is not an emergency. Part of the practice is working with the constraint of collective review.

---

## Testing the Process

### First PR Exercise

After setting up protection, create a test PR:

1. Make a trivial change (fix a typo in README)
2. Follow the full PR process
3. Have someone else review and approve
4. Merge and verify deployment works
5. Check that direct push to main is blocked

This verifies your protection is working correctly.

---

## Evolving the Process

These protection settings are **not final**. They can change as you learn:

- Too slow? Reduce approval requirements for minor changes
- Too fast? Increase approvals for core documents
- Too centralized? Rotate maintainer access more frequently
- Not inclusive? Expand who can review and approve

**Change the process through the process itself** — submit a PR to modify these guidelines.

---

## Key Principle

> The goal is **thoughtfulness, not bureaucracy**.  
> Protection enables collective discernment, not control.  
> When in doubt, favor transparency and discussion over speed.

---

## Current Status

**Action Required**: 
- [ ] Enable branch protection on `main`
- [ ] Set required approvals to 1 (initially)
- [ ] Add trusted collaborators
- [ ] Create test PR to verify setup
- [ ] Document who has access and when it rotates

Once configured, update this section with:
- Date protection enabled
- Current approval requirements  
- Current maintainers and rotation schedule

