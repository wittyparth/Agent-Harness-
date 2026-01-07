# 🚀 DEVOPS MASTERY

> **Complete knowledge for deploying and operating production systems.**
> **What a 20+ year veteran SRE/DevOps engineer knows about keeping systems running.**

---

## 🎯 CORE MISSION

DevOps bridges development and operations. Your job is to ensure:
- **Reliability**: System is always available
- **Scalability**: System handles growth
- **Security**: System is protected
- **Observability**: You know what's happening
- **Efficiency**: Resources aren't wasted
- **Speed**: Deployments are fast and safe

---

## 📋 COMPLETE DEVOPS IMPLEMENTATION GUIDE

### PHASE 1: ENVIRONMENT STRATEGY

#### 1.1 Environment Structure

| Environment | Purpose | Data | Access |
|-------------|---------|------|--------|
| **Local** | Developer machines | Fake/seed data | Developers |
| **Development** | Integration testing | Fake data | Developers |
| **Staging** | Pre-production testing | Anonymized production copy | Team |
| **Production** | Real users | Real data | Restricted |

#### 1.2 Environment Parity

**Keep All Environments Similar:**
- Same OS and versions
- Same database type and version
- Same service configurations
- Same environment variable structure
- Same networking model

**What Can Differ:**
- Scale (fewer instances in staging)
- Data (anonymized in non-production)
- Third-party services (sandbox vs production keys)
- Resource allocation (smaller in non-prod)

#### 1.3 Configuration Management

**Environment Variables for:**
- Database connection strings
- API keys and secrets
- Feature flags
- Service URLs
- Log levels

**Configuration Hierarchy:**
1. Default values in code
2. Environment-specific config files
3. Environment variables (override files)
4. Secret manager (for sensitive values)

**Never In Code:**
- Credentials
- API keys
- Environment-specific URLs
- Secrets of any kind

---

### PHASE 2: CONTAINERIZATION

#### 2.1 Container Strategy

**Why Containers:**
- Consistent environment across dev/staging/prod
- Isolated dependencies
- Easy scaling
- Portable across cloud providers

#### 2.2 Container Best Practices

**Image Building:**
- Use specific base image versions (not `latest`)
- Use minimal base images (alpine, distroless)
- Multi-stage builds (build in one, run in another)
- Don't run as root
- Include health check commands
- Minimize layers
- Order commands for cache efficiency

**Runtime:**
- Set resource limits (CPU, memory)
- Use read-only file systems where possible
- Don't store state in containers
- Log to stdout/stderr
- Handle signals properly (graceful shutdown)

**Security:**
- Scan images for vulnerabilities
- Use signed images
- Don't include secrets in images
- Update base images regularly

#### 2.3 Container Composition

**Development:**
- Use compose for local multi-service setup
- Include database, cache, other dependencies
- Volume mounts for hot reload
- Network for service communication

**Production:**
- Use orchestration (Kubernetes, ECS, Cloud Run)
- Service discovery
- Load balancing
- Auto-scaling

---

### PHASE 3: CI/CD PIPELINE

#### 3.1 Pipeline Stages

```
[Code Push] → [Build] → [Test] → [Security Scan] → [Deploy Staging] → [Deploy Production]
                 ↓         ↓            ↓                  ↓                   ↓
              Compile    Unit      Dependency           Smoke              Smoke
              Lint       Integration  SAST              E2E                 Monitor
              Type check  E2E       Container
```

#### 3.2 Pipeline Stage Details

**Build Stage:**
- Compile/transpile code
- Run linters
- Run type checking
- Generate build artifacts
- Build container images
- Tag with commit SHA

**Test Stage:**
- Unit tests (fast, every commit)
- Integration tests (every PR)
- E2E tests (before deploy)
- Coverage reporting

**Security Stage:**
- Dependency vulnerability scan
- SAST (static application security testing)
- Container image scan
- Secrets detection

