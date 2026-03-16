# Paramount MD SEO Agent

A superpowered SEO plugin built for Paramount MD — Victor Sirgado's digital marketing agency for healthcare practices and medical experts.

This plugin gives Claude the knowledge and commands to act as a senior SEO strategist: auditing pages, tracking rankings, generating content briefs, and syncing everything to Notion.

---

## What This Plugin Does

- **Full site audits** — technical, on-page, E-E-A-T, and AI search readiness, scored 0-100
- **Deep page audits** — single-page analysis with prioritized fix lists and exact copy suggestions
- **Keyword rank tracking** — check where clients rank for their core keywords, logged to Notion
- **Content brief generation** — research-backed SEO briefs ready for a writer or AI to execute
- **AI SEO audits** — specialized check for AI Overview / Perplexity / ChatGPT citation readiness
- **Autonomous auditor agent** — deploys independently for multi-page research and competitive analysis

All outputs sync to Notion automatically.

---

## Components

| Component | Name | What It Does |
|-----------|------|-------------|
| Skill | `seo-intelligence` | Core SEO knowledge: healthcare SEO, E-E-A-T, AI SEO, ranking factors |
| Command | `/seo-audit` | Full domain audit → Notion report |
| Command | `/page-audit` | Deep single-page audit → Notion report |
| Command | `/rank-tracker` | Keyword ranking snapshot → Notion table |
| Command | `/content-brief` | Full content brief for a keyword → Notion page |
| Command | `/ai-seo-check` | AI citation readiness audit → Notion report |
| Agent | `seo-auditor` | Autonomous multi-step SEO analyst |

---

## Usage

### Full Domain Audit
```
/seo-audit drjanesmith.com "Dr. Jane Smith Dermatology"
```

### Single Page Audit
```
/page-audit https://drjanesmith.com/botox-miami botox miami
```

### Track Rankings
```
/rank-tracker drjanesmith.com "Dr. Jane Smith" "botox miami, dermatologist miami, lip filler miami"
```

### Generate a Content Brief
```
/content-brief "knee replacement surgery miami" "South Florida Ortho" service
```

### AI SEO Check
```
/ai-seo-check https://drjanesmith.com/botox "what is botox"
```

### Deploy the Autonomous Agent
Just describe what you need in plain language — the `seo-auditor` agent will activate when the task requires multi-step autonomous research.

---

## Setup

### Notion Integration
This plugin pushes all reports and briefs to your Notion workspace. Notion is connected via the Notion MCP server. Make sure your Notion MCP is connected in Claude settings before running commands.

**Recommended Notion structure:**
- Database: "SEO Reports" — for all audits
- Database: "Content Calendar" or "Content Briefs" — for content briefs
- Database: "Rankings" — for rank tracking logs

If these databases don't exist, the plugin will create pages in your Notion workspace root and you can organize them from there.

---

## SEO Standards

This plugin is built on:
- Google's E-E-A-T guidelines (Experience, Expertise, Authoritativeness, Trustworthiness)
- YMYL (Your Money or Your Life) best practices for healthcare content
- Core Web Vitals scoring (LCP, INP, CLS)
- AI search optimization for Google AI Overviews, Perplexity, ChatGPT, and Claude
- Local SEO best practices for medical practice visibility

---

## Reference Library

| File | Contents |
|------|----------|
| `skills/seo-intelligence/references/technical-seo.md` | Full technical audit checklist with scoring rubrics |
| `skills/seo-intelligence/references/on-page-seo.md` | Title/meta/heading formulas, E-E-A-T checklist |
| `skills/seo-intelligence/references/ai-seo-optimization.md` | AEO/GEO playbook for AI citation optimization |
| `skills/seo-intelligence/references/content-brief-framework.md` | Complete content brief template and generation system |
| `skills/seo-intelligence/references/ranking-factors.md` | Prioritized ranking factors for healthcare/medical sites |

---

*Built by Paramount MD | Version 1.0.0*
