---
description: Track keyword rankings for a client domain and log results to Notion
argument-hint: [domain] [client-name] [keyword1, keyword2, keyword3...]
allowed-tools: WebSearch, WebFetch, Read
---

Track Google keyword rankings for the domain and keywords in $ARGUMENTS.

Parse $ARGUMENTS:
- First value: domain (e.g., southfloridaortho.com)
- Second value: client name (e.g., "South Florida Ortho")
- Remaining values (comma-separated or listed): keywords to track

If no keywords are provided, infer likely target keywords from the domain/client name by fetching the homepage and extracting the main services and specialties.

## Step 1: Identify Keywords to Track

If keywords are explicitly provided, use those.

If not provided, fetch the client's homepage and extract:
- Primary specialty/service (from H1, nav, or above-fold content)
- Location (city/state from address, footer, or contact page)
- Construct 5-10 tracking keywords:
  - `[specialty] [city]`
  - `[specialty] near me`
  - `best [specialty] [city]`
  - `dr [doctor name] [specialty]`
  - `[procedure 1] [city]`
  - `[procedure 2] [city]`
  - `[condition] treatment [city]`
  - `[specialty] [city] cost`

## Step 2: Check Rankings for Each Keyword

For each keyword:
1. Use WebSearch to search the exact keyword
2. Scan results to find where the client's domain appears
3. Record:
   - Keyword
   - Current Position (1-10, page 1; 11-20, page 2; etc.; or "Not found in top 20")
   - Result type: organic, local pack, featured snippet, People Also Ask
   - Competing URL that ranks #1 (if client isn't #1)

**Note:** Report positions as observed in current search results. These are point-in-time snapshots.

## Step 3: Identify Movement Opportunities

For each keyword where the client is NOT in positions 1-3:
- Fetch the #1 ranking page
- Identify 1-2 specific reasons why it outranks the client
- Recommend the single highest-leverage action to close the gap

## Step 4: Compile Ranking Report

---
# Keyword Ranking Report — {Client Name}
**Domain:** {domain}
**Date:** {today's date}
**Tracked by:** Paramount MD SEO Agent

## Ranking Summary

| Keyword | Position | Result Type | vs. Competitor |
|---------|----------|-------------|----------------|
| [keyword] | [X or Not in top 20] | Organic / Local / Featured | [#1 competitor domain] |

## 🏆 Strong Positions (1-3)
[List keywords where client is in top 3 — celebrate wins]

## 📈 Near-Page-1 Opportunities (Positions 4-20)
[Keywords close to page 1 with highest upward potential]

## 🎯 Gap Targets (Not Ranking or Page 2+)
[Keywords with high value that need a real strategy]

## Priority Action Plan
1. [Highest-leverage keyword] → [Specific action to improve ranking]
2. [Second keyword] → [Specific action]
3. [Third keyword] → [Specific action]
---

## Step 5: Push to Notion

Create or update a Notion page:
- Title: "Ranking Report — {Client Name} — {Date}"
- Look for a Notion database called "Rankings" or "SEO Tracking" or "Client Reports"
- If none found, create the page in the workspace root
- Set properties: Client, Date, Top-3 Count, Total Tracked Keywords
- Include the full ranking table in the page body

If a previous ranking report exists for this client, note which keywords have moved up or down since the last report (compare the tables).

Confirm Notion page URL once created and summarize top 3 ranking insights.
