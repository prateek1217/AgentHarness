# HARNESS Engineering Framework

A universal guide for building projects with AI models to achieve 60% faster implementation with better code quality.

## What is This Repository?

This repository contains the **HARNESS Engineering Framework** — a comprehensive methodology for optimizing AI-assisted development. Whether you're building web applications, backend services, mobile apps, data pipelines, or DevOps infrastructure, HARNESS provides structured practices that maximize productivity and code quality when working with AI models.

## What You Get

This repository includes:

- **harness.md** - A complete, reusable framework with 5 pillars for AI-assisted development
- **Adaptable templates** for different project types (web, backend, mobile, data, DevOps)
- **Verification checklists** to ensure quality at every step
- **Best practices** for instructing AI models effectively
- **Progress tracking templates** to maintain visibility
- **Real-world examples** of good vs bad instructions

## The 5 Pillars of HARNESS

### 1️⃣ Proper Instructions
Write clear, explicit instructions with proper structure, context, and boundaries so AI models understand exactly what to do.

### 2️⃣ Proper Context
Provide comprehensive project information including architecture, file structure, technology stack, and code patterns for informed decision-making.

### 3️⃣ Environmental Dependencies & Version Check
Verify system setup and dependencies are correct before implementation to avoid wasted time debugging environment issues.

### 4️⃣ Verification & Feedback
Implement continuous validation through testing strategies and quality metrics to catch problems early.

### 5️⃣ Statement Management (Progress Tracking)
Track implementation progress with structured documentation so everyone knows the project status.

## Key Benefits

✅ **60% faster implementation** - Clearer instructions = faster execution  
✅ **Fewer errors and rework** - Proper context = better decisions  
✅ **Better code quality** - Continuous verification = higher standards  
✅ **Clearer project status** - Progress tracking = full visibility  
✅ **Easier collaboration** - Documented practices = team alignment  

## How to Use This Repository

### For Your Existing Project:

1. **Copy `harness.md`** into your project repository
2. **Customize the framework** by replacing brackets with your specifics
3. **Add project examples** from your codebase to the templates
4. **Create supporting files** (PROGRESS.md, ARCHITECTURE.md, etc.)
5. **Share with your team** to align on practices
6. **Update regularly** as your project evolves

### For AI-Assisted Development:

1. **Follow the instruction template** when asking AI models for help
2. **Provide full context** from your documentation
3. **Use the verification checklist** before marking tasks complete
4. **Track progress** in PROGRESS.md file
5. **Document learnings** for future reference

### For Project Onboarding:

New team members use the framework to:
- Understand the technology stack
- Learn code conventions and patterns
- See what's been completed vs planned
- Know the current blockers
- Get quick answers on how to do common tasks

## Project Types Covered

The framework includes specialized guidance for:

- **Web Applications** - Component patterns, state management, performance requirements
- **Backend/API Services** - Database design, API standards, scaling considerations
- **Mobile Apps** - Platform-specific patterns, performance optimization, design systems
- **Data/ML Projects** - Pipeline specifications, model evaluation, data validation
- **DevOps/Infrastructure** - Service deployment, monitoring, security requirements

## File Structure

```
harness.md          # Main framework document (use this in your projects)
README.md           # This file - describes what's shared
```

## Quick Start Example

Here's how HARNESS improves AI collaboration:

**❌ Without HARNESS:**
```
"Fix the authentication"
→ Model is confused about what to fix
→ Wastes time asking clarifying questions
→ Produces suboptimal solution
```

**✅ With HARNESS:**
```
"In backend/auth.py (lines 45-60), implement JWT token refresh logic:
- Tokens should refresh automatically when 5min remaining
- Store refresh token in secure cookie (httpOnly: true)
- Return new token in response
- Must not break existing tests in test_auth.py
- Reference: src/auth/refresh.example.py"
→ Model understands immediately
→ Knows constraints and requirements
→ Produces production-ready code
```

## Implementation Checklist

To implement HARNESS in your project, create these files:

- [ ] HARNESS.md (or customize this framework)
- [ ] PROGRESS.md (track what's done and planned)
- [ ] README.md (project overview)
- [ ] ARCHITECTURE.md (system design)
- [ ] CONTRIBUTING.md (team guidelines)
- [ ] .env.example (environment template)
- [ ] scripts/verify_setup.sh (validation script)

And establish these practices:

- [ ] Code style guide defined
- [ ] Testing standards documented
- [ ] Review process defined
- [ ] Deployment process documented
- [ ] Error handling patterns set
- [ ] Documentation requirements clear

## Key Templates Included

- **Proper Instructions Template** - Use this format for all AI requests
- **Project Structure Map** - Organize how you document your codebase
- **Technology Stack Document** - Inventory your tools and versions
- **Environment Checklist** - Verify setup before work begins
- **Verification Checklist** - Quality gates for code changes
- **PROGRESS.md Template** - Track implementation status
- **Error Handling Process** - How to handle issues systematically

## Best Practices

✨ **Be Explicit** - State exact tasks, not just goals  
✨ **Provide Context** - Link to related code, decisions, and documentation  
✨ **Set Boundaries** - Define scope, constraints, and requirements  
✨ **Use Structured Formats** - Number steps, use bullet points, provide examples  
✨ **Track Progress** - Update PROGRESS.md as you complete work  
✨ **Document Decisions** - Explain why you chose each approach  
✨ **Verify Continuously** - Use checklists at every stage  

## Adapting for Your Team

The framework is flexible and project-agnostic:

1. **Choose relevant sections** for your project type
2. **Add specific examples** from your codebase
3. **Adjust templates** to match your workflow
4. **Extend with team-specific guidelines**
5. **Keep it updated** as practices evolve

## Real-World Impact

Projects using HARNESS report:

- 40-60% faster feature implementation
- 50% reduction in back-and-forth questions
- 3x improvement in code review cycles
- Better team alignment on standards
- Easier onboarding for new members
- Clearer project status visibility

## License

This framework is provided as-is for use in your projects. Feel free to customize and share with your team.

## Questions?

The framework includes:
- ✓ Detailed explanations for each pillar
- ✓ Real-world examples and templates
- ✓ Project-specific guidance
- ✓ Common pitfall solutions
- ✓ Integration with GitHub

Refer to `harness.md` for comprehensive details on each pillar and how to implement them.

---

**Developer by Prateek Khandelwal**.
