# Building an AI agent harness for production-grade full-stack development

**Created:** 1/7/2026 16:41:05  
**Updated:** 1/7/2026 17:49:54  
**Exported:** 1/7/2026 19:37:33  
**Link:** [https://claude.ai/chat/4fdba6d6-f980-479a-a03c-622b4146ee27](https://claude.ai/chat/4fdba6d6-f980-479a-a03c-622b4146ee27)  

## Prompt:
1/7/2026, 4:41:08 PM

Hey claude I have built many full stack applications and after doing that with AI I have realised that AI can give you insane output but you just need to have domain knowledge and instruct it in such a way to build it so basically the output is same as your knowledge and your ability to explain it, plan, fix the errors so right now what I want to do is after bouncing back with so many errors I have built two complex full stack application but after reading about antropic agent harness which can build full stack applications end to end I want to build such a harness that I can use with antigravity google agentic ide so this is my goal I my aim is that any ai can give you basic frontend shit but you have to give very very good instructions to get the best color theme, micro interactions, elements, functionality, best design choices, orientations and all the important hings like responsisvenes, how to structure the state etc, how to make such that api integration becomes easy, make it scalable, optimization etc most importantly for frontend, there similar for backend that I want it have scalable, good and proper code, good folder structure, security, authentication, rate limiting, error handling, best database design, database optimizations, query optimizations, decision choices, designing of system, observability,caching. Ratelimiting etc I am not able to tell all those but I want you search and find all the things that should be present in the full stack web application to make it really production level code, ready to deploy, containerisation, migrations etc and all the best things so basically I want a professional software engineers team and it should have an entire sslc team of 100s of engineers I think you know sslc so basically if not search for sslc and need to have all those sdlc teams should work but here they ai agents will become sdlc and now your role is to figure out effectively orchestrated those agent and one with the best knowledge should orchestrated all the agents and each one should be able discuss with each other and can even ask me for feedback so basically what I want is that I will give some ideas or should validate, design features, ask me questions, analyze market for, and everything like sdlc teams and give beat output with everything tested 
I want to make such harness help me do it so basically it should give production ready, scalable and perfect code, I should not go back and forth to fix the errors 
But rhai is very very important most of the time ai will give bad ui/ux I don't know how you do it I want the best output for this no need to consider tokens 
You mention explicitly and force the agents that tokens are not the issue you can use any number of tokens but priority is very very good output and perfect code and you can even break a task into parts of needed but no compromise in quality should look like it is shipped by group of engineers and also keep a log of progress and make a proper comoit messages and push to GitHub



## Response:
1/7/2026, 4:41:34 PM

I'll help you build a comprehensive AI agent harness for production-grade full-stack development. Let me first search for best practices and then create the system.

````plaintext
Web Search: SDLC software development life cycle teams roles
````

> **SDLC Roles and Responsibilities: The Complete Guide** [djangostars.com](https://djangostars.com/blog/roles-in-the-sdlc/)
>
> **SDLC Success Strategies: Establishing SLAs and Team Roles** [ubiminds.com](https://ubiminds.com/en-us/key-development-team-roles-sdlc/)
>
> **Software Development Life Cycle: Team Roles and Responsibilities** [scand.com](https://scand.com/company/blog/main-roles-and-responsibilities-in-the-software-development-cycle/)
>
> **Software Development Life Cycle (SDLC): Process Steps, Team Roles, and Common & Alternative Models | by Dilan Örtülü | Medium** [medium.com](https://medium.com/@dilaleynartl/software-development-life-cycle-sdlc-process-steps-team-roles-and-common-alternative-models-e53740c66ab4)
>
> **Software Development Life Cycle (SDLC) Explained | Comidor** [comidor.com](https://www.comidor.com/knowledge-base/low-code-platform/software-development-life-cycle/)
>
> **Software Development Life Cycle (SDLC) - GeeksforGeeks** [geeksforgeeks.org](https://www.geeksforgeeks.org/software-engineering/software-development-life-cycle-sdlc/)
>
> **Software Development Lifecycle (SDLC): Definition, Examples, and Applications | LaunchNotes** [launchnotes.com](https://www.launchnotes.com/glossary/software-development-lifecycle-sdlc-in-product-management-and-operations)
>
> **What Is The SDLC Life Cycle and Who Is Involved?** [computercareers.org](https://www.computercareers.org/what-is-the-sdlc-life-cycle-and-who-is-involved/)
>
> **Software Development Life Cycle (SDLC)** [vitelco.com](https://vitelco.com/vitelco-blog/software-development-life-cycle-sdlc)
>
> **What is SDLC? - Software Development Lifecycle Explained - AWS** [amazon.com](https://aws.amazon.com/what-is/sdlc/)
>
````plaintext
Web Search: production ready full stack application best practices frontend backend
````

> **How to Build Production-Ready Full Stack Apps with the MERN Stack** [freecodecamp.org](https://www.freecodecamp.org/news/how-to-build-production-ready-full-stack-apps-with-the-mern-stack/)
>
> **How to setup a Full Stack project with Example - DEV Community** [dev.to](https://dev.to/shanu001x/how-to-setup-full-stack-project-for-production-in-nodejs-environment-2d7l)
>
> **Frontend vs Backend Development: What Comes First When Building a Web App? - XB Software** [xbsoftware.com](https://xbsoftware.com/blog/front-end-or-back-end-development/)
>
> **10 Best Full Stack Frameworks for 2026: Guide for Beginners - Metana** [metana.io](https://metana.io/blog/10-best-full-stack-frameworks-guide-for-beginners/)
>
> **Best Practices in Fullstack Development: Bridging Frontend and Backend | by Freddy D. Alvarez | Medium** [medium.com](https://medium.com/@falvarezpinto/best-practices-in-fullstack-development-bridging-frontend-and-backend-d0bfc28b978c)
>
> **Mastering Fullstack Development: Learn How to Build Modern Web Apps - Thinkster** [thinkster.io](https://thinkster.io/tutorials/fullstack)
>
> **Part 1: From 0 to 1 — Creating a Full-Stack Web Application Platform from Scratch and Operating it for (almost) Free | by Isaac Adams | Medium** [medium.com](https://medium.com/@isaac.adams/part-1-from-0-to-1-creating-a-full-stack-web-application-platform-from-scratch-and-operating-it-cd56ed8c2b0a)
>
> **Full-Stack Development Evolution: Trends and Best Practices** [slaknoah.com](https://www.slaknoah.com/blog/full-stack-development-evolution-trends-and-best-practices)
>
> **Do you build the front-end or back-end first in full-stack development? - Codemzy's Blog** [codemzy.com](https://www.codemzy.com/blog/build-front-end-or-back-end-first)
>
> **From Frontend to Backend: Full Stack Development Best Practices | by Vignesh Selvaraju | Medium** [medium.com](https://medium.com/@vigneshselvaraju1999/from-frontend-to-backend-full-stack-development-best-practices-2f07ce3e6d35)
>
````plaintext
Web Search: UI UX design best practices micro interactions modern web design 2025
````

> **Micro Interactions 2025: Best Practices to Elevate User Experience** [stan.vision](https://www.stan.vision/journal/micro-interactions-2025-in-web-design)
>
> **10 Best Microinteraction Examples to Improve UX in 2025** [designstudiouiux.com](https://www.designstudiouiux.com/blog/micro-interactions-examples/)
>
> **Web App UI/UX Best Practices in 2025 | Cygnis** [cygnis.co](https://cygnis.co/blog/web-app-ui-ux-best-practices-2025/)
>
> **UX Design Trends 2025 & UI Innovations: The Future of UX | FullStack Blog** [fullstack.com](https://www.fullstack.com/labs/resources/blog/top-5-ux-ui-design-trends-in-2025-the-future-of-user-experiences)
>
> **14 Micro-interaction Examples to Enhance UX and Reduce Frustration** [userpilot.com](https://userpilot.com/blog/micro-interaction-examples/)
>
> **11 UI Design Best Practices for UX Designers (2026 Guide)** [uxplaybook.org](https://uxplaybook.org/articles/ui-fundamentals-best-practices-for-ux-designers)
>
> **UI Design Best Practices for 2025** [webstacks.com](https://www.webstacks.com/blog/ui-design-best-practices)
>
> **5 UI UX Best Practices 2025/2026 [UI UX 2026]** [whizzbridge.com](https://www.whizzbridge.com/blog/ui-ux-best-practices-2025)
>
> **Best web micro-interaction examples and guidelines for 2025 - Justinmind** [justinmind.com](https://www.justinmind.com/web-design/micro-interactions)
>
> **Better UX Through Microinteractions | Toptal®** [toptal.com](https://www.toptal.com/designers/product-design/microinteractions-better-ux)
>
Now let me search for more specific information about scalability, security, and deployment best practices.

````plaintext
Web Search: web application security best practices authentication rate limiting 2025
````

> **API Security in 2025: Top Best Practices Every Security Team Must Know** [securityonline.info](https://securityonline.info/api-security-in-2025-top-best-practices-every-security-team-must-know/)
>
> **Web Application Security in 2025: Key Threats and Strategies | by Eastgate Software | Medium** [medium.com](https://medium.com/@eastgate/web-application-security-in-2025-key-threats-and-strategies-9ead529f0dae)
>
> **OWASP API Top 10 2023: Risks and How to Mitigate Them | CyCognito** [cycognito.com](https://www.cycognito.com/learn/api-security/owasp-api-security.php)
>
> **Rate limiting best practices · Cloudflare Web Application Firewall (WAF) docs** [cloudflare.com](https://developers.cloudflare.com/waf/rate-limiting-rules/best-practices/)
>
> **API2:2023 Broken Authentication - OWASP API Security Top 10** [owasp.org](https://owasp.org/API-Security/editions/2023/en/0xa2-broken-authentication/)
>
> **20+ Web Application Security Best Practices Guide 2025** [spaceo.ca](https://www.spaceo.ca/blog/web-application-security-best-practices/)
>
> **Best Practices for Application Security in 2025** [happiestminds.com](https://www.happiestminds.com/blogs/best-practices-for-application-security-in-2025/)
>
> **Implement API rate limiting to reduce attack surfaces | TechTarget** [techtarget.com](https://www.techtarget.com/searchsecurity/feature/Implement-API-rate-limiting-to-reduce-attack-surfaces)
>
> **OWASP API Top 10: How to Secure Your APIs, Complete Guide** [pynt.io](https://www.pynt.io/learning-hub/owasp-top-10-guide/owasp-api-top-10)
>
> **Secure Web Application Best Practices 2025: - Inovo Technologies** [inovotechnologies.co](https://inovotechnologies.co/2025/10/05/secure-web-application-development-best-practices-2025/)
>
Now let me create a comprehensive AI agent harness system for you. This will be a production-grade orchestration system with multiple specialized agents.

**Production-Grade AI Agent Harness for Full-Stack Development**

````jsx
import React, { useState, useRef, useEffect } from 'react';
import { Play, Users, GitBranch, Database, Shield, Zap, Eye, MessageSquare, CheckCircle, XCircle, Clock, Code, Palette, Server, FileCode, TestTube, Package, Settings, AlertCircle, TrendingUp } from 'lucide-react';

const AgentHarnessOrchestrator = () => {
  const [projectName, setProjectName] = useState('');
  const [projectDescription, setProjectDescription] = useState('');
  const [isRunning, setIsRunning] = useState(false);
  const [currentPhase, setCurrentPhase] = useState('');
  const [agentLogs, setAgentLogs] = useState([]);
  const [agentStatuses, setAgentStatuses] = useState({});
  const [progress, setProgress] = useState(0);
  const [commitHistory, setCommitHistory] = useState([]);
  const logsEndRef = useRef(null);

  const scrollToBottom = () => {
    logsEndRef.current?.scrollIntoView({ behavior: 'smooth' });
  };

  useEffect(() => {
    scrollToBottom();
  }, [agentLogs]);

  const agents = [
    {
      id: 'chief_architect',
      name: 'Chief Architect',
      icon: Users,
      role: 'Orchestrator & System Designer',
      color: 'text-purple
````





## Prompt:
1/7/2026, 5:34:40 PM

Give the output in parts if necessary but I want the best output but first tell me what you are going to give it I have any feedback I will tell you then and we will create harness



## Response:
1/7/2026, 5:35:44 PM

Perfect! Let me outline the complete system architecture before we build it. I want your feedback on this plan:

## **AI Agent Harness Architecture - Complete Blueprint**

### **🎯 Core Philosophy**
- **Zero compromise on quality** - Tokens are unlimited, quality is priority #1
- **Production-ready code** - Deploy-ready, not prototype-ready
- **Human-in-the-loop** - You approve major decisions, agents handle execution
- **Collaborative agents** - Agents can discuss with each other and ask you questions
- **Complete SDLC coverage** - From ideation to deployment

---

### **🤖 Agent Team Structure (17 Specialized Agents)**

#### **1. ORCHESTRATION LAYER**
- **Chief Architect Agent**: Master orchestrator, makes high-level decisions, coordinates all agents
- **Project Manager Agent**: Sprint planning, task breakdown, progress tracking, timeline management

#### **2. REQUIREMENTS & DESIGN PHASE**
- **Business Analyst Agent**: Requirements gathering, user stories, feature validation, market research
- **UX Research Agent**: User research, competitor analysis, usability patterns
- **Product Designer Agent**: Wireframes, user flows, information architecture
- **UI/UX Designer Agent**: Visual design, color theory, micro-interactions, animations, responsive layouts

#### **3. FRONTEND DEVELOPMENT PHASE**
- **Frontend Architect Agent**: Component architecture, state management strategy, folder structure
- **Frontend Developer Agent**: React/Vue/Next.js implementation, component building
- **CSS/Design Systems Agent**: Tailwind configuration, design tokens, theming, accessibility (WCAG 2.1)

#### **4. BACKEND DEVELOPMENT PHASE**
- **Backend Architect Agent**: API design, database schema, system architecture, scalability planning
- **Backend Developer Agent**: API implementation, business logic, integrations
- **Database Engineer Agent**: Schema design, migrations, indexing, query optimization, normalization

#### **5. QUALITY & SECURITY PHASE**
- **QA Engineer Agent**: Test planning, E2E tests, integration tests, unit tests, edge cases
- **Security Engineer Agent**: OWASP compliance, authentication, authorization, rate limiting, input validation
- **Performance Engineer Agent**: Bundle optimization, lazy loading, caching strategies, CDN setup, database query optimization

#### **6. DEVOPS & DEPLOYMENT PHASE**
- **DevOps Engineer Agent**: Docker containerization, CI/CD pipelines, environment configuration
- **Monitoring Agent**: Logging, error tracking, APM, health checks, observability

---

### **📋 Complete Checklist of Production Requirements**

#### **FRONTEND EXCELLENCE**
- ✅ **Design System**: Consistent colors, typography, spacing, shadows, borders
- ✅ **Micro-interactions**: Hover states, loading states, transitions, animations
- ✅ **Responsive Design**: Mobile-first, tablet, desktop breakpoints
- ✅ **Accessibility**: ARIA labels, keyboard navigation, screen reader support, color contrast
- ✅ **Performance**: Code splitting, lazy loading, image optimization, bundle size < 200KB
- ✅ **State Management**: Redux/Zustand/Context with proper separation
- ✅ **Error Boundaries**: Graceful error handling, fallback UI
- ✅ **SEO**: Meta tags, Open Graph, structured data, sitemap
- ✅ **PWA Features**: Service workers, offline support, app manifest
- ✅ **Loading States**: Skeletons, spinners, progressive loading
- ✅ **Empty States**: Meaningful placeholders and CTAs
- ✅ **Form Validation**: Real-time validation, clear error messages
- ✅ **Toast Notifications**: Success, error, warning messages

#### **BACKEND EXCELLENCE**
- ✅ **API Design**: RESTful or GraphQL, versioning, documentation (OpenAPI/Swagger)
- ✅ **Authentication**: JWT, refresh tokens, OAuth2, session management
- ✅ **Authorization**: RBAC, permissions, resource-level access control
- ✅ **Rate Limiting**: Per-user, per-IP, sliding window algorithm
- ✅ **Input Validation**: Schema validation, sanitization, type checking
- ✅ **Error Handling**: Structured errors, proper HTTP codes, error logging
- ✅ **Database Design**: Normalized schema, proper indexes, foreign keys, constraints
- ✅ **Database Optimization**: Query optimization, connection pooling, read replicas
- ✅ **Caching**: Redis/Memcached, cache invalidation strategies
- ✅ **Background Jobs**: Queue system (Bull/BullMQ), job retry logic
- ✅ **File Uploads**: S3/Cloud storage, file validation, virus scanning
- ✅ **Email System**: Transactional emails, templates, delivery tracking
- ✅ **Logging**: Structured logging (Winston/Pino), log levels, log rotation
- ✅ **Monitoring**: Health checks, metrics, alerting
- ✅ **Security Headers**: CORS, CSP, HSTS, X-Frame-Options
- ✅ **SQL Injection Prevention**: Parameterized queries, ORM usage
- ✅ **XSS Prevention**: Output encoding, CSP
- ✅ **CSRF Protection**: CSRF tokens, SameSite cookies
- ✅ **Secrets Management**: Environment variables, vault integration

#### **DATABASE EXCELLENCE**
- ✅ **Schema Design**: Proper relationships, data types, constraints
- ✅ **Indexing Strategy**: B-tree, composite indexes, covering indexes
- ✅ **Migrations**: Version controlled, rollback capability, seed data
- ✅ **Backup Strategy**: Automated backups, point-in-time recovery
- ✅ **Scalability**: Partitioning, sharding strategy (if needed)

#### **DEVOPS EXCELLENCE**
- ✅ **Containerization**: Multi-stage Docker builds, optimized images
- ✅ **CI/CD Pipeline**: GitHub Actions/GitLab CI, automated testing, deployment
- ✅ **Environment Config**: Dev, staging, production environments
- ✅ **Infrastructure as Code**: Docker Compose, Kubernetes (if needed)
- ✅ **SSL/TLS**: HTTPS enforcement, certificate management
- ✅ **Monitoring**: Prometheus, Grafana, ELK stack, or cloud-native solutions
- ✅ **Error Tracking**: Sentry or similar
- ✅ **Load Balancing**: Nginx, reverse proxy configuration
- ✅ **Auto-scaling**: Horizontal scaling configuration
- ✅ **Zero-downtime Deployment**: Blue-green or rolling deployments

#### **CODE QUALITY**
- ✅ **Folder Structure**: Feature-based or layer-based, consistent organization
- ✅ **Code Style**: ESLint, Prettier, consistent conventions
- ✅ **Documentation**: README, API docs, architecture docs, setup guides
- ✅ **Git Strategy**: Feature branches, conventional commits, PR templates
- ✅ **Testing**: Unit (>80% coverage), integration, E2E tests
- ✅ **Type Safety**: TypeScript with strict mode
- ✅ **Code Reviews**: Automated checks, review checklist

---

### **🔄 Workflow Phases**

**Phase 1: Discovery & Planning (Agents: BA, UX Research, PM)**
- Market research, competitor analysis
- Requirements gathering, user stories
- Technical feasibility assessment
- Timeline and sprint planning
- **Output**: PRD document, user stories, technical architecture proposal

**Phase 2: Design (Agents: Product Designer, UI/UX Designer)**
- Wireframes and user flows
- Visual design with color palette, typography
- Design system creation
- Prototype with micro-interactions
- **Output**: Figma/design files, design system documentation, **your approval required**

**Phase 3: Architecture (Agents: Chief Architect, Frontend Architect, Backend Architect, DB Engineer)**
- System architecture diagram
- Database schema design
- API contract definition
- State management architecture
- Folder structure planning
- **Output**: Architecture documents, **your approval required**

**Phase 4: Frontend Development (Agents: Frontend Dev, CSS/Design Systems)**
- Component library building
- Page implementation
- State management integration
- Responsive implementation
- **Output**: Working frontend with all interactions

**Phase 5: Backend Development (Agents: Backend Dev, DB Engineer)**
- API implementation
- Database migrations
- Business logic implementation
- Integration points
- **Output**: Working backend with API documentation

**Phase 6: Quality Assurance (Agents: QA, Security, Performance)**
- Test suite creation and execution
- Security audit and fixes
- Performance optimization
- Accessibility audit
- **Output**: Test reports, security report, performance metrics

**Phase 7: DevOps & Deployment (Agents: DevOps, Monitoring)**
- Docker containerization
- CI/CD pipeline setup
- Environment configuration
- Monitoring setup
- **Output**: Deployment scripts, infrastructure code

**Phase 8: Documentation & Handoff**
- README with setup instructions
- API documentation
- Architecture documentation
- Deployment guide
- **Output**: Complete documentation package

---

### **🎨 UI/UX Excellence Standards**

**Color Palette Strategy**
- Primary, secondary, tertiary colors
- Semantic colors (success, error, warning, info)
- Neutral grays (9 shades)
- Dark mode palette
- Accessibility contrast ratios (WCAG AA minimum)

**Typography System**
- Heading hierarchy (H1-H6) with proper scaling
- Body text sizes (small, base, large)
- Font weights (light, regular, medium, semibold, bold)
- Line heights optimized for readability
- Letter spacing for headings

**Spacing System**
- 8px base unit scale (4, 8, 12, 16, 24, 32, 48, 64, 96, 128)
- Consistent padding and margins
- Component spacing rules

**Component Library**
- Buttons (primary, secondary, ghost, icon, loading states)
- Forms (inputs, selects, checkboxes, radio, file upload)
- Cards with hover effects
- Modals and dialogs
- Toasts and notifications
- Tables with sorting/filtering
- Navigation (navbar, sidebar, breadcrumbs)
- Loaders and skeletons
- Empty states
- Error states

**Micro-interactions**
- Smooth transitions (200-300ms)
- Hover states on all interactive elements
- Focus indicators for accessibility
- Button press animations
- Loading spinners with proper timing
- Page transitions
- Scroll animations (subtle)

---

### **🛠️ Technical Implementation Details**

**Harness Features:**
1. **Agent Communication Protocol**: Agents can send messages to each other, request clarification, escalate decisions
2. **Human Approval Gates**: Critical decisions pause for your approval
3. **Live Progress Dashboard**: Real-time view of all agent activities
4. **Log System**: Detailed logs of every decision, action, and output
5. **Git Integration**: Automatic commits with proper messages, branch management
6. **Rollback Capability**: Can revert to any previous state
7. **Quality Gates**: Automated checks before moving to next phase
8. **Cost Tracking**: Token usage per agent (though unlimited, still good to track)

**API Integration with Anthropic:**
- Each agent is a separate Claude instance with specialized system prompts
- Chief Architect has context of all agents and orchestrates
- Agents use extended context windows (200K tokens) for complex decisions
- Artifact generation for code, designs, documentation

---

### **📊 Output Format**

**What You'll Get:**
1. **Interactive Dashboard** (React app) - Control panel for entire harness
2. **Agent System Prompts** - 17 specialized prompts for each agent role
3. **Orchestration Engine** - Workflow management and agent coordination
4. **Quality Checklists** - Validation criteria for each phase
5. **Integration Guide** - How to connect with Google IDX or local environment
6. **Example Workflows** - Sample projects demonstrating the system

---

### **🤔 Questions for You:**

1. **Primary Stack Preference**: React or Next.js? Node.js/Express or NestJS backend? PostgreSQL, MySQL, or MongoDB?

2. **Deployment Target**: AWS, GCP, Azure, Vercel, or self-hosted?

3. **Agent Interaction Style**: Should agents be fully autonomous between approval gates, or should they ask you questions frequently during execution?

4. **UI Complexity Level**: Do you want ultra-modern glassmorphism/3D effects, or clean minimalist design as default?

5. **Testing Level**: How deep should automated testing go? (Unit + Integration, or also E2E with Playwright/Cypress?)

6. **Single Harness vs Modular**: One mega-application or separate modules you can enable/disable per project?

---

**Tell me your feedback on:**
- Any agents you want to add/remove/modify?
- Any checklist items missing?
- Preferences on the questions above?
- Any specific concerns or priorities?

Once you approve, I'll build this in parts, starting with the orchestration dashboard and agent system prompts!



## Prompt:
1/7/2026, 5:43:07 PM

What you have given is great but just like I have mentioned from frontend there will so many other things which I have forgot to mention and there will so many things which a production level engineer who has built scalable systems for thousands of people will have knowledge of I want you include all those because knowledge,planning and the way we instruct changes the quality of the output whether we get shit output or very good output so I want all the very very deep domain knowledge of a engineer who has built million dollar apps for each section agent we should provide that knowledge explicitly because we should give knowledge and enforce that standard not just some basic vibe coding stuff
What you have given is good about the agent distribution but I think you can still improve in the distribution and sdlc 
The agents should first ask me in such a way that even any person can answer and also help me decide tech stack 
I want you improve this overall and we are competing with companies like Google we want similar output and ship sass application even very complex with no issue in short time but quality is most important and I don't want ai output where the design,code or some other things are inconsistent and there are some buttons they don't work etc there should be perfect sync between frotend and backend and overall app they should happen perfectly
Give me improved plan I want best output



## Response:
1/7/2026, 5:45:47 PM

# **🚀 ELITE AI AGENT HARNESS - PRODUCTION-GRADE SYSTEM**
## *Engineering Excellence at Scale - Zero Compromise Architecture*

---

## **🎯 CORE MISSION**
Build a harness that produces **Google/Meta/Netflix-level quality** - the kind of code that handles millions of users, where every pixel is intentional, every API call is optimized, and every edge case is handled.

---

## **🧠 DEEP DOMAIN KNOWLEDGE INTEGRATION**

### **The Knowledge Problem You've Identified**
You're absolutely right - the difference between "AI code" and "production code" is **deep domain expertise**. Here's what separates million-dollar apps from prototypes:

#### **What Beginners Miss (That We'll Enforce):**

**FRONTEND MASTERY**
- **Performance Budget**: Lighthouse score >90, FCP <1.8s, TTI <3.5s, CLS <0.1
- **Bundle Optimization**: Tree shaking, code splitting per route, dynamic imports, vendor chunking
- **Image Strategy**: WebP/AVIF with PNG fallback, responsive images with srcset, lazy loading with intersection observer, blur-up technique
- **Font Loading**: FOUT prevention, font-display swap, variable fonts, subsetting
- **Critical CSS**: Above-fold inlining, unused CSS purging, CSS containment
- **JavaScript Optimization**: Debouncing/throttling, web workers for heavy computation, requestIdleCallback for non-critical tasks
- **Memory Management**: Event listener cleanup, subscription management, preventing memory leaks in SPAs
- **Reflow/Repaint Optimization**: Layout thrashing prevention, CSS transforms over position, will-change property usage
- **Accessibility Deep Dive**: Skip links, focus management, ARIA live regions, reduced motion preferences, keyboard trap prevention
- **State Management Architecture**: Normalization, selector memoization, optimistic updates, offline-first patterns
- **Error Recovery**: Error boundaries per route, retry logic with exponential backoff, graceful degradation
- **Real-time Features**: WebSocket connection management, reconnection logic, message queuing, heartbeat mechanisms
- **Form UX Excellence**: Autosave drafts, progress indication, inline validation without annoying users, smart defaults
- **Design System Science**: 8pt grid system, golden ratio typography scale, color systems with perceptual uniformity (OKLCH), elevation system with proper shadows
- **Micro-interaction Timing**: Material Design motion principles, easing functions (ease-out for entrances), choreography (stagger animations)
- **Mobile-Specific**: Touch target sizes (44x44px minimum), gesture handling, mobile safari quirks, PWA install prompts

**BACKEND MASTERY**
- **API Design Patterns**: HATEOAS for true REST, GraphQL N+1 query prevention, cursor-based pagination over offset
- **Database Connection Pooling**: Proper pool sizing (formula: connections = ((core_count * 2) + effective_spindle_count)), connection lifecycle management
- **Transaction Management**: ACID compliance, isolation levels, distributed transaction patterns (Saga pattern)
- **Query Optimization**: Explain analyze usage, avoiding SELECT *, index-only scans, covering indexes, partial indexes, expression indexes
- **Caching Layers**: Cache-aside pattern, write-through/write-behind, cache invalidation strategies, TTL strategies per data type
- **Rate Limiting Architecture**: Token bucket algorithm, sliding window counters, distributed rate limiting with Redis
- **Authentication Security**: Password hashing (Argon2id or bcrypt with cost factor 12+), secure session management, JWT rotation, refresh token family detection
- **Authorization Patterns**: Attribute-based access control (ABAC), policy-based authorization, permission inheritance
- **API Versioning**: URL versioning vs header versioning, deprecation timelines, backward compatibility
- **Idempotency**: Idempotency keys for payments/critical operations, deduplication windows
- **Background Job Patterns**: Job retry with exponential backoff, dead letter queues, job prioritization, job chaining
- **File Upload Security**: File type validation (magic number checking), file size limits, virus scanning, presigned URLs for direct S3 upload
- **API Documentation**: OpenAPI 3.1, interactive docs, code generation, contract testing
- **Observability**: Distributed tracing (OpenTelemetry), structured logging with correlation IDs, metrics (RED/USE methods), SLIs/SLOs definition
- **Error Handling Philosophy**: Error codes, error context, PII-free logging, user-friendly error messages, error aggregation
- **Webhooks**: Retry logic, signature verification, webhook version management, idempotent webhook processing
- **Data Validation**: JSON Schema validation, custom validators, sanitization, business rule validation separate from schema validation
- **Microservices Patterns** (if applicable): Circuit breakers, service discovery, health checks, graceful degradation, bulkheads

**DATABASE MASTERY**
- **Normalization vs Denormalization**: When to denormalize for read performance, materialized views, CQRS pattern
- **Index Strategy**: B-tree vs Hash vs GIN vs GiST indexes, multi-column index column order, index maintenance
- **Partitioning**: Range, list, hash partitioning strategies, partition pruning
- **Replication**: Master-slave vs multi-master, replication lag handling, read replica routing
- **Connection Management**: Connection pooling, prepared statements, connection leak detection
- **Migration Strategy**: Blue-green migrations, backward-compatible migrations, data migration vs schema migration
- **Soft Deletes vs Hard Deletes**: Audit trail requirements, GDPR compliance, cascade delete rules
- **Full-Text Search**: PostgreSQL FTS vs Elasticsearch, search ranking, fuzzy matching
- **Time-Series Data**: Time-bucketing, continuous aggregates, retention policies
- **Geospatial Data**: PostGIS, spatial indexes, distance queries optimization
- **JSON Columns**: When to use JSONB, indexing JSON fields, query performance
- **Locking Strategy**: Optimistic vs pessimistic locking, row-level locks, deadlock prevention
- **Backup & Recovery**: Point-in-time recovery, backup testing, disaster recovery plan

**SECURITY MASTERY**
- **OWASP Top 10**: SQL injection, XSS, CSRF, broken authentication, security misconfiguration, vulnerable components, insufficient logging
- **Content Security Policy**: Nonce-based CSP, report-only mode testing, CSP violation reporting
- **CORS Configuration**: Preflight handling, credential handling, wildcard domain risks
- **Secrets Management**: HashiCorp Vault, AWS Secrets Manager, secret rotation
- **Input Validation**: Whitelist validation, length checks, type checking, business logic validation
- **Output Encoding**: Context-aware encoding (HTML, JavaScript, URL, CSS)
- **Secure Headers**: HSTS with preload, X-Content-Type-Options, X-Frame-Options, Referrer-Policy
- **Dependency Security**: Automated dependency scanning, SCA tools, license compliance
- **API Security**: OAuth 2.1, PKCE flow, scope management, token introspection
- **PII Protection**: Data classification, encryption at rest and in transit, data retention policies, right to be forgotten
- **Penetration Testing**: Regular security audits, bug bounty programs
- **DDoS Protection**: Cloudflare/AWS Shield, rate limiting, IP reputation

**DEVOPS MASTERY**
- **Container Optimization**: Multi-stage builds, layer caching, minimal base images (Alpine/distroless), security scanning
- **CI/CD Pipeline**: Parallel jobs, artifact caching, deployment strategies (canary, blue-green, rolling)
- **Infrastructure as Code**: Terraform, Pulumi, proper state management, environment parity
- **Monitoring Strategy**: Golden signals (latency, traffic, errors, saturation), alerting thresholds, on-call runbooks
- **Log Management**: Log aggregation, log retention policies, log-based metrics, sensitive data redaction
- **Secrets in CI/CD**: Secret injection, secret rotation, no secrets in code/configs
- **Database Migrations in CI/CD**: Migration testing, rollback procedures, zero-downtime migrations
- **Environment Variables**: 12-factor app principles, environment-specific configs, feature flags
- **Health Checks**: Liveness vs readiness probes, startup probes, graceful shutdown
- **Auto-scaling**: Metrics-based scaling, predictive scaling, cost optimization
- **Disaster Recovery**: RTO/RPO requirements, backup testing, failover procedures

**TESTING MASTERY**
- **Testing Pyramid**: Unit (70%), integration (20%), E2E (10%)
- **Test Patterns**: AAA pattern, test fixtures, test factories, mocking strategies
- **Frontend Testing**: Component testing, visual regression testing, accessibility testing
- **Backend Testing**: API contract testing, database testing, integration testing
- **E2E Testing**: Critical user journey testing, flaky test prevention, parallel execution
- **Performance Testing**: Load testing, stress testing, spike testing, soak testing
- **Security Testing**: SAST, DAST, dependency scanning, penetration testing
- **Test Data Management**: Test data generation, database seeding, test isolation
- **Coverage Goals**: 80%+ for critical paths, 100% for security/payment logic

---

## **🏗️ IMPROVED AGENT ARCHITECTURE (25 Specialized Agents)**

### **TIER 1: STRATEGIC LAYER (Human Collaboration Intensive)**

#### **1. Product Strategist Agent** 🎯
**Deep Knowledge**: Product-market fit, user psychology, growth loops, monetization strategies, competitive positioning
- Conducts market research and competitive analysis
- Helps you validate the idea with structured questions (even non-technical person can answer)
- Identifies target audience, pain points, value proposition
- Defines success metrics (KPIs, OKRs)
- **Output**: Product brief, market analysis, success metrics

#### **2. Technical Advisor Agent** 🤝
**Deep Knowledge**: Every tech stack's trade-offs, scaling characteristics, team size implications, ecosystem maturity
- Asks about your requirements in simple terms:
  - Expected user volume? (100s, 1000s, millions?)
  - Real-time features needed? (chat, notifications, live updates?)
  - Geographic distribution? (local, national, global?)
  - Team size and expertise?
  - Budget constraints?
  - Time to market priorities?
- **Recommends tech stack** with detailed justification:
  - Frontend framework (React, Vue, Svelte, Next.js, Remix)
  - Backend framework (Express, Fastify, NestJS, Django, FastAPI)
  - Database (PostgreSQL, MySQL, MongoDB, Cassandra)
  - Caching (Redis, Memcached)
  - Message queue (RabbitMQ, Kafka, Redis Streams)
  - Infrastructure (AWS, GCP, Azure, Vercel, Railway)
- **Output**: Technology decision document with trade-off analysis

#### **3. Chief Architect Agent** 👑
**Deep Knowledge**: Distributed systems, CAP theorem, microservices vs monolith, event-driven architecture, CQRS, saga patterns
- Creates high-level system architecture
- Defines service boundaries (if microservices)
- Plans data flow and communication patterns
- Identifies technical risks and mitigation strategies
- Reviews all technical decisions from other agents
- **Output**: System architecture diagram, ADR (Architecture Decision Records)

---

### **TIER 2: REQUIREMENTS & DESIGN LAYER**

#### **4. Business Analyst Agent** 📋
**Deep Knowledge**: User story mapping, job-to-be-done framework, acceptance criteria, edge case identification
- Converts ideas into detailed requirements
- Creates user stories with acceptance criteria
- Identifies edge cases and error scenarios
- Prioritizes features (MoSCoW method)
- **Output**: PRD, user stories backlog

#### **5. UX Researcher Agent** 🔍
**Deep Knowledge**: User research methodologies, cognitive load theory, mental models, usability heuristics
- Analyzes user behavior patterns
- Researches competitor UX
- Identifies usability best practices for your domain
- **Output**: UX research report, user personas

#### **6. Information Architect Agent** 🗺️
**Deep Knowledge**: Information hierarchy, navigation patterns, user flows, card sorting
- Designs site structure and navigation
- Creates user flows for key journeys
- Plans information hierarchy
- **Output**: Sitemap, user flow diagrams

#### **7. UI/UX Designer Agent** 🎨
**Deep Knowledge**: Design systems, color theory (perceptual color spaces), typography, gestalt principles, accessibility, micro-interactions
- Creates wireframes and high-fidelity designs
- Designs comprehensive design system:
  - Color palette (primary, secondary, semantic, neutrals) with accessibility verification
  - Typography scale (modular scale, line heights, font weights)
  - Spacing system (8pt grid)
  - Component library designs
  - Micro-interaction specifications
  - Animation timing curves
  - Responsive breakpoints
  - Dark mode variant
- **Output**: Design system, Figma files, style guide

---

### **TIER 3: FRONTEND DEVELOPMENT LAYER**

#### **8. Frontend Architect Agent** 🏛️
**Deep Knowledge**: Component composition, state management patterns, code splitting strategies, performance budgets
- Designs folder structure:
  ```
  src/
    components/
      ui/           # Reusable UI components
      features/     # Feature-specific components
      layouts/      # Layout components
    hooks/          # Custom hooks
    contexts/       # React contexts
    store/          # State management
    services/       # API services
    utils/          # Utility functions
    types/          # TypeScript types
    constants/      # Constants
    config/         # Configuration
  ```
- Defines state management architecture
- Plans code splitting strategy
- Defines component abstraction levels
- **Output**: Frontend architecture document, folder structure

#### **9. Design System Engineer Agent** 🎨
**Deep Knowledge**: Atomic design, component API design, theming systems, CSS architecture
- Implements design system in code
- Creates component library with:
  - All states (default, hover, focus, active, disabled, loading)
  - All variants (sizes, colors, styles)
  - Accessibility built-in
  - Full TypeScript support
  - Storybook documentation
- Implements theming system
- **Output**: Complete component library

#### **10. Frontend Developer Agent - Core** 💻
**Deep Knowledge**: React/Vue best practices, hooks optimization, render optimization, virtual DOM understanding
- Implements pages and features
- Integrates components from design system
- Implements state management
- Handles routing
- **Output**: Feature implementations

#### **11. Frontend Developer Agent - Interactions** ✨
**Deep Knowledge**: Animation libraries, gesture handling, scroll effects, loading strategies
- Implements all micro-interactions
- Adds animations and transitions
- Implements loading states
- Implements empty states
- Implements error states
- **Output**: Polished, interactive UI

#### **12. Frontend Performance Engineer** ⚡
**Deep Knowledge**: Browser rendering pipeline, performance profiling, optimization techniques
- Analyzes bundle size
- Implements code splitting
- Optimizes images
- Implements lazy loading
- Optimizes fonts
- Implements service workers
- Runs Lighthouse audits
- **Output**: Performance optimization report, Lighthouse score >90

#### **13. Accessibility Engineer** ♿
**Deep Knowledge**: WCAG 2.1 AAA, ARIA specification, screen reader testing, keyboard navigation patterns
- Audits accessibility
- Implements ARIA labels
- Ensures keyboard navigation
- Tests with screen readers
- Implements focus management
- **Output**: WCAG 2.1 compliance report

---

### **TIER 4: BACKEND DEVELOPMENT LAYER**

#### **14. Backend Architect Agent** 🏗️
**Deep Knowledge**: API design, system scalability, distributed systems, caching strategies
- Designs API structure (RESTful or GraphQL)
- Plans database architecture
- Designs caching strategy
- Plans background job system
- Defines authentication/authorization flow
- **Output**: API specification (OpenAPI), backend architecture doc

#### **15. Database Architect Agent** 🗄️
**Deep Knowledge**: Database normalization, indexing strategies, query optimization, replication
- Designs database schema
- Creates ER diagrams
- Plans indexing strategy
- Designs migration strategy
- Plans backup strategy
- **Output**: Database schema, migration files, ER diagram

#### **16. Backend Developer Agent - Core** 🔧
**Deep Knowledge**: Framework best practices, dependency injection, middleware patterns
- Implements API endpoints
- Implements business logic
- Implements validation
- Implements error handling
- Integrates with database
- **Output**: API implementation

#### **17. Backend Developer Agent - Integrations** 🔌
**Deep Knowledge**: Third-party API integration, webhook handling, OAuth flows
- Implements third-party integrations
- Implements file upload system
- Implements email system
- Implements payment processing
- Implements webhook handlers
- **Output**: Integration implementations

#### **18. API Performance Engineer** 🚀
**Deep Knowledge**: Query optimization, caching patterns, connection pooling, load balancing
- Optimizes database queries
- Implements caching
- Implements connection pooling
- Optimizes API response times
- Implements rate limiting
- **Output**: Performance optimization report

---

### **TIER 5: QUALITY ASSURANCE LAYER**

#### **19. QA Architect Agent** 🧪
**Deep Knowledge**: Testing strategies, test automation, quality metrics
- Creates test strategy
- Defines test cases for all features
- Plans automated testing approach
- **Output**: Test plan, test cases

#### **20. Test Engineer Agent - Unit & Integration** ✅
**Deep Knowledge**: Testing frameworks, mocking strategies, test patterns
- Writes unit tests (80%+ coverage)
- Writes integration tests
- Implements test fixtures
- **Output**: Comprehensive test suite

#### **21. Test Engineer Agent - E2E** 🎭
**Deep Knowledge**: E2E testing tools, flaky test prevention, cross-browser testing
- Writes E2E tests for critical flows
- Implements visual regression tests
- Tests across browsers
- **Output**: E2E test suite

#### **22. Security Engineer Agent** 🔒
**Deep Knowledge**: OWASP Top 10, security testing, penetration testing techniques
- Conducts security audit
- Implements security headers
- Implements input validation
- Implements authentication security
- Scans dependencies for vulnerabilities
- **Output**: Security audit report, fixes implemented

---

### **TIER 6: DEVOPS & DEPLOYMENT LAYER**

#### **23. DevOps Engineer Agent** 🐳
**Deep Knowledge**: Container orchestration, CI/CD patterns, infrastructure as code
- Creates Dockerfiles (multi-stage, optimized)
- Creates docker-compose for local dev
- Sets up CI/CD pipeline
- Configures environments (dev, staging, prod)
- **Output**: Deployment infrastructure

#### **24. Monitoring & Observability Engineer** 📊
**Deep Knowledge**: Observability patterns, log aggregation, metrics collection, alerting
- Implements logging system
- Implements error tracking (Sentry)
- Implements metrics collection
- Implements health checks
- Creates dashboards
- **Output**: Monitoring setup, dashboards

#### **25. Documentation Engineer** 📚
**Deep Knowledge**: Technical writing, API documentation, documentation generators
- Writes README with setup instructions
- Writes API documentation
- Writes architecture documentation
- Creates deployment guide
- Creates troubleshooting guide
- **Output**: Complete documentation

---

## **🔄 ENHANCED WORKFLOW WITH QUALITY GATES**

### **Phase 0: INITIALIZATION (Human-Led)**
**Agents**: Product Strategist, Technical Advisor
**Duration**: 1-2 hours of Q&A with you

1. **Product Strategist asks you** (simple questions):
   - What problem are you solving?
   - Who is your target user?
   - What are similar products?
   - What makes your solution different?
   - What's your primary goal? (revenue, users, impact)

2. **Technical Advisor asks you**:
   - How many users in month 1? 6 months? 1 year?
   - Do you need real-time features?
   - Do you need to handle payments?
   - Do you need user authentication?
   - Do you need file uploads?
   - Do you need email notifications?
   - What's your budget?
   - Do you have a team or solo?
   - What's your timeline?

3. **Output**: Product brief + Tech stack recommendation
4. **Your Approval Required**: ✅ Yes/No on tech stack

---

### **Phase 1: REQUIREMENTS & DESIGN (2-3 days)**
**Agents**: BA, UX Researcher, Info Architect, UI/UX Designer
**Quality Gate**: Design review with you

1. BA creates detailed requirements
2. UX Researcher analyzes UX patterns
3. Info Architect creates site structure
4. UI/UX Designer creates designs

**Quality Checks**:
- All user stories have acceptance criteria ✅
- All edge cases documented ✅
- Design system is complete ✅
- Accessibility considered in design ✅
- Responsive design for all breakpoints ✅
- Dark mode variant created ✅

**Your Approval Required**: ✅ Design sign-off

---

### **Phase 2: ARCHITECTURE (1 day)**
**Agents**: Chief Architect, Frontend Architect, Backend Architect, DB Architect
**Quality Gate**: Architecture review

1. Chief Architect creates system design
2. Frontend Architect plans frontend structure
3. Backend Architect plans API structure
4. DB Architect designs database schema

**Quality Checks**:
- Scalability considered ✅
- Security considered ✅
- Performance considered ✅
- All services/modules defined ✅
- Data flow documented ✅
- API contract defined ✅

**Your Approval Required**: ✅ Architecture sign-off

---

### **Phase 3: FRONTEND DEVELOPMENT (3-5 days)**
**Agents**: Design System Engineer, Frontend Devs, Performance Engineer, Accessibility Engineer
**Quality Gate**: Frontend functionality review

1. Design System Engineer builds component library
2. Frontend Dev - Core implements pages
3. Frontend Dev - Interactions adds polish
4. Performance Engineer optimizes
5. Accessibility Engineer audits

**Quality Checks**:
- All designs implemented pixel-perfect ✅
- All interactions work smoothly ✅
- All buttons/links functional ✅
- Forms work with validation ✅
- Loading states everywhere ✅
- Error states everywhere ✅
- Empty states everywhere ✅
- Responsive on all devices ✅
- Accessible (keyboard, screen reader) ✅
- Lighthouse score >90 ✅
- Bundle size <200KB ✅

**Your Review**: Test the frontend, report any issues

---

### **Phase 4: BACKEND DEVELOPMENT (3-5 days)**
**Agents**: Backend Devs, DB Architect, API Performance Engineer
**Quality Gate**: API functionality review

1. DB Architect creates migrations
2. Backend Dev - Core implements APIs
3. Backend Dev - Integrations adds features
4. API Performance Engineer optimizes

**Quality Checks**:
- All API endpoints implemented ✅
- API documentation complete ✅
- Database migrations created ✅
- Authentication working ✅
- Authorization working ✅
- Validation on all inputs ✅
- Error handling everywhere ✅
- Rate limiting implemented ✅
- Caching implemented ✅
- Background jobs working ✅
- API response time <200ms ✅
- Database queries optimized ✅

**Your Review**: Test API with Postman/similar

---

### **Phase 5: INTEGRATION (1-2 days)**
**Agents**: Frontend Dev, Backend Dev, Integration Testing
**Quality Gate**: Full app functionality review

1. Connect frontend to backend
2. Test all user flows end-to-end
3. Fix any integration issues

**Quality Checks**:
- All API calls working ✅
- All forms submitting correctly ✅
- All data displaying correctly ✅
- Error handling works across stack ✅
- Loading states trigger correctly ✅
- Real-time features working (if any) ✅
- File uploads working (if any) ✅
- Payment flow working (if any) ✅

**Your Review**: Test the full application

---

### **Phase 6: TESTING & SECURITY (2-3 days)**
**Agents**: QA Architect, Test Engineers, Security Engineer
**Quality Gate**: Test coverage and security review

1. QA Architect creates test plan
2. Test Engineers write tests
3. Security Engineer audits

**Quality Checks**:
- Unit test coverage >80% ✅
- Integration tests cover all APIs ✅
- E2E tests cover critical flows ✅
- All tests passing ✅
- Security audit complete ✅
- No critical vulnerabilities ✅
- No high-severity vulnerabilities ✅
- Dependencies up to date ✅

**Your Review**: Review test and security reports

---

### **Phase 7: DEVOPS & DEPLOYMENT (1-2 days)**
**Agents**: DevOps Engineer, Monitoring Engineer
**Quality Gate**: Deployment readiness review

1. DevOps Engineer creates deployment setup
2. Monitoring Engineer sets up observability

**Quality Checks**:
- Docker images build successfully ✅
- CI/CD pipeline working ✅
- All environments configured ✅
- Monitoring setup complete ✅
- Error tracking setup complete ✅
- Health checks working ✅
- Backup strategy implemented ✅
- SSL certificates configured ✅

**Your Review**: Review deployment setup

---

### **Phase 8: DOCUMENTATION & LAUNCH (1 day)**
**Agents**: Documentation Engineer, All Agents
**Quality Gate**: Final launch review

1. Documentation Engineer creates docs
2. All agents review their work
3. Final quality checklist

**Quality Checks**:
- README complete ✅
- API docs complete ✅
- Setup guide complete ✅
- Troubleshooting guide complete ✅
- Architecture docs complete ✅
- All commits have proper messages ✅
- Git history clean ✅

**Your Approval Required**: ✅ Launch sign-off

---

## **🎛️ HARNESS FEATURES**

### **1. Intelligent Orchestration**
- **Chief Architect** oversees everything, coordinates agents
- Agents can discuss with each other (logged)
- Agents can ask you questions (with context)
- Agents can escalate issues to Chief Architect

### **2. Quality Enforcement**
- Every phase has quality gates
- Automated checks before proceeding
- Manual review points for critical decisions
- Rollback capability if quality drops

### **3. Perfect Sync Guarantee**
- **API Contract First**: Backend and frontend agree on API contract before implementation
- **Type Safety**: TypeScript types generated from API schema
- **Integration Tests**: Automated tests ensure frontend-backend sync
- **Mock Data**: Frontend can develop with mock data matching real API

### **4. Consistency Enforcement**
- **Design System**: All UI from same component library
- **Code Style**: ESLint + Prettier enforced
- **Naming Conventions**: Enforced across codebase
- **File Structure**: Consistent organization

### **5. Progress Tracking**
- Real-time dashboard showing all agent activity
- Detailed logs of every decision
- Commit history with proper messages
- Progress percentage per phase

### **6. Git Integration**
- **Branch Strategy**: feature branches, main branch
- **Commit Convention**: Conventional commits (feat, fix, refactor, test, docs)
- **PR Generation**: Auto-generated PRs with descriptions
- **Code Review**: Agents review each other's code

### **7. Human-in-the-Loop**
- Approval gates at critical points
- Ability to provide feedback at any point
- Agents ask clarifying questions
- You can pause/resume at any time

---

## **🎨 UI/UX EXCELLENCE ENFORCEMENT**

### **Mandatory Standards (Non-Negotiable)**

**Visual Consistency**:
- Color palette used consistently throughout
- Typography hierarchy maintained everywhere
- Spacing system followed religiously
- Component variants used appropriately

**Interaction Excellence**:
- EVERY clickable element has hover state
- EVERY action has loading state
- EVERY error has error state
- EVERY empty list has empty state
- ALL animations use consistent timing (200ms for micro, 300ms for transitions)

**User Feedback**:
- Toast notifications for all actions
- Confirmation dialogs for destructive actions
- Progress indicators for multi-step processes
- Success states for completed actions

**Responsive Design**:
- Mobile-first approach
- Tested on: 320px, 375px, 768px, 1024px, 1440px, 1920px
- Touch targets ≥44px on mobile
- Navigation adapts per screen size

**Accessibility**:
- Color contrast ratio ≥4.5:1 for text
- Focus indicators on all interactive elements
- Keyboard navigation for all actions
- Screen reader tested
- Skip to content link
- ARIA labels where needed

**Performance**:
- Images optimized and lazy loaded
- Code split per route
- Fonts preloaded
- Critical CSS inlined
- Service worker for offline support

---

## **💾 BACKEND EXCELLENCE ENFORCEMENT**

### **Mandatory Standards (Non-Negotiable)**

**API Quality**:
- RESTful conventions followed
- Consistent response format
- Proper HTTP status codes
- Rate limiting on all endpoints
- Request validation on all endpoints
- API documentation (OpenAPI/Swagger)

**Security**:
- All inputs validated and sanitized
- SQL injection prevention (parameterized queries)
- XSS prevention (output encoding)
- CSRF protection (tokens)
- Authentication required for protected routes
- Authorization checked for all actions
- Secrets in environment variables (never in code)
- Security headers configured

**Database**:
- Proper indexes on frequently queried columns
- Foreign keys for relationships
- Constraints for data integrity
- Migrations version controlled
- Seeds for development data
- Backup strategy documented

**Error Handling**:
- Try-catch on all async operations
- Structured error responses
- Error logging with context
- User-friendly error messages (no stack traces to users)

**Performance**:
- Database queries optimized (no N+1)
- Caching implemented for frequent reads
- Connection pooling configured
- Response time <200ms for most endpoints
- Background jobs for long-running tasks

**Code Quality**:
- TypeScript with strict mode
- ESLint + Prettier
- Consistent file structure
- Separation of concerns (routes, controllers, services, models)
- Dependency injection where appropriate

---

## **🧪 TESTING EXCELLENCE ENFORCEMENT**

### **Mandatory Coverage**

**Frontend**:
- Component tests for all components
- Hook tests for custom hooks
- Integration tests for complex features
- E2E tests for critical user journeys
- Visual regression tests
- Accessibility tests

**Backend**:
- Unit tests for all services/utilities
- Integration tests for all API endpoints
- Database tests with test database
- Security tests (injection attempts)
- Performance tests (load testing)

**Test Quality**:
- Tests are readable (clear naming)
- Tests are isolated (no dependencies between tests)
- Tests use factories for test data
- Mocking done appropriately
- Coverage >80% overall
- Critical paths have 100% coverage

---

## **📦 DELIVERABLES**

### **What You'll Get**

**1. Interactive Harness Dashboard** (React app)
   - Agent status monitoring
   - Real-time logs
   - Progress tracking
   - Quality gate approvals
   - Git integration panel

**2. 25 Agent System Prompts**
   - Each with deep domain knowledge embedded
   - Quality checklists built-in
   - Communication protocols defined

**3. Orchestration Engine**
   - Agent coordination logic
   - Quality gate enforcement
   - Rollback mechanisms

**4. Quality Checklist System**
   - Phase-specific checklists
   - Automated verification where possible
   - Manual review prompts

**5. Integration Templates**
   - Google IDX integration
   - Local development setup
   - CI/CD templates

**6. Knowledge Base**
   - Best practices encyclopedia
   - Trade-off analysis documents
   - Decision trees for common choices

---

## **❓ CRITICAL QUESTIONS FOR YOU**

### **1. Starting Point**
- [ ] Starting from scratch?
- [ ] Have existing design/mockups?
- [ ] Have existing backend?
- [ ] Have specific tech preferences?

### **2. Project Type** (helps agents ask better questions)
- [ ] SaaS product
- [ ] Marketplace
- [ ] Social network
- [ ] E-commerce
- [ ] Content platform
- [ ] Internal tool
- [ ] Other: ___________

### **3. Complexity Level**
- [ ] Simple (Todo app, landing page)
- [ ] Medium (Blog, booking system)
- [ ] Complex (Multi-tenant SaaS)
- [ ] Very Complex (Real-time collaboration tool)

### **4. Timeline Priority**
- [ ] Speed is critical (MVP in 2 weeks)
- [ ] Balanced (production-ready in 4-6 weeks)
- [ ] Quality over speed (perfect product, timeline flexible)

### **5. Deployment Preference**
- [ ] Cheapest (shared hosting, serverless)
- [ ] Balanced (VPS, managed services)
- [ ] Enterprise (Kubernetes, multi-region)

### **6. Your Involvement Level**
- [ ] Hands-off (approve gates, agents do everything)
- [ ] Collaborative (frequent discussions)
- [ ] Code-along (you write code too)

---

## **🚀 NEXT STEPS**

Once you answer the questions above and approve this architecture:

**I will build in this order:**

1. **Part 1**: Harness Orchestration Dashboard (Interactive React app for controlling everything)

2. **Part 2**: Agent System Prompts - Strategic Layer (Product Strategist + Technical Advisor with question flows)

3. **Part 3**: Agent System Prompts - Requirements & Design Layer (



## Prompt:
1/7/2026, 5:47:20 PM

Continue



## Response:
1/7/2026, 5:49:42 PM

3. **Part 3**: Agent System Prompts - Requirements & Design Layer (BA, UX Researcher, Info Architect, UI/UX Designer with complete design system knowledge)

4. **Part 4**: Agent System Prompts - Frontend Development Layer (All 6 frontend agents with deep React/performance/accessibility knowledge)

5. **Part 5**: Agent System Prompts - Backend Development Layer (All 5 backend agents with scalability/security/optimization knowledge)

6. **Part 6**: Agent System Prompts - QA & Security Layer (All 4 testing agents with comprehensive testing strategies)

7. **Part 7**: Agent System Prompts - DevOps Layer (DevOps + Monitoring agents with deployment excellence)

8. **Part 8**: Orchestration Engine Logic (Agent coordination, quality gates, rollback system)

9. **Part 9**: Quality Enforcement System (Automated checks, validation rules, approval workflows)

10. **Part 10**: Integration Guide (How to connect with Google IDX, Claude API, Git)

---

## **🎯 WHAT MAKES THIS DIFFERENT FROM OTHER AI TOOLS**

### **Current AI Tools (Cursor, Copilot, etc.)**
- ❌ Single agent doing everything
- ❌ No domain expertise built-in
- ❌ No quality gates
- ❌ No coordination between components
- ❌ Generic outputs
- ❌ You fix all the bugs

### **This Harness**
- ✅ 25 specialized expert agents
- ✅ Deep domain knowledge in each agent
- ✅ Quality gates at every phase
- ✅ Perfect sync between frontend/backend
- ✅ Production-grade outputs
- ✅ Agents fix their own bugs through testing phases

### **Anthropic's Agent Harness vs This**
- Anthropic's: General purpose, code generation focused
- **This**: Production-grade, full SDLC, quality-obsessed, UI/UX excellence built-in

---

## **🔥 ADDITIONAL IMPROVEMENTS I'LL ADD**

### **1. Domain-Specific Knowledge Injection**

For each project type, agents get specialized knowledge:

**SaaS Products**:
- Multi-tenancy patterns (schema per tenant, database per tenant, shared schema)
- Subscription management (Stripe integration, billing cycles, proration)
- Onboarding flows (progressive disclosure, empty states, tours)
- Admin dashboards (user management, analytics, system health)
- Usage tracking and analytics
- Feature flags for gradual rollouts

**E-commerce**:
- Product catalog architecture
- Shopping cart state management
- Checkout flow optimization (reduce abandonment)
- Payment processing (Stripe, PayPal integration)
- Inventory management
- Order fulfillment workflows
- Email notifications (order confirmation, shipping)

**Social Networks**:
- Feed algorithm design
- Real-time notifications (WebSocket)
- User relationships (followers, friends, blocks)
- Content moderation
- Image/video upload and processing
- Infinite scroll performance
- Activity streams

**Marketplaces**:
- Two-sided marketplace patterns
- Escrow and payment splitting
- Review and rating systems
- Search and discovery
- Messaging between users
- Trust and safety features

### **2. Learning System**

The harness will learn from each project:
- Track which decisions led to best outcomes
- Build a knowledge base of successful patterns
- Improve agent prompts based on results
- Store reusable components and patterns

### **3. Rollback & Version Control**

- Every agent action creates a git commit
- Can rollback to any point
- Can create alternative branches to try different approaches
- Can compare approaches before choosing

### **4. Cost Optimization Intelligence**

Since you mentioned tokens aren't an issue, but still good to optimize:
- Agents use extended context efficiently
- Agents reuse previous context instead of repeating
- Agents compress learnings into knowledge artifacts
- Chief Architect prevents redundant work

### **5. Real-Time Collaboration**

- You can chat with any agent at any time
- Agents can request your input when uncertain
- You can provide feedback on any output
- Agents iterate based on your feedback immediately

### **6. Progressive Enhancement Strategy**

Build in phases with working product at each stage:
- **Week 1**: MVP with core features (deployable)
- **Week 2**: Enhanced features + polish (deployable)
- **Week 3**: Advanced features + optimizations (deployable)
- **Week 4**: Production hardening + security (production-ready)

Each week you have a working, deployable product that gets better.

---

## **🛡️ QUALITY GUARANTEES**

### **Frontend Quality Guarantee**

**Visual Quality**:
- ✅ Every page matches design pixel-perfect (±2px tolerance)
- ✅ Every hover state implemented
- ✅ Every loading state implemented
- ✅ Every error state implemented
- ✅ Every empty state implemented
- ✅ Consistent spacing throughout
- ✅ Consistent colors throughout
- ✅ Animations smooth (60fps)

**Functional Quality**:
- ✅ Every button clicks and does something
- ✅ Every form validates and submits
- ✅ Every link navigates correctly
- ✅ Every modal opens and closes
- ✅ Every dropdown expands and selects
- ✅ Every infinite scroll loads more
- ✅ Every search filters/searches

**Technical Quality**:
- ✅ Lighthouse Performance >90
- ✅ Lighthouse Accessibility >95
- ✅ Lighthouse Best Practices >95
- ✅ Lighthouse SEO >90
- ✅ Bundle size <200KB (gzipped)
- ✅ FCP <1.8s
- ✅ TTI <3.5s
- ✅ CLS <0.1

### **Backend Quality Guarantee**

**API Quality**:
- ✅ Every endpoint returns correct data structure
- ✅ Every endpoint validates inputs
- ✅ Every endpoint handles errors gracefully
- ✅ Every endpoint has proper authentication
- ✅ Every endpoint has proper authorization
- ✅ Every endpoint is documented
- ✅ Every endpoint has rate limiting

**Performance Quality**:
- ✅ Average response time <200ms
- ✅ P95 response time <500ms
- ✅ P99 response time <1000ms
- ✅ Database queries optimized (explain analyze)
- ✅ N+1 queries eliminated
- ✅ Caching implemented for frequent reads
- ✅ Connection pooling configured

**Security Quality**:
- ✅ No SQL injection vulnerabilities
- ✅ No XSS vulnerabilities
- ✅ No CSRF vulnerabilities
- ✅ Passwords hashed properly (bcrypt/Argon2)
- ✅ Secrets not in code
- ✅ Security headers configured
- ✅ Dependencies scanned for vulnerabilities

### **Testing Quality Guarantee**

- ✅ Unit test coverage >80%
- ✅ Integration test coverage for all APIs
- ✅ E2E tests for critical user flows
- ✅ All tests passing
- ✅ No flaky tests
- ✅ Tests run in CI/CD
- ✅ Failed tests block deployment

### **Code Quality Guarantee**

- ✅ TypeScript strict mode enabled
- ✅ ESLint configured and passing
- ✅ Prettier configured
- ✅ No console.logs in production
- ✅ No commented-out code
- ✅ No TODO comments without issues
- ✅ Consistent naming conventions
- ✅ Proper error handling everywhere
- ✅ No hardcoded values (use constants/env)

---

## **📊 PROGRESS TRACKING & TRANSPARENCY**

### **Real-Time Dashboard Will Show**

**Agent Activity Panel**:
- Which agents are currently working
- What each agent is doing right now
- Progress percentage per agent
- Estimated time remaining per task

**Quality Metrics Panel**:
- Current test coverage percentage
- Current Lighthouse scores
- Current security scan results
- Open issues/warnings count

**Git Activity Panel**:
- Recent commits with messages
- Current branch
- Files changed count
- Lines of code added/removed

**Phase Progress Panel**:
- Current phase highlighted
- Completed phases checkmarked
- Upcoming phases grayed out
- Overall completion percentage

**Communication Log**:
- Agent-to-agent discussions
- Agent-to-human questions
- Human feedback
- Decision logs

**Quality Gate Status**:
- Upcoming approval needed
- Passed quality gates
- Failed quality checks (if any)

---

## **🎨 DESIGN SYSTEM EXCELLENCE DEEP DIVE**

Since you emphasized UI/UX being critical, here's what the UI/UX Designer Agent will enforce:

### **Color System (OKLCH color space for perceptual uniformity)**

**Primary Palette**:
- 50, 100, 200, 300, 400, 500 (base), 600, 700, 800, 900
- Contrast ratio verified for each combination
- Dark mode variants automatically generated

**Semantic Colors**:
- Success: Green shades (confirmation, success states)
- Error: Red shades (errors, validation, destructive actions)
- Warning: Amber shades (caution, warnings)
- Info: Blue shades (information, tips)

**Neutral Palette**:
- 9 shades from white to black
- Used for text, borders, backgrounds
- Ensures proper contrast ratios

**Gradients** (if applicable):
- Maximum 2-3 gradients
- Consistent angle (usually 135deg)
- Used sparingly for emphasis

### **Typography System (Modular Scale)**

**Font Selection**:
- Primary font (headlines, UI)
- Secondary font (body text)
- Monospace font (code, data)

**Type Scale** (based on 1.250 ratio - major third):
- xs: 12px
- sm: 14px
- base: 16px
- lg: 20px
- xl: 24px
- 2xl: 30px
- 3xl: 36px
- 4xl: 48px
- 5xl: 60px

**Font Weights**:
- Light (300): Rarely used, large headings
- Regular (400): Body text
- Medium (500): Emphasized text
- Semibold (600): Subheadings, buttons
- Bold (700): Headings, important UI

**Line Heights**:
- Tight (1.25): Large headings
- Snug (1.375): Subheadings
- Normal (1.5): Body text
- Relaxed (1.625): Long-form content
- Loose (2): Very spaced content

### **Spacing System (8pt Grid)**

**Scale**: 4, 8, 12, 16, 24, 32, 48, 64, 96, 128

**Usage**:
- 4px: Icon spacing, tight UI
- 8px: Component internal spacing
- 16px: Component padding
- 24px: Section spacing
- 32px: Large section spacing
- 48px: Major section breaks
- 64px+: Hero sections, page-level spacing

### **Elevation System (Shadows)**

**5 Levels**:
- Level 1: Subtle (cards)
- Level 2: Moderate (dropdowns, tooltips)
- Level 3: Prominent (modals, dialogs)
- Level 4: High (navigation)
- Level 5: Extreme (drag & drop active state)

**Shadow Composition**:
- Multiple shadows for depth (ambient + directional)
- Blur radius scales with elevation
- Opacity decreases with elevation

### **Border System**

**Radius Scale**:
- None: 0px (square)
- sm: 2px (subtle)
- base: 4px (default)
- md: 6px (cards)
- lg: 8px (buttons)
- xl: 12px (prominent elements)
- 2xl: 16px (very rounded)
- full: 9999px (pills, avatars)

**Border Widths**:
- 0: No border
- 1: Default (1px)
- 2: Emphasized (2px)
- 4: Heavy (4px)

### **Animation System**

**Duration**:
- Fast: 150ms (micro-interactions)
- Base: 200ms (most transitions)
- Slow: 300ms (page transitions)
- Slower: 500ms (complex animations)

**Easing Functions**:
- ease-in: For exits (element leaving)
- ease-out: For entrances (element appearing) - MOST COMMON
- ease-in-out: For movements (element changing position)
- spring: For playful interactions

**Animation Types**:
- Fade: Opacity transitions
- Slide: Transform translateX/Y
- Scale: Transform scale
- Rotate: Transform rotate
- Stagger: Sequential animations

**Micro-interactions** (all included):
- Button hover: Scale 1.02, shadow increase
- Button active: Scale 0.98
- Card hover: Shadow increase, slight lift
- Link hover: Color change, underline animation
- Input focus: Border color, shadow (focus ring)
- Checkbox/radio: Checkmark animation
- Toggle: Smooth slide
- Dropdown: Fade + slide down
- Modal: Fade backdrop, scale content
- Toast: Slide in from edge
- Loading: Spinner or skeleton pulse
- Success: Checkmark draw animation
- Error: Shake animation

### **Component States (EVERY component has these)**

**Button States**:
- Default
- Hover
- Active (pressed)
- Focus (keyboard)
- Disabled
- Loading (spinner inside)

**Input States**:
- Default
- Focus
- Filled
- Error (with error message)
- Disabled
- Read-only

**Interactive States**:
- Idle
- Hover
- Active
- Focus
- Disabled
- Loading
- Success
- Error

### **Responsive Breakpoints**

**Mobile First Approach**:
```css
/* Default: Mobile (320px - 639px) */
sm: 640px   /* Large phones */
md: 768px   /* Tablets */
lg: 1024px  /* Laptops */
xl: 1280px  /* Desktops */
2xl: 1536px /* Large desktops */
```

**Layout Strategy**:
- Single column on mobile
- 2 columns on tablet
- 3-4 columns on desktop
- Navigation collapses to hamburger on mobile
- Forms stack vertically on mobile

### **Accessibility Built-In**

**Keyboard Navigation**:
- Tab order logical
- Focus indicators visible (custom styled)
- Skip to content link
- Keyboard shortcuts documented
- No keyboard traps

**Screen Readers**:
- ARIA labels on icons
- ARIA live regions for dynamic content
- ARIA expanded/collapsed for dropdowns
- Alt text on all images
- Proper heading hierarchy (H1 → H2 → H3)

**Visual Accessibility**:
- Contrast ratios meet WCAG AA (4.5:1 for text)
- Focus indicators (3:1 contrast ratio)
- No information by color alone
- Sufficient touch target sizes (44x44px)
- Text scalable to 200% without loss

**Motion Accessibility**:
- Respect prefers-reduced-motion
- Option to disable animations
- No autoplaying videos without control

---

## **🔐 SECURITY DEEP DIVE**

### **Authentication Security**

**Password Requirements**:
- Minimum 12 characters (configurable)
- Mix of uppercase, lowercase, numbers, symbols
- Check against common password lists (haveibeenpwned API)
- Password strength meter shown to user

**Password Storage**:
- bcrypt with cost factor 12+ OR Argon2id
- Never store plain text
- Never log passwords
- Secure password reset flow

**Session Management**:
- JWT with short expiry (15 min access token)
- Refresh token with longer expiry (7 days)
- Refresh token rotation (new refresh token on each use)
- Refresh token family detection (security breach detection)
- HttpOnly cookies for tokens
- Secure flag on cookies (HTTPS only)
- SameSite=Strict for CSRF protection

**Multi-Factor Authentication** (if required):
- TOTP (Time-based One-Time Password)
- Backup codes generation
- SMS fallback option

**OAuth Integration** (if required):
- Google, GitHub, Microsoft, etc.
- Secure state parameter
- PKCE for mobile apps
- Token storage best practices

### **Authorization Patterns**

**Role-Based Access Control (RBAC)**:
- Roles: Admin, Manager, User, Guest
- Permissions: Read, Write, Delete, Manage
- Role hierarchy (Admin inherits all permissions)

**Resource-Level Authorization**:
- Check ownership before actions
- Prevent horizontal privilege escalation
- Check permissions on every request (not just frontend)

**API Key Management** (if applicable):
- API keys stored hashed
- API key rotation capability
- Rate limiting per API key
- API key scopes/permissions

### **Input Validation & Sanitization**

**Validation Strategy**:
- Schema validation (Zod, Joi, Yup)
- Type checking (TypeScript)
- Business rule validation
- Custom validators for complex rules

**Sanitization**:
- HTML sanitization (DOMPurify)
- SQL parameter escaping (ORM handles this)
- NoSQL injection prevention
- File name sanitization
- URL validation

**Common Attacks Prevention**:
- SQL Injection: Parameterized queries, ORM
- XSS: Output encoding, CSP, sanitization
- CSRF: CSRF tokens, SameSite cookies
- Open Redirect: Whitelist allowed redirects
- Path Traversal: Validate file paths
- XXE: Disable external entities in XML parsers
- Command Injection: Never execute user input
- SSRF: Validate and whitelist URLs

### **Rate Limiting Strategy**

**Per-User Limits**:
- API calls: 1000/hour
- Login attempts: 5/15 minutes
- Password reset: 3/hour
- Email sending: 10/hour

**Per-IP Limits**:
- Registration: 5/hour
- Contact form: 10/hour
- Public API: 100/hour

**Expensive Operations**:
- File uploads: 10/hour
- Report generation: 5/hour
- Bulk operations: 1/minute

**Implementation**:
- Sliding window counter (Redis)
- Token bucket algorithm
- Response headers (X-RateLimit-Remaining)
- 429 Too Many Requests status

### **Data Protection**

**Encryption**:
- Encryption at rest (database-level)
- Encryption in transit (TLS 1.3)
- Encrypted backups
- Secure key management (AWS KMS, etc.)

**PII Handling**:
- Identify all PII fields
- Minimize PII collection
- Encrypt sensitive PII
- Never log PII
- Data retention policies
- Right to be forgotten (GDPR)

**Audit Logging**:
- Log all authentication attempts
- Log all authorization failures
- Log all data modifications
- Log all admin actions
- Logs include: user ID, IP, timestamp, action
- Logs stored securely, immutable

---

## **⚡ PERFORMANCE OPTIMIZATION DEEP DIVE**

### **Frontend Performance**

**Bundle Optimization**:
- Code splitting by route
- Dynamic imports for heavy components
- Tree shaking enabled
- Dead code elimination
- Minification and compression (Brotli)
- Vendor chunks separate from app code

**Image Optimization**:
- WebP/AVIF with fallbacks
- Responsive images (srcset, sizes)
- Lazy loading below fold
- Blur-up placeholder technique
- Image CDN (Cloudinary, Imgix)
- Proper image dimensions in HTML

**Font Optimization**:
- Preload critical fonts
- font-display: swap
- Subset fonts (only needed characters)
- Variable fonts where applicable
- Self-host fonts

**JavaScript Optimization**:
- Defer non-critical JavaScript
- Inline critical JavaScript
- Remove console.logs in production
- Use Web Workers for heavy computation
- requestIdleCallback for non-critical tasks
- Debounce scroll/resize handlers
- Virtualization for long lists (react-window)

**CSS Optimization**:
- Critical CSS inlined
- Unused CSS purged
- CSS minification
- Avoid @import
- Use CSS containment
- Prefer transforms over position

**Rendering Optimization**:
- React.memo for expensive components
- useMemo for expensive computations
- useCallback for functions passed to children
- Avoid inline functions in JSX
- Key prop optimization
- Avoid deeply nested state
- Batch state updates

**Network Optimization**:
- HTTP/2 or HTTP/3
- Preconnect to required origins
- Prefetch next likely navigation
- Service Worker for caching
- Offline-first strategy (if applicable)

**Monitoring**:
- Real User Monitoring (RUM)
- Core Web Vitals tracking
- Performance budgets enforced
- Synthetic monitoring

### **Backend Performance**

**Database Optimization**:
- Query optimization (EXPLAIN ANALYZE)
- Proper indexes (B-tree, partial, covering)
- Avoid N+1 queries (eager loading)
- Connection pooling (size = ((core_count * 2) + effective_spindle_count))
- Read replicas for read-heavy apps
- Database query caching
- Materialized views for complex queries

**Caching Strategy**:
- Redis/Memcached for application cache
- Cache-aside pattern
- Write-through pattern (for critical data)
- TTL based on data update frequency
- Cache warming on deployment
- Cache invalidation on updates
- HTTP caching headers (ETag, Cache-Control)

**API Optimization**:
- Compression (gzip/Brotli)
- Pagination for large datasets
- Field filtering (GraphQL or sparse fieldsets)
- Batch endpoints for multiple operations
- Async/background jobs for slow operations
- Response size optimization
- Connection keep-alive

**Scaling**:
- Horizontal scaling ready
- Stateless application design
- Load balancer configuration
- Session storage in Redis (not memory)
- File storage in S3/Cloud Storage (not local)
- Database connection pooling

---

## **🚀 DEVOPS EXCELLENCE**

### **Docker Optimization**

**Multi-Stage Builds**:
```dockerfile
# Build stage
FROM node:18-alpine AS builder
# ... build

# Production stage
FROM node:18-alpine
COPY --from=builder ...
# Only production dependencies
```

**Image Optimization**:
- Use Alpine base images
- Minimize layers
- .dockerignore file
- Layer caching optimization
- Security scanning (Trivy, Snyk)
- Non-root user
- Health checks included

### **CI/CD Pipeline**

**GitHub Actions Workflow**:
1. **Code Quality**: Lint, format check
2. **Security**: Dependency scan, SAST
3. **Test**: Unit, integration, E2E
4. **Build**: Docker images
5. **Deploy**: Dev → Staging → Production

**Pipeline Optimization**:
- Parallel jobs
- Caching dependencies
- Fail fast strategy
- Deployment only on main/release branches
- Automatic rollback on failure

### **Environment Strategy**

**Three Environments**:
1. **Development**: Feature testing, debugging enabled
2. **Staging**: Production-like, QA testing
3. **Production**: Live, monitoring enabled

**Environment Parity**:
- Same infrastructure as code
- Same configuration structure
- Same deployment process
- Database migrations tested in staging first

### **Monitoring & Observability**

**Logging Strategy**:
- Structured logging (JSON format)
- Log levels: ERROR, WARN, INFO, DEBUG
- Correlation IDs across services
- Log aggregation (ELK, Loki, CloudWatch)
- Log retention policies
- Sensitive data redaction

**Metrics Collection**:
- Application metrics (response time, throughput, errors)
- System metrics (CPU, memory, disk, network)
- Business metrics (signups, conversions, revenue)
- Custom metrics for critical paths

**Error Tracking**:
- Sentry or similar
- Source maps for production errors
- Error grouping and deduplication
- Slack/email notifications for critical errors
- Error rate monitoring

**APM (Application Performance Monitoring)**:
- Distributed tracing
- Slow query detection
- Memory leak detection
- Performance regression alerts

**Health Checks**:
- Liveness probe (is app running?)
- Readiness probe (is app ready to serve traffic?)
- Startup probe (has app started?)
- Database connectivity check
- External service connectivity check

**Alerting**:
- Error rate threshold alerts
- Response time threshold alerts
- CPU/memory threshold alerts
- Disk space threshold alerts
- Certificate expiry alerts
- On-call rotation setup

---

## **📚 DOCUMENTATION STANDARDS**

### **README.md**

**Structure**:
```markdown
# Project Name

## Description
Brief description of what this does

## Features
- Feature 1
- Feature 2

## Tech Stack
- Frontend: React, TypeScript, Tailwind
- Backend: Node.js, Express, PostgreSQL
- Infrastructure: Docker, AWS

## Prerequisites
- Node.js 18+
- PostgreSQL 14+
- Docker

## Installation
Step-by-step setup instructions

## Environment Variables
List of required env vars with descriptions

## Running Locally
Commands to run dev servers

## Running Tests
Commands for unit, integration, E2E tests

## Deployment
Deployment instructions

## API Documentation
Link to API docs

## Contributing
Contribution guidelines

## License
License information
```

### **API Documentation**

**OpenAPI/Swagger**:
- All endpoints documented
- Request/response schemas
- Authentication described
- Error responses documented
- Example requests/responses
- Interactive API explorer

### **Architecture Documentation**

**Includes**:
- System architecture diagram
- Database ER diagram
- Data flow diagrams
- Sequence diagrams for complex flows
- Technology decisions with rationale
- Scalability considerations
- Security measures

### **Code Comments**

**When to Comment**:
- Complex algorithms (explain WHY, not WHAT)
- Business logic that's non-obvious
- Workarounds with explanation
- TODOs with issue links

**When NOT to Comment**:
- Self-explanatory code
- Obvious functionality
- Redundant comments

---

## **✅ PRE-LAUNCH CHECKLIST**

The harness will verify ALL of these before allowing production deployment:

### **Security Checklist**
- [ ] All inputs validated
- [ ] All outputs encoded
- [ ] Authentication implemented
- [ ] Authorization checked everywhere
- [ ] Rate limiting enabled
- [ ] HTTPS enforced
- [ ] Security headers configured
- [ ] Secrets in environment variables
- [ ] Dependencies scanned for vulnerabilities
- [ ] SQL injection impossible (parameterized queries)
- [ ] XSS impossible (output encoding, CSP)
- [ ] CSRF protection enabled
- [ ] Session management secure
- [ ] Password hashing secure (bcrypt/Argon2)
- [ ] File upload validation
- [ ] API keys properly managed
- [ ] Audit logging enabled
- [ ] Error messages don't leak sensitive info

### **Performance Checklist**
- [ ] Lighthouse Performance >90
- [ ] FCP <1.8s
- [ ] TTI <3.5s
- [ ] CLS <0.1
- [ ] Bundle size <200KB
- [ ] Images optimized
- [ ] Code splitting implemented
- [ ] Lazy loading implemented
- [ ] Database queries optimized
- [ ] Indexes on frequently queried columns
- [ ] Caching implemented
- [ ] API response times <200ms average

### **Accessibility Checklist**
- [ ] Keyboard navigation works
- [ ] Focus indicators visible
- [ ] Screen reader tested
- [ ] Color contrast ratios meet WCAG AA
- [ ] Alt text on all images
- [ ] ARIA labels where needed
- [ ] Heading hierarchy correct
- [ ] Forms labeled properly
- [ ] Error messages accessible
- [ ] Skip to content link present

### **Quality Checklist**
- [ ] Unit test coverage >80%
- [ ] Integration tests cover all APIs
- [ ] E2E tests cover critical flows
- [ ] All tests passing
- [ ] No console.logs in production
- [ ] No commented-out code
- [ ] ESLint passing
- [ ] TypeScript strict mode enabled
- [ ] Prettier formatting applied
- [ ] No hardcoded values

### **Functionality Checklist**
- [ ] All features work as expected
- [ ] All forms submit correctly
- [ ] All validation works
- [ ] All error handling works
- [ ] All loading states show
- [ ] All empty states show
- [ ] All success states show
- [ ] All buttons/links functional
- [ ] Navigation works correctly
- [ ] Authentication works
- [ ] Authorization works
- [ ] File uploads work
- [ ] Payments work (if applicable)
- [ ] Emails send correctly
- [ ] Real-time features work (if applicable)

### **DevOps Checklist**
- [ ] Docker images build successfully
- [ ] CI/CD pipeline configured
- [ ] Environment variables documented
- [ ] Database migrations work
- [ ] Backups configured
- [ ] Monitoring configured
- [ ] Error tracking configured
- [ ] Health checks working
- [ ] SSL certificate configured
- [ ] DNS configured correctly
- [ ] CDN configured (if applicable)
- [ ] Load balancer configured (if applicable)

### **Documentation Checklist**
- [ ] README complete with setup instructions
- [ ] API documentation complete
- [ ] Architecture documentation complete
- [ ] Environment variables documented
- [ ] Deployment guide complete
- [ ] Troubleshooting guide complete
- [ ] Changelog present

---

## **💬 FEEDBACK & ITERATION**

Tell me:

1. **Does this level of depth match what you need?**

2. **Any domains/requirements I'm still missing?**

3. **Should I add more agents or adjust the existing ones?**

4. **Do you want to start with a specific project type?** (I can customize the agent knowledge for your specific domain)

5. **Timeline expectation?** How quickly do you want the harness built?

6. **Your answers to the questions in the previous section?**

Once you give me feedback, I'll start building the harness piece by piece, starting with the orchestration dashboard so you can see the system in action!





---
Powered by [Claude Exporter](https://www.claudexporter.com)