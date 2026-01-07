# 🏗️ PHASE 03: ARCHITECTURE

> **Design the system before building it. The right architecture makes everything easier.**

---

## 🎯 PURPOSE

Make critical technology and structure decisions:
- Choose the optimal tech stack for THIS project
- Design system architecture
- Define data models and relationships
- Plan for scalability, security, and performance
- Create Architecture Decision Records (ADRs)

**Time Investment**: 2-4 hours
**Skip Risk**: Rewrites, scaling failures, security vulnerabilities

---

## 📥 INPUTS REQUIRED

1. Requirements Document (from Phase 02)
2. Non-Functional Requirements
3. User Stories with acceptance criteria

---

## 📤 EXPECTED OUTPUTS

1. **Architecture Document** (`projects/[name]/docs/ARCHITECTURE.md`)
   - System overview
   - Tech stack with justification
   - Component diagram
   - Data model

2. **Tech Stack Decision** (logged in DECISION_LOG.md)
   - Frontend framework
   - Backend framework/language
   - Database
   - Infrastructure/hosting
   - Key libraries

3. **Data Model** (`projects/[name]/docs/DATA_MODEL.md`)
   - Entity definitions
   - Relationships
   - Initial schema

4. **Updated State Files**
   - ACTIVE_PROJECT.md
   - DECISION_LOG.md with all tech decisions

---

## 🔄 PROCESS

### Step 1: Gather Requirements Context

Review these from Phase 02:
```markdown
## CONTEXT FOR ARCHITECTURE DECISIONS

### Scale Requirements
- Expected users: [from requirements]
- Expected data volume: [estimate]
- Concurrent users: [estimate]
- Growth trajectory: [stable/growing/explosive]

### Feature Requirements
- Real-time needed? [Yes/No - affects tech choice]
- File uploads? [Yes/No - affects storage choice]
- AI/ML features? [Yes/No - affects language choice]
- Complex queries? [Yes/No - affects database choice]
- Offline support? [Yes/No - affects frontend choice]

### Team/Constraints
- Developer expertise: [List known technologies]
- Timeline: [How fast?]
- Budget for infra: [Range]
- Existing systems to integrate: [List]
```

### Step 2: Tech Stack Selection

**DO NOT default to a stack. Analyze requirements first.**

#### Frontend Framework Decision Tree

```markdown
## FRONTEND FRAMEWORK SELECTION

### If you need:
- SEO + Server rendering + Easy deployment → Next.js
- Pure SPA, no SEO needs → Vite + React or Vue
- Maximum performance → Svelte/SvelteKit
- Enterprise + Strong typing → Angular
- Rapid prototyping → Next.js or Remix

### Default Recommendation Tiers:

#### Tier 1: Next.js (App Router)
Best for: Most web apps, SaaS, content sites
Pros: SSR, great DX, Vercel deployment, huge ecosystem
Cons: Vendor lock-in concerns, App Router learning curve

#### Tier 2: Remix
Best for: Full-stack apps with complex data loading
Pros: Progressive enhancement, great forms, nested routing
Cons: Smaller ecosystem than Next.js

#### Tier 3: Vite + React
Best for: SPAs, dashboards, internal tools
Pros: Fast dev server, simple, flexible
Cons: Need to set up SSR manually if needed

#### Tier 4: SvelteKit
Best for: Performance-critical apps
Pros: Best performance, simple syntax
Cons: Smaller ecosystem, fewer developers

### Recommendation Format:
**Frontend: [Choice]**
**Why**: [2-3 sentences]
**Alternatives considered**: [What else and why not]
```

#### Backend Framework Decision Tree

```markdown
## BACKEND FRAMEWORK SELECTION

### If you need:
- TypeScript everywhere → NestJS or Next.js API Routes
- Python ecosystem (AI/ML) → FastAPI or Django
- Maximum performance → Go (Gin/Fiber) or Rust
- Rapid development → Express.js or FastAPI
- Enterprise features → NestJS or Django

### Default Recommendation Tiers:

#### Tier 1: Next.js API Routes (if frontend is Next.js)
Best for: Simple to medium APIs, same-repo deployment
Pros: One codebase, shared types, simple deployment
Cons: Limited for complex backends, monolith

#### Tier 2: FastAPI (Python)
Best for: AI/ML apps, data processing, speed + Python
Pros: Async, auto docs, type hints, Python ecosystem
Cons: Different language from frontend

#### Tier 3: NestJS (TypeScript)
Best for: Enterprise apps, complex domain logic
Pros: Strong architecture, decorators, TypeScript
Cons: More boilerplate, steeper learning curve

#### Tier 4: Express.js + TypeScript
Best for: Simple APIs, microservices
Pros: Flexible, huge ecosystem, simple
Cons: No structure (you define it), less opinionated

### Recommendation Format:
**Backend: [Choice]**
**Why**: [2-3 sentences]
**Alternatives considered**: [What else and why not]
```

#### Database Decision Tree

