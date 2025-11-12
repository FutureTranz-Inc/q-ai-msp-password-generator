# GitHub Repository Setup Guide

**Repository:** https://github.com/FutureTranz-Inc/q-ai-msp-password-generator
**Organization:** FutureTranz-Inc
**Type:** Private Repository
**License:** Proprietary

---

## Prerequisites

- GitHub account with access to FutureTranz-Inc organization
- Git installed and configured locally
- SSH key or GitHub Personal Access Token configured

---

## Step 1: Create Private Repository on GitHub

### Via GitHub Web Interface

1. Navigate to https://github.com/FutureTranz-Inc
2. Click "New repository" button
3. Configure repository settings:
   - **Repository name:** `q-ai-msp-password-generator`
   - **Description:** Enterprise password generator for Q-AI-MSP platform with compliance framework support
   - **Visibility:** Private (IMPORTANT: This contains proprietary code)
   - **Initialize repository:** ❌ Do NOT initialize with README (we already have one)
   - **Add .gitignore:** None (we already have one)
   - **Add license:** None (proprietary)

4. Click "Create repository"

### Via GitHub CLI (Alternative)

```bash
# Install GitHub CLI if not already installed
brew install gh  # macOS
# or: sudo apt install gh  # Ubuntu/Debian
# or: choco install gh  # Windows

# Authenticate with GitHub
gh auth login

# Create private repository
gh repo create FutureTranz-Inc/q-ai-msp-password-generator \
  --private \
  --description "Enterprise password generator for Q-AI-MSP platform with compliance framework support" \
  --disable-wiki \
  --disable-issues=false
```

---

## Step 2: Connect Local Repository to GitHub

### If starting from existing local repository:

```bash
# Navigate to project directory
cd q-ai-msp-password-generator

# Verify current git status
git status
git log --oneline -5

# Add GitHub remote (if not already added)
git remote add origin git@github.com:FutureTranz-Inc/q-ai-msp-password-generator.git

# Verify remote is configured
git remote -v

# Push all branches to GitHub
git push -u origin main

# Push all tags (if any)
git push --tags

# Initialize and push submodule (ai-dev-tasks)
git submodule update --init --recursive
git push --recurse-submodules=on-demand
```

### If cloning from GitHub (for team members):

```bash
# Clone repository with submodules
git clone --recurse-submodules git@github.com:FutureTranz-Inc/q-ai-msp-password-generator.git

# Navigate to project
cd q-ai-msp-password-generator

# Install dependencies
npm install

# Set up environment
cp .env.example .env
# Edit .env with your credentials

# Install git hooks for ai-dev-tasks
bash ai-dev-tasks/scripts/install-hooks.sh
```

---

## Step 3: Configure Repository Settings

### Branch Protection Rules

1. Go to repository settings: https://github.com/FutureTranz-Inc/q-ai-msp-password-generator/settings
2. Navigate to "Branches" → "Branch protection rules"
3. Add rule for `main` branch:
   - ✅ Require pull request reviews before merging (1 approval)
   - ✅ Require status checks to pass before merging
     - ✅ `lint` check
     - ✅ `test` check
     - ✅ `build` check
   - ✅ Require branches to be up to date before merging
   - ✅ Require linear history
   - ✅ Do not allow bypassing the above settings (even for admins)

### Repository Access

1. Navigate to "Settings" → "Collaborators and teams"
2. Add team members as needed:
   - **Admin access:** Repository owners and maintainers
   - **Write access:** Core development team
   - **Read access:** Product and QA teams

### Security Settings

1. Navigate to "Settings" → "Security & analysis"
2. Enable:
   - ✅ Dependency graph
   - ✅ Dependabot alerts
   - ✅ Dependabot security updates
   - ✅ Secret scanning
   - ✅ Push protection (prevents committing secrets)

### Repository Topics

Add topics for discoverability within organization:
- `password-generator`
- `security`
- `compliance`
- `msp`
- `enterprise`
- `nist`
- `pci-dss`
- `hipaa`
- `soc2`
- `q-ai-msp`

---

## Step 4: Set Up GitHub Actions (CI/CD)

Create `.github/workflows/ci.yml`:

```yaml
name: CI

on:
  push:
    branches: [main, develop]
  pull_request:
    branches: [main, develop]

jobs:
  lint:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
        with:
          submodules: recursive
      - uses: actions/setup-node@v4
        with:
          node-version: '20'
          cache: 'npm'
      - run: npm ci
      - run: npm run lint

  test:
    runs-on: ubuntu-latest
    services:
      postgres:
        image: postgres:16
        env:
          POSTGRES_PASSWORD: postgres
        options: >-
          --health-cmd pg_isready
          --health-interval 10s
          --health-timeout 5s
          --health-retries 5
      redis:
        image: redis:7
        options: >-
          --health-cmd "redis-cli ping"
          --health-interval 10s
          --health-timeout 5s
          --health-retries 5
    steps:
      - uses: actions/checkout@v4
        with:
          submodules: recursive
      - uses: actions/setup-node@v4
        with:
          node-version: '20'
          cache: 'npm'
      - run: npm ci
      - run: npm test
        env:
          DATABASE_URL: postgresql://postgres:postgres@localhost:5432/passgen_test
          REDIS_URL: redis://localhost:6379

  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
        with:
          submodules: recursive
      - uses: actions/setup-node@v4
        with:
          node-version: '20'
          cache: 'npm'
      - run: npm ci
      - run: npm run build
```

