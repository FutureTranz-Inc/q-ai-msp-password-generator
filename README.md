# Q-AI-MSP Enterprise Password Generator

**Version:** 1.0.0
**Status:** 🔴 PRE-PRODUCTION
**Project Type:** Q-AI-MSP Add-on Module

---

## Overview

Enterprise-grade automated password generation webapp for MSPs managing multiple client environments. Generates compliance-ready passwords based on industry standards (NIST, PCI-DSS, HIPAA, SOC2, ISO 27001, CIS Benchmarks) with comprehensive audit logging and tamper-proof records.

### Key Features

- **6 Compliance Frameworks:** NIST SP 800-63B, PCI-DSS v4.0, HIPAA, SOC2 Type II, ISO 27001:2022, CIS Benchmarks
- **Multiple Generation Methods:** Random (cryptographically secure), Diceware passphrases, pronounceable passwords
- **Bulk Operations:** Generate up to 10,000 passwords at once (<5 seconds)
- **Export Formats:** CSV, JSON, Excel (.xlsx), PDF reports
- **Breach Detection:** Have I Been Pwned (HIBP) API integration with k-anonymity
- **Audit Excellence:** Tamper-proof hash chain logging for compliance reporting
- **Q-AI-MSP Integration:** SSO, RBAC, white-label branding
- **REST API:** Programmatic password generation with authentication

---

## Quick Start

### Prerequisites

- **Node.js** 20+ LTS
- **npm** 10+
- **PostgreSQL** 16+
- **Redis** 7+
- **Git**

### Installation

```bash
# Clone repository
cd "/Users/vquinones/Q Dropbox/FutureTranz/Technology/Dev"
git clone https://github.com/FutureTranz-Inc/q-ai-msp-password-generator.git
cd q-ai-msp-password-generator

# Install dependencies
npm install

# Set up environment variables
cp .env.example .env
# Edit .env with your database and API credentials

# Run database migrations
npm run migrate

# Start development servers
npm run dev
```

**Access the application:**
- Frontend: http://localhost:3000
- Backend API: http://localhost:3001
- API Docs: http://localhost:3001/api-docs

---

## Project Structure

```
q-ai-msp-password-generator/
├── frontend/                   # React TypeScript app
│   ├── src/
│   │   ├── components/         # Reusable UI components
│   │   ├── pages/              # Page components (Generate, Bulk, Audit)
│   │   ├── lib/                # Utilities (passwordGenerator, hibpClient)
│   │   ├── hooks/              # Custom React hooks
│   │   └── App.tsx             # Main app component
│   ├── public/                 # Static assets
│   └── package.json
│
├── backend/                    # Express.js API
│   ├── src/
│   │   ├── routes/             # API routes (/api/v1/passwords, /api/v1/audit)
│   │   ├── middleware/         # Auth, rate limiting, error handling
│   │   ├── services/           # Business logic
│   │   ├── database/           # PostgreSQL connection, migrations
│   │   └── server.ts           # Entry point
│   └── package.json
│
├── shared/                     # Shared TypeScript types & utilities
│   ├── types/                  # ComplianceFramework, PasswordOptions
│   └── data/                   # Compliance profiles, Diceware wordlist
│
├── docs/                       # Documentation
│   ├── prd/                    # Product Requirements Document
│   ├── tasks/                  # Development task lists
│   ├── USER_GUIDE.md           # End-user documentation
│   └── RUNBOOK.md              # Operations guide
│
├── infrastructure/             # Terraform/CloudFormation (AWS/Azure)
│   ├── terraform/              # Infrastructure as Code
│   └── docker/                 # Docker Compose for local dev
│
├── tests/                      # End-to-end tests
│   └── e2e/                    # Playwright or Cypress tests
│
├── .gitignore
├── package.json                # Monorepo workspace config
├── LICENSE
└── README.md
```

---

## Core Capabilities

### 1. Compliance Frameworks

#### NIST SP 800-63B
- Minimum 15 characters (no composition rules)
- Breach check against HIBP database
- No mandatory rotation (change on compromise only)

#### PCI-DSS v4.0
- Minimum 12 characters
- All character types required
- 90-day rotation
- No username in password

#### HIPAA Security Rule
- Minimum 12 characters
- 3 of 4 character types
- 60-90 day rotation
- 24-month uniqueness

#### SOC2 Type II
- Minimum 12 characters
- All character types
- No sequential characters
- 10 password history

#### ISO 27001:2022
- Minimum 12 characters
- No dictionary words
- Mix of character types
- Change on suspected compromise

#### CIS Benchmarks
- Minimum 14 characters (strongest)
- All character types
- 24 password history
- 365-day rotation (60 days for privileged)

### 2. Generation Methods

