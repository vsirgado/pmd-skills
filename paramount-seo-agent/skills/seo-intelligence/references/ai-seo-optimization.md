# AI SEO Optimization — AEO/GEO Playbook

## What Is AI SEO?

**Answer Engine Optimization (AEO)** / **Generative Engine Optimization (GEO)** is the practice of optimizing content so that AI assistants (ChatGPT, Perplexity, Google AI Overviews, Claude, Gemini, Bing Copilot) cite, quote, and recommend your content in generated answers.

By 2026, a significant portion of search queries are answered directly by AI without the user clicking a result. If your client's website is not cited by AI, they are invisible to this growing segment of searchers.

---

## The AI Citation Framework

AI systems cite content that is:

1. **Authoritative** — from a named, credentialed expert or recognized organization
2. **Direct** — answers the question clearly in the first 1-3 sentences
3. **Structured** — uses headers, lists, and defined sections AI can extract cleanly
4. **Factual** — contains specific statistics, dates, citations, and named entities
5. **Consistent** — the same entity appears across multiple sources (websites, directories, publications)
6. **Fresh** — has a visible date and is recently updated

---

## Content Patterns AI Loves to Cite

### Pattern 1: The Direct Answer Block
Place a 40-60 word direct answer at the very top of the content, before any preamble.

```
## What Is [Topic]?

[Topic] is [concise definition with key details]. [One sentence on who it affects or why it matters].
[One sentence on what to do or key takeaway].
```

**Example:**
```
## What Is a Septoplasty?

A septoplasty is a surgical procedure to correct a deviated nasal septum — the cartilage dividing the nasal passages. It improves breathing, reduces snoring, and relieves chronic sinus issues. Recovery typically takes 1-2 weeks, and results are permanent.
```

### Pattern 2: The Structured FAQ
Each FAQ entry should:
- Have a specific, conversational question (matching how people ask AI)
- Provide a complete, standalone answer in 2-4 sentences
- Include the primary keyword in the question
- Be wrapped in FAQPage schema

```
## Frequently Asked Questions

### How long does Botox last?
Botox typically lasts 3-4 months for most patients. Results can vary based on the treatment area, the number of units used, and individual metabolism. Regular maintenance treatments can extend the duration over time.

### How much does Botox cost per unit?
Botox costs between $10-$25 per unit on average in the United States. A typical forehead treatment requires 20-30 units, making the average cost $200-$500 per session. Prices vary by provider experience and geographic location.
```

### Pattern 3: The Expert Summary Box
A "key takeaways" or "summary" box at the top of articles signals structured, AI-extractable content.

```
**Key Takeaways**
- [Fact 1 with specific detail]
- [Fact 2 with specific detail]
- [Fact 3 with specific detail]
- Reviewed by: [Dr. Name, Credential, Date]
```

### Pattern 4: The Statistics-Rich Paragraph
AI assistants frequently cite content that contains specific, citable statistics.

Include in every article:
- Prevalence statistics: "X% of Americans suffer from..."
- Outcome statistics: "Studies show X% improvement in..."
- Cost data: "The average cost of [procedure] is $X-$Y"
- Timeline data: "Recovery takes X-Y weeks in most cases"

Always cite the source inline: `(Source: American Academy of Dermatology, 2024)`

### Pattern 5: The Comparison Table
AI systems extract tabular data efficiently. Include comparison tables for:
- Treatment options vs. alternatives
- Before/after metrics
- Procedure vs. procedure
- Cost ranges by location or provider type

---

## Entity Optimization (Critical for Healthcare)

AI systems maintain a model of the world organized around **entities** — named people, places, organizations, and things.

### Make Your Physician/Practice a Strong Named Entity

1. **Consistent Name Format**: Dr. [First] [Last], [Credential] — use identically everywhere
2. **Wikipedia/Wikidata presence**: Not always possible, but link to existing profiles
3. **Google Knowledge Panel**: Claim and complete at google.com/business
4. **Authority Directory Listings**: Ensure consistent entity across:
   - Healthgrades
   - Doximity
   - Vitals.com
   - WebMD Find a Doctor
   - US News Health
   - Zocdoc
   - Castle Connolly
   - America's Top Doctors
5. **Social Profiles**: LinkedIn (especially), YouTube, Twitter/X — all with same name format
6. **Author Pages**: Rich bio pages on the client website with sameAs links to all profiles

### sameAs Schema for Entity Building
```json
{
  "@context": "https://schema.org",
  "@type": "Physician",
  "name": "Dr. Jane Smith, MD",
  "sameAs": [
    "https://www.healthgrades.com/physician/dr-jane-smith-xxxxx",
    "https://www.doximity.com/pub/jane-smith-md",
    "https://www.linkedin.com/in/drjanesmith",
    "https://www.instagram.com/drjanesmith"
  ]
}
```

---

## Google AI Overviews Optimization

Google's AI Overviews (formerly SGE) appear above organic results for informational queries. To appear in AI Overviews:

1. **Rank on page 1 first** — AI Overviews typically pull from top-10 results
2. **Use clear headers** — AI extracts content by section
3. **Include definitions** — define key terms early
4. **Use numbered steps** for procedural content ("How to...", "What to expect...")
5. **Match search intent exactly** — if the query is informational, don't make content salesy

### AI Overviews Trigger Queries (Optimize for These)
- "What is [procedure]?"
- "How long does [treatment] last?"
- "Is [procedure] covered by insurance?"
- "What are the risks of [procedure]?"
- "How much does [treatment] cost?"
- "What's the difference between [X] and [Y]?"
- "How do I know if I need [procedure]?"

---

## Perplexity & ChatGPT Citation Signals

These AI systems use web search to ground their answers. Key signals:

1. **PageRank still matters** — higher-authority domains get cited more
2. **Fresh content** — recently published or updated content is preferred
3. **HTTPS required** — HTTP pages are rarely cited
4. **Clean HTML structure** — avoid JavaScript-rendered content for key copy
5. **Breadcrumb schema** — helps AI understand page hierarchy and context
6. **Publisher schema** — clearly identifies who published the content and when

---

## AI SEO Audit Checklist

- [ ] Every key page has a direct-answer paragraph in the first 100 words
- [ ] FAQ section with schema on every service and blog page
- [ ] All statistics include source citations with year
- [ ] Physician/practice entity is consistent across 10+ authority directories
- [ ] sameAs schema implemented on doctor and practice pages
- [ ] Author bylines with credentials on all health content
- [ ] datePublished and dateModified visible and in schema
- [ ] Comparison tables present for procedure comparison pages
- [ ] Key takeaways / summary box at top of long-form articles
- [ ] Headers are complete sentences or clear questions (not just keywords)
- [ ] Content is accessible without JavaScript (SSR or static HTML)
