---
description: Full SEO audit for a client domain — technical, on-page, AI readiness
argument-hint: [domain-or-url] [client-name]
allowed-tools: WebFetch, WebSearch, Read
---

Run a comprehensive, multi-dimensional SEO audit for the domain or URL provided in $ARGUMENTS.

Parse $ARGUMENTS as: first value = URL/domain, second value (optional) = client name.

## Step 1: Technical Health Check

Fetch the homepage and up to 3 key service pages:
- robots.txt: `{domain}/robots.txt`
- sitemap.xml: `{domain}/sitemap.xml`
- Homepage HTML
- One service/procedure page (find from sitemap or homepage nav)

Analyze for:
- robots.txt blocking issues
- Sitemap presence and structure
- HTTPS status
- Meta viewport tag (mobile-friendly signal)
- Page load indicators (image formats, script count, render-blocking resources)
- Schema markup presence (look for application/ld+json in HTML)
- Canonical tags
- Title tag and meta description on each page

Score each technical section 0-25 per the rubric in `references/technical-seo.md`.

## Step 2: On-Page SEO Analysis

For each page fetched, evaluate:
- Title tag: length, keyword placement, uniqueness
- Meta description: length, CTA presence, keyword
- H1: presence, uniqueness, keyword alignment
- H2-H6 hierarchy: logical structure, keyword coverage
- Content length estimate (word count proxy from HTML)
- Internal link count
- Image alt text presence
- Author byline presence (critical for healthcare YMYL)

## Step 3: E-E-A-T & Trust Signals

Search for: `{domain} site:healthgrades.com OR site:doximity.com OR site:vitals.com`
Search for: `{client-name} OR {domain} reviews`

Evaluate:
- Medical directory presence
- Author credentials visible on site
- About page quality
- Review visibility and volume

## Step 4: AI Search Readiness

Review fetched pages for:
- Direct answer paragraphs in first 100 words
- FAQ sections present
- Statistics with source citations
- Structured data for FAQPage
- Schema sameAs entity links
- Author entity markup

## Step 5: Local SEO Signals (if applicable)

Search for: `{client-name} Google Business Profile`
Analyze contact page for:
- NAP (Name, Address, Phone) consistency
- Location schema
- Google Maps embed

## Step 6: Keyword Visibility Snapshot

Search Google for 3-5 core keywords the site should rank for:
- `[primary service] [city]`
- `dr [name] [specialty]`
- `[condition] treatment [city]`

Note current ranking positions.

## Step 7: Compile Full Report

Structure the report as:

---
# SEO Audit Report — {Client Name}
**Date:** {today's date}
**Domain:** {domain}
**Audited by:** Paramount MD SEO Agent

## Executive Summary
[3-5 sentence summary of overall health, top wins, and top risks]

## Overall Score: X/100

| Dimension | Score | Status |
|-----------|-------|--------|
| Technical SEO | X/25 | 🔴/🟡/🟢 |
| On-Page Optimization | X/25 | 🔴/🟡/🟢 |
| E-E-A-T & Authority | X/25 | 🔴/🟡/🟢 |
| AI Search Readiness | X/25 | 🔴/🟡/🟢 |

## 🚨 Critical Issues (Fix Immediately)
[Issues blocking rankings — numbered list with specific fixes]

## ⚡ High-Impact Wins (This Week)
[Quick actions that will move the needle fastest — numbered list]

## 🗓️ 30-Day Roadmap
[Strategic improvements with effort estimates]

## Detailed Findings
[Full findings per dimension with specifics]

## Keyword Ranking Snapshot
[Table of tracked keywords + current positions]
---

## Step 8: Push to Notion

After generating the report, create a new Notion page with:
- Title: "SEO Audit — {Client Name} — {Date}"
- Content: the full report in Notion markdown format
- Database: look for a Notion database called "SEO Reports" or "Client Reports" or create one if it doesn't exist
- Properties to set: Client Name, Audit Date, Overall Score, Status = "New"

Confirm the Notion page URL once created.
