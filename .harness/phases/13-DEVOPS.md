# 🚀 PHASE 13: DEVOPS & DEPLOYMENT

> **Prepare for production deployment. CI/CD, infrastructure, and operations.**

---

## 🎯 PURPOSE

Set up production infrastructure and deployment:
- CI/CD pipeline
- Container configuration
- Infrastructure setup
- Monitoring and logging
- Disaster recovery preparation

**Time Investment**: 2-4 hours
**Skip Risk**: Failed deployments, downtime, operational issues

---

## 📥 INPUTS REQUIRED

1. Working application (all prior phases)
2. Architecture decisions from Phase 03
3. Security requirements validated in Phase 11

---

## 📤 EXPECTED OUTPUTS

1. **CI/CD Pipeline**
   - Build automation
   - Test automation
   - Deployment automation

2. **Infrastructure Configuration**
   - Container definitions
   - Infrastructure as code
   - Environment configuration

3. **Operations Setup**
   - Monitoring
   - Logging
   - Alerting

---

## 🔄 PROCESS

### Step 1: Container Configuration

**Create Container Configuration:**
- Base image selection (minimal, secure)
- Multi-stage build (build → production)
- Non-root user
- Health check command
- Environment variable handling

**Container Best Practices Checklist:**
- [ ] Using specific base image version (not `latest`)
- [ ] Using minimal base image
- [ ] Multi-stage build implemented
- [ ] Running as non-root user
- [ ] Health check defined
- [ ] No secrets in image
- [ ] .dockerignore configured
- [ ] Layer caching optimized

### Step 2: CI/CD Pipeline Setup

**Pipeline Stages:**

```
┌─────────┐   ┌──────┐   ┌────────────┐   ┌────────────┐   ┌────────────┐
│  Push   │──▶│Build │──▶│   Test     │──▶│  Security  │──▶│   Deploy   │
└─────────┘   └──────┘   └────────────┘   └────────────┘   └────────────┘
                │              │                │                │
           Compile        Unit tests      Dependency       Deploy to
           Lint           Integration     scan             environment
           Type check     E2E             SAST
           Build image                    Image scan
```

**Build Stage:**
- [ ] Install dependencies
- [ ] Run linting
- [ ] Run type checking
- [ ] Compile/build
- [ ] Build container image
- [ ] Push image to registry

**Test Stage:**
- [ ] Run unit tests
- [ ] Run integration tests
- [ ] Run E2E tests (on PR merge)
- [ ] Report coverage

**Security Stage:**
- [ ] Scan dependencies for vulnerabilities
- [ ] Run SAST (Static Application Security Testing)
- [ ] Scan container image
- [ ] Block on critical vulnerabilities

**Deploy Stage:**
- [ ] Deploy to staging automatically
- [ ] Run smoke tests
- [ ] Manual approval for production (optional)
- [ ] Deploy to production
- [ ] Run production smoke tests
- [ ] Rollback on failure

### Step 3: Environment Configuration

**Environment Variables:**

| Variable Type | Example | Management |
|---------------|---------|------------|
| Application config | PORT, LOG_LEVEL | Environment variables |
| Service URLs | API_URL, DB_HOST | Environment variables |
| Secrets | DB_PASSWORD, JWT_SECRET | Secret manager |
| Feature flags | ENABLE_FEATURE_X | Environment variables |

**Per-Environment Config:**
- Development: Local/dev services
- Staging: Staging services, test data
- Production: Production services, real data

**Environment Setup Checklist:**
- [ ] Environment variables documented
- [ ] Secrets in secret manager
- [ ] Different values per environment
- [ ] No secrets in code or images

### Step 4: Database Operations

**Database for Production:**
- [ ] Managed database service (or properly configured)
- [ ] Automatic backups enabled
- [ ] Point-in-time recovery available
- [ ] Monitoring enabled
- [ ] Connection pooling configured

**Migration Strategy:**
- [ ] Migrations run before deployment
- [ ] Backward-compatible migrations
- [ ] Rollback plan for migrations
- [ ] Migration testing in staging

### Step 5: Logging Setup

**Log Aggregation:**
- [ ] Centralized log collection
- [ ] Structured JSON logging
- [ ] Log levels configured (INFO in prod)
- [ ] Log retention policy defined
- [ ] Sensitive data excluded

