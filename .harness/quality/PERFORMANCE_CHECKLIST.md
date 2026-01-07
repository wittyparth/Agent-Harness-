# ⚡ PERFORMANCE CHECKLIST

> **Quality gate for performance optimization (Phase 12).**

---

## ✅ Frontend Performance

### Core Web Vitals
- [ ] Largest Contentful Paint (LCP) < 2.5s
- [ ] First Input Delay (FID) < 100ms
- [ ] Cumulative Layout Shift (CLS) < 0.1
- [ ] Time to Interactive (TTI) < 3.5s
- [ ] First Contentful Paint (FCP) < 1.8s

### Lighthouse Score
- [ ] Performance score > 90
- [ ] Accessibility score > 90
- [ ] Best Practices score > 90
- [ ] SEO score > 90 (if public)

### JavaScript
- [ ] Main bundle < 100KB gzipped
- [ ] Total JS < 300KB gzipped
- [ ] Code splitting by route
- [ ] Dynamic imports for heavy components
- [ ] Tree shaking working
- [ ] No unused dependencies

### CSS
- [ ] Total CSS < 50KB gzipped
- [ ] Critical CSS inlined
- [ ] No unused CSS
- [ ] CSS minified

### Images
- [ ] All images compressed
- [ ] Using WebP or AVIF
- [ ] Responsive images (srcset)
- [ ] Lazy loading below fold
- [ ] Dimensions specified

### Fonts
- [ ] Minimal font files (≤ 3)
- [ ] Font-display: swap
- [ ] Preload critical fonts
- [ ] Subset fonts (if applicable)

### Rendering
- [ ] No layout shifts after load
- [ ] Above-fold content prioritized
- [ ] Skeleton loaders for async content
- [ ] No render-blocking resources

---

## ✅ Backend Performance

### Response Times
- [ ] P50 < 100ms
- [ ] P95 < 200ms
- [ ] P99 < 500ms
- [ ] No endpoint > 1s regularly

### Database
- [ ] No N+1 queries
- [ ] Queries < 50ms average
- [ ] Indexes on query columns
- [ ] Connection pooling configured
- [ ] Query plans analyzed
- [ ] Slow query log enabled

### Caching
- [ ] Appropriate caching strategy
- [ ] Cache hit rate > 80%
- [ ] Cache invalidation working
- [ ] No stale data issues

### Resource Usage
- [ ] Memory usage stable
- [ ] No memory leaks
- [ ] CPU usage reasonable
- [ ] Connection pool not exhausted

---

## ✅ Network Performance

### Compression
- [ ] Brotli or Gzip enabled
- [ ] All text resources compressed
- [ ] Compression ratio > 70%

### Caching
- [ ] Static assets cached (long TTL)
- [ ] Hashed filenames for cache busting
- [ ] ETags working
- [ ] Cache-Control headers correct

### CDN
- [ ] Static assets on CDN
- [ ] CDN cache hit rate high
- [ ] Geographic distribution
- [ ] HTTPS on CDN

### HTTP
- [ ] HTTP/2 or HTTP/3 enabled
- [ ] Keep-alive connections
- [ ] Minimal redirects

---

## ✅ Load Testing

### Load Test Results
- [ ] Normal load: All targets met
- [ ] Peak load: Acceptable degradation
- [ ] Spike load: Recovers gracefully
- [ ] Breaking point identified

### Scalability
- [ ] Auto-scaling configured (if needed)
- [ ] Horizontal scaling works
- [ ] Database can scale
- [ ] Cache can scale

---

## ✅ Monitoring

### Performance Monitoring
- [ ] Response times tracked
- [ ] Error rates tracked
- [ ] Throughput tracked
- [ ] Resource usage tracked

### Alerts
- [ ] Alert on response time increase
- [ ] Alert on error rate increase
- [ ] Alert on resource exhaustion

### Dashboards
- [ ] Real-time metrics visible
- [ ] Historical trends available
- [ ] Bottlenecks identifiable

---

## 📋 Metrics Summary

Document current metrics:

| Metric | Target | Current | Status |
|--------|--------|---------|--------|
| LCP | < 2.5s | | |
| CLS | < 0.1 | | |
| Lighthouse Score | > 90 | | |
| Bundle Size | < 100KB | | |
| API P95 | < 200ms | | |
| Cache Hit Rate | > 80% | | |

---

## 📋 Sign-off

Performance verified:

| Item | Status | Notes |
|------|--------|-------|
| Frontend Performance | [ ] Met | |
| Backend Performance | [ ] Met | |
| Network Performance | [ ] Met | |
| Load Testing | [ ] Complete | |
| Monitoring | [ ] Active | |

---

**All targets must be met before launch.**
