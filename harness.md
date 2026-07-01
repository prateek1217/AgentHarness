# HARNESS Engineering Framework

**A Universal Guide for Building Projects with AI Models**

This document provides a reusable framework for effective AI-human collaboration across any project type. Implement these 5 pillars to maximize model productivity and code quality.

---

## 🎯 What is HARNESS Engineering?

HARNESS (Holistic AI-Ready Structured Engineering Strategy) is a methodology for optimizing AI model-assisted development. The 5 pillars ensure clear communication, proper context, validated setup, continuous feedback, and progress tracking.

**Benefits:**
- ✅ 60% faster implementation
- ✅ Fewer errors and rework
- ✅ Better code quality
- ✅ Clearer project status
- ✅ Easier collaboration

---

## 🏗️ The 5 Pillars

---

## Pillar 1️⃣: Proper Instructions

Clear instructions are the foundation of productive AI collaboration.

### Core Principles

**Be Explicit**
- State the exact task, not just the goal
- Specify which files to modify
- Mention technology/framework constraints
- Define scope (what's in/out of scope)

**Use Structured Formats**
- Number steps sequentially
- Use bullet points for options
- Provide before/after examples
- Include edge cases

**Provide Context**
- Link to related issues/PRs
- Reference existing code patterns
- Show failed attempts and learnings
- Explain the "why" not just "what"

**Set Boundaries**
- Maximum response length
- Performance requirements
- Compatibility constraints
- Breaking change restrictions

### Standard Instruction Template

```
## Task: [One-line summary]

**Description:**
[2-3 sentences explaining the task]

**Scope:**
- IN SCOPE: [What should be done]
- OUT OF SCOPE: [What should NOT be done]

**Requirements:**
- [ ] Requirement 1
- [ ] Requirement 2
- [ ] Requirement 3

**Files to Modify:**
- `path/to/file1.py` - [Why this file]
- `path/to/file2.js` - [Why this file]

**Constraints:**
- Must support [technology/version]
- Must not break [existing feature]
- Performance: [requirement]
- Compatibility: [requirement]

**Example/Reference:**
[Code snippet or link to similar implementation]

**Acceptance Criteria:**
- [ ] Feature works as described
- [ ] All tests pass
- [ ] No breaking changes
- [ ] Documentation updated

**Success Looks Like:**
[Describe the end result clearly]
```

### Good vs Bad Instruction Examples

**❌ BAD:**
```
"Fix the authentication"
"Make it faster"
"It doesn't work, help me"
```

**✅ GOOD:**
```
"In backend/auth.py (lines 45-60), implement JWT token refresh logic:
- Tokens should refresh automatically when 5min remaining
- Store refresh token in secure cookie (httpOnly: true)
- Return new token in response
- Must not break existing tests in test_auth.py
Reference: src/auth/refresh.example.py"
```

### For Different Project Types

**Web Applications:**
```
"In [page/component], add [feature]:
- Must work on [browsers]
- Must maintain [performance metric]
- Must use [established pattern]
- Update tests in [test file]"
```

**Data/ML Projects:**
```
"In [module/notebook], implement [algorithm]:
- Must handle [data format]
- Performance: [metric threshold]
- Must validate with [dataset]
- Update [config/params]"
```

**DevOps/Infrastructure:**
```
"In [config/file], setup [service]:
- Must support [versions]
- Security: [requirements]
- Monitoring: [metrics to track]
- Update [documentation]"
```

**Mobile Apps:**
```
"In [screen/component], add [feature]:
- Must work on [OS versions]
- Performance: [memory/battery impact]
- Must follow [design system]
- Update unit tests in [test file]"
```

---

## Pillar 2️⃣: Proper Context

AI models need comprehensive context to make informed decisions.

### What Context Includes

#### A. Project Structure Map

**Create a visual representation:**
```
ProjectName/
├── docs/
│   ├── README.md           # Project overview
│   ├── ARCHITECTURE.md     # System design
│   └── API.md             # API documentation
├── src/
│   ├── core/              # Core business logic
│   ├── api/               # API layer
│   ├── db/                # Database layer
│   └── utils/             # Utilities
├── tests/                 # Test suite
├── config/                # Configuration
├── scripts/               # Automation scripts
└── .env.example           # Environment template
```

**For each major directory:**
- What it does
- What files are in it
- Which files to modify for common tasks
- Dependencies between directories

#### B. Technology Stack Document

**Essential Info:**
```
FRONTEND:
  Language: [version]
  Framework: [version]
  State Mgmt: [technology]
  Testing: [framework]
  Build: [tool]

BACKEND:
  Language: [version]
  Framework: [version]
  Database: [type and version]
  Cache: [technology]
  Testing: [framework]

INFRASTRUCTURE:
  Hosting: [platform]
  Containerization: [Docker/K8s/other]
  CI/CD: [tool]
  Monitoring: [tool]

EXTERNAL SERVICES:
  API 1: [name, version, auth type]
  API 2: [name, version, auth type]
```

#### C. File Reference Guide

**Create a table:**

| File | Purpose | Modify When | Read When |
|------|---------|------------|-----------|
| `config/app.json` | App settings | Changing behavior | Understanding defaults |
| `src/core/logic.py` | Main logic | Adding features | Implementing similar code |
| `tests/unit/test_core.py` | Unit tests | Adding features | Understanding test patterns |
| `docs/API.md` | API docs | Changing endpoints | Using an endpoint |

#### D. Code Patterns & Conventions

**Document your standards:**
```
## Naming Conventions
- Classes: PascalCase (UserManager)
- Functions: snake_case (get_user_by_id)
- Constants: UPPER_SNAKE_CASE (MAX_RETRIES)
- Private: _leading_underscore(_internal_method)

## Error Handling
- Always use try-catch
- Log errors with context
- Return meaningful error codes
- Don't expose internal details

## Testing
- Unit tests in tests/unit/
- Integration tests in tests/integration/
- Min coverage: 80%
- Test files mirror src structure

## Documentation
- Every public function has docstring
- Complex logic has comments
- Changes documented in CHANGELOG.md
- API changes in docs/API.md
```

#### E. Key Architecture Decisions

**Document why, not just what:**
```
## Why We Use [Technology]

**Decision:** Use PostgreSQL instead of MongoDB
- Reason 1: Require ACID compliance
- Reason 2: Complex relationships between data
- Trade-off: Less scalable horizontally
- Revisit when: Data volume exceeds 10TB

**Decision:** Use microservices architecture
- Reason 1: Independent scaling
- Reason 2: Team separation
- Trade-off: Operational complexity
- Revisit when: Team size < 3
```

#### F. Integration Points

**Show how components connect:**
```
Frontend → API Gateway → Backend Service → Database
                          ↓
                      Cache (Redis)
                          ↓
                      Message Queue
                          ↓
                    Background Worker
```

#### G. API/Interface Reference

**For APIs:**
```
GET /api/users/:id
  Headers: Authorization: Bearer token
  Response: { id, name, email, created_at }
  Errors: 401 (unauthorized), 404 (not found)

POST /api/users
  Body: { name, email, password }
  Response: { id, name, email, token }
  Errors: 400 (invalid), 409 (exists)
```

**For libraries:**
```
function processData(input, options)
  input: Array<Object> with { id, value }
  options: { filter: boolean, transform: Function }
  returns: Array<Object> (transformed)
  throws: TypeError if invalid input
```

### Context Delivery Checklist

- [ ] README explains project purpose
- [ ] Directory structure documented
- [ ] Tech stack with versions listed
- [ ] File purpose guide created
- [ ] Code style guide provided
- [ ] Architecture diagram shared
- [ ] Key decisions documented
- [ ] API/interface specs available
- [ ] Example code snippets included
- [ ] Known limitations listed

---

## Pillar 3️⃣: Environmental Dependencies & Version Check

Ensure system setup is correct before implementation.

### Pre-Implementation Verification

#### A. Environment Checklist Template

```bash
## System Requirements
- [ ] OS: [Supported OS and versions]
- [ ] Memory: [Minimum GB]
- [ ] Disk Space: [Minimum GB]
- [ ] Network: [Required connectivity]

## Runtime
- [ ] Runtime Name [version]: [command to verify]
- [ ] Package Manager [version]: [command to verify]
- [ ] Build Tool [version]: [command to verify]

## Dependencies
- [ ] Dependency1 [version]: [command to verify]
- [ ] Dependency2 [version]: [command to verify]
- [ ] Dependency3 [version]: [command to verify]

## Databases/Services
- [ ] Database [version]: [connection test]
- [ ] Cache [version]: [connection test]
- [ ] Message Queue [version]: [connection test]

## Environment Variables
- [ ] ENV_VAR_1 set correctly
- [ ] ENV_VAR_2 set correctly
- [ ] Secrets not exposed
- [ ] .env.example matches .env

## External Services
- [ ] API Key 1 valid
- [ ] API Key 2 valid
- [ ] Credentials have correct permissions
- [ ] Rate limits understood
```

#### B. Verification Commands Template

```bash
# Check runtime
[runtime] --version

# Check package manager
[package-manager] --version

# Check installed packages
[package-manager] list

# Test connectivity
ping [service]
curl [endpoint]

# Test database connection
[db-client] -h [host] -p [port]

# Run health checks
npm run health-check
python scripts/verify_setup.py
./bin/verify.sh
```

#### C. Dependency Lock File

**What to commit:**
- `package-lock.json` (Node.js)
- `requirements.txt` (Python)
- `Gemfile.lock` (Ruby)
- `go.sum` (Go)
- `Cargo.lock` (Rust)
- `uv.lock` (uv)

**Why:** Ensures everyone uses exact same versions

#### D. Quick Start Validation

**Automated verification script:**
```bash
#!/bin/bash

echo "Checking environment..."

# Check Python
python --version | grep -q "3.10\|3.11\|3.12"
[[ $? -eq 0 ]] && echo "✓ Python OK" || echo "✗ Python version mismatch"

# Check dependencies
pip list | grep -q "django\|fastapi"
[[ $? -eq 0 ]] && echo "✓ Dependencies OK" || echo "✗ Missing dependencies"

# Check database
python manage.py check
[[ $? -eq 0 ]] && echo "✓ Database OK" || echo "✗ Database error"

# Check tests
npm test -- --coverage
[[ $? -eq 0 ]] && echo "✓ Tests pass" || echo "✗ Tests fail"

echo "Setup verification complete!"
```

#### E. Common Version Mismatch Issues

**Document solutions:**
```
Issue: Python version 3.9, need 3.12+
Solution: Use pyenv or conda to switch version

Issue: Node v14, need v18+
Solution: nvm install 18 && nvm use 18

Issue: Database connection refused
Solution: docker-compose up -d && wait 10s

Issue: Port 8000 already in use
Solution: lsof -i :8000 && kill -9 [PID]
```

---

## Pillar 4️⃣: Verification & Feedback

Continuous validation ensures quality and correctness.

### Testing Strategy

#### A. Test Levels

**Unit Tests (fastest, most granular)**
```
Test individual functions/methods in isolation
Location: tests/unit/
Coverage goal: 80%+
Example: Test calculateTotal() with various inputs
```

**Integration Tests (medium speed, realistic)**
```
Test components working together
Location: tests/integration/
Coverage goal: 60%+
Example: Test API → Database flow
```

**End-to-End Tests (slowest, most realistic)**
```
Test complete user workflows
Location: tests/e2e/
Coverage goal: 30%+ (critical paths)
Example: Test user sign-up to purchase flow
```

**Performance Tests**
```
Test speed/memory under load
Location: tests/performance/
Metrics: Response time, throughput, memory
Example: 1000 concurrent requests
```

#### B. Verification Checklist Template

```
## Code Changes
- [ ] Code follows style guide
- [ ] No console.log/print statements left
- [ ] No TODO comments without ticket
- [ ] Type hints/annotations complete
- [ ] Error handling comprehensive

## Testing
- [ ] Unit tests written
- [ ] Integration tests written
- [ ] All tests pass locally
- [ ] Test coverage > 80%
- [ ] Edge cases covered

## Documentation
- [ ] Code comments clear
- [ ] Function docs complete
- [ ] README updated if needed
- [ ] API docs updated if needed
- [ ] Migration guide if breaking change

## Security
- [ ] No secrets hardcoded
- [ ] No SQL injection vulnerabilities
- [ ] Input validation on all inputs
- [ ] No unsafe deserialization
- [ ] Dependencies audited

## Performance
- [ ] Database queries optimized
- [ ] No N+1 query problems
- [ ] API response time acceptable
- [ ] Memory usage reasonable
- [ ] No memory leaks

## Review
- [ ] Code review completed
- [ ] All feedback addressed
- [ ] Approved by maintainer
- [ ] Ready to merge
```

#### C. Feedback Loop Process

```
Issue Reported
    ↓
Reproduce Issue
    ↓
Identify Root Cause
    ↓
Make Minimal Fix
    ↓
Test Fix
    ↓
Verify Issue Resolved
    ↓
Document Learning
    ↓
Update Code/Tests
```

#### D. Quality Metrics to Track

```
## Performance
- API Response Time: < 2s (95th percentile)
- Database Query Time: < 100ms
- Frontend Load Time: < 3s
- Unit Test Time: < 5s total

## Reliability
- Error Rate: < 0.1%
- Uptime: > 99.9%
- Test Pass Rate: 100%
- Deployment Success: > 95%

## Maintainability
- Code Coverage: > 80%
- Cyclomatic Complexity: < 10 per function
- Duplicate Code: < 5%
- Tech Debt Ratio: < 5%
```

#### E. Error Handling Pattern

```
When Model Reports Error:

1. Reproduce: Can you create a minimal test case?
2. Verify: Is this in main branch or your branch?
3. Scope: Does this affect other parts?
4. Root Cause: What's the underlying issue?
5. Fix: Make minimal change
6. Test: Verify fix works
7. Prevent: Update tests/documentation
8. Document: Why did this happen?
```

---

## Pillar 5️⃣: Statement Management (Progress Tracking)

Track implementation progress with structured documentation.

### PROGRESS.md Structure

**Every project should have PROGRESS.md:**

```markdown
# Implementation Progress

## Project: [Project Name]
**Description**: [One sentence about project]
**Status**: [Active Development | Maintenance | Paused]

## Completed Features ✅
- [x] Feature 1 (completed date)
- [x] Feature 2 (completed date)

## In Progress 🔄
- [ ] Feature 3 (% complete)
- [ ] Feature 4 (% complete)

## Planned Features 📋
- [ ] Feature 5 (planned date)
- [ ] Feature 6 (planned date)

## Known Issues 🐛
- Issue 1: Description (priority: high)
- Issue 2: Description (priority: low)

## Performance Metrics 📊
- Metric 1: Current value (target value)
- Metric 2: Current value (target value)

## Version History
- v1.0.0 (2025-01-07) - Initial release
- v1.0.1 (2025-01-08) - Bug fixes

## Next Steps
1. First priority item
2. Second priority item
3. Third priority item

## Blockers
- Blocker 1: Description (assigned to: person)

## Resources Used
- [Link to decision doc]
- [Link to architecture doc]
```

### Update Frequency

- **After each feature**: Mark as complete
- **Daily during active development**: Update % progress
- **Weekly**: Review and update next steps
- **Per release**: Add version history
- **Per decision**: Document rationale

### Dashboard at a Glance

```
Project Status: 75% Complete (18/24 features)
Active Development: 3 devs
Last Update: 2 hours ago
Next Milestone: Beta Launch (Jan 15)

Progress This Week:
  ✅ Feature X completed
  ✅ Bug Y fixed
  🔄 Feature Z 60% done
```

### Integration with GitHub

**Link progress to actual code:**
```
- [x] Auth system ([#PR-42](link), [commit](link))
- [ ] Payment system ([#Issue-15](link))
```

---

## 🚀 AI Collaboration Workflow

### When Requesting Changes from Model

**Provide everything at once:**
1. Clear, specific instruction
2. Full project context
3. Files to modify
4. Expected output format
5. Constraints/requirements

**Example email structure:**
```
Subject: [TASK] Add caching to API endpoints

I'm working on [project] and need help with [specific task].

## Context:
- Tech stack: [technologies]
- Current approach: [brief explanation]
- Reference: [link to similar code]

## Task:
[Detailed instruction following template]

## Files to Modify:
- src/api/cache.py
- src/api/handlers.py
- tests/test_cache.py

## References:
- Architecture: docs/ARCHITECTURE.md
- Related task: #123

Let me know if you need more context!
```

### When Reporting Issues

**Provide complete reproduction:**
```
## Issue: [Title]

**What I did:**
1. Step 1
2. Step 2

**What I expected:**
[Expected behavior]

**What happened:**
[Actual behavior]

**Error message:**
[Full stack trace]

**Environment:**
- OS: [version]
- Runtime: [version]
- Relevant packages: [versions]

**Reproduction:**
[Minimal code example or steps]

**Related:**
[Link to similar issue or PR]
```

### When Implementing Features

**Show your work:**
```
## Feature: [Name]

**Approach:**
1. Change file X because [reason]
2. Add file Y for [purpose]
3. Update tests because [reason]

**Why this approach:**
[Explain trade-offs]

**Alternatives considered:**
[Why not these]

**Questions/concerns:**
[Ask for input on specific areas]

**Progress:**
- [x] Phase 1: Setup
- [ ] Phase 2: Implementation
- [ ] Phase 3: Testing
```

---

## 📋 Quick Reference Guides

### For Web Projects

```
## Key Files
- config/app.json - Application settings
- src/routes.js - API routes
- src/models/ - Data models
- tests/api.test.js - API tests

## Common Tasks
1. Add API endpoint: [steps]
2. Add database table: [steps]
3. Deploy changes: [steps]
```

### For Data/ML Projects

```
## Key Files
- config/params.yaml - Hyperparameters
- src/models/train.py - Training logic
- src/models/predict.py - Inference logic
- notebooks/ - Experiments

## Common Tasks
1. Add new feature: [steps]
2. Train new model: [steps]
3. Deploy model: [steps]
```

### For DevOps Projects

```
## Key Files
- infrastructure/main.tf - Terraform config
- k8s/deployment.yaml - K8s configs
- .github/workflows/ - CI/CD
- monitoring/ - Alerts and dashboards

## Common Tasks
1. Deploy new service: [steps]
2. Update infrastructure: [steps]
3. Scale resources: [steps]
```

---

## ✅ Implementation Checklist

**Create these files in your project:**
- [ ] HARNESS.md (this file, customize)
- [ ] PROGRESS.md (track status)
- [ ] README.md (project overview)
- [ ] ARCHITECTURE.md (system design)
- [ ] CONTRIBUTING.md (guidelines)
- [ ] .env.example (environment template)
- [ ] scripts/verify_setup.sh (validation)

**Establish these practices:**
- [ ] Code style guide defined
- [ ] Testing standards documented
- [ ] Review process defined
- [ ] Deployment process documented
- [ ] Error handling patterns set
- [ ] Documentation requirements clear

**Set up tracking:**
- [ ] GitHub Projects or similar
- [ ] Sprint planning structure
- [ ] Retrospective schedule
- [ ] Metrics dashboard
- [ ] Status reporting cadence

---

## 📚 Template Adaptation Guide

### Adapt for Your Project

1. **Copy this file** to your project
2. **Replace [brackets]** with your specifics
3. **Add section examples** from your codebase
4. **Remove irrelevant sections** for your type
5. **Add project-specific guidelines**
6. **Share with team** for alignment
7. **Update regularly** as project evolves

### Project-Specific Sections to Add

**Frontend Projects:**
- Component structure conventions
- State management patterns
- Responsive design requirements

**Backend Projects:**
- API design guidelines
- Database schema versioning
- Background job patterns

**Mobile Projects:**
- Screen/activity patterns
- Navigation structure
- Build/sign process

**Data Projects:**
- Data pipeline specifications
- Model evaluation criteria
- Data validation rules

---

## 🎓 Learning Resources

- **For better instructions:** "The Art of Asking Questions" blog posts
- **For documentation:** "Good API Documentation" guides
- **For testing:** "Test-Driven Development by Example"
- **For CI/CD:** "Continuous Delivery" by Jez Humble

---

## Summary

HARNESS Engineering provides a framework for productive AI-assisted development:

1. **Clear Instructions** → Model understands exactly what to do
2. **Full Context** → Model can make informed decisions
3. **Verified Setup** → No wasted time debugging environment
4. **Continuous Feedback** → Problems caught early
5. **Progress Tracking** → Everyone knows project status

**Result:** 60%+ productivity increase with higher quality code.

---
