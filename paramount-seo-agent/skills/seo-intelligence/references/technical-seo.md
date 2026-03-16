# Technical SEO Reference — Full Audit Checklist

## Scoring Rubric

Score each section 0-25 for a total of 100. Deduct points per issue found.

---

## Section 1: Crawlability & Indexation (0-25)

### robots.txt Audit
- [ ] File exists at domain.com/robots.txt
- [ ] No critical pages blocked (especially service pages, blog posts, landing pages)
- [ ] Sitemap URL is declared: `Sitemap: https://domain.com/sitemap.xml`
- [ ] User-agent rules are not overly restrictive
- **Deduct 5pts** if important pages are disallowed
- **Deduct 3pts** if sitemap not declared

### XML Sitemap Audit
- [ ] Sitemap exists and is accessible
- [ ] All canonical URLs included (no noindex pages in sitemap)
- [ ] Last modified dates are accurate
- [ ] Submitted to Google Search Console
- [ ] Under 50,000 URLs (or properly split)
- **Deduct 5pts** if sitemap missing or inaccessible
- **Deduct 3pts** if noindex pages included in sitemap

### Indexation Status
- Perform: `site:domain.com` in Google — check indexed pages vs. expected
- [ ] No critical pages are noindexed unintentionally
- [ ] Thin/duplicate pages are noindexed intentionally
- [ ] Google Search Console shows no coverage errors for key pages
- **Deduct 5pts** per unintentionally deindexed important page

### Canonical Tags
- [ ] Every page has a self-referencing canonical
- [ ] Paginated pages canonicalize to first page or use rel=next/prev
- [ ] No conflicting canonical signals (canonical says X but robots.txt blocks X)
- [ ] HTTP versions redirect to HTTPS (no canonical conflicts)
- **Deduct 4pts** if canonicals are missing sitewide

---

## Section 2: Site Speed & Core Web Vitals (0-25)

### Largest Contentful Paint (LCP) — Target: < 2.5s
- [ ] Hero image or header text loads under 2.5 seconds
- [ ] Images above the fold are preloaded: `<link rel="preload">`
- [ ] Server response time (TTFB) under 800ms
- [ ] No render-blocking resources above the fold
- **Deduct 5pts** if LCP > 4.0s
- **Deduct 3pts** if LCP 2.5s-4.0s

### Interaction to Next Paint (INP) — Target: < 200ms
- [ ] No heavy JavaScript blocking main thread
- [ ] Event handlers are efficient
- [ ] No long tasks over 50ms in the critical path
- **Deduct 4pts** if INP > 500ms

### Cumulative Layout Shift (CLS) — Target: < 0.1
- [ ] Images have defined width/height attributes
- [ ] No ads/embeds without reserved space
- [ ] Web fonts load without layout shift (use font-display: swap)
- **Deduct 4pts** if CLS > 0.25

### Additional Speed Factors
- [ ] Images compressed and served in WebP/AVIF format
- [ ] Lazy loading enabled for below-fold images
- [ ] CSS/JS minified and bundled
- [ ] CDN in use (Cloudflare, Fastly, etc.)
- [ ] Browser caching headers set (Cache-Control, ETag)
- [ ] Gzip/Brotli compression enabled
- **Deduct 2pts** per missing optimization

---

## Section 3: Mobile & HTTPS (0-25)

### Mobile-First Optimization
- [ ] Passes Google Mobile-Friendly Test
- [ ] Viewport meta tag present: `<meta name="viewport" content="width=device-width, initial-scale=1">`
- [ ] Touch targets minimum 48x48px
- [ ] No horizontal scrolling
- [ ] Font size minimum 16px for body text
- [ ] No interstitials blocking content on mobile
- **Deduct 5pts** if fails Mobile-Friendly Test
- **Deduct 3pts** per significant mobile usability issue

### HTTPS & Security
- [ ] Valid SSL certificate installed
- [ ] HTTP automatically redirects to HTTPS (301)
- [ ] No mixed content (HTTP resources loaded on HTTPS pages)
- [ ] HSTS header present
- [ ] No security warnings in browser console
- **Deduct 8pts** if site is HTTP only
- **Deduct 3pts** for mixed content warnings

---

## Section 4: Structured Data & Schema (0-25)

### Healthcare Schema Requirements

#### MedicalOrganization / Physician Schema
```json
{
  "@context": "https://schema.org",
  "@type": "Physician",
  "name": "Dr. [Name]",
  "medicalSpecialty": "[Specialty]",
  "address": {
    "@type": "PostalAddress",
    "streetAddress": "...",
    "addressLocality": "...",
    "addressRegion": "...",
    "postalCode": "..."
  },
  "telephone": "...",
  "url": "...",
  "sameAs": ["https://www.healthgrades.com/...", "https://www.doximity.com/..."]
}
```

#### LocalBusiness Schema (for practice pages)
- [ ] @type: MedicalClinic or Physician
- [ ] name, address, telephone, url
- [ ] openingHours
- [ ] geo coordinates
- [ ] priceRange (optional)
- [ ] aggregateRating (if reviews exist)

#### FAQPage Schema (for FAQ sections)
- [ ] Each Q&A pair wrapped in Question/Answer schema
- [ ] Answers under 300 words each
- [ ] Passes Google Rich Results Test

#### Article Schema (for blog posts)
- [ ] @type: MedicalWebPage or Article
- [ ] author with @type: Physician or Person with credentials
- [ ] datePublished and dateModified
- [ ] publisher with logo

### Validation
- Run all pages through: https://search.google.com/test/rich-results
- Run all pages through: https://validator.schema.org/
- **Deduct 5pts** if no schema implemented
- **Deduct 3pts** per schema validation error
- **Deduct 2pts** if schema doesn't match visible content

---

## Technical SEO Scoring Summary

| Section | Max Points | Earned |
|---------|-----------|--------|
| Crawlability & Indexation | 25 | |
| Site Speed & Core Web Vitals | 25 | |
| Mobile & HTTPS | 25 | |
| Structured Data & Schema | 25 | |
| **TOTAL** | **100** | |

### Score Interpretation
- **90-100**: Excellent — minor polish only
- **75-89**: Good — address high-impact items
- **60-74**: Needs Work — fix critical issues within 30 days
- **Below 60**: Poor — technical issues are likely suppressing rankings significantly