**Random (Cryptographically Secure)**
- Web Crypto API (`crypto.getRandomValues()`)
- 256-bit entropy source (CSPRNG)
- 8-128 character length
- Character sets: Uppercase, lowercase, numbers, symbols, extended Unicode
- Example: `Xk9#mL2$vN8pQ@5r` (16 chars, 105 bits entropy)

**Passphrase (Diceware)**
- EFF Long Wordlist (7,776 words)
- 4-10 word passphrases
- Separator options: space, dash, underscore, camelCase
- Example: `correct-horse-battery-staple-89` (5 words, 64.6 bits entropy)

**Pronounceable**
- Consonant-vowel-consonant (CVC) pattern
- More memorable, easier to type
- Example: `Trobami-Vixel-32!` (18 chars, ~60 bits entropy)

### 3. Bulk Generation

- Generate 1-10,000 passwords at once
- Enforce uniqueness (no duplicates)
- Apply same policy to entire batch
- CSV/JSON/Excel export with metadata
- Progress indicator (real-time updates)
- Performance: 10,000 passwords in <5 seconds (Web Worker)

### 4. Export Formats

**CSV (UTF-8)**
```csv
Password,Generated,Compliance,Expiration,User,Notes
Xk9#mL2$vN8pQ@5r,2025-11-12T14:32:15Z,PCI-DSS v4.0,2026-02-10,,Admin account
```

**JSON (API-compatible)**
```json
{
  "version": "1.0",
  "passwords": [
    {
      "password": "Xk9#mL2$vN8pQ@5r",
      "entropy_bits": 105,
      "compliance": "PCI-DSS v4.0"
    }
  ]
}
```

**Excel (.xlsx)**
- Sheet 1: Passwords table (formatted, conditional coloring)
- Sheet 2: Metadata (export info, compliance details)

**PDF Reports**
- Audit log reports with digital signature
- Compliance attestation certificates
- Professional formatting with Q-AI-MSP branding

### 5. Have I Been Pwned Integration

**k-Anonymity Privacy Protection:**
1. Hash password with SHA-1
2. Send first 5 characters to HIBP API
3. HIBP returns ~500-1,000 matching hashes
4. Client checks if full hash exists (offline)
5. Password never sent to HIBP (privacy preserved)

**750M+ breached passwords** checked in real-time. If match found, password automatically regenerated (up to 3 attempts).

### 6. Audit Logging

**Tamper-Proof Hash Chain:**
- Each log entry includes SHA-256 hash of previous entry
- Immutable (append-only, no delete/edit)
- Encrypted at rest (AES-256-GCM)
- 7-year retention (HIPAA/SOC2 compliance)

**Logged Events:**
- Timestamp (UTC), User ID, Action (single/bulk generation)
- Password count, Compliance framework
- Password hash (first 8 chars of SHA-256, for reference only)
- IP address (anonymized, last octet masked)
- User agent (browser/OS detection)

---

## API Documentation

### Authentication

All API requests require Bearer token authentication:

```bash
Authorization: Bearer <JWT_TOKEN>
```

Get token via Q-AI-MSP OAuth 2.0 flow.

### Generate Passwords

**Endpoint:** `POST /api/v1/passwords/generate`

**Request:**
```json
{
  "count": 10,
  "compliance": "PCI-DSS",
  "length": 16,
  "type": "random",
  "options": {
    "uppercase": true,
    "lowercase": true,
    "numbers": true,
    "symbols": true,
    "excludeAmbiguous": true
  }
}
```

**Response:**
```json
{
  "passwords": ["Xk9#mL2$vN8pQ@5r", ...],
  "metadata": {
    "generated_at": "2025-11-12T14:32:15Z",
    "compliance": "PCI-DSS v4.0",
    "entropy_bits": 105,
    "batch_id": "uuid-here"
  }
}
```

**Rate Limits:**
- Single generation: 100 requests/minute
- Bulk generation: 10 requests/hour

### Query Audit Logs

**Endpoint:** `GET /api/v1/audit?start_date=&end_date=&limit=100`

**Response:**
```json
{
  "logs": [
    {
      "timestamp": "2025-11-12T14:32:15Z",
      "user_id": "user123",
      "action": "bulk_generate",
      "password_count": 100,
      "compliance_framework": "PCI-DSS v4.0"
    }
  ],
  "total": 1247
}
```

**API Documentation:** http://localhost:3001/api-docs (Swagger UI)

---

## Development

### Prerequisites

- Node.js 20+ LTS
- PostgreSQL 16+ (local or Docker)
- Redis 7+ (local or Docker)

### Local Setup

```bash
# Install dependencies
npm install

# Start PostgreSQL and Redis (Docker Compose)
cd infrastructure/docker
docker-compose up -d

# Run database migrations
npm run migrate

# Start dev servers (frontend + backend)
npm run dev
```

### Testing

```bash
# Run all tests
npm test

# Run tests with coverage
npm run test:coverage

# Run E2E tests
npm run test:e2e
```