**Log Content:**
- Request logs (method, path, status, duration)
- Error logs (with stack traces and context)
- Security events
- Business events (key actions)

### Step 6: Monitoring Setup

**Application Monitoring:**
- [ ] Request rate
- [ ] Error rate
- [ ] Response time (P50, P95, P99)
- [ ] Active users
- [ ] Key business metrics

**Infrastructure Monitoring:**
- [ ] CPU usage
- [ ] Memory usage
- [ ] Disk usage
- [ ] Network I/O
- [ ] Container health

**Database Monitoring:**
- [ ] Query performance
- [ ] Connection pool usage
- [ ] Slow query log
- [ ] Replication lag (if applicable)

### Step 7: Alerting Setup

**Configure Alerts For:**

| Condition | Severity | Action |
|-----------|----------|--------|
| Service down | Critical | Page on-call |
| Error rate > 5% | High | Page on-call |
| P95 latency > 1s | High | Notify team |
| P95 latency > 500ms | Medium | Log for review |
| Disk > 80% | Medium | Notify team |
| Memory > 90% | High | Notify team |
| Certificate expiring | Medium | Notify team |
| Backup failed | High | Notify team |

**Alert Best Practices:**
- [ ] Every alert is actionable
- [ ] Runbooks linked to alerts
- [ ] Alert fatigue avoided
- [ ] Escalation policy defined

### Step 8: CDN & Static Assets

**CDN Setup:**
- [ ] CDN configured for static assets
- [ ] Proper cache headers
- [ ] HTTPS enabled
- [ ] Custom domain (optional)

**Asset Delivery:**
- [ ] Images served via CDN
- [ ] JS/CSS served via CDN
- [ ] Fonts served via CDN
- [ ] Cache busting with hashes

### Step 9: SSL/TLS Configuration

**Certificate Setup:**
- [ ] Valid SSL certificate
- [ ] Auto-renewal configured
- [ ] TLS 1.2+ required
- [ ] HSTS header configured
- [ ] Certificate monitoring

### Step 10: Backup & Recovery

**Backup Configuration:**
- [ ] Database backups automated
- [ ] Backup verified (test restore)
- [ ] Backup retention defined
- [ ] Offsite backup location
- [ ] Recovery procedure documented

**Recovery Testing:**
- [ ] Document recovery steps
- [ ] Test recovery in staging
- [ ] Measure recovery time
- [ ] Update documentation

### Step 11: Runbooks

**Create Runbooks For:**
- [ ] Deployment procedure
- [ ] Rollback procedure
- [ ] Service restart
- [ ] Scale up/down
- [ ] Database recovery
- [ ] Common issues and fixes
- [ ] Incident response

### Step 12: Pre-Production Checklist

**Before First Production Deploy:**
- [ ] All secrets configured
- [ ] DNS configured
- [ ] SSL certificate installed
- [ ] Database provisioned
- [ ] Backups configured
- [ ] Monitoring active
- [ ] Logging active
- [ ] Alerts configured
- [ ] Runbooks written

---

## ✅ QUALITY GATE

Before proceeding to Phase 14, verify:

### CI/CD
- [ ] Build pipeline working
- [ ] Tests run in pipeline
- [ ] Security scanning in pipeline
- [ ] Deployment automated
- [ ] Rollback possible

### Infrastructure
- [ ] Containers properly configured
- [ ] Environment variables set
- [ ] Secrets in secret manager
- [ ] Database configured
- [ ] CDN configured
- [ ] SSL configured

### Operations
- [ ] Logging centralized
- [ ] Monitoring active
- [ ] Alerts configured
- [ ] Backups automated
- [ ] Runbooks written

- [ ] ACTIVE_PROJECT.md updated
- [ ] Git commit made

---

## 📚 KNOWLEDGE REFERENCES

- `.harness/knowledge/DEVOPS_MASTERY.md` - Complete DevOps guide

---

## ⚠️ COMMON MISTAKES

### Mistake 1: Secrets in Code/Images
Always use secret managers.

### Mistake 2: No Rollback Plan
Every deployment needs a rollback.

### Mistake 3: Alerting on Everything
Alert fatigue leads to ignored alerts.

### Mistake 4: Untested Backups
Test restores regularly.

### Mistake 5: Manual Deployments
Automate everything.

---

**Phase Complete? Update ACTIVE_PROJECT.md and proceed to Phase 14: Documentation.**
