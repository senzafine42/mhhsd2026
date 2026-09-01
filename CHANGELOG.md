# Changelog

## 2026
- 2026-08-31: Reconciled repository changelog with the live 2026 website
    - [x] Modernized site design and removed Bootstrap dependency in favor of custom responsive CSS
    - [x] Redesigned homepage around the 2026 event flyer
    - [x] Added responsive desktop/mobile navigation
    - [x] Added event highlights cards for Drag Racing, Auto Contest, and Camping
    - [x] Added additional RC helicopter friends / event photo section
    - [x] Added embedded Parker, CO weather forecast
    - [x] Added embedded Google Map for Crosswinds RC Club
    - [x] Added nearby hotel links to the Field Location page
    - [x] Added Crosswinds RC Club website link
    - [x] Added AMA membership requirement to registration information
    - [x] Modernized PayPal registration page
    - [x] Added page descriptions, Open Graph metadata, favicon references, and Twitter card metadata
    - [x] Added accessibility improvements including skip-to-content links and ARIA navigation labels
    - [x] Updated RV camping status on the live homepage to sold out / standby list
- 2026-08-31: S3 website bucket cleanup
    - [x] Removed accidentally uploaded `.git/` repository metadata from the public website bucket
    - [x] Standardized S3 sync commands to exclude Git metadata and repository-only files
- 2026-01-14: Added info to README (commit 11e3a29)
- 2026-01-14: Updated dates to 2026
    - [x] 2026 September 11th-13th!  The location is at Crosswinds RC Club in Parker, CO.
    - [x] New Video Link:  https://youtu.be/-r7s-4r3aWs
    - [x] Google Pin Location:  https://maps.app.goo.gl/v9A9J32BEJeSUhoc6
    - [x] RVs:  Drycamping only and limited to 10 RVs.  Must reserve with Adam after registration
    - [x] Registration including Saturday Night Pilot Dinner:  $35
    - [ ] Power:  Limited AC power
    - [x] Crosswinds Website:  https://crosswindsrc.com/
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
