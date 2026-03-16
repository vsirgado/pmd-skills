---
description: Deep single-page SEO audit with optimization recommendations
argument-hint: [page-url] [target-keyword]
allowed-tools: WebFetch, WebSearch, Read
---

Run a deep SEO audit on the single page provided in $ARGUMENTS.

Parse $ARGUMENTS as: first value = page URL, second value (optional) = target keyword.

## Step 1: Fetch and Parse the Page

Fetch the full HTML of the page URL. Extract and analyze:

**Title Tag:**
- Full text
- Character count
- Contains target keyword? (Y/N)
- Keyword position (first 3 words? yes/no)
- Assessment: Too short / Too long / Optimal / Missing keyword

**Meta Description:**
- Full text
- Character count
- Contains target keyword? (Y/N)
- Contains CTA? (Y/N)
- Assessment

**H1:**
- Full text
- Count (should be exactly 1)
- Contains target keyword? (Y/N)
- Assessment

**Heading Structure:**
- List all H2-H6 tags with their text
- Assess hierarchy and keyword coverage

**Content Analysis:**
- Estimated word count
- Target keyword in first 100 words? (Y/N)
- Keyword density estimate
- Author byline present? (Y/N + credentials if found)
- Date published/updated present? (Y/N)
- External citations present? (Y/N)
- Internal links count

**Images:**
- Count
- Alt text present on all? (Y/N)
- File format indicators (WebP? JPG?)

**Schema Markup:**
- List all schema types found (extract application/ld+json)
- Validate completeness of each schema type
- Missing schema types recommended

**Technical Signals:**
- HTTPS? (Y/N)
- Canonical tag? (Y/N + value)
- Meta robots? (Y/N + value)
- Viewport meta tag? (Y/N)

## Step 2: SERP Competitive Analysis

If a target keyword is provided, search for it and analyze the top 3 results:
- What title tag formats are winning?
- What content length do they use?
- What schema do they have?
- What does our page do better/worse?

## Step 3: AI Citation Readiness

Check the page for:
- Direct answer paragraph in first 60 words (score: present/missing)
- FAQ section with structured Q&A (present/missing)
- Statistics with cited sources (present/missing/count)
- Definition of key term early in content (present/missing)
- Expert author entity (present/missing)

## Step 4: Generate Optimization Checklist

Produce a prioritized fix list:

---
# Page Audit — {URL}
**Target Keyword:** {keyword}
**Date:** {today}

## Page Health Score: X/100

## Priority Fix List

### 🔴 Critical (Fix Today)
- [ ] [Specific fix with exact new copy or instruction]

### 🟡 High Priority (This Week)
- [ ] [Specific fix]

### 🟢 Optimization (30 Days)
- [ ] [Specific improvement]

## Suggested Title Tag
`[New title tag — 50-60 chars]`

## Suggested Meta Description
`[New meta description — 150-160 chars]`

## Suggested H1
`[New H1 if needed]`

## Missing Schema (Add These)
[Schema type + JSON-LD template to implement]

## Content Gaps vs. Top Competitors
[What the top-ranking pages cover that this page misses]

## AI SEO Improvements
[Specific direct-answer paragraph draft + FAQ questions to add]
---

## Step 5: Push to Notion

Create a Notion page titled "Page Audit — {URL slug} — {Date}" with the full report. Look for an existing "SEO Reports" or "Page Audits" database. Set status property to "Action Required" if critical issues found, "Review" if only optimizations.
