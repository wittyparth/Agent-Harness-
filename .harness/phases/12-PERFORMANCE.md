# ⚡ PHASE 12: PERFORMANCE OPTIMIZATION

> **Optimize for speed and efficiency. Make it fast.**

---

## 🎯 PURPOSE

Optimize application performance:
- Frontend loading and interactivity
- Backend response times
- Database query optimization
- Resource usage optimization

**Time Investment**: 2-4 hours
**Skip Risk**: Slow application, poor user experience, high costs

---

## 📥 INPUTS REQUIRED

1. Working application (all prior phases)
2. Performance baselines from Phase 10
3. Non-functional requirements from Phase 02

---

## 📤 EXPECTED OUTPUTS

1. **Performance Improvements**
   - Optimizations implemented
   - Metrics improved

2. **Performance Documentation**
   - Current metrics
   - Optimization decisions
   - Monitoring setup

---

## 🔄 PROCESS

### Step 1: Frontend Performance Audit

**Run Lighthouse Audit:**
- Performance score
- First Contentful Paint
- Largest Contentful Paint
- Time to Interactive
- Total Blocking Time
- Cumulative Layout Shift

**Performance Targets:**
| Metric | Target | Maximum |
|--------|--------|---------|
| Lighthouse Performance | > 90 | > 80 |
| First Contentful Paint | < 1.8s | < 3s |
| Largest Contentful Paint | < 2.5s | < 4s |
| Time to Interactive | < 3.5s | < 5s |
| Total Blocking Time | < 200ms | < 600ms |
| Cumulative Layout Shift | < 0.1 | < 0.25 |

### Step 2: JavaScript Optimization

**Bundle Analysis:**
- [ ] Analyze bundle size
- [ ] Identify large dependencies
- [ ] Remove unused dependencies
- [ ] Tree shake unused code

**Code Splitting:**
- [ ] Route-based code splitting
- [ ] Dynamic imports for heavy components
- [ ] Lazy load below-the-fold content

**Optimization Techniques:**
- [ ] Minification enabled
- [ ] Dead code elimination
- [ ] Modern bundle for modern browsers
- [ ] Legacy bundle only if needed

**Target:**
- Main bundle < 100KB gzipped
- Total JS < 300KB gzipped

### Step 3: CSS Optimization

**CSS Audit:**
- [ ] Remove unused CSS
- [ ] Minify CSS
- [ ] Inline critical CSS
- [ ] Defer non-critical CSS

**Optimization Techniques:**
- [ ] Use CSS containment where applicable
- [ ] Avoid expensive selectors
- [ ] Use efficient layout (flex/grid)
- [ ] Minimize reflows

### Step 4: Image Optimization

**Image Audit:**
- [ ] All images compressed
- [ ] Using modern formats (WebP, AVIF)
- [ ] Responsive images (srcset)
- [ ] Lazy loading for offscreen images
- [ ] Correct dimensions specified
- [ ] Using image CDN (if applicable)

**Optimization Techniques:**
- [ ] Compress all images
- [ ] Serve WebP with fallback
- [ ] Use correct image sizes per breakpoint
- [ ] Lazy load images below fold
- [ ] Use placeholder/blur for loading

### Step 5: Font Optimization

**Font Audit:**
- [ ] Minimal font families (1-2)
- [ ] Minimal weights loaded
- [ ] Font-display: swap
- [ ] Preload critical fonts
- [ ] Self-hosted or fast CDN
- [ ] Subset fonts (if applicable)

### Step 6: Network Optimization

**Verify:**
- [ ] Compression enabled (Brotli or Gzip)
- [ ] HTTP/2 or HTTP/3 enabled
- [ ] CDN for static assets
- [ ] Proper cache headers
- [ ] Keep-alive connections

**Cache Strategy:**
- Immutable assets (hashed): Cache forever
- HTML: Short cache or no-cache
- API responses: Cache based on data volatility

### Step 7: Backend Performance Audit

**API Response Times:**
- Measure all endpoints
- Identify slow endpoints (> 200ms P95)
- Profile slow endpoints

