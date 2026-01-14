# Changelog

## 2026
- 2026-01-14: Added info to README (commit 11e3a29)
- 2026-01-14: Updated dates to 2026
    - [x] 2026 September 11th-13th!  The location is at Crosswinds RC Club in Parker, CO.
    - [x] New Video Link:  https://youtu.be/-r7s-4r3aWs
    - [x] Google Pin Location:  https://maps.app.goo.gl/v9A9J32BEJeSUhoc6
    - [ ] RVs:  Drycamping only and limited to 10 RVs.  Must reserve with Adam after registration
    - [ ] Registration including Saturday Night Pilot Dinner:  $35
    - [ ] Power:  Limited AC power
    - [ ] Crosswinds Website:  crosswindsrc.com
    - [ ] Shade:  Limited Shade

## 2025 (frozen)
- Final commit: be95388 (Final version of 2025 website)

### Planned / TODO

#### Security Hardening
- [x] Block access to `/.git/*` and other sensitive paths on web server
- [x] Run site through https://securityheaders.com and record baseline score
- [ ] Add baseline HTTP security headers:
  - [ ] `Strict-Transport-Security: max-age=31536000; includeSubDomains; preload`
        - (Only after confirming HTTPS is enforced everywhere)
  - [ ] `Content-Security-Policy`
        - Start permissive, tighten iteratively
  - [ ] `X-Content-Type-Options: nosniff`
  - [ ] `Referrer-Policy: strict-origin-when-cross-origin`
  - [ ] `Permissions-Policy`
        - Disable unused browser features
  - [ ] `X-Frame-Options: DENY`
        - Or `frame-ancestors 'none'` via CSP
- [ ] Document security header configuration in `docs/01-security.md`
- [ ] Re-run security scan and record improved score

#### Performance Improvements
- [ ] Optimize images:
  - [ ] Convert images to WebP / AVIF
  - [ ] Resize images to actual display dimensions
  - [ ] Add explicit `width` and `height` attributes
  - [ ] Lazy-load non-hero images using:
        - `loading="lazy"`
        - `decoding="async"`
- [ ] Enable aggressive caching:
  - [ ] Long cache headers for `/img/*`
  - [ ] Long cache headers for CSS assets
  - [ ] Use file versioning / cache busting where applicable
- [ ] Enable compression:
  - [ ] Brotli for HTML / CSS
  - [ ] Gzip fallback where Brotli unavailable
- [ ] Reduce render-blocking:
  - [ ] Minimize CSS payload
  - [ ] Move non-critical JavaScript to `defer`
- [ ] Add CDN:
  - [ ] Front site with CloudFront or Cloudflare
  - [ ] Enable CDN-level caching
  - [ ] Leverage CDN for security headers and optional WAF
- [ ] Document performance changes in `docs/02-performance.md`
- [ ] Run Lighthouse and record baseline vs improved scores

#### Security Baseline
- 2026-01-14: Initial securityheaders.com scan
  - Grade: **F**
  - Missing headers:
    - Strict-Transport-Security
    - Content-Security-Policy
    - X-Frame-Options
    - X-Content-Type-Options
    - Referrer-Policy
    - Permissions-Policy
  - Purpose: establish pre-hardening baseline before 2026 improvements