```markdown
## DATABASE SELECTION

### If you need:
- Relational data + Complex queries → PostgreSQL
- Document storage + Flexibility → MongoDB
- Simple relational → MySQL
- Serverless/Edge → PlanetScale, Neon, or Turso
- Maximum performance → Redis (cache) + PostgreSQL
- Full-text search → PostgreSQL (FTS) or Elasticsearch

### Default Recommendation: PostgreSQL
Why: Reliable, feature-rich, JSON support, excellent tooling

### ORM/Query Builder Selection:
- Prisma: Best DX, type safety, migrations
- Drizzle: Lighter weight, SQL-like syntax
- TypeORM: Enterprise patterns, decorators
- Kysely: Type-safe query builder
- Raw SQL: Maximum control (rare cases)

### Recommendation Format:
**Database: [Choice]**
**ORM: [Choice]**
**Why**: [2-3 sentences]
**Scaling strategy**: [Read replicas, sharding, etc.]
```

#### Infrastructure Decision Tree

```markdown
## INFRASTRUCTURE SELECTION

### Budget Tiers:

#### Free/Minimal ($0-20/month)
- Vercel (frontend + API routes)
- Railway or Render (backend)
- Supabase or Neon (database)
- Cloudflare (CDN, DNS)

#### Startup ($20-200/month)
- Vercel or Netlify (frontend)
- Railway, Render, or Fly.io (backend)
- Supabase, PlanetScale, or AWS RDS (database)
- Upstash Redis (caching)

#### Scale ($200+/month)
- AWS / GCP / Azure
- Kubernetes or ECS
- Managed PostgreSQL (RDS/Cloud SQL)
- ElastiCache or Upstash Redis
- CloudFront or Cloudflare CDN

### Recommendation Format:
**Hosting**: [Choice]
**Why**: [2-3 sentences]
**Estimated cost**: [Range]
**Scaling path**: [How to scale when needed]
```

### Step 3: System Architecture Design

```markdown
## SYSTEM ARCHITECTURE

### Architecture Pattern Selection

#### Monolith (Recommended for MVP)
Single deployable unit containing all code.
Best for: Small teams, MVPs, simple domains
Pros: Simple deployment, easy debugging, low overhead
Cons: Can become unwieldy, single point of failure

#### Modular Monolith
Monolith with clear module boundaries.
Best for: Medium complexity, future microservices path
Pros: Organized, can extract services later
Cons: Discipline required to maintain boundaries

#### Microservices
Separate deployable services.
Best for: Large teams, complex domains, different scaling needs
Pros: Independent deployment, scaling, technology choice
Cons: Operational complexity, network overhead

### RECOMMENDATION: Start Monolith → Extract if Needed

## Architecture Diagram
Create a diagram showing:
- User (Browser/Mobile)
- Frontend (Next.js/etc.)
- Backend (API)
- Database
- Cache (if applicable)
- External Services (Auth, Email, etc.)
- CDN (if applicable)

Example:
```
┌──────────────┐     ┌──────────────┐     ┌──────────────┐
│   Browser    │────▶│    CDN       │────▶│   Frontend   │
└──────────────┘     └──────────────┘     │   (Next.js)  │
                                          └──────┬───────┘
                                                 │
                                          ┌──────▼───────┐
                                          │   Backend    │
                                          │   (API)      │
                                          └──────┬───────┘
                                                 │
                     ┌───────────────────────────┼───────────────────────────┐
                     │                           │                           │
              ┌──────▼───────┐           ┌──────▼───────┐           ┌───────▼──────┐
              │   Database   │           │    Cache     │           │   External   │
              │  (PostgreSQL)│           │   (Redis)    │           │   Services   │
              └──────────────┘           └──────────────┘           └──────────────┘
```

### Step 4: Data Model Design

```markdown
## DATA MODEL

### Entities
List all data entities from requirements:
- User
- [Entity 2]
- [Entity 3]
- ...

### Entity Details

#### User
| Field | Type | Constraints | Notes |
|-------|------|-------------|-------|
| id | UUID | PK | |
| email | String | Unique, Not Null | Validated format |
| passwordHash | String | Not Null | Argon2id hashed |
| name | String | Not Null | |
| createdAt | DateTime | Not Null | Auto-set |
| updatedAt | DateTime | Not Null | Auto-update |

#### [Entity 2]
[Same format]

### Relationships
```
User ───< Team (one-to-many through membership)
Team ───< Project (one-to-many)
Project ───< Task (one-to-many)
User ───< Task (one-to-many, assigned)
```

### Indexes (Initial)
- User: email (unique)
- [Entity]: [field] ([reason])

### Seed Data Requirements
- Admin user for testing
- Sample data for development
```

### Step 5: API Architecture

```markdown
## API ARCHITECTURE

### API Style
- [ ] REST (default for most apps)
- [ ] GraphQL (complex data relationships, mobile apps)
- [ ] tRPC (TypeScript end-to-end, same repo)

### Authentication Strategy
Recommendation with reasoning.

Options:
1. JWT + Refresh Token (stateless, scalable)
2. Session-based (simpler, server-side state)
3. OAuth only (third-party auth)

