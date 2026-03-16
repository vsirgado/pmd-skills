---
description: Audit a page for AI search citation readiness (AEO/GEO/AI Overviews)
argument-hint: [page-url] [target-topic]
allowed-tools: WebFetch, WebSearch, Read
---

Run a specialized AI Search Optimization audit on the page URL in $ARGUMENTS.

Parse $ARGUMENTS: first value = page URL, second value (optional) = target topic or query.

This audit determines whether AI assistants (ChatGPT, Perplexity, Google AI Overviews, Claude, Gemini) are likely to cite this page in their generated answers.

## Step 1: Fetch and Analyze the Page

Fetch the full HTML/text content of the URL. Then evaluate across 8 AI citation signals:

### Signal 1: Direct Answer Quality (0-15 points)
- Is there a clear, self-contained answer in the first 60 words? (+8)
- Does it answer "what is" or "how to" directly? (+4)
- Is it 40-60 words (ideal for snippets)? (+3)
**Note:** If no direct answer exists, draft one for the recommendation.

### Signal 2: Structured Content Format (0-15 points)
- Logical H2/H3 hierarchy that AI can navigate (+5)
- Numbered steps or bullet lists for procedural content (+5)
- Tables for comparison or data (+5)

### Signal 3: FAQ Section (0-15 points)
- FAQ section present? (+6)
- Questions match conversational query style? (+5)
- FAQPage schema implemented? (+4)

### Signal 4: Citation-Ready Statistics (0-10 points)
- Contains specific statistics? (+5)
- Statistics are cited with source and year? (+5)
- **Deduct 5** if statistics are uncited or appear made-up

### Signal 5: Entity Optimization (0-15 points)
- Named author with credentials prominently visible? (+6)
- Practice/physician entity matches external directories? (+5)
- sameAs schema linking to authority profiles? (+4)

### Signal 6: Freshness Signals (0-10 points)
- datePublished visible? (+3)
- dateModified visible and recent? (+4)
- References to current year or recent studies? (+3)

### Signal 7: Topical Authority (0-10 points)
- Page is deeply comprehensive, not thin? (+5)
- Site has multiple related pages on this topic cluster? (+5)

### Signal 8: Technical Accessibility (0-10 points)
- Page content accessible without JavaScript? (+5)
- Clean semantic HTML with proper heading structure? (+3)
- No interstitial blocking content before AI can read it? (+2)

## Step 2: AI Visibility Test

Search for the primary topic/query in Web Search.
Check: Does the client's page appear in the top 10 results?
(AI Overviews primarily pulls from top-10. If not ranking there, AI visibility is very limited regardless of on-page optimization.)

Also search: `site:{domain} "{key phrase}"` — is this the most relevant page the site has on this topic?

## Step 3: Compile AI SEO Report

---
# AI Search Optimization Audit — {URL}
**Topic:** {target topic}
**Date:** {today's date}
**Audited by:** Paramount MD SEO Agent

## AI Citation Score: X/100

| Signal | Score | Status |
|--------|-------|--------|
| Direct Answer Quality | X/15 | 🔴/🟡/🟢 |
| Structured Content Format | X/15 | 🔴/🟡/🟢 |
| FAQ Section | X/15 | 🔴/🟡/🟢 |
| Citation-Ready Statistics | X/10 | 🔴/🟡/🟢 |
| Entity Optimization | X/15 | 🔴/🟡/🟢 |
| Freshness Signals | X/10 | 🔴/🟡/🟢 |
| Topical Authority | X/10 | 🔴/🟡/🟢 |
| Technical Accessibility | X/10 | 🔴/🟡/🟢 |

## Is This Page Likely to Be Cited by AI? [Yes / Not Yet / No]

**Why or why not:** [2-3 sentence explanation]

## 🎯 Top 3 Actions to Increase AI Citation Probability

1. **[Action 1]** — [Specific what to do + expected impact]
2. **[Action 2]** — [Specific what to do + expected impact]
3. **[Action 3]** — [Specific what to do + expected impact]

## ✍️ Recommended Direct Answer Paragraph (Add to Page Top)
[40-60 word draft ready to implement — quotable, factual, complete standalone answer]

## Recommended FAQ Additions
[3-5 new Q&A pairs targeting AI query patterns — with conversational questions]

## Schema Gaps
[Specific schema types missing with implementation recommendations]

## Entity Optimization Checklist
[Specific directories or profiles where entity is missing or inconsistent]
---

## Step 4: Push to Notion

Create a Notion page titled "AI SEO Audit — {URL slug} — {Date}". Look for an "SEO Reports" or "AI SEO" database. Set a score property if available. Mark status as "Needs Work" if score < 60, "Good" if 60-79, "Excellent" if 80+.

Return the Notion page link and the AI Citation Score once complete.