---

## Step 5: Create Initial Release

### Via GitHub CLI

```bash
# Create and push a version tag
git tag -a v1.0.0-alpha.1 -m "Initial pre-production release"
git push origin v1.0.0-alpha.1

# Create GitHub release
gh release create v1.0.0-alpha.1 \
  --title "v1.0.0-alpha.1 - Initial Pre-Production Release" \
  --notes "**Status:** PRE-PRODUCTION

## Features
- Project scaffolding and documentation
- Compliance framework specifications (6 frameworks)
- Architecture design and PRD
- Development workflow setup with ai-dev-tasks

## Next Steps
- Phase 1 implementation (Weeks 1-4)
- Core password generation engine
- Single password UI
- HIBP integration"
```

### Via GitHub Web Interface

1. Go to https://github.com/FutureTranz-Inc/q-ai-msp-password-generator/releases
2. Click "Draft a new release"
3. Choose tag: `v1.0.0-alpha.1` (create new tag)
4. Release title: `v1.0.0-alpha.1 - Initial Pre-Production Release`
5. Add release notes (see above)
6. Mark as pre-release: ✅
7. Click "Publish release"

---

## Step 6: Configure Repository Secrets (for CI/CD)

1. Navigate to "Settings" → "Secrets and variables" → "Actions"
2. Add repository secrets:
   - `DATABASE_URL` - PostgreSQL connection string
   - `REDIS_URL` - Redis connection string
   - `JWT_SECRET` - JWT signing key
   - `HIBP_API_KEY` - Have I Been Pwned API key (optional)

---

## Step 7: Set Up Project Board (Optional)

1. Navigate to "Projects" → "New project"
2. Create project: "Q-AI-MSP Password Generator Development"
3. Template: "Team backlog"
4. Add views:
   - **Backlog:** All tasks not yet started
   - **Sprint:** Current iteration (2-week sprints)
   - **In Progress:** Active development
   - **Review:** Code review and QA
   - **Done:** Completed tasks

---

## Verification Checklist

After setup, verify:

```bash
# ✅ Remote is configured correctly
git remote -v
# Should show: origin  git@github.com:FutureTranz-Inc/q-ai-msp-password-generator.git

# ✅ Can push to repository
git push origin main

# ✅ Can pull from repository
git pull origin main

# ✅ Submodule is properly initialized
git submodule status
# Should show: [commit-hash] ai-dev-tasks (heads/main)

# ✅ GitHub Actions are running
gh run list --limit 5

# ✅ Branch protection is active
gh api repos/FutureTranz-Inc/q-ai-msp-password-generator/branches/main/protection
```

---

## Team Onboarding

Share this command sequence with new team members:

```bash
# 1. Clone repository
git clone --recurse-submodules git@github.com:FutureTranz-Inc/q-ai-msp-password-generator.git
cd q-ai-msp-password-generator

# 2. Install dependencies
npm install

# 3. Set up environment
cp .env.example .env
# Edit .env with your credentials

# 4. Install ai-dev-tasks hooks
bash ai-dev-tasks/scripts/install-hooks.sh

# 5. Verify setup
npm run lint
npm test

# 6. Start development
npm run dev
```

---

## Troubleshooting

### Issue: Permission denied (publickey)

**Solution:** Configure SSH key or use HTTPS with Personal Access Token

```bash
# Check SSH key
ssh -T git@github.com

# Or switch to HTTPS
git remote set-url origin https://github.com/FutureTranz-Inc/q-ai-msp-password-generator.git
```

### Issue: Submodule not initializing

**Solution:**

```bash
git submodule update --init --recursive
git submodule sync
```

### Issue: GitHub Actions failing

**Solution:** Check secrets are configured correctly

```bash
# List repository secrets
gh secret list

# Set missing secrets
gh secret set DATABASE_URL
gh secret set REDIS_URL
gh secret set JWT_SECRET
```

---

## Additional Resources

- **Repository:** https://github.com/FutureTranz-Inc/q-ai-msp-password-generator
- **GitHub CLI Docs:** https://cli.github.com/manual/
- **GitHub Actions Docs:** https://docs.github.com/en/actions
- **Git Submodules:** https://git-scm.com/book/en/v2/Git-Tools-Submodules

---

**Document last updated:** 2025-11-12
**Prepared by:** FutureTranz Development Team
**Document ID:** GITHUB-SETUP-q-ai-msp-password-generator