### Linting & Formatting

```bash
# Lint code
npm run lint

# Fix linting issues
npm run lint:fix

# Format code
npm run format
```

---

## Deployment

### Production Checklist

- [ ] Set environment variables (DATABASE_URL, REDIS_URL, JWT_SECRET)
- [ ] Run database migrations
- [ ] Build frontend and backend (`npm run build`)
- [ ] Start production server (`npm start`)
- [ ] Configure SSL/TLS certificate
- [ ] Enable WAF (SQL injection, XSS protection)
- [ ] Set up monitoring (CloudWatch, Datadog)
- [ ] Configure auto-scaling (ECS Fargate or Kubernetes)

### AWS Deployment (ECS Fargate)

```bash
# Build Docker images
docker build -t password-gen-frontend:latest ./frontend
docker build -t password-gen-backend:latest ./backend

# Push to ECR
aws ecr get-login-password --region us-east-1 | docker login --username AWS --password-stdin <account-id>.dkr.ecr.us-east-1.amazonaws.com
docker tag password-gen-frontend:latest <account-id>.dkr.ecr.us-east-1.amazonaws.com/password-gen-frontend:latest
docker push <account-id>.dkr.ecr.us-east-1.amazonaws.com/password-gen-frontend:latest

# Deploy with Terraform
cd infrastructure/terraform
terraform init
terraform plan
terraform apply
```

---

## Security

### Security Features

- **Zero Storage:** Passwords never stored on server (generated client-side)
- **Zero Transmission:** Passwords never sent to server (except hash in audit log)
- **Breach Detection:** HIBP API checks against 750M+ breached passwords
- **Audit Logging:** Tamper-proof hash chain (SHA-256)
- **Encryption at Rest:** AES-256-GCM for audit logs
- **Rate Limiting:** Redis-backed (100 req/min single, 10 req/hour bulk)
- **RBAC:** Role-based access control (compliance officer vs standard user)

### Vulnerability Disclosure

If you discover a security vulnerability, please email: security@futuretranz.com

**Do NOT** create a public GitHub issue for security vulnerabilities.

---

## Performance Targets

| Metric | Target | Actual |
|--------|--------|--------|
| Page Load (LCP) | <2.5s | TBD |
| Single Password Generation | <50ms | TBD |
| Bulk (1,000 passwords) | <2s | TBD |
| Bulk (10,000 passwords) | <5s | TBD |
| API Response (p95) | <500ms | TBD |
| Lighthouse Score | 95+ | TBD |
| Uptime | 99.9% | TBD |

---

## Support

### Documentation

- **User Guide:** docs/USER_GUIDE.md
- **FAQ:** docs/FAQ.md
- **API Docs:** http://localhost:3001/api-docs
- **Runbook:** docs/RUNBOOK.md (for ops team)

### Contact

- **Technical Support:** support@futuretranz.com
- **General Inquiries:** info@futuretranz.com
- **Security Issues:** security@futuretranz.com

---

## Roadmap

### Phase 1: Foundation (Weeks 1-4) ✅ Current
- Core password generation engine
- Single password UI
- Compliance frameworks (NIST, PCI-DSS, HIPAA)
- HIBP integration
- Audit logging

### Phase 2: Bulk & Export (Weeks 5-8)
- Bulk generation (10,000 passwords)
- CSV, JSON, Excel export
- REST API with authentication
- Passphrase and pronounceable generators

### Phase 3: Compliance & Audit (Weeks 9-12)
- Additional frameworks (SOC2, ISO 27001, CIS)
- Custom policy builder
- Audit reporting with PDF export
- Security audit and penetration testing

### Phase 4: Integration & Launch (Weeks 13-16)
- Q-AI-MSP SSO integration
- RBAC synchronization
- White-label branding
- Production deployment

### Phase 5: Enhancement & Scale (Ongoing)
- Mobile responsive UI
- Dark mode support
- Active Directory integration
- Multi-language support (Spanish, French, German)
- Advanced analytics dashboard

---

## License

**Proprietary License**

Copyright (c) 2025 FutureTranz, Inc. All rights reserved.

This software is proprietary and confidential. Unauthorized copying, distribution,
or use is strictly prohibited. See LICENSE file for full terms.

---

## Acknowledgments

- **EFF Diceware Wordlist:** https://www.eff.org/deeplinks/2016/07/new-wordlists-random-passphrases
- **Have I Been Pwned:** https://haveibeenpwned.com/
- **NIST SP 800-63B:** https://pages.nist.gov/800-63-3/sp800-63b.html
- **Q-AI-MSP Platform:** Integration partner

---

**Project Status:** 🔴 PRE-PRODUCTION
**Last Updated:** 2025-11-12
**Next Milestone:** Phase 1 Complete (Week 4)