### Authorization Strategy
- Role-Based Access Control (RBAC)
- Resource ownership checks
- Permission levels

### API Versioning
- URL versioning: /api/v1/...
- Header versioning: Accept-Version: v1

### Rate Limiting
- Per-user: X requests/hour
- Per-IP: Y requests/hour
```

### Step 6: Security Architecture

```markdown
## SECURITY ARCHITECTURE

### Authentication
- Method: [JWT/Session/OAuth]
- Token storage: [HttpOnly Cookie/localStorage]
- Token lifetime: [Access: 15min, Refresh: 7days]

### Secrets Management
- All secrets in environment variables
- Never in code or version control
- Use: [.env.local for dev, platform secrets for prod]

### Data Protection
- Encryption at rest: [Database-level]
- Encryption in transit: [TLS 1.3]
- PII handling: [What data, how protected]

### Security Headers
- CORS policy
- CSP policy
- HSTS
- X-Frame-Options

### Dependency Security
- Automated scanning: [Dependabot/Snyk]
- Update schedule
```

### Step 7: Create Architecture Document

```markdown
# Architecture Document: [Project Name]

## Overview
[2-3 paragraph summary of architecture]

## Tech Stack
| Layer | Technology | Version | Justification |
|-------|------------|---------|---------------|
| Frontend | Next.js | 14.x | [Why] |
| Backend | [Choice] | [Ver] | [Why] |
| Database | PostgreSQL | 15+ | [Why] |
| ORM | Prisma | 5.x | [Why] |
| Cache | Redis | 7.x | [Why] |
| Hosting | Vercel + Railway | - | [Why] |

## Architecture Diagram
[Include diagram from Step 3]

## Data Model
[Include from Step 4 or reference DATA_MODEL.md]

## API Design
[Include from Step 5]

## Security
[Include from Step 6]

## Folder Structure
```
project/
├── src/
│   ├── app/              # Next.js pages (if Next.js)
│   ├── components/       # React components
│   │   ├── ui/          # Base UI components
│   │   └── features/    # Feature components
│   ├── lib/             # Utilities, helpers
│   ├── hooks/           # Custom React hooks
│   ├── services/        # API clients, external services
│   ├── types/           # TypeScript types
│   └── styles/          # Global styles
├── prisma/              # Database schema, migrations
├── public/              # Static assets
├── tests/               # Test files
└── docs/                # Documentation
```

## Development Workflow
- Local dev: [Instructions]
- Testing: [Strategy]
- Deployment: [Process]

## Future Considerations
- Scaling strategy
- Potential service extraction
- Technology upgrades planned

## Decision Log References
- Decision #[X]: [Tech stack choice]
- Decision #[Y]: [Architecture pattern]
- Decision #[Z]: [Database choice]
```

---

## ✅ QUALITY GATE

Before proceeding to Phase 04, verify:

- [ ] Tech stack selected with justification
- [ ] All tech decisions logged in DECISION_LOG.md
- [ ] System architecture diagram created
- [ ] Data model defined with all entities
- [ ] Relationships and indexes planned
- [ ] API architecture defined
- [ ] Security architecture defined
- [ ] Folder structure defined
- [ ] Architecture document created and saved
- [ ] User has approved tech stack
- [ ] ACTIVE_PROJECT.md updated
- [ ] Git commit made

---

## 📚 KNOWLEDGE REFERENCES

- `.harness/knowledge/BACKEND_MASTERY.md` - API patterns, auth
- `.harness/knowledge/DATABASE_MASTERY.md` - Schema design
- `.harness/knowledge/SECURITY_MASTERY.md` - Security patterns
- `.harness/knowledge/DEVOPS_MASTERY.md` - Infrastructure options

---

## ⚠️ COMMON MISTAKES

### Mistake 1: Over-Engineering
Don't build for 1M users when you have 100.
Start simple, scale when needed.

### Mistake 2: Resume-Driven Development
Don't choose tech because it's trendy.
Choose what's right for THIS project.

### Mistake 3: Ignoring Team Expertise
The best tech is what your team can execute well.
Factor in learning curve.

### Mistake 4: Premature Microservices
Almost always start with monolith.
Extract services when you have clear reasons.

### Mistake 5: Underestimating Security
Security is not a feature—it's a requirement.
Design it in from the start.

### Mistake 6: No Data Model
"We'll figure out the database later."
No. Model the data now.

---

## 💡 TIPS

### Tip 1: Boring Technology
Choose proven, boring technology over cutting-edge.
Excitement is for product features, not infrastructure.

### Tip 2: Document Trade-offs
Every decision has trade-offs. Document them.
"We chose X, accepting trade-off Y, because Z."

### Tip 3: Think in Layers
Separate: Presentation, Business Logic, Data.
Makes testing and changes easier.

### Tip 4: Plan for Failure
What happens when the database is down?
When an external API fails? Design for it.

### Tip 5: Start with User Flows
Architecture should support user flows, not the other way around.
If architecture makes a key flow hard, rethink it.

---

**Phase Complete? Update ACTIVE_PROJECT.md and proceed to Phase 04: UX Design.**
