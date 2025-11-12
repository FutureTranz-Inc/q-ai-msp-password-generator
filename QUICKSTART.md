# Quick Start Guide

**Get started in 30 minutes**

This guide walks you through setting up the Q-AI-MSP Enterprise Password Generator on your local machine and generating your first password.

---

## Prerequisites Checklist

Before you begin, ensure you have:

- [ ] **Node.js 20+ LTS** - [Download](https://nodejs.org/)
- [ ] **npm 10+** (comes with Node.js)
- [ ] **Git** - [Download](https://git-scm.com/)
- [ ] **PostgreSQL 16+** - [Download](https://www.postgresql.org/download/) or use Docker
- [ ] **Redis 7+** - [Download](https://redis.io/download/) or use Docker
- [ ] **Code Editor** (VS Code recommended)

**Verify installations:**
```bash
node --version   # Should show v20.x.x or higher
npm --version    # Should show v10.x.x or higher
git --version    # Should show version
psql --version   # Should show 16.x or higher
redis-cli --version  # Should show 7.x or higher
```

---

## Step 1: Clone Repository (2 minutes)

```bash
# Clone the repository
git clone https://github.com/FutureTranz-Inc/q-ai-msp-password-generator.git

# Enter project directory
cd q-ai-msp-password-generator

# Verify structure
ls -la
```

**Expected output:**
```
drwxr-xr-x  frontend/
drwxr-xr-x  backend/
drwxr-xr-x  shared/
drwxr-xr-x  docs/
drwxr-xr-x  infrastructure/
-rw-r--r--  README.md
-rw-r--r--  package.json
-rw-r--r--  LICENSE
```

---

## Step 2: Install Dependencies (5 minutes)

```bash
# Install all workspace dependencies
npm install

# This installs dependencies for:
# - Root project
# - frontend/ workspace
# - backend/ workspace
# - shared/ workspace
```

**What gets installed:**
- **Frontend**: React, TypeScript, Tailwind CSS, Vite
- **Backend**: Express, PostgreSQL client, Redis client, JWT
- **Shared**: TypeScript types, compliance profiles, utilities
- **Dev Tools**: ESLint, Prettier, Husky, Concurrently

**Troubleshooting:**
```bash
# If you get EACCES errors:
sudo chown -R $(whoami) ~/.npm

# If you get gyp errors (native modules):
npm install --ignore-scripts

# Clear cache if needed:
npm cache clean --force
rm -rf node_modules package-lock.json
npm install
```

---

## Step 3: Set Up Environment Variables (3 minutes)

```bash
# Copy example environment file
cp .env.example .env

# Edit with your preferred editor
code .env  # VS Code
# or
nano .env  # Terminal editor
```

**Required environment variables:**

```bash
# .env file

# Database Configuration
DATABASE_URL=postgresql://postgres:password@localhost:5432/password_generator
DATABASE_HOST=localhost
DATABASE_PORT=5432
DATABASE_NAME=password_generator
DATABASE_USER=postgres
DATABASE_PASSWORD=your_secure_password_here

# Redis Configuration
REDIS_URL=redis://localhost:6379
REDIS_HOST=localhost
REDIS_PORT=6379

# Backend Server
PORT=3001
NODE_ENV=development

# JWT Authentication
JWT_SECRET=your_super_secret_jwt_key_change_this_in_production
JWT_EXPIRATION=24h

# Have I Been Pwned API
HIBP_API_KEY=optional_but_recommended_for_higher_rate_limits
HIBP_API_URL=https://api.pwnedpasswords.com

# Frontend
VITE_API_URL=http://localhost:3001
VITE_API_VERSION=v1

# Rate Limiting
RATE_LIMIT_WINDOW_MS=60000
RATE_LIMIT_MAX_REQUESTS=100

# Audit Logging
AUDIT_LOG_RETENTION_DAYS=2555  # 7 years
AUDIT_LOG_ENCRYPTION_KEY=your_32_byte_encryption_key_here
```

**Generate secure secrets:**
```bash
# Generate JWT secret (32 bytes)
node -e "console.log(require('crypto').randomBytes(32).toString('hex'))"

# Generate encryption key (32 bytes for AES-256)
node -e "console.log(require('crypto').randomBytes(32).toString('hex'))"
```

---

## Step 4: Start Database Services (5 minutes)

### Option A: Using Docker (Recommended)

```bash
# Navigate to infrastructure directory
cd infrastructure/docker

# Start PostgreSQL and Redis containers
docker-compose up -d

# Verify containers are running
docker ps

# Expected output:
# CONTAINER ID   IMAGE            STATUS
# abc123...      postgres:16      Up 2 minutes
# def456...      redis:7-alpine   Up 2 minutes
```

**Docker Compose configuration** (`infrastructure/docker/docker-compose.yml`):
```yaml
version: '3.8'
services:
  postgres:
    image: postgres:16-alpine
    ports:
      - "5432:5432"
    environment:
      POSTGRES_DB: password_generator
      POSTGRES_USER: postgres
      POSTGRES_PASSWORD: password
    volumes:
      - postgres_data:/var/lib/postgresql/data

  redis:
    image: redis:7-alpine
    ports:
      - "6379:6379"
    volumes:
      - redis_data:/data

volumes:
  postgres_data:
  redis_data:
```

### Option B: Local Installation

**PostgreSQL:**
```bash
# macOS (Homebrew)
brew install postgresql@16
brew services start postgresql@16

# Create database
psql postgres
CREATE DATABASE password_generator;
\q

# Verify connection
psql -h localhost -U postgres -d password_generator
```

**Redis:**
```bash
# macOS (Homebrew)
brew install redis
brew services start redis

# Verify connection
redis-cli ping
# Should return: PONG
```

---

## Step 5: Run Database Migrations (2 minutes)

```bash
# Return to project root
cd ../..

# Run migrations to create database schema
npm run migrate

# Expected output:
# Running migrations...
# ✓ 001_create_audit_logs_table.sql
# ✓ 002_create_hash_chain_index.sql
# ✓ 003_create_users_table.sql
# Migrations complete!
```

**Verify database schema:**
```bash
psql -h localhost -U postgres -d password_generator -c "\dt"

# Expected tables:
#  public | audit_logs           | table | postgres
#  public | users                | table | postgres
#  public | schema_migrations    | table | postgres
```

---

## Step 6: Start Development Servers (2 minutes)

```bash
# Start both frontend and backend concurrently
npm run dev

# This runs:
# - Frontend: http://localhost:3000 (Vite dev server)
# - Backend: http://localhost:3001 (Express API)
```

**Expected console output:**
```
> q-ai-msp-password-generator@1.0.0 dev
> concurrently "npm run dev:frontend" "npm run dev:backend"

[0]
[0] > frontend@1.0.0 dev
[0] > vite
[0]
[0]   VITE v5.0.0  ready in 523 ms
[0]
[0]   ➜  Local:   http://localhost:3000/
[0]   ➜  Network: use --host to expose
[0]
[1]
[1] > backend@1.0.0 dev
[1] > nodemon src/server.ts
[1]
[1] [nodemon] 3.0.2
[1] [nodemon] to restart at any time, enter `rs`
[1] [nodemon] watching path(s): src/**/*
[1] [nodemon] watching extensions: ts
[1] [nodemon] starting `ts-node src/server.ts`
[1]
[1] Server running on http://localhost:3001
[1] Database connected: password_generator
[1] Redis connected: localhost:6379
```

**Troubleshooting:**
```bash
# If port 3000 is already in use:
# Edit frontend/vite.config.ts and change port
# Or kill the process:
lsof -ti:3000 | xargs kill -9

# If port 3001 is already in use:
# Edit backend/.env and change PORT
# Or kill the process:
lsof -ti:3001 | xargs kill -9

# If database connection fails:
# Verify PostgreSQL is running:
pg_isready -h localhost -p 5432

# If Redis connection fails:
# Verify Redis is running:
redis-cli ping
```

---

## Step 7: Generate Your First Password (5 minutes)

### Using the Web Interface

1. **Open browser to http://localhost:3000**

2. **Select compliance framework:**
   - Click "Compliance Framework" dropdown
   - Choose "NIST SP 800-63B" (recommended for first test)

3. **Configure password options:**
   - Length: 16 characters (default)
   - Character types: All enabled (uppercase, lowercase, numbers, symbols)
   - Exclude ambiguous: ✓ (recommended)

4. **Generate password:**
   - Click "Generate Password" button
   - Password appears in the result field
   - Entropy displayed: ~105 bits (for 16-char random)
   - HIBP breach check: ✓ Not found in breaches

5. **View details:**
   - Compliance status: ✓ Meets NIST SP 800-63B requirements
   - Expiration: None (NIST does not require rotation)
   - Character distribution: Displayed below password

6. **Copy password:**
   - Click "Copy to Clipboard" icon
   - Password copied (confirmation toast appears)

### Using the API

**Generate a single password:**
```bash
curl -X POST http://localhost:3001/api/v1/passwords/generate \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer YOUR_JWT_TOKEN" \
  -d '{
    "count": 1,
    "compliance": "NIST",
    "length": 16,
    "type": "random",
    "options": {
      "uppercase": true,
      "lowercase": true,
      "numbers": true,
      "symbols": true,
      "excludeAmbiguous": true
    }
  }'
```

**Response:**
```json
{
  "passwords": ["Xk9#mL2$vN8pQ@5r"],
  "metadata": {
    "generated_at": "2025-11-12T14:32:15Z",
    "compliance": "NIST SP 800-63B",
    "entropy_bits": 105,
    "breach_check": "passed",
    "batch_id": "550e8400-e29b-41d4-a716-446655440000"
  }
}
```

**Get JWT token (first-time setup):**
```bash
# Register a user
curl -X POST http://localhost:3001/api/v1/auth/register \
  -H "Content-Type: application/json" \
  -d '{
    "email": "admin@example.com",
    "password": "YourSecurePassword123!",
    "name": "Admin User"
  }'

# Login to get token
curl -X POST http://localhost:3001/api/v1/auth/login \
  -H "Content-Type: application/json" \
  -d '{
    "email": "admin@example.com",
    "password": "YourSecurePassword123!"
  }'

# Response includes JWT token:
# {
#   "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...",
#   "user": { ... }
# }
```

---

## Step 8: Explore Additional Features (5 minutes)

### Generate Passphrase (Diceware)

**Web Interface:**
1. Select "Passphrase (Diceware)" from generation method dropdown
2. Choose number of words: 5 (recommended)
3. Select separator: dash (-)
4. Click "Generate Password"
5. Result: `correct-horse-battery-staple-89` (64.6 bits entropy)

**API:**
```bash
curl -X POST http://localhost:3001/api/v1/passwords/generate \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer YOUR_JWT_TOKEN" \
  -d '{
    "count": 1,
    "type": "passphrase",
    "options": {
      "words": 5,
      "separator": "-",
      "includeNumber": true
    }
  }'
```

### Bulk Generation

**Web Interface:**
1. Navigate to "Bulk Generation" tab
2. Enter quantity: 100
3. Select compliance: PCI-DSS v4.0
4. Click "Generate Bulk Passwords"
5. Progress bar shows generation status
6. Download as CSV, JSON, or Excel

**API:**
```bash
curl -X POST http://localhost:3001/api/v1/passwords/bulk \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer YOUR_JWT_TOKEN" \
  -d '{
    "count": 100,
    "compliance": "PCI-DSS",
    "length": 16,
    "type": "random",
    "format": "csv"
  }'
```

### View Audit Logs

**Web Interface:**
1. Navigate to "Audit Logs" tab
2. Filter by date range, user, compliance framework
3. View detailed audit trail with tamper-proof hash chain
4. Export audit report as PDF

**API:**
```bash
curl -X GET "http://localhost:3001/api/v1/audit?start_date=2025-11-01&end_date=2025-11-12&limit=100" \
  -H "Authorization: Bearer YOUR_JWT_TOKEN"
```

---

## Step 9: Run Tests (3 minutes)

```bash
# Run all tests (unit + integration + E2E)
npm test

# Run tests with coverage
npm run test:coverage

# Run only unit tests
npm run test:unit

# Run only E2E tests
npm run test:e2e

# Run tests in watch mode (for development)
npm run test:watch
```

**Expected output:**
```
Test Suites: 42 passed, 42 total
Tests:       247 passed, 247 total
Snapshots:   0 total
Time:        12.456 s
Coverage:    92.3% (target: 90%)
```

---

## Step 10: Access API Documentation (1 minute)

**Swagger UI:** http://localhost:3001/api-docs

**Interactive API documentation** with:
- All endpoints documented
- Request/response schemas
- Try it out functionality
- Authentication flow
- Rate limit information

---

## Common Tasks

### Stop Development Servers

```bash
# Press Ctrl+C in the terminal running `npm run dev`

# Or kill processes manually:
lsof -ti:3000,3001 | xargs kill -9
```

### Stop Database Services (Docker)

```bash
cd infrastructure/docker
docker-compose down

# To remove volumes (WARNING: deletes all data):
docker-compose down -v
```

### Reset Database

```bash
# Drop and recreate database
psql postgres
DROP DATABASE password_generator;
CREATE DATABASE password_generator;
\q

# Run migrations again
npm run migrate
```

### Clear Redis Cache

```bash
redis-cli FLUSHALL
```

### Rebuild Dependencies

```bash
# Clean install
rm -rf node_modules package-lock.json
npm install

# Rebuild native modules
npm rebuild
```

---

## Next Steps

Now that you have the application running, explore:

1. **User Guide** - docs/USER_GUIDE.md
   - Detailed feature documentation
   - Best practices for password generation
   - Compliance framework deep dives

2. **API Documentation** - http://localhost:3001/api-docs
   - Complete API reference
   - Authentication guide
   - Rate limiting details

3. **Development Guide** - docs/DEVELOPMENT.md
   - Code architecture
   - Contributing guidelines
   - Testing strategy

4. **Task List** - docs/tasks/tasks-0001-enterprise-password-generator.md
   - 156 tasks across 5 phases
   - Development roadmap
   - Sprint planning

5. **Runbook** - docs/RUNBOOK.md
   - Operations guide
   - Monitoring and alerts
   - Incident response

---

## Troubleshooting

### Issue: Frontend won't load

**Symptoms:** Browser shows "Cannot GET /" or connection refused

**Solutions:**
1. Verify Vite dev server is running: `ps aux | grep vite`
2. Check console for errors: `npm run dev:frontend`
3. Clear browser cache and hard reload (Cmd+Shift+R)
4. Try a different browser

### Issue: Backend API errors

**Symptoms:** 500 Internal Server Error or connection refused

**Solutions:**
1. Verify Express server is running: `ps aux | grep node`
2. Check backend logs: `npm run dev:backend`
3. Verify database connection: `psql -h localhost -U postgres -d password_generator`
4. Verify Redis connection: `redis-cli ping`
5. Check environment variables: `cat .env`

### Issue: Database migration fails

**Symptoms:** "relation does not exist" or "permission denied"

**Solutions:**
1. Verify PostgreSQL is running: `pg_isready`
2. Check database exists: `psql -l | grep password_generator`
3. Verify user permissions:
   ```bash
   psql postgres
   GRANT ALL PRIVILEGES ON DATABASE password_generator TO postgres;
   \q
   ```
4. Run migrations again: `npm run migrate`

### Issue: Tests failing

**Symptoms:** Test suites fail or timeout

**Solutions:**
1. Verify test database exists: `psql -l | grep password_generator_test`
2. Set test environment: `NODE_ENV=test npm test`
3. Clear test cache: `npm run test:clean`
4. Run tests individually: `npm test -- <test-file-name>`

### Issue: HIBP API rate limiting

**Symptoms:** 429 Too Many Requests from Have I Been Pwned

**Solutions:**
1. Get HIBP API key: https://haveibeenpwned.com/API/Key
2. Add to .env: `HIBP_API_KEY=your_key_here`
3. Restart backend server
4. Rate limit: 1 request/1.5 seconds (without key), 10 requests/second (with key)

---

## Getting Help

- **Documentation:** docs/ directory
- **API Docs:** http://localhost:3001/api-docs
- **GitHub Issues:** https://github.com/FutureTranz-Inc/q-ai-msp-password-generator/issues
- **Technical Support:** support@futuretranz.com
- **Security Issues:** security@futuretranz.com (do NOT create public issues)

---

**Congratulations! You have successfully set up the Q-AI-MSP Enterprise Password Generator.**

**Next:** Start development with Task 1.1 from docs/tasks/tasks-0001-enterprise-password-generator.md