**Target Response Times:**
| Endpoint Type | Target P95 | Maximum P95 |
|---------------|------------|-------------|
| Simple read | < 50ms | < 100ms |
| Complex read | < 100ms | < 200ms |
| List with pagination | < 100ms | < 200ms |
| Creation | < 200ms | < 500ms |
| Update | < 150ms | < 300ms |

### Step 8: Database Optimization

**Query Analysis:**
- [ ] Identify slow queries
- [ ] Add missing indexes
- [ ] Optimize N+1 queries
- [ ] Use eager loading appropriately
- [ ] Review query plans

**Index Audit:**
- [ ] All foreign keys indexed
- [ ] Query columns indexed
- [ ] Composite indexes where needed
- [ ] No unused indexes

**Connection Optimization:**
- [ ] Connection pooling configured
- [ ] Pool size appropriate
- [ ] Connection timeout set

### Step 9: Caching Implementation

**Cache Strategy:**

| Data Type | Cache Location | TTL |
|-----------|----------------|-----|
| Static assets | CDN + Browser | Long (days/forever) |
| User session | Memory/Redis | Token lifetime |
| Frequent reads | Redis | Minutes to hours |
| Expensive computations | Redis | Based on staleness tolerance |

**Implement Caching For:**
- [ ] Session data
- [ ] Frequently accessed data
- [ ] Expensive computations
- [ ] External API responses

### Step 10: Resource Optimization

**Memory Usage:**
- [ ] No memory leaks
- [ ] Appropriate instance sizing
- [ ] Garbage collection tuned (if applicable)

**CPU Usage:**
- [ ] No CPU-bound operations in request path
- [ ] Heavy computations in background jobs
- [ ] Async processing where appropriate

### Step 11: Load Testing

**Conduct Load Tests:**
- Simulate expected concurrent users
- Measure response times under load
- Identify breaking points
- Document capacity limits

**Verify System Handles:**
- Normal load: All metrics within target
- Peak load: Graceful degradation
- Spike: Doesn't crash, recovers

### Step 12: Performance Monitoring Setup

**Set Up Monitoring For:**
- Response time (P50, P95, P99)
- Error rate
- Throughput
- Database query time
- Cache hit rate
- Memory/CPU usage

**Set Up Alerts For:**
- Response time exceeds threshold
- Error rate exceeds threshold
- Database slow queries
- Memory/CPU high usage

---

## ✅ QUALITY GATE

Before proceeding to Phase 13, verify:

### Frontend Performance
- [ ] Lighthouse Performance > 90
- [ ] LCP < 2.5s
- [ ] CLS < 0.1
- [ ] TTI < 3.5s
- [ ] Bundle size optimized
- [ ] Images optimized
- [ ] Fonts optimized

### Backend Performance
- [ ] API P95 < 200ms
- [ ] Slow queries optimized
- [ ] Indexes added
- [ ] Connection pooling configured
- [ ] Caching implemented

### Infrastructure
- [ ] CDN configured
- [ ] Compression enabled
- [ ] Cache headers correct
- [ ] Load testing completed

### Monitoring
- [ ] Performance metrics tracked
- [ ] Alerts configured
- [ ] Dashboards created

- [ ] ACTIVE_PROJECT.md updated
- [ ] Git commit made

---

## 📚 KNOWLEDGE REFERENCES

- `.harness/knowledge/FRONTEND_MASTERY.md` - Frontend performance
- `.harness/knowledge/BACKEND_MASTERY.md` - Backend performance
- `.harness/knowledge/DATABASE_MASTERY.md` - Database optimization

---

## ⚠️ COMMON MISTAKES

### Mistake 1: Premature Optimization
Measure first, then optimize what matters.

### Mistake 2: Ignoring Mobile
Mobile devices are slower. Test on real devices.

### Mistake 3: Caching Forever
Data changes. Set appropriate TTLs.

### Mistake 4: Over-Indexing
Indexes slow writes. Add only what's needed.

### Mistake 5: No Load Testing
Performance under load differs from single user.

---

**Phase Complete? Update ACTIVE_PROJECT.md and proceed to Phase 13: DevOps.**
