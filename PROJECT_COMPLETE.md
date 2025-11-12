# Project Complete Reference

**Q-AI-MSP Enterprise Password Generator - Master Documentation**

This document serves as the master reference for the Q-AI-MSP Enterprise Password Generator project, providing deep technical dives, complete feature specifications, and PromptNinja methodology documentation.

---

## Table of Contents

1. [Project Overview](#project-overview)
2. [PromptNinja Methodology](#promptninja-methodology)
3. [Technical Architecture Deep Dive](#technical-architecture-deep-dive)
4. [Compliance Framework Specifications](#compliance-framework-specifications)
5. [Password Generation Algorithms](#password-generation-algorithms)
6. [Security Implementation](#security-implementation)
7. [HIBP Integration](#hibp-integration)
8. [Audit Logging System](#audit-logging-system)
9. [API Reference](#api-reference)
10. [Performance Optimization](#performance-optimization)
11. [Q-AI-MSP Integration](#q-ai-msp-integration)
12. [Deployment Architecture](#deployment-architecture)
13. [Development Roadmap](#development-roadmap)
14. [Complete Feature Matrix](#complete-feature-matrix)

---

## Project Overview

### Executive Summary

The Q-AI-MSP Enterprise Password Generator is a specialized webapp designed for Managed Service Providers (MSPs) to generate compliance-ready passwords for enterprise clients across multiple regulated industries. The application supports six major compliance frameworks (NIST SP 800-63B, PCI-DSS v4.0, HIPAA, SOC2 Type II, ISO 27001:2022, CIS Benchmarks) and provides tamper-proof audit logging for regulatory reporting.

### Business Problem

MSPs managing multiple clients across regulated industries (healthcare, finance, government) face significant challenges:

1. **Compliance Complexity**: Different clients require passwords meeting different regulatory standards
2. **Audit Requirements**: Regulators require proof of password policy compliance with immutable records
3. **Scale**: MSPs need to generate hundreds or thousands of passwords during client onboarding
4. **Security**: Weak passwords are the #1 cause of breaches (81% of hacking-related breaches)
5. **Efficiency**: Manual password generation is time-consuming and error-prone

### Solution

An automated password generation webapp that:
- Generates cryptographically secure passwords meeting specific compliance requirements
- Checks against 750M+ breached passwords via Have I Been Pwned API
- Provides tamper-proof audit logs with hash chain verification
- Supports bulk generation (up to 10,000 passwords in <5 seconds)
- Exports in multiple formats (CSV, JSON, Excel, PDF)
- Integrates with Q-AI-MSP platform (SSO, RBAC, white-label branding)

### Target Users

1. **MSP Technicians**: Generate passwords during client setup and onboarding
2. **Compliance Officers**: Generate audit reports for regulatory reviews
3. **Security Teams**: Enforce password policies across client environments
4. **IT Administrators**: Bulk password generation for user account creation

---

## PromptNinja Methodology

This project was created using the PromptNinja v2 framework, a structured 5-phase approach to enterprise software development.

### Phase 1: Vision & Requirements (PRD)

**Duration:** 8 hours
**Output:** Product Requirements Document (docs/prd/0001-prd-enterprise-password-generator.md)

**Process:**
1. **Discovery Interview**: Understand business problem, target users, success criteria
2. **Market Research**: Analyze competitors (1Password, LastPass, Bitwarden) and identify gaps
3. **Requirements Gathering**: Document functional and non-functional requirements
4. **Feature Prioritization**: Use MoSCoW method (Must-Have, Should-Have, Could-Have, Won't-Have)
5. **Technical Architecture**: Define technology stack, infrastructure, security requirements
6. **Success Metrics**: Define KPIs (generation speed, uptime, compliance coverage, user satisfaction)

**PRD Contents:**
- Executive summary (2 pages)
- Market analysis (5 pages)
- User personas and stories (12 pages)
- Core features with detailed specifications (45 pages)
- Technical architecture (15 pages)
- Development roadmap (8 pages)
- Budget and resource allocation (5 pages)
- Risk assessment and mitigation (4 pages)
- Appendices (compliance specifications, API schemas, wireframes)

**Total:** 2,127 lines, 96 pages

### Phase 2: Task Breakdown

**Duration:** 6 hours
**Output:** Task list (docs/tasks/tasks-0001-enterprise-password-generator.md)

**Process:**
1. **Epic Creation**: Break PRD features into 5 major epics (Foundation, Bulk & Export, Compliance & Audit, Integration & Launch, Enhancement & Scale)
2. **Task Decomposition**: Break epics into 156 actionable tasks
3. **Estimation**: Assign duration estimates (8h, 4h, 2h, 1h) to each task
4. **Prioritization**: Assign priority (P0-P3) based on dependencies and business value
5. **Resource Assignment**: Identify owner (Frontend Dev, Backend Dev, DevOps, QA)
6. **Dependency Mapping**: Identify task dependencies and create critical path
7. **Sprint Planning**: Organize tasks into 16 one-week sprints

**Task Breakdown:**
- Phase 1 (Foundation): 42 tasks, 160 hours, 4 weeks
- Phase 2 (Bulk & Export): 38 tasks, 160 hours, 4 weeks
- Phase 3 (Compliance & Audit): 34 tasks, 160 hours, 4 weeks
- Phase 4 (Integration & Launch): 28 tasks, 160 hours, 4 weeks
- Phase 5 (Enhancement & Scale): 14 tasks, ongoing

**Total:** 156 tasks, 640 hours base estimate, 16 weeks

### Phase 3: Project Structure

**Duration:** 2 hours
**Output:** Complete directory structure and monorepo configuration

**Process:**
1. **Monorepo Design**: Choose npm workspaces (vs Lerna, Turborepo, Nx)
2. **Directory Structure**: Create frontend, backend, shared, docs, infrastructure, tests directories
3. **Package Configuration**: Set up package.json with workspace scripts
4. **TypeScript Configuration**: Configure tsconfig.json for each workspace
5. **Linting & Formatting**: Set up ESLint, Prettier, Husky, lint-staged
6. **Git Configuration**: Initialize repository, configure .gitignore

**Structure:**
```
q-ai-msp-password-generator/
├── frontend/                   # React + TypeScript + Tailwind
├── backend/                    # Express + TypeScript
├── shared/                     # Shared types and utilities
├── docs/                       # Documentation
│   ├── prd/                    # Product requirements
│   ├── tasks/                  # Task lists
│   ├── USER_GUIDE.md
│   ├── FAQ.md
│   └── RUNBOOK.md
├── infrastructure/             # IaC (Terraform/CloudFormation)
│   ├── terraform/
│   └── docker/
├── tests/                      # E2E tests (Playwright)
├── .gitignore
├── package.json                # Monorepo workspace config
├── LICENSE
├── README.md
├── QUICKSTART.md
└── PROJECT_COMPLETE.md
```

### Phase 4: Documentation

**Duration:** 4 hours
**Output:** README.md, QUICKSTART.md, PROJECT_COMPLETE.md

**Process:**
1. **README Creation**: Comprehensive project overview with quick start, features, API docs
2. **QUICKSTART Guide**: 30-minute onboarding for new developers
3. **PROJECT_COMPLETE**: Master reference document with deep technical dives
4. **User Documentation**: User guide, FAQ, troubleshooting (deferred to Phase 1 development)
5. **Operations Documentation**: Runbook, incident response, monitoring (deferred to Phase 4)

### Phase 5: Git Initialization

**Duration:** 1 hour
**Output:** Git repository with initial commit

**Process:**
1. **Git Init**: Initialize repository with `git init`
2. **Branch Rename**: Rename master → main
3. **User Configuration**: Set git user.name and user.email
4. **Initial Commit**: Commit all planning and documentation files
5. **Remote Setup**: Configure GitHub remote (FutureTranz-Inc organization)
6. **Branch Protection**: Configure main branch protection rules on GitHub

---

## Technical Architecture Deep Dive

### Frontend Architecture

**Framework:** React 18.2+ with TypeScript 5.3+

**Why React:**
- Mature ecosystem with extensive component libraries
- Excellent TypeScript support
- Strong community and documentation
- Virtual DOM for performance
- Hooks API for state management

**UI Framework:** Tailwind CSS 3.4+ with Headless UI

**Why Tailwind:**
- Utility-first approach (fast development)
- Minimal CSS bundle size (tree-shaking)
- Responsive design utilities
- Dark mode support
- Customizable design system

**State Management:** Zustand

**Why Zustand:**
- Minimal boilerplate (vs Redux)
- No context providers needed
- TypeScript-first design
- DevTools support
- Middleware for persistence

**Form Handling:** React Hook Form + Zod

**Why React Hook Form:**
- Uncontrolled components (better performance)
- Minimal re-renders
- Built-in validation
- Easy integration with Zod schemas

**Build Tool:** Vite 5.0+

**Why Vite:**
- Lightning-fast HMR (Hot Module Replacement)
- Native ES modules (no bundling in dev)
- Optimized production builds with Rollup
- TypeScript support out of the box

**Testing:** Vitest + React Testing Library + Playwright

**Directory Structure:**
```
frontend/
├── src/
│   ├── components/             # Reusable UI components
│   │   ├── ui/                 # Base UI components (Button, Input, Select)
│   │   ├── forms/              # Form components (PasswordOptionsForm)
│   │   ├── results/            # Result display (PasswordResult, StrengthMeter)
│   │   └── layout/             # Layout components (Header, Sidebar, Footer)
│   ├── pages/                  # Page components
│   │   ├── GeneratePage.tsx    # Single password generation
│   │   ├── BulkPage.tsx        # Bulk generation
│   │   ├── AuditPage.tsx       # Audit logs
│   │   └── SettingsPage.tsx    # User settings
│   ├── lib/                    # Utilities and helpers
│   │   ├── passwordGenerator.ts   # Core password generation logic
│   │   ├── hibpClient.ts          # Have I Been Pwned API client
│   │   ├── complianceEngine.ts    # Compliance validation
│   │   ├── entropyCalculator.ts   # Password entropy calculation
│   │   └── exportUtils.ts         # CSV, JSON, Excel export
│   ├── hooks/                  # Custom React hooks
│   │   ├── usePasswordGenerator.ts
│   │   ├── useComplianceCheck.ts
│   │   ├── useBulkGeneration.ts
│   │   └── useAuditLogs.ts
│   ├── stores/                 # Zustand stores
│   │   ├── passwordStore.ts
│   │   ├── userStore.ts
│   │   └── settingsStore.ts
│   ├── types/                  # TypeScript types
│   │   ├── password.ts
│   │   ├── compliance.ts
│   │   └── audit.ts
│   ├── App.tsx                 # Main app component
│   └── main.tsx                # Entry point
├── public/                     # Static assets
│   ├── favicon.ico
│   └── logo.svg
├── index.html
├── vite.config.ts
├── tsconfig.json
└── package.json
```

### Backend Architecture

**Runtime:** Node.js 20+ LTS (with TypeScript 5.3+)

**Why Node.js:**
- JavaScript ecosystem (shared language with frontend)
- Excellent async I/O performance
- Large package ecosystem (npm)
- Easy horizontal scaling
- Strong community support

**Framework:** Express.js 4.18+

**Why Express:**
- Minimal and unopinionated
- Middleware ecosystem
- Mature and stable
- Easy to integrate with other libraries
- Strong TypeScript support

**Database:** PostgreSQL 16+

**Why PostgreSQL:**
- ACID compliance (critical for audit logs)
- JSON support (flexible schema)
- Excellent performance for read-heavy workloads
- Row-level security
- Streaming replication for HA

**Cache/Queue:** Redis 7+

**Why Redis:**
- In-memory performance (sub-millisecond latency)
- Rate limiting support
- Session storage
- Pub/sub for real-time updates
- Persistence options

**Authentication:** JWT (JSON Web Tokens)

**Why JWT:**
- Stateless (no server-side session storage)
- Works across distributed systems
- Self-contained (includes user claims)
- Works with Q-AI-MSP OAuth 2.0

**Testing:** Jest + Supertest + TestContainers

**Directory Structure:**
```
backend/
├── src/
│   ├── routes/                 # API routes
│   │   ├── auth.ts             # Authentication routes
│   │   ├── passwords.ts        # Password generation routes
│   │   ├── audit.ts            # Audit log routes
│   │   └── health.ts           # Health check route
│   ├── middleware/             # Express middleware
│   │   ├── auth.ts             # JWT authentication
│   │   ├── rateLimit.ts        # Rate limiting
│   │   ├── errorHandler.ts    # Global error handler
│   │   ├── validation.ts       # Request validation
│   │   └── logging.ts          # Request logging
│   ├── services/               # Business logic
│   │   ├── passwordService.ts  # Password generation
│   │   ├── complianceService.ts # Compliance checking
│   │   ├── hibpService.ts      # HIBP API client
│   │   ├── auditService.ts     # Audit logging
│   │   └── exportService.ts    # Export (CSV, JSON, Excel, PDF)
│   ├── database/               # Database layer
│   │   ├── connection.ts       # PostgreSQL connection
│   │   ├── migrations/         # SQL migrations
│   │   │   ├── 001_create_audit_logs_table.sql
│   │   │   ├── 002_create_hash_chain_index.sql
│   │   │   └── 003_create_users_table.sql
│   │   ├── models/             # Data models
│   │   │   ├── AuditLog.ts
│   │   │   └── User.ts
│   │   └── repositories/       # Data access layer
│   │       ├── auditLogRepository.ts
│   │       └── userRepository.ts
│   ├── utils/                  # Utilities
│   │   ├── crypto.ts           # Encryption/hashing
│   │   ├── logger.ts           # Winston logger
│   │   └── validator.ts        # Validation helpers
│   ├── config/                 # Configuration
│   │   ├── database.ts
│   │   ├── redis.ts
│   │   └── auth.ts
│   ├── types/                  # TypeScript types
│   │   ├── express.d.ts        # Express type extensions
│   │   └── api.ts              # API request/response types
│   └── server.ts               # Entry point
├── tests/                      # Tests
│   ├── unit/
│   ├── integration/
│   └── e2e/
├── .env.example
├── tsconfig.json
└── package.json
```

### Shared Package

**Purpose:** Share TypeScript types, utilities, and constants between frontend and backend

**Directory Structure:**
```
shared/
├── types/                      # Shared types
│   ├── ComplianceFramework.ts  # Compliance framework enum and types
│   ├── PasswordOptions.ts      # Password generation options
│   ├── AuditLog.ts             # Audit log types
│   └── APIResponse.ts          # API response types
├── data/                       # Shared data
│   ├── complianceProfiles.ts   # Compliance framework profiles
│   ├── dicewareWordlist.ts     # EFF Long Wordlist (7,776 words)
│   └── characterSets.ts        # Character set definitions
├── utils/                      # Shared utilities
│   ├── entropyCalculator.ts    # Entropy calculation
│   └── passwordValidator.ts    # Password validation
└── package.json
```

**Why Shared Package:**
- Single source of truth for types
- Prevents type drift between frontend and backend
- Easier refactoring (change once, applies everywhere)
- Smaller bundle size (no type duplication)

---

## Compliance Framework Specifications

### 1. NIST SP 800-63B (Digital Identity Guidelines)

**Source:** National Institute of Standards and Technology
**Document:** Special Publication 800-63B, Revision 3
**URL:** https://pages.nist.gov/800-63-3/sp800-63b.html

**Requirements:**

**Minimum Length:**
- **Requirement:** At least 8 characters for user-chosen passwords
- **Recommendation:** 15+ characters for strength
- **Implementation:** Default to 15 characters, allow 8-128

**Composition Rules:**
- **Requirement:** NO mandatory character type requirements
- **Rationale:** Composition rules reduce password space and user memorability
- **Implementation:** Allow users to enable character types, but don't enforce

**Breach Check:**
- **Requirement:** MUST check against known breached password databases
- **Implementation:** Have I Been Pwned API with k-anonymity
- **Action:** Reject password if found in breach database

**Password Rotation:**
- **Requirement:** NO mandatory periodic rotation
- **Rationale:** Forced rotation leads to predictable patterns (password1 → password2)
- **Action:** Only require change on evidence of compromise

**Username in Password:**
- **Requirement:** NO username or parts of username in password
- **Implementation:** Check if password contains username (case-insensitive)

**Context-Specific Words:**
- **Requirement:** NO service name, variations, or common words in password
- **Implementation:** Check against list of context-specific words

**Code Example:**
```typescript
interface NISTRequirements {
  minLength: 8;
  recommendedLength: 15;
  maxLength: 128;
  compositionRules: false;
  breachCheck: true;
  mandatoryRotation: false;
  rotationOnCompromise: true;
  usernameInPassword: false;
  contextSpecificWords: false;
}

function validateNISTPassword(password: string, username: string): ValidationResult {
  const errors: string[] = [];

  // Length check
  if (password.length < 8) {
    errors.push('Password must be at least 8 characters');
  }

  // Username check
  if (password.toLowerCase().includes(username.toLowerCase())) {
    errors.push('Password cannot contain username');
  }

  // Breach check (async, performed separately)
  // See HIBP Integration section

  return {
    valid: errors.length === 0,
    errors,
    warnings: password.length < 15 ? ['Consider using 15+ characters for better security'] : []
  };
}
```

**Expiration Policy:**
- **Display:** "No expiration (change on compromise)"
- **Implementation:** No automatic expiration date

---

### 2. PCI-DSS v4.0 (Payment Card Industry Data Security Standard)

**Source:** PCI Security Standards Council
**Document:** PCI DSS Requirements and Testing Procedures, Version 4.0
**URL:** https://www.pcisecuritystandards.org/

**Requirements:**

**Minimum Length:**
- **Requirement:** At least 12 characters (increased from 7 in v3.2.1)
- **Section:** Requirement 8.3.6
- **Implementation:** Enforce 12 character minimum, allow up to 128

**Composition:**
- **Requirement:** Passwords must contain characters from at least three of the following categories:
  - Uppercase letters (A-Z)
  - Lowercase letters (a-z)
  - Numbers (0-9)
  - Special characters (!@#$%^&*)
- **Section:** Requirement 8.3.6
- **Implementation:** Enforce all four categories for stronger security

**Password Rotation:**
- **Requirement:** Change every 90 days
- **Section:** Requirement 8.3.9
- **Implementation:** Set expiration date 90 days from generation

**Password History:**
- **Requirement:** Cannot reuse any of the last four passwords
- **Section:** Requirement 8.3.8
- **Implementation:** Track password hashes (not stored in this app, enforced in target system)

**Username in Password:**
- **Requirement:** Password cannot be the same as the user ID
- **Section:** Requirement 8.3.6
- **Implementation:** Check if password equals username

**First-Time Password Change:**
- **Requirement:** Must change temporary passwords after first use
- **Section:** Requirement 8.3.6
- **Implementation:** Mark generated passwords as "temporary" in export

**Code Example:**
```typescript
interface PCIDSSRequirements {
  minLength: 12;
  maxLength: 128;
  uppercase: true;
  lowercase: true;
  numbers: true;
  symbols: true;
  minCategories: 4; // Enforce all four
  rotationDays: 90;
  passwordHistory: 4;
  usernameInPassword: false;
  temporaryPasswordChange: true;
}

function validatePCIDSSPassword(password: string, username: string): ValidationResult {
  const errors: string[] = [];

  // Length check
  if (password.length < 12) {
    errors.push('Password must be at least 12 characters (PCI-DSS v4.0)');
  }

  // Composition check
  const hasUppercase = /[A-Z]/.test(password);
  const hasLowercase = /[a-z]/.test(password);
  const hasNumber = /[0-9]/.test(password);
  const hasSymbol = /[!@#$%^&*()_+\-=\[\]{};':"\\|,.<>/?]/.test(password);

  const categoriesMet = [hasUppercase, hasLowercase, hasNumber, hasSymbol].filter(Boolean).length;

  if (categoriesMet < 4) {
    errors.push('Password must contain uppercase, lowercase, numbers, and symbols');
  }

  // Username check
  if (password === username) {
    errors.push('Password cannot be the same as username');
  }

  return {
    valid: errors.length === 0,
    errors,
    expirationDate: new Date(Date.now() + 90 * 24 * 60 * 60 * 1000), // 90 days
    metadata: {
      framework: 'PCI-DSS v4.0',
      section: '8.3.6',
      rotation: '90 days',
      temporary: true // Requires change after first use
    }
  };
}
```

---

### 3. HIPAA Security Rule

**Source:** U.S. Department of Health and Human Services (HHS)
**Document:** 45 CFR Part 164, Subpart C (Security Standards)
**URL:** https://www.hhs.gov/hipaa/for-professionals/security/

**Requirements:**

**Minimum Length:**
- **Requirement:** Not explicitly specified in HIPAA
- **Best Practice:** 12+ characters (recommended by HHS)
- **Implementation:** 12 character minimum

**Composition:**
- **Requirement:** Not explicitly specified
- **Best Practice:** At least 3 of 4 character types
- **Section:** § 164.308(a)(5)(ii)(D) (Password Management)
- **Implementation:** Enforce uppercase, lowercase, numbers, at least one symbol

**Password Rotation:**
- **Requirement:** "Procedures for creating, changing, and safeguarding passwords"
- **Best Practice:** Change every 60-90 days
- **Section:** § 164.308(a)(5)(ii)(D)
- **Implementation:** 90-day rotation (configurable 60-90 days)

**Unique Passwords:**
- **Requirement:** Must be unique (not reused)
- **Best Practice:** 24-month uniqueness (at least 12 passwords)
- **Section:** § 164.308(a)(5)(ii)(D)
- **Implementation:** Track password hashes for 24 months

**Automatic Logoff:**
- **Requirement:** Automatic logoff after period of inactivity
- **Section:** § 164.312(a)(2)(iii)
- **Note:** Not password-related, but important for HIPAA compliance

**Code Example:**
```typescript
interface HIPAARequirements {
  minLength: 12;
  uppercase: true;
  lowercase: true;
  numbers: true;
  symbols: true;
  minCategories: 3; // At least 3 of 4
  rotationDays: 90; // Configurable 60-90
  uniquenessMonths: 24; // 24-month uniqueness
  automaticLogoffMinutes: 15; // Not password-related, system setting
}

function validateHIPAAPassword(password: string): ValidationResult {
  const errors: string[] = [];

  // Length check
  if (password.length < 12) {
    errors.push('Password must be at least 12 characters (HIPAA best practice)');
  }

  // Composition check
  const hasUppercase = /[A-Z]/.test(password);
  const hasLowercase = /[a-z]/.test(password);
  const hasNumber = /[0-9]/.test(password);
  const hasSymbol = /[!@#$%^&*()_+\-=\[\]{};':"\\|,.<>/?]/.test(password);

  const categoriesMet = [hasUppercase, hasLowercase, hasNumber, hasSymbol].filter(Boolean).length;

  if (categoriesMet < 3) {
    errors.push('Password must contain at least 3 of: uppercase, lowercase, numbers, symbols');
  }

  return {
    valid: errors.length === 0,
    errors,
    expirationDate: new Date(Date.now() + 90 * 24 * 60 * 60 * 1000), // 90 days
    metadata: {
      framework: 'HIPAA Security Rule',
      section: '§ 164.308(a)(5)(ii)(D)',
      rotation: '90 days',
      uniqueness: '24 months'
    }
  };
}
```

---

### 4. SOC2 Type II

**Source:** American Institute of CPAs (AICPA)
**Document:** SOC 2 Trust Services Criteria (TSC)
**URL:** https://www.aicpa.org/interestareas/frc/assuranceadvisoryservices/socforserviceorganizations

**Requirements:**

**Minimum Length:**
- **Requirement:** Not explicitly specified in SOC2
- **Best Practice:** 12+ characters
- **Trust Service:** CC6.1 (Logical and Physical Access Controls)
- **Implementation:** 12 character minimum

**Composition:**
- **Requirement:** Complex passwords required
- **Best Practice:** All character types (uppercase, lowercase, numbers, symbols)
- **Trust Service:** CC6.1
- **Implementation:** Enforce all four types

**Sequential Characters:**
- **Requirement:** No sequential or repetitive characters
- **Examples:** "abc", "123", "aaa"
- **Implementation:** Check for sequences (ascending, descending, repeating)

**Password Rotation:**
- **Requirement:** Not explicitly specified
- **Best Practice:** 90 days (aligned with audit cycle)
- **Trust Service:** CC6.1
- **Implementation:** 90-day rotation

**Password History:**
- **Requirement:** Cannot reuse recent passwords
- **Best Practice:** 10 password history
- **Trust Service:** CC6.1
- **Implementation:** Track last 10 password hashes

**Account Lockout:**
- **Requirement:** Lock account after failed login attempts
- **Best Practice:** 5 failed attempts, 30-minute lockout
- **Trust Service:** CC6.1
- **Note:** Not password-related, system setting

**Code Example:**
```typescript
interface SOC2Requirements {
  minLength: 12;
  uppercase: true;
  lowercase: true;
  numbers: true;
  symbols: true;
  noSequential: true;
  noRepeating: true;
  rotationDays: 90;
  passwordHistory: 10;
  accountLockoutAttempts: 5; // System setting
  lockoutDurationMinutes: 30; // System setting
}

function validateSOC2Password(password: string): ValidationResult {
  const errors: string[] = [];

  // Length check
  if (password.length < 12) {
    errors.push('Password must be at least 12 characters');
  }

  // Composition check
  const hasUppercase = /[A-Z]/.test(password);
  const hasLowercase = /[a-z]/.test(password);
  const hasNumber = /[0-9]/.test(password);
  const hasSymbol = /[!@#$%^&*()_+\-=\[\]{};':"\\|,.<>/?]/.test(password);

  if (!hasUppercase || !hasLowercase || !hasNumber || !hasSymbol) {
    errors.push('Password must contain uppercase, lowercase, numbers, and symbols');
  }

  // Sequential character check
  const hasSequential = /abc|bcd|cde|def|efg|fgh|ghi|hij|ijk|jkl|klm|lmn|mno|nop|opq|pqr|qrs|rst|stu|tuv|uvw|vwx|wxy|xyz|012|123|234|345|456|567|678|789/i.test(password);
  if (hasSequential) {
    errors.push('Password cannot contain sequential characters (abc, 123, etc.)');
  }

  // Repeating character check
  const hasRepeating = /(.)\1{2,}/.test(password);
  if (hasRepeating) {
    errors.push('Password cannot contain repeating characters (aaa, 111, etc.)');
  }

  return {
    valid: errors.length === 0,
    errors,
    expirationDate: new Date(Date.now() + 90 * 24 * 60 * 60 * 1000), // 90 days
    metadata: {
      framework: 'SOC2 Type II',
      trustService: 'CC6.1',
      rotation: '90 days',
      history: '10 passwords'
    }
  };
}
```

---

### 5. ISO 27001:2022

**Source:** International Organization for Standardization (ISO)
**Document:** ISO/IEC 27001:2022 Information Security Management
**URL:** https://www.iso.org/standard/27001

**Requirements:**

**Minimum Length:**
- **Requirement:** Not explicitly specified
- **Best Practice:** 12+ characters
- **Control:** A.9.4.3 (Password Management System)
- **Implementation:** 12 character minimum

**Composition:**
- **Requirement:** Mix of alphabetic, numeric, and special characters
- **Control:** A.9.4.3
- **Implementation:** Uppercase, lowercase, numbers, symbols

**Dictionary Words:**
- **Requirement:** Passwords shall not be based on anything easily guessable (names, dictionary words, dates)
- **Control:** A.9.4.3
- **Implementation:** Check against common password lists (Top 10,000 passwords)

**Password Rotation:**
- **Requirement:** Change on suspected compromise
- **Best Practice:** Optional periodic change (90-180 days)
- **Control:** A.9.4.3
- **Implementation:** No mandatory rotation, change on compromise only

**Password Confidentiality:**
- **Requirement:** Passwords must not be stored in unencrypted form
- **Control:** A.9.4.3
- **Note:** This app does NOT store passwords, only generates them

**Code Example:**
```typescript
interface ISO27001Requirements {
  minLength: 12;
  uppercase: true;
  lowercase: true;
  numbers: true;
  symbols: true;
  noDictionaryWords: true;
  rotationOnCompromise: true;
  optionalPeriodicRotation: false; // Organization policy
  encryptedStorage: true; // Not applicable to this app
}

// Top 10,000 most common passwords (subset shown)
const COMMON_PASSWORDS = [
  'password', '123456', '123456789', 'qwerty', 'abc123',
  'password1', '12345678', '111111', '1234567', 'sunshine',
  // ... (full list in shared/data/commonPasswords.ts)
];

function validateISO27001Password(password: string): ValidationResult {
  const errors: string[] = [];

  // Length check
  if (password.length < 12) {
    errors.push('Password must be at least 12 characters');
  }

  // Composition check
  const hasUppercase = /[A-Z]/.test(password);
  const hasLowercase = /[a-z]/.test(password);
  const hasNumber = /[0-9]/.test(password);
  const hasSymbol = /[!@#$%^&*()_+\-=\[\]{};':"\\|,.<>/?]/.test(password);

  if (!hasUppercase || !hasLowercase || !hasNumber || !hasSymbol) {
    errors.push('Password must contain alphabetic (upper/lower), numeric, and special characters');
  }

  // Dictionary word check (case-insensitive)
  const passwordLower = password.toLowerCase();
  const foundCommonPassword = COMMON_PASSWORDS.some(common => passwordLower.includes(common));
  if (foundCommonPassword) {
    errors.push('Password cannot contain common dictionary words');
  }

  return {
    valid: errors.length === 0,
    errors,
    expirationDate: null, // No mandatory rotation
    metadata: {
      framework: 'ISO 27001:2022',
      control: 'A.9.4.3',
      rotation: 'On compromise only',
      note: 'Optional periodic change per organization policy'
    }
  };
}
```

---

### 6. CIS Benchmarks (Center for Internet Security)

**Source:** Center for Internet Security
**Document:** CIS Controls v8, Control 6 (Access Control Management)
**URL:** https://www.cisecurity.org/controls/

**Requirements:**

**Minimum Length:**
- **Requirement:** 14+ characters (CIS Critical Security Control 6.3)
- **Rationale:** Strongest requirement among major frameworks
- **Implementation:** 14 character minimum

**Composition:**
- **Requirement:** All character types (uppercase, lowercase, numbers, symbols)
- **Control:** CIS Control 6.3
- **Implementation:** Enforce all four types

**Password Rotation:**
- **Requirement:** Change every 365 days for standard accounts
- **Requirement:** Change every 60 days for privileged accounts (admin, root)
- **Control:** CIS Control 6.5
- **Implementation:** 365-day rotation (default), 60-day for privileged

**Password History:**
- **Requirement:** 24 password history (cannot reuse last 24 passwords)
- **Control:** CIS Control 6.5
- **Implementation:** Track last 24 password hashes

**Multi-Factor Authentication:**
- **Requirement:** MFA required for all external network access
- **Control:** CIS Control 6.4
- **Note:** Not password-related, but important for CIS compliance

**Account Lockout:**
- **Requirement:** Lock account after 5 failed login attempts
- **Control:** CIS Control 6.2
- **Note:** System setting, not password generation

**Code Example:**
```typescript
interface CISRequirements {
  minLength: 14; // Strongest requirement
  uppercase: true;
  lowercase: true;
  numbers: true;
  symbols: true;
  rotationDaysStandard: 365;
  rotationDaysPrivileged: 60;
  passwordHistory: 24; // Longest history requirement
  mfaRequired: true; // System setting
  accountLockoutAttempts: 5; // System setting
}

function validateCISPassword(password: string, isPrivileged: boolean = false): ValidationResult {
  const errors: string[] = [];

  // Length check (strictest requirement)
  if (password.length < 14) {
    errors.push('Password must be at least 14 characters (CIS Benchmark)');
  }

  // Composition check (all types required)
  const hasUppercase = /[A-Z]/.test(password);
  const hasLowercase = /[a-z]/.test(password);
  const hasNumber = /[0-9]/.test(password);
  const hasSymbol = /[!@#$%^&*()_+\-=\[\]{};':"\\|,.<>/?]/.test(password);

  if (!hasUppercase || !hasLowercase || !hasNumber || !hasSymbol) {
    errors.push('Password must contain uppercase, lowercase, numbers, and symbols');
  }

  // Calculate expiration based on account type
  const rotationDays = isPrivileged ? 60 : 365;
  const expirationDate = new Date(Date.now() + rotationDays * 24 * 60 * 60 * 1000);

  return {
    valid: errors.length === 0,
    errors,
    expirationDate,
    metadata: {
      framework: 'CIS Benchmarks v8',
      control: 'CIS Control 6.3',
      rotation: isPrivileged ? '60 days (privileged)' : '365 days (standard)',
      history: '24 passwords',
      accountType: isPrivileged ? 'privileged' : 'standard'
    }
  };
}
```

---

## Password Generation Algorithms

### Method 1: Cryptographically Secure Random

**Algorithm:** Web Crypto API (`crypto.getRandomValues()`)

**Why Web Crypto API:**
- **CSPRNG**: Cryptographically Secure Pseudorandom Number Generator
- **Native Browser API**: No external dependencies
- **256-bit Entropy**: Backed by OS-level entropy source
- **Non-Blocking**: Async operation, doesn't block UI
- **Standardized**: W3C standard, supported by all modern browsers

**Entropy Source:**
- **Desktop**: `/dev/urandom` (Linux/macOS) or `CryptGenRandom` (Windows)
- **Mobile**: Platform-specific secure random (e.g., SecureRandom on Android)
- **Fallback**: Node.js crypto module for backend generation

**Implementation:**

```typescript
// frontend/src/lib/passwordGenerator.ts

interface PasswordOptions {
  length: number; // 8-128
  uppercase: boolean;
  lowercase: boolean;
  numbers: boolean;
  symbols: boolean;
  excludeAmbiguous: boolean; // Exclude 0, O, l, I, 1
  excludeSimilar: boolean; // Exclude i, l, 1, L, o, 0, O
}

// Character sets
const UPPERCASE = 'ABCDEFGHIJKLMNOPQRSTUVWXYZ';
const LOWERCASE = 'abcdefghijklmnopqrstuvwxyz';
const NUMBERS = '0123456789';
const SYMBOLS = '!@#$%^&*()_+-=[]{}|;:,.<>?';

const AMBIGUOUS = '0Ol1I'; // Commonly confused characters
const SIMILAR = 'il1Lo0O'; // Visually similar characters

function generateRandomPassword(options: PasswordOptions): string {
  // Build character pool
  let charset = '';
  if (options.uppercase) charset += UPPERCASE;
  if (options.lowercase) charset += LOWERCASE;
  if (options.numbers) charset += NUMBERS;
  if (options.symbols) charset += SYMBOLS;

  // Remove ambiguous/similar characters if requested
  if (options.excludeAmbiguous || options.excludeSimilar) {
    const excludeSet = new Set(
      (options.excludeAmbiguous ? AMBIGUOUS : '') +
      (options.excludeSimilar ? SIMILAR : '')
    );
    charset = charset.split('').filter(char => !excludeSet.has(char)).join('');
  }

  if (charset.length === 0) {
    throw new Error('At least one character type must be selected');
  }

  // Generate password with Web Crypto API
  const password: string[] = [];
  const randomValues = new Uint32Array(options.length);
  crypto.getRandomValues(randomValues);

  for (let i = 0; i < options.length; i++) {
    const randomIndex = randomValues[i] % charset.length;
    password.push(charset[randomIndex]);
  }

  // Ensure at least one character from each selected type
  // (Fisher-Yates shuffle to avoid predictable positions)
  const requiredChars: string[] = [];
  if (options.uppercase) requiredChars.push(getRandomChar(UPPERCASE));
  if (options.lowercase) requiredChars.push(getRandomChar(LOWERCASE));
  if (options.numbers) requiredChars.push(getRandomChar(NUMBERS));
  if (options.symbols) requiredChars.push(getRandomChar(SYMBOLS));

  // Replace first N characters with required characters
  for (let i = 0; i < requiredChars.length; i++) {
    password[i] = requiredChars[i];
  }

  // Fisher-Yates shuffle
  for (let i = password.length - 1; i > 0; i--) {
    const randomValues = new Uint32Array(1);
    crypto.getRandomValues(randomValues);
    const j = randomValues[0] % (i + 1);
    [password[i], password[j]] = [password[j], password[i]];
  }

  return password.join('');
}

function getRandomChar(charset: string): string {
  const randomValues = new Uint32Array(1);
  crypto.getRandomValues(randomValues);
  const randomIndex = randomValues[0] % charset.length;
  return charset[randomIndex];
}
```

**Entropy Calculation:**

```typescript
function calculateEntropy(password: string, charset: string): number {
  // Entropy (bits) = log2(charset_size^password_length)
  // = password_length * log2(charset_size)

  const charsetSize = charset.length;
  const passwordLength = password.length;

  return passwordLength * Math.log2(charsetSize);
}

// Example: 16-character password with all character types
// Charset: 26 uppercase + 26 lowercase + 10 numbers + 32 symbols = 94 characters
// Entropy = 16 * log2(94) = 16 * 6.55 = 104.8 bits

// Strength guidelines:
// < 28 bits: Very weak (cracked instantly)
// 28-35 bits: Weak (cracked in seconds)
// 36-59 bits: Reasonable (cracked in hours/days)
// 60-127 bits: Strong (cracked in years/centuries)
// 128+ bits: Very strong (effectively unbreakable)
```

**Performance:**
- **Single password**: <10ms
- **100 passwords**: <100ms
- **1,000 passwords**: <1 second
- **10,000 passwords**: <5 seconds (using Web Worker)

---

### Method 2: Passphrase (Diceware)

**Algorithm:** EFF Long Wordlist with cryptographic randomness

**Why Diceware:**
- **Memorability**: Easier to remember than random characters
- **High Entropy**: 12.9 bits per word (vs 6.55 bits per random character)
- **XKCD Famous**: Popularized by XKCD comic "correct horse battery staple"
- **NIST Recommended**: Mentioned in NIST SP 800-63B as alternative to complex passwords

**Wordlist:** EFF Long Wordlist (7,776 words)
**Source:** https://www.eff.org/files/2016/07/18/eff_large_wordlist.txt
**Entropy per Word:** log2(7,776) = 12.9 bits

**Why EFF Long Wordlist:**
- **No Profanity**: Family-friendly words only
- **No Homophones**: Avoid confusion (e.g., "there" vs "their")
- **Unique Prefixes**: First 4 characters are unique (easier to autocomplete)
- **Common Words**: Recognizable English words

**Implementation:**

```typescript
// shared/data/dicewareWordlist.ts
export const DICEWARE_WORDLIST: string[] = [
  'abacus', 'abdomen', 'abdominal', 'abide', 'abiding', 'ability',
  // ... (7,776 words total)
  'zoom', 'zoot', 'zoologist', 'zoology', 'zounds', 'zucchini'
];

// frontend/src/lib/passwordGenerator.ts
interface PassphraseOptions {
  words: number; // 4-10 words
  separator: '-' | '_' | ' ' | 'camelCase' | 'PascalCase' | 'none';
  capitalize: boolean; // Capitalize first letter of each word
  includeNumber: boolean; // Append random 2-digit number
}

function generatePassphrase(options: PassphraseOptions): string {
  const { words, separator, capitalize, includeNumber } = options;

  // Generate random words using Web Crypto API
  const selectedWords: string[] = [];
  const randomValues = new Uint32Array(words);
  crypto.getRandomValues(randomValues);

  for (let i = 0; i < words; i++) {
    const randomIndex = randomValues[i] % DICEWARE_WORDLIST.length;
    let word = DICEWARE_WORDLIST[randomIndex];

    // Capitalize if requested
    if (capitalize) {
      word = word.charAt(0).toUpperCase() + word.slice(1);
    }

    // Handle camelCase/PascalCase
    if (separator === 'camelCase' && i > 0) {
      word = word.charAt(0).toUpperCase() + word.slice(1);
    } else if (separator === 'PascalCase') {
      word = word.charAt(0).toUpperCase() + word.slice(1);
    }

    selectedWords.push(word);
  }

  // Join with separator
  let passphrase = separator === 'camelCase' || separator === 'PascalCase' || separator === 'none'
    ? selectedWords.join('')
    : selectedWords.join(separator);

  // Append random number if requested
  if (includeNumber) {
    const randomNum = new Uint32Array(1);
    crypto.getRandomValues(randomNum);
    const twoDigitNumber = (randomNum[0] % 90) + 10; // 10-99
    passphrase += separator === 'none' ? twoDigitNumber : `${separator}${twoDigitNumber}`;
  }

  return passphrase;
}

// Entropy calculation for passphrases
function calculatePassphraseEntropy(wordCount: number, includeNumber: boolean): number {
  // Entropy per word: log2(7,776) = 12.9 bits
  const wordsEntropy = wordCount * 12.9;

  // Entropy for 2-digit number: log2(90) = 6.5 bits (10-99)
  const numberEntropy = includeNumber ? 6.5 : 0;

  return wordsEntropy + numberEntropy;
}

// Examples:
// 4 words: 51.6 bits (minimum for reasonable security)
// 5 words: 64.5 bits (good security)
// 6 words: 77.4 bits (strong security)
// 7 words: 90.3 bits (very strong security)

// 5 words + number: 64.5 + 6.5 = 71 bits (XKCD example: "correct-horse-battery-staple-42")
```

**Performance:**
- **Single passphrase**: <5ms
- **100 passphrases**: <50ms
- **1,000 passphrases**: <500ms
- **10,000 passphrases**: <3 seconds

---

### Method 3: Pronounceable Passwords

**Algorithm:** Consonant-Vowel-Consonant (CVC) pattern with cryptographic randomness

**Why Pronounceable:**
- **Memorability**: Easier to remember than pure random
- **Typability**: Easier to type (no complex symbol sequences)
- **Phone-Friendly**: Easier to communicate over phone
- **Balance**: Trade-off between security and usability

**Pattern:** (CVC-CVC-NN)*
**Example:** `Trobami-Vixel-32`

**Character Sets:**
- **Consonants**: `bcdfghjklmnpqrstvwxyz` (21 chars)
- **Vowels**: `aeiou` (5 chars)
- **Numbers**: `0123456789` (10 chars)

**Implementation:**

```typescript
// frontend/src/lib/passwordGenerator.ts

const CONSONANTS = 'bcdfghjklmnpqrstvwxyz';
const VOWELS = 'aeiou';
const NUMBERS = '0123456789';

interface PronounceableOptions {
  syllables: number; // 3-6 syllables
  separator: '-' | '_' | ' ' | 'none';
  capitalize: boolean; // Capitalize first letter
  includeNumber: boolean; // Append 2-digit number
  includeSymbol: boolean; // Append symbol (for compliance)
}

function generatePronounceablePassword(options: PronounceableOptions): string {
  const { syllables, separator, capitalize, includeNumber, includeSymbol } = options;

  const password: string[] = [];

  for (let i = 0; i < syllables; i++) {
    // Generate CVC syllable
    const consonant1 = getRandomChar(CONSONANTS);
    const vowel = getRandomChar(VOWELS);
    const consonant2 = getRandomChar(CONSONANTS);

    let syllable = consonant1 + vowel + consonant2;

    // Capitalize first syllable if requested
    if (capitalize && i === 0) {
      syllable = syllable.charAt(0).toUpperCase() + syllable.slice(1);
    }

    password.push(syllable);
  }

  // Join with separator
  let result = separator === 'none' ? password.join('') : password.join(separator);

  // Append number if requested
  if (includeNumber) {
    const randomNum = new Uint32Array(1);
    crypto.getRandomValues(randomNum);
    const twoDigitNumber = (randomNum[0] % 90) + 10; // 10-99
    result += separator === 'none' ? twoDigitNumber : `${separator}${twoDigitNumber}`;
  }

  // Append symbol if requested (for compliance)
  if (includeSymbol) {
    const symbol = getRandomChar(SYMBOLS);
    result += symbol;
  }

  return result;
}

// Entropy calculation for pronounceable passwords
function calculatePronounceableEntropy(
  syllables: number,
  includeNumber: boolean,
  includeSymbol: boolean
): number {
  // Entropy per syllable (CVC pattern):
  // C: log2(21) = 4.39 bits
  // V: log2(5) = 2.32 bits
  // C: log2(21) = 4.39 bits
  // Total: 4.39 + 2.32 + 4.39 = 11.1 bits per syllable

  const syllableEntropy = syllables * 11.1;

  // Number entropy: log2(90) = 6.5 bits (10-99)
  const numberEntropy = includeNumber ? 6.5 : 0;

  // Symbol entropy: log2(32) = 5 bits (assuming 32 symbols)
  const symbolEntropy = includeSymbol ? 5 : 0;

  return syllableEntropy + numberEntropy + symbolEntropy;
}

// Examples:
// 3 syllables: 33.3 bits (weak)
// 4 syllables: 44.4 bits (reasonable)
// 5 syllables + number: 55.5 + 6.5 = 62 bits (good)
// 6 syllables + number + symbol: 66.6 + 6.5 + 5 = 78.1 bits (strong)

// Example output:
// Trobami-Vixel-Nokaf-32! (5 syllables + number + symbol, 62 + 6.5 + 5 = 73.5 bits)
```

**Performance:**
- **Single password**: <5ms
- **100 passwords**: <50ms
- **1,000 passwords**: <500ms
- **10,000 passwords**: <3 seconds

---

## Security Implementation

### Zero-Knowledge Architecture

**Principle:** Passwords are NEVER stored on the server. Generated entirely client-side.

**Why:**
- **No Server Breach Risk**: If server is compromised, no passwords are exposed
- **Privacy**: Passwords never leave user's browser (except for HIBP check via k-anonymity)
- **Compliance**: Meets "data minimization" requirements (GDPR, HIPAA, SOC2)
- **Trust**: Users can verify client-side generation by inspecting browser DevTools

**Implementation:**

```typescript
// frontend/src/lib/passwordGenerator.ts

// ALL password generation happens in browser
// NEVER send password to server

export function generatePassword(options: PasswordOptions): GeneratedPassword {
  // Generate password client-side
  const password = generateRandomPassword(options);

  // Calculate entropy client-side
  const entropy = calculateEntropy(password, buildCharset(options));

  // Check breach status client-side (k-anonymity)
  const breachCheck = await checkPasswordBreach(password);

  // Return password (stays in browser)
  return {
    password,
    entropy,
    breachCheck,
    compliance: validateCompliance(password, options)
  };
}

// backend/src/services/auditService.ts

// Server ONLY stores password hash (first 8 chars of SHA-256) for audit reference
export async function logPasswordGeneration(userId: string, metadata: AuditMetadata): Promise<void> {
  // DO NOT receive actual password from client
  // Only log metadata: timestamp, user, compliance framework, count

  const auditLog: AuditLog = {
    timestamp: new Date().toISOString(),
    userId,
    action: metadata.action, // 'single_generation' or 'bulk_generation'
    passwordCount: metadata.count,
    complianceFramework: metadata.compliance,
    passwordHashPrefix: metadata.hashPrefix, // First 8 chars of SHA-256 (for reference only)
    ipAddress: anonymizeIP(metadata.ipAddress), // Last octet masked
    userAgent: metadata.userAgent,
    previousHash: await getLastAuditLogHash(userId) // For hash chain
  };

  // Hash current log entry
  auditLog.hash = await hashAuditLog(auditLog);

  // Store in PostgreSQL
  await db.auditLogs.insert(auditLog);
}
```

**Security Guarantees:**
- ✅ Passwords generated client-side (Web Crypto API)
- ✅ Passwords NEVER transmitted to server
- ✅ Passwords NEVER stored in database
- ✅ Only audit metadata stored (timestamp, user, compliance, hash prefix)
- ✅ Audit logs encrypted at rest (AES-256-GCM)
- ✅ Hash chain prevents tampering

---

### OWASP Top 10 Protection

**1. Injection (SQL, NoSQL, Command)**

**Risk:** Malicious input executed as code

**Mitigation:**
- **Parameterized Queries**: Use prepared statements for all database queries
- **Input Validation**: Validate all user input against strict schemas (Zod)
- **Output Encoding**: Encode all output to prevent XSS

**Code Example:**
```typescript
// ❌ VULNERABLE (SQL Injection)
const query = `SELECT * FROM users WHERE email = '${userEmail}'`;

// ✅ SECURE (Parameterized Query)
const query = 'SELECT * FROM users WHERE email = $1';
const result = await db.query(query, [userEmail]);
```

**2. Broken Authentication**

**Risk:** Attackers gain access to user accounts

**Mitigation:**
- **JWT Authentication**: Stateless tokens with expiration
- **Secure Password Hashing**: bcrypt with 12 rounds (not applicable to this app, no password storage)
- **Rate Limiting**: Prevent brute-force attacks (100 req/min single, 10 req/hour bulk)
- **Account Lockout**: Lock after 5 failed login attempts (30-minute lockout)

**Code Example:**
```typescript
// backend/src/middleware/rateLimit.ts
import rateLimit from 'express-rate-limit';
import RedisStore from 'rate-limit-redis';

const limiter = rateLimit({
  store: new RedisStore({
    client: redisClient,
    prefix: 'rate_limit:'
  }),
  windowMs: 60 * 1000, // 1 minute
  max: 100, // 100 requests per minute
  message: 'Too many requests, please try again later'
});

app.use('/api/', limiter);
```

**3. Sensitive Data Exposure**

**Risk:** Sensitive data leaked via logs, errors, or insecure transmission

**Mitigation:**
- **HTTPS Only**: Enforce HTTPS with HSTS header
- **No Password Storage**: Passwords never stored on server
- **Encrypted Audit Logs**: AES-256-GCM encryption at rest
- **Anonymized IP Addresses**: Last octet masked in audit logs
- **Secure Headers**: Helmet.js for security headers

**Code Example:**
```typescript
// backend/src/middleware/security.ts
import helmet from 'helmet';

app.use(helmet()); // Sets multiple security headers

// HSTS (HTTP Strict Transport Security)
app.use(helmet.hsts({
  maxAge: 31536000, // 1 year
  includeSubDomains: true,
  preload: true
}));

// Content Security Policy
app.use(helmet.contentSecurityPolicy({
  directives: {
    defaultSrc: ["'self'"],
    scriptSrc: ["'self'", "'unsafe-inline'"], // Needed for Vite HMR in dev
    styleSrc: ["'self'", "'unsafe-inline'"],
    imgSrc: ["'self'", 'data:', 'https:'],
    connectSrc: ["'self'", 'https://api.pwnedpasswords.com']
  }
}));
```

**4. XML External Entities (XXE)**

**Risk:** XML parser processes malicious external entities

**Mitigation:**
- **No XML Parsing**: This app does not parse XML (JSON only)
- **If XML Required**: Disable external entity processing

**5. Broken Access Control**

**Risk:** Users access resources they shouldn't

**Mitigation:**
- **JWT Authentication**: Verify token on every API request
- **RBAC**: Role-based access control (standard user vs compliance officer)
- **Principle of Least Privilege**: Users only access their own audit logs

**Code Example:**
```typescript
// backend/src/middleware/auth.ts
import jwt from 'jsonwebtoken';

export function authenticateJWT(req: Request, res: Response, next: NextFunction) {
  const authHeader = req.headers.authorization;

  if (!authHeader) {
    return res.status(401).json({ error: 'No token provided' });
  }

  const token = authHeader.split(' ')[1]; // Bearer <token>

  try {
    const decoded = jwt.verify(token, process.env.JWT_SECRET!) as JWTPayload;
    req.user = decoded; // Attach user to request
    next();
  } catch (error) {
    return res.status(403).json({ error: 'Invalid or expired token' });
  }
}

// backend/src/routes/audit.ts
app.get('/api/v1/audit', authenticateJWT, async (req, res) => {
  const userId = req.user.id;
  const userRole = req.user.role;

  // Users can only access their own logs
  // Compliance officers can access all logs
  const logs = userRole === 'compliance_officer'
    ? await auditLogRepository.findAll()
    : await auditLogRepository.findByUserId(userId);

  res.json({ logs });
});
```

**6. Security Misconfiguration**

**Risk:** Default configurations expose vulnerabilities

**Mitigation:**
- **Remove Default Credentials**: No default passwords
- **Disable Directory Listing**: Prevent file enumeration
- **Error Handling**: Generic error messages (no stack traces in production)
- **Security Headers**: Helmet.js for secure defaults

**7. Cross-Site Scripting (XSS)**

**Risk:** Malicious scripts executed in user's browser

**Mitigation:**
- **React Auto-Escaping**: React automatically escapes JSX output
- **Content Security Policy**: Restrict script sources
- **Input Validation**: Validate and sanitize all user input
- **Output Encoding**: Encode HTML entities

**Code Example:**
```typescript
// ✅ SECURE (React auto-escapes)
<div>{userInput}</div>

// ❌ VULNERABLE (dangerouslySetInnerHTML)
<div dangerouslySetInnerHTML={{ __html: userInput }} />

// ✅ SECURE (DOMPurify for HTML sanitization if needed)
import DOMPurify from 'dompurify';
<div dangerouslySetInnerHTML={{ __html: DOMPurify.sanitize(userInput) }} />
```

**8. Insecure Deserialization**

**Risk:** Malicious data deserialized into objects

**Mitigation:**
- **JSON Only**: No native serialization (pickle, marshal, etc.)
- **Schema Validation**: Validate all incoming JSON (Zod schemas)

**9. Using Components with Known Vulnerabilities**

**Risk:** Outdated dependencies with CVEs

**Mitigation:**
- **npm audit**: Run `npm audit` before every deploy
- **Dependabot**: GitHub Dependabot for automatic PRs
- **Renovate**: Alternative for dependency updates
- **Snyk**: Vulnerability scanning in CI/CD

**10. Insufficient Logging & Monitoring**

**Risk:** Attacks go undetected

**Mitigation:**
- **Audit Logging**: Tamper-proof hash chain for all password generations
- **Request Logging**: Log all API requests (Winston logger)
- **Error Logging**: Log all errors with stack traces (dev only)
- **Monitoring**: CloudWatch (AWS) or Application Insights (Azure)
- **Alerting**: Alert on suspicious patterns (rate limit violations, failed auth)

---

## HIBP Integration

### Have I Been Pwned (HIBP) API

**Service:** https://haveibeenpwned.com/
**Creator:** Troy Hunt
**Database:** 750M+ breached passwords from data breaches
**Privacy:** k-Anonymity model (password never sent to HIBP)

### k-Anonymity Protocol

**Problem:** Sending password to HIBP would expose it to third party

**Solution:** k-Anonymity via hash prefix matching

**How It Works:**

1. **Hash Password**: SHA-1 hash of password (client-side)
   ```
   Password: "P@ssw0rd123"
   SHA-1 Hash: "21BD12DC183F740EE76F27B78EB39C8AD972A757"
   ```

2. **Extract Prefix**: First 5 characters of hash
   ```
   Prefix: "21BD1"
   ```

3. **API Request**: Send prefix to HIBP API (NOT full hash, NOT password)
   ```
   GET https://api.pwnedpasswords.com/range/21BD1
   ```

4. **API Response**: HIBP returns ~500-1,000 hash suffixes (last 35 chars) and breach counts
   ```
   2DC183F740EE76F27B78EB39C8AD972A757:3
   003D68EB55068C33ACE09247EE4C639306B:3
   012C192B2F16F82EA0EB9EF18D9D539B0DD:1
   ... (500-1,000 hashes)
   ```

5. **Client-Side Match**: Check if full hash exists in response (offline)
   ```typescript
   const fullHashSuffix = fullHash.slice(5); // "2DC183F740EE76F27B78EB39C8AD972A757"
   const found = response.includes(fullHashSuffix);
   // found = true (password is breached 3 times)
   ```

6. **Privacy Preserved**: HIBP never sees full password or full hash

**Implementation:**

```typescript
// frontend/src/lib/hibpClient.ts

interface HIBPResult {
  breached: boolean;
  breachCount: number;
}

export async function checkPasswordBreach(password: string): Promise<HIBPResult> {
  // 1. Hash password with SHA-1 (client-side)
  const encoder = new TextEncoder();
  const data = encoder.encode(password);
  const hashBuffer = await crypto.subtle.digest('SHA-1', data);
  const hashArray = Array.from(new Uint8Array(hashBuffer));
  const hashHex = hashArray.map(b => b.toString(16).padStart(2, '0')).join('').toUpperCase();

  // 2. Extract first 5 characters
  const prefix = hashHex.slice(0, 5);
  const suffix = hashHex.slice(5);

  // 3. Send prefix to HIBP API
  const response = await fetch(`https://api.pwnedpasswords.com/range/${prefix}`, {
    headers: {
      'User-Agent': 'Q-AI-MSP-Password-Generator/1.0',
      // Optional: Add HIBP API key for higher rate limits
      ...(process.env.VITE_HIBP_API_KEY && {
        'hibp-api-key': process.env.VITE_HIBP_API_KEY
      })
    }
  });

  if (!response.ok) {
    throw new Error(`HIBP API error: ${response.status}`);
  }

  const text = await response.text();

  // 4. Parse response (format: "SUFFIX:COUNT\r\n")
  const lines = text.split('\r\n');
  for (const line of lines) {
    const [hashSuffix, countStr] = line.split(':');
    if (hashSuffix === suffix) {
      return {
        breached: true,
        breachCount: parseInt(countStr, 10)
      };
    }
  }

  // 5. Password not found in breaches
  return {
    breached: false,
    breachCount: 0
  };
}
```

**Auto-Regeneration:**

If password is found in breach database, automatically regenerate (up to 3 attempts):

```typescript
export async function generateSecurePassword(options: PasswordOptions): Promise<GeneratedPassword> {
  let attempts = 0;
  const maxAttempts = 3;

  while (attempts < maxAttempts) {
    const password = generateRandomPassword(options);
    const hibpResult = await checkPasswordBreach(password);

    if (!hibpResult.breached) {
      return {
        password,
        entropy: calculateEntropy(password, buildCharset(options)),
        breachCheck: hibpResult
      };
    }

    attempts++;
  }

  // After 3 attempts, return with warning (statistically extremely rare)
  throw new Error('Unable to generate non-breached password after 3 attempts. Try increasing length or complexity.');
}
```

**Rate Limits:**

- **Without API Key**: 1 request per 1.5 seconds per IP
- **With API Key**: 10 requests per second per API key

**API Key:** https://haveibeenpwned.com/API/Key (optional, $3.50/month for supporters)

---

## Audit Logging System

### Tamper-Proof Hash Chain

**Goal:** Create immutable audit logs that cannot be altered without detection

**Approach:** Blockchain-inspired hash chain (each log entry includes hash of previous entry)

**How It Works:**

1. **Genesis Entry**: First audit log has `previousHash = null`
2. **Subsequent Entries**: Each entry includes hash of previous entry
3. **Hash Calculation**: SHA-256 of concatenated log fields
4. **Verification**: Recalculate all hashes to verify chain integrity
5. **Tampering Detection**: If any entry is altered, hash chain breaks

**Visual Representation:**

```
Entry 1:
  data: { timestamp, userId, action, ... }
  previousHash: null
  hash: SHA-256(data + null) = "abc123..."

Entry 2:
  data: { timestamp, userId, action, ... }
  previousHash: "abc123..." (from Entry 1)
  hash: SHA-256(data + "abc123...") = "def456..."

Entry 3:
  data: { timestamp, userId, action, ... }
  previousHash: "def456..." (from Entry 2)
  hash: SHA-256(data + "def456...") = "ghi789..."
```

**If Entry 2 is tampered with:**
```
Entry 2 (modified):
  data: { timestamp, userId, action (MODIFIED), ... }
  previousHash: "abc123..."
  hash: SHA-256(modified data + "abc123...") = "xyz999..." (DIFFERENT)

Entry 3:
  previousHash: "def456..." (NO LONGER MATCHES Entry 2's hash "xyz999...")
  ❌ HASH CHAIN BROKEN - TAMPERING DETECTED
```

**Implementation:**

```typescript
// backend/src/services/auditService.ts

interface AuditLog {
  id: string; // UUID
  timestamp: string; // ISO 8601 UTC
  userId: string;
  action: 'single_generation' | 'bulk_generation' | 'export';
  passwordCount: number;
  complianceFramework: string;
  passwordHashPrefix: string; // First 8 chars of SHA-256 (reference only)
  ipAddress: string; // Anonymized (last octet masked)
  userAgent: string;
  previousHash: string | null; // Hash of previous entry (null for genesis)
  hash: string; // SHA-256 of this entry
  encrypted: boolean; // Whether entry is encrypted at rest
}

async function hashAuditLog(log: Omit<AuditLog, 'hash'>): Promise<string> {
  // Concatenate all fields in deterministic order
  const data = [
    log.id,
    log.timestamp,
    log.userId,
    log.action,
    log.passwordCount,
    log.complianceFramework,
    log.passwordHashPrefix,
    log.ipAddress,
    log.userAgent,
    log.previousHash || ''
  ].join('|');

  // SHA-256 hash
  const encoder = new TextEncoder();
  const dataBuffer = encoder.encode(data);
  const hashBuffer = await crypto.subtle.digest('SHA-256', dataBuffer);
  const hashArray = Array.from(new Uint8Array(hashBuffer));
  const hashHex = hashArray.map(b => b.toString(16).padStart(2, '0')).join('');

  return hashHex;
}

export async function createAuditLog(data: Omit<AuditLog, 'id' | 'previousHash' | 'hash'>): Promise<AuditLog> {
  // Get hash of last audit log entry (for hash chain)
  const lastLog = await db.auditLogs.findLast();
  const previousHash = lastLog ? lastLog.hash : null;

  // Create new audit log entry
  const auditLog: Omit<AuditLog, 'hash'> = {
    id: crypto.randomUUID(),
    ...data,
    previousHash
  };

  // Calculate hash of current entry
  const hash = await hashAuditLog(auditLog);

  // Final audit log entry
  const finalLog: AuditLog = {
    ...auditLog,
    hash
  };

  // Encrypt at rest (AES-256-GCM)
  const encryptedLog = await encryptAuditLog(finalLog);

  // Store in PostgreSQL
  await db.auditLogs.insert(encryptedLog);

  return finalLog;
}

// Verify hash chain integrity
export async function verifyHashChain(): Promise<{ valid: boolean; errors: string[] }> {
  const errors: string[] = [];

  // Retrieve all audit logs (oldest first)
  const logs = await db.auditLogs.findAll({ orderBy: 'timestamp ASC' });

  for (let i = 0; i < logs.length; i++) {
    const log = logs[i];

    // Verify previousHash matches previous entry's hash
    if (i === 0) {
      // Genesis entry should have previousHash = null
      if (log.previousHash !== null) {
        errors.push(`Entry ${log.id}: Genesis entry has non-null previousHash`);
      }
    } else {
      const prevLog = logs[i - 1];
      if (log.previousHash !== prevLog.hash) {
        errors.push(
          `Entry ${log.id}: previousHash (${log.previousHash}) does not match previous entry's hash (${prevLog.hash})`
        );
      }
    }

    // Recalculate hash and verify it matches stored hash
    const { hash, ...logWithoutHash } = log;
    const recalculatedHash = await hashAuditLog(logWithoutHash);
    if (recalculatedHash !== hash) {
      errors.push(
        `Entry ${log.id}: Stored hash (${hash}) does not match recalculated hash (${recalculatedHash}). Entry may have been tampered with.`
      );
    }
  }

  return {
    valid: errors.length === 0,
    errors
  };
}
```

**Encryption at Rest:**

Audit logs encrypted with AES-256-GCM before storage in PostgreSQL:

```typescript
// backend/src/utils/crypto.ts
import crypto from 'crypto';

const ENCRYPTION_KEY = Buffer.from(process.env.AUDIT_LOG_ENCRYPTION_KEY!, 'hex'); // 32 bytes (256 bits)
const ALGORITHM = 'aes-256-gcm';

export function encryptAuditLog(log: AuditLog): EncryptedAuditLog {
  const iv = crypto.randomBytes(16); // Initialization vector
  const cipher = crypto.createCipheriv(ALGORITHM, ENCRYPTION_KEY, iv);

  const plaintext = JSON.stringify(log);
  let encrypted = cipher.update(plaintext, 'utf8', 'hex');
  encrypted += cipher.final('hex');

  const authTag = cipher.getAuthTag(); // For GCM authentication

  return {
    id: log.id, // Not encrypted (for indexing)
    timestamp: log.timestamp, // Not encrypted (for querying)
    userId: log.userId, // Not encrypted (for filtering)
    encryptedData: encrypted,
    iv: iv.toString('hex'),
    authTag: authTag.toString('hex')
  };
}

export function decryptAuditLog(encryptedLog: EncryptedAuditLog): AuditLog {
  const iv = Buffer.from(encryptedLog.iv, 'hex');
  const authTag = Buffer.from(encryptedLog.authTag, 'hex');
  const decipher = crypto.createDecipheriv(ALGORITHM, ENCRYPTION_KEY, iv);

  decipher.setAuthTag(authTag);

  let decrypted = decipher.update(encryptedLog.encryptedData, 'hex', 'utf8');
  decrypted += decipher.final('utf8');

  return JSON.parse(decrypted);
}
```

**Retention Policy:**

- **HIPAA/SOC2 Requirement**: 7 years (2,555 days)
- **PCI-DSS Requirement**: 1 year (365 days)
- **Implementation**: Archive logs to S3 Glacier after 1 year, delete after 7 years

---

## Development Roadmap

### Phase 1: Foundation (Weeks 1-4) ✅ Current

**Status:** 🔴 Pre-Production (Planning Complete, Development Starts Week 1)

**Goals:**
- Set up project infrastructure
- Implement core password generation engine
- Single password UI
- NIST, PCI-DSS, HIPAA compliance
- HIBP integration
- Basic audit logging

**Key Deliverables:**
1. **Repository Setup** (Week 1)
   - GitHub repository creation
   - Branch protection rules
   - CI/CD pipeline (GitHub Actions)
   - Frontend scaffolding (React + Vite)
   - Backend scaffolding (Express + TypeScript)

2. **Password Generation Engine** (Week 1-2)
   - Web Crypto API random generator
   - Character set configuration
   - Entropy calculation
   - Basic validation

3. **Compliance Framework Engine** (Week 2)
   - NIST SP 800-63B profile
   - PCI-DSS v4.0 profile
   - HIPAA Security Rule profile
   - Compliance validation logic

4. **Single Password UI** (Week 2-3)
   - Password options form (length, character types)
   - Compliance framework selector
   - Password result display
   - Copy to clipboard
   - Strength meter (entropy visualization)
   - Breach check indicator

5. **HIBP Integration** (Week 3)
   - k-Anonymity implementation
   - SHA-1 hash calculation
   - API client with error handling
   - Rate limiting (1 req/1.5s)
   - Auto-regeneration on breach

6. **Audit Logging** (Week 3-4)
   - PostgreSQL schema creation
   - Hash chain implementation
   - Encryption at rest (AES-256-GCM)
   - Audit log API endpoints

7. **Authentication** (Week 4)
   - JWT authentication
   - User registration/login
   - Role-based access control (RBAC)
   - Session management

**Success Criteria:**
- ✅ Single password generation working
- ✅ NIST, PCI-DSS, HIPAA compliance validation
- ✅ HIBP breach check functional
- ✅ Audit logs storing with hash chain
- ✅ User authentication working

---

### Phase 2: Bulk & Export (Weeks 5-8)

**Goals:**
- Bulk password generation (up to 10,000)
- Export in multiple formats (CSV, JSON, Excel)
- Passphrase and pronounceable generators
- REST API with authentication

**Key Deliverables:**
1. **Bulk Generation** (Week 5)
   - Bulk generation form (quantity, compliance)
   - Web Worker for performance (non-blocking UI)
   - Progress indicator (real-time updates)
   - Uniqueness enforcement (no duplicates)
   - Performance optimization (<5s for 10,000 passwords)

2. **Export Functionality** (Week 5-6)
   - CSV export (UTF-8 encoding)
   - JSON export (API-compatible schema)
   - Excel export (.xlsx with SheetJS)
   - Export metadata (timestamp, compliance, user)
   - Conditional formatting (Excel)

3. **Passphrase Generator** (Week 6)
   - Diceware implementation (EFF wordlist)
   - Word count selection (4-10 words)
   - Separator options (dash, underscore, space, camelCase)
   - Capitalization options
   - Number appending

4. **Pronounceable Generator** (Week 6)
   - CVC pattern implementation
   - Syllable count selection (3-6)
   - Separator options
   - Number/symbol appending

5. **REST API** (Week 7-8)
   - `/api/v1/passwords/generate` endpoint (single)
   - `/api/v1/passwords/bulk` endpoint (bulk)
   - `/api/v1/audit` endpoint (audit logs)
   - `/api/v1/auth` endpoints (login, register)
   - Swagger/OpenAPI documentation
   - Rate limiting (100 req/min single, 10 req/hour bulk)

**Success Criteria:**
- ✅ Bulk generation of 10,000 passwords in <5 seconds
- ✅ Export in CSV, JSON, Excel formats
- ✅ Passphrase and pronounceable generators working
- ✅ REST API endpoints functional
- ✅ API documentation published

---

### Phase 3: Compliance & Audit (Weeks 9-12)

**Goals:**
- Additional compliance frameworks (SOC2, ISO 27001, CIS)
- Custom policy builder
- Audit reporting with PDF export
- Security audit and penetration testing

**Key Deliverables:**
1. **Additional Compliance Frameworks** (Week 9)
   - SOC2 Type II profile
   - ISO 27001:2022 profile
   - CIS Benchmarks profile
   - Extended validation logic

2. **Custom Policy Builder** (Week 9-10)
   - UI for custom policy creation
   - Save/load custom policies
   - Policy templates
   - Organization-specific policies

3. **Audit Reporting** (Week 10-11)
   - Audit log query interface (date range, user, compliance)
   - Export audit logs to CSV, JSON
   - PDF report generation (professional formatting)
   - Hash chain verification tool
   - Compliance attestation certificates

4. **Security Audit** (Week 11)
   - OWASP Top 10 review
   - Dependency vulnerability scan (npm audit, Snyk)
   - Code review for security issues
   - Penetration testing (OWASP ZAP, Burp Suite)
   - Security fixes

5. **Performance Optimization** (Week 12)
   - Frontend bundle size optimization (tree-shaking, code splitting)
   - Backend query optimization (indexing, caching)
   - Load testing (10,000 concurrent users)
   - CDN configuration (CloudFront)

**Success Criteria:**
- ✅ All 6 compliance frameworks implemented
- ✅ Custom policy builder functional
- ✅ PDF audit reports generated
- ✅ Security audit complete (no critical vulnerabilities)
- ✅ Performance targets met (see README.md)

---

### Phase 4: Integration & Launch (Weeks 13-16)

**Goals:**
- Q-AI-MSP SSO integration
- RBAC synchronization
- White-label branding
- Production deployment

**Key Deliverables:**
1. **Q-AI-MSP Integration** (Week 13-14)
   - OAuth 2.0 SSO integration
   - RBAC synchronization (standard user vs compliance officer)
   - White-label branding (logo, colors, domain)
   - Session synchronization

2. **Production Infrastructure** (Week 14-15)
   - AWS ECS Fargate deployment
   - RDS PostgreSQL Multi-AZ
   - ElastiCache Redis
   - S3 Glacier (audit log archive)
   - CloudFront CDN
   - Route 53 DNS

3. **Monitoring & Alerting** (Week 15)
   - CloudWatch dashboards
   - Log aggregation (CloudWatch Logs)
   - Error tracking (Sentry)
   - Uptime monitoring (UptimeRobot)
   - Alerting (SNS → Email/Slack)

4. **Launch Preparation** (Week 16)
   - User acceptance testing (UAT)
   - Load testing (10,000 concurrent users)
   - Disaster recovery testing
   - Documentation review (user guide, FAQ, runbook)
   - Launch checklist

**Success Criteria:**
- ✅ Q-AI-MSP SSO integration working
- ✅ Production deployment complete
- ✅ Monitoring dashboards operational
- ✅ UAT passed
- ✅ Ready for production launch

---

### Phase 5: Enhancement & Scale (Ongoing)

**Goals:**
- Mobile responsive UI
- Dark mode support
- Active Directory integration
- Multi-language support
- Advanced analytics dashboard

**Future Enhancements:**
- Mobile app (React Native)
- Browser extension (Chrome, Firefox, Safari)
- Password manager integration (1Password, LastPass, Bitwarden)
- Advanced reporting (usage analytics, compliance trends)
- Machine learning (detect weak password patterns)

---

**Total Duration:** 16 weeks (4 months) to production launch
**Ongoing Enhancement:** Continuous improvement and feature additions

**Last Updated:** 2025-11-12
**Next Milestone:** Week 1 (Repository Setup & Password Generation Engine)