**Deploy Stage:**
- Deploy to target environment
- Run smoke tests
- Health check verification
- Rollback on failure

#### 3.3 Deployment Strategies

| Strategy | Description | Risk | Rollback Speed |
|----------|-------------|------|----------------|
| **Rolling** | Replace instances gradually | Low | Medium |
| **Blue/Green** | Deploy parallel, switch traffic | Low | Fast |
| **Canary** | Small % traffic first, expand | Lowest | Fast |
| **Recreate** | Stop all, deploy new | High | Slow |

**Recommended Default:** Rolling or Blue/Green

**Canary For:**
- Critical services
- High-traffic applications
- When extra caution needed

#### 3.4 Deployment Best Practices

**Pre-Deployment:**
- Database migrations run first
- Backward compatible migrations only
- Feature flags for gradual rollout

**During Deployment:**
- Monitor error rates
- Watch response times
- Check resource usage
- Verify health checks pass

**Post-Deployment:**
- Smoke tests pass
- Alert on anomalies
- Easy rollback available
- Keep previous version ready

---

### PHASE 4: INFRASTRUCTURE AS CODE

#### 4.1 IaC Principles

**Everything in Code:**
- Infrastructure definitions
- Network configurations
- Security groups
- Monitoring setup
- All environments

**Benefits:**
- Reproducible
- Version controlled
- Reviewable
- Testable
- Self-documenting

#### 4.2 IaC Best Practices

**Structure:**
- Modular (reusable components)
- Environment-specific variables
- Secrets via secret manager (not in code)
- State management (remote, locked)

**Change Management:**
- Preview changes before apply
- Review infrastructure changes like code
- Apply in stages (dev → staging → prod)
- Document significant changes

**Drift Management:**
- Regular drift detection
- Reconcile or document intentional drift
- Automated enforcement where possible

---

### PHASE 5: MONITORING & OBSERVABILITY

#### 5.1 The Three Pillars

**Metrics:**
- Quantitative measurements over time
- What: CPU, memory, request rate, error rate, latency
- For: Dashboards, alerts, capacity planning

**Logs:**
- Discrete events with context
- What: Requests, errors, business events
- For: Debugging, audit, forensics

**Traces:**
- Request flow through systems
- What: Request path, timing per service
- For: Performance debugging, bottleneck identification

#### 5.2 Key Metrics to Monitor

**Infrastructure Metrics:**
- CPU utilization
- Memory usage
- Disk I/O and usage
- Network I/O
- Container restarts

**Application Metrics (RED Method):**
- **R**ate: Requests per second
- **E**rrors: Failed requests per second
- **D**uration: Latency (p50, p95, p99)

**Business Metrics:**
- Signup rate
- Active users
- Transactions completed
- Revenue (if applicable)

**Database Metrics:**
- Query latency
- Connection pool usage
- Slow query count
- Replication lag

**External Service Metrics:**
- Response time
- Error rate
- Availability

#### 5.3 Logging Best Practices

**Log Format (Structured JSON):**
```json
{
  "timestamp": "2024-01-15T10:30:00.123Z",
  "level": "error",
  "message": "Failed to process order",
  "service": "order-service",
  "request_id": "abc-123",
  "user_id": "user-456",
  "order_id": "order-789",
  "error": "Payment declined",
  "stack_trace": "..."
}
```

**What to Log:**
- Request/response (without sensitive data)
- Errors with context
- Business events
- Performance metrics
- Security events

**What NOT to Log:**
- Passwords, tokens, secrets
- Personal data (unless required)
- Excessive debug info in production
- High-volume events that provide no value

**Log Levels in Production:**
- ERROR: Operation failed
- WARN: Unexpected but handled
- INFO: Key business events
- (DEBUG/TRACE off or very limited)

#### 5.4 Alerting Strategy

**Alert on Symptoms, Not Causes:**
- Alert: "5% of requests failing"
- Don't alert: "CPU at 80%"

