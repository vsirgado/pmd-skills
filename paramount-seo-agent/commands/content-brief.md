---
description: Generate a complete SEO content brief for a target keyword
argument-hint: [target-keyword] [client-name] [page-type]
allowed-tools: WebSearch, WebFetch, Read
---

Generate a comprehensive, research-backed SEO content brief for the keyword and client in $ARGUMENTS.

Parse $ARGUMENTS:
- First value: target keyword (e.g., "knee replacement surgery miami")
- Second value: client name (e.g., "South Florida Ortho")
- Third value (optional): page type — service / blog / condition / location / faq (default: infer from keyword)

## Step 1: Keyword Intelligence

Search the target keyword and analyze the SERP:
- What is the dominant result type? (articles, service pages, video, local pack)
- What is the search intent? (informational / commercial / transactional)
- What format wins? (listicle, how-to, ultimate guide, service page)
- Identify the top 3 ranking URLs

## Step 2: Competitive Content Analysis

Fetch each of the top 3 ranking URLs. For each, extract:
- Exact title tag
- H1
- Full heading structure (H2-H6)
- Approximate word count
- Presence of FAQ section (Y/N)
- Schema types detected
- Author credentials (Y/N)
- Content unique strengths

Identify:
- Common themes all 3 cover (must-include topics)
- Topics only 1-2 cover (differentiation opportunities)
- Topics NONE cover (content gap and angle to own)

## Step 3: People Also Ask Extraction

Search the keyword and note the "People Also Ask" questions. These become:
- FAQ section questions
- H2 subheading ideas
- AI Overview optimization targets

Also note "Related Searches" for secondary/LSI keywords.

## Step 4: Generate the Complete Content Brief

Use the template from `references/content-brief-framework.md` and populate every section with research-backed data:

**REQUIRED SECTIONS:**
- Overview (client, URL target, page type, author, deadline)
- Keyword targeting (primary, secondary, LSI, long-tail)
- Search intent analysis (type, patient journey stage, emotional context)
- Competitive analysis (top 3 URLs, gaps, our differentiator)
- Page structure (title, meta, H1, full recommended outline)
- Required elements (author byline, citations, CTAs, schema checklist)
- AI SEO requirements (direct answer paragraph DRAFT, FAQ questions, key statistics)
- Success criteria (90-day targets, measurement plan)

**DRAFT THE DIRECT ANSWER PARAGRAPH:**
Based on the keyword, write a 40-60 word direct answer paragraph that would appear at the top of the page. This should be quotable by AI assistants and optimized for featured snippets.

**SUGGEST EXACT COPY FOR:**
- Title tag (50-60 chars)
- Meta description (150-160 chars)
- H1

**SUGGEST 5 FAQ QUESTIONS** (sourced from People Also Ask + your SEO expertise)

**SUGGEST STATISTICS TO INCLUDE** — provide 3-5 real statistics from authoritative medical sources with citations.

## Step 5: Word Count & Format Recommendation

Based on competitive analysis:
- What is the average word count of the top 3 results?
- What word count will help us match or exceed them?
- Recommended format: long-form article / structured service page / FAQ hub / pillar page

## Step 6: Push to Notion

Create a new Notion page:
- Title: "Content Brief — {keyword} — {client name}"
- Look for a Notion database called "Content Calendar," "Content Briefs," or "Editorial" — use the first match found
- If no content database found, create the page in the workspace root
- Set properties where available: Client, Keyword, Page Type, Target Publish Date, Status = "Brief Ready"
- Include the complete brief as the page body
- Format using Notion-compatible headers and tables

Confirm the Notion page URL once created and provide a 3-bullet summary of the brief's key strategic angles.