**Good Alerts Are:**
- Actionable (someone can do something)
- Timely (before users notice)
- Clear (what's wrong, where to look)
- Rare (alert fatigue is real)

**Alert Severity:**
| Severity | Response Time | Examples |
|----------|---------------|----------|
| Critical | Immediate (page) | Service down, data loss |
| High | Within 1 hour | High error rate, degraded performance |
| Medium | Within 4 hours | Growing queue, elevated latency |
| Low | Next business day | Non-critical warnings |

**Anti-Patterns:**
- Alerting on everything
- Alerts that aren't actionable
- Alerts without runbooks
- Ignoring alerts regularly

---

### PHASE 6: DATABASE OPERATIONS

#### 6.1 Database Deployment

**Migration Process:**
1. Apply migrations to staging first
2. Test thoroughly
3. Schedule production migration
4. Take backup before migration
5. Apply migration
6. Verify application works
7. Monitor for issues

**Zero-Downtime Migrations:**
- Add columns as nullable first
- Deploy code that handles both states
- Populate new columns
- Deploy code using new columns
- Remove old columns in later migration

#### 6.2 Backup Strategy

**Backup Schedule:**
- Full backup: Daily
- Incremental: Hourly
- Point-in-time recovery: Continuous (if needed)

**Backup Storage:**
- Multiple locations
- Different cloud region
- Encrypted
- Tested regularly

**Recovery Testing:**
- Monthly recovery drills
- Document exact steps
- Measure RTO (recovery time)
- Verify data integrity

#### 6.3 Database Scaling

**Read Scaling:**
- Read replicas
- Connection pooling
- Caching layer

**Write Scaling:**
- Vertical scaling (bigger instance)
- Sharding (complex, last resort)
- Queue writes (eventual consistency)

---

### PHASE 7: SECURITY OPERATIONS

#### 7.1 Security Hardening

**Network Security:**
- Firewall rules (least privilege)
- Private subnets for databases
- VPN for administrative access
- DDoS protection

**Server Security:**
- Minimal installed packages
- Regular patching
- Disabled unnecessary ports
- SSH key authentication only

**Container Security:**
- Non-root users
- Read-only file systems
- Security scanning
- Regular base image updates

#### 7.2 Secret Management

**Production Secrets:**
- Use dedicated secret manager
- Rotate regularly
- Audit access
- Never in environment files or code

**Secret Rotation:**
| Secret Type | Rotation Frequency |
|-------------|-------------------|
| API keys | 90 days |
| Database passwords | 90 days |
| JWT signing keys | 6-12 months |
| SSL certificates | Before expiry (automate) |

#### 7.3 Access Control

**Principle of Least Privilege:**
- Minimal required access
- Separate accounts per environment
- Time-limited access for debugging
- Audit all access

**Production Access:**
- Require justification
- Time-limited
- Logged
- Multi-person approval for critical actions

---

### PHASE 8: INCIDENT MANAGEMENT

#### 8.1 Incident Response Process

**1. Detection**
- Monitoring alerts
- User reports
- Automated checks

**2. Triage**
- Assess severity
- Identify impact
- Assign responders

**3. Communication**
- Status page update
- Stakeholder notification
- Customer communication (if needed)

**4. Resolution**
- Diagnose root cause
- Implement fix
- Verify resolution
- Monitor for recurrence

**5. Post-Incident**
- Incident report
- Blameless retrospective
- Action items
- Knowledge base update

#### 8.2 Incident Severity Levels

| Severity | Definition | Response Time | Example |
|----------|------------|---------------|---------|
| SEV1 | Service down | Immediate | Complete outage |
| SEV2 | Major degradation | 15 minutes | 50% of requests failing |
| SEV3 | Minor issue | 1 hour | Non-critical feature broken |
| SEV4 | Minimal impact | 4 hours | Cosmetic issues |

#### 8.3 Runbooks

**Every Service Should Have:**
- How to check health
- How to restart
- How to scale up/down
- How to rollback
- How to access logs
- Common issues and fixes
- Escalation contacts

---

### PHASE 9: SCALING & PERFORMANCE

#### 9.1 Scaling Strategies

**Horizontal Scaling (Scale Out):**
- Add more instances
- Works for stateless services
- Requires load balancer

**Vertical Scaling (Scale Up):**
- Bigger instance
- Simpler but has limits
- Good for databases initially

**Auto-Scaling:**
- Scale based on metrics (CPU, requests)
- Set min and max instances
- Scale out fast, scale in slow
- Handle warm-up time

#### 9.2 Scaling Preparation

**Before You Need to Scale:**
- Stateless application design
- Externalized sessions
- Database connection pooling
- CDN for static assets
- Caching layer ready
- Load testing completed

#### 9.3 Performance Optimization

**Application Level:**
- Optimize slow queries
- Add appropriate caching
- Reduce payload sizes
- Compress responses
- Lazy load where appropriate

**Infrastructure Level:**
- Right-size instances
- Use CDN
- Geographic distribution
- Database read replicas

---

### PHASE 10: DISASTER RECOVERY

#### 10.1 DR Planning

**Define:**
- RTO: Recovery Time Objective (how fast)
- RPO: Recovery Point Objective (data loss tolerance)

**Common Targets:**
| Tier | RTO | RPO | Cost |
|------|-----|-----|------|
| Tier 1 (Critical) | Minutes | Near-zero | High |
| Tier 2 (Important) | Hours | Hours | Medium |
| Tier 3 (Standard) | Days | Daily | Low |

#### 10.2 DR Strategies

**Backup/Restore:**
- Restore from backups
- Slowest RTO
- Lowest cost

**Pilot Light:**
- Minimal standby environment
- Data replicated
- Scale up when needed

**Warm Standby:**
- Reduced-scale environment running
- Quick scale-up

**Active-Active:**
- Full capacity in multiple regions
- Automatic failover
- Highest cost and complexity

#### 10.3 DR Testing

**Regular DR Drills:**
- Schedule quarterly
- Document process
- Measure actual RTO
- Identify gaps
- Update runbooks

---

## ✅ DEVOPS QUALITY CHECKLIST

Before marking DevOps complete:

### CI/CD
- [ ] Automated build pipeline
- [ ] Automated test execution
- [ ] Security scanning in pipeline
- [ ] Automated deployments
- [ ] Rollback capability
- [ ] Environment promotion

### Infrastructure
- [ ] Infrastructure as code
- [ ] Environments are consistent
- [ ] Secrets properly managed
- [ ] Network security configured
- [ ] SSL/TLS everywhere

### Monitoring
- [ ] Application metrics collected
- [ ] Logs centralized
- [ ] Alerts configured
- [ ] Dashboards created
- [ ] On-call rotation set

### Operations
- [ ] Runbooks documented
- [ ] Backup strategy implemented
- [ ] Backup restoration tested
- [ ] Incident process defined
- [ ] DR plan exists

### Security
- [ ] Access control implemented
- [ ] Secrets rotated
- [ ] Security patches current
- [ ] Vulnerability scanning active

---

## 💡 HARD-LEARNED LESSONS

1. **Automate everything**: If you do it twice, automate it.

2. **Test your backups**: Untested backups are Schrödinger's backups.

3. **Monitor from day one**: Adding monitoring later means missed issues.

4. **Alerts should be actionable**: Every alert should have a response.

5. **Rollback is not optional**: Every deployment needs a rollback plan.

6. **Incidents happen**: Have a process before you need it.

7. **Documentation decays**: Keep runbooks updated.

8. **Cost matters**: Right-size resources, delete unused.

9. **Security is continuous**: Not a one-time setup.

10. **Chaos engineering works**: Regularly test failure scenarios.

---

**Apply this knowledge to every DevOps decision.**
