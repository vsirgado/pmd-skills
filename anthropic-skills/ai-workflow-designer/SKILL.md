---
name: ai-workflow-designer
description: >
  PMD's AI systems and automation design intelligence. Use when designing, building, documenting, or scoping any Make.com scenario, GHL automation, AI agent workflow, or business digitization system — for PMD internally or for client engagements.

  Triggers: "design a workflow," "build an automation," "Make.com scenario," "GHL automation," "AI agent," "workflow design," "automate this," "digitize this process," "build a system for," "how do I automate," "trigger and action," "webhook," "workflow architecture," "AI systems engagement," "scope the automation," or any time a client or internal project needs an automation or AI system designed, documented, or deployed. Use proactively whenever an AI Systems prospect or client engagement is being discussed.
---

# AI Workflow Designer — Paramount MD

This skill is PMD's core IP layer for the AI Systems & Automation service line. It codifies the methodology Victor uses to design, build, and deploy AI-powered operational systems for healthcare organizations. Everything here is built from real systems — not theory.

**Always read `/sessions/eloquent-pensive-bohr/mnt/CoWork OS/PMD-context.md` first** — specifically the AI Systems & Automation service line section and active client/prospect context.

---

## 1. PMD's Core Tech Stack for AI Systems

Know these tools cold. Every system is assembled from combinations of these.

| Layer | Tool | Role |
|-------|------|------|
| **CRM & Operations Hub** | GoHighLevel (GHL) | Contact management, pipelines, automations, forms, appointments, SMS/email |
| **Automation Engine** | Make.com (formerly Celonis) | Scenario-based automation connecting apps via API/webhook |
| **AI Brain** | Claude (Anthropic API) | Intelligent processing, response generation, content creation, analysis |
| **AI Backup** | ChatGPT / OpenAI API | Alternative AI layer, image generation |
| **Voice AI** | 11LABS | Voice cloning, audio content generation |
| **Operations DB** | Airtable | Structured data, content calendars, client tracking |
| **Knowledge Base** | Notion | Documentation, SOPs, project management |
| **Video** | Frame.io, ECAMM, Loom | Video review, recording, async communication |
| **Commerce** | FastSpring, Paddle.com | Course and product payments |
| **Utilities** | Cloudconvert, PDF.co, Placid | File conversion, PDF ops, dynamic image generation |

**The default system architecture:** GHL handles the client-facing layer (CRM, communications, forms). Make.com handles the automation logic and connects everything. Claude handles the intelligence layer (drafting, analyzing, deciding). Airtable or Notion handles structured data and documentation.

---

## 2. Automation Design Principles

**Principle 1 — Trigger clarity**
Every automation starts with a single, unambiguous trigger. If you can't state the trigger in one sentence, it's not ready to build.
> "When a new contact is tagged [new-lead] in GHL → do X"
> "When a form is submitted on [page] → do Y"
> "Every Monday at 9am → do Z"

**Principle 2 — Fail gracefully**
Every scenario must have error handling. What happens when an API call fails? When data is missing? When a step times out? Build the error path before the success path.

**Principle 3 — Idempotency**
Running the same automation twice should not double-charge, double-message, or create duplicates. Add deduplication logic at the trigger point.

**Principle 4 — Observable systems**
Every production system needs a log. Whether that's a Make.com execution log, a GHL activity feed, or an Airtable record — you must be able to answer "did this run, when, and what happened?" at any time.

**Principle 5 — HIPAA guard rails for healthcare**
- Never pass patient identifiable information (name, DOB, condition, contact info) through unsecured channels
- Use GHL's HIPAA-compliant messaging for anything PHI-adjacent
- No patient data in Airtable free tier, Notion public pages, or unencrypted webhooks
- When in doubt: store the GHL contact ID, not the patient data — retrieve from GHL only when needed

---

## 3. Core Healthcare Automation Patterns

These are the highest-impact, most commonly deployed systems in healthcare. Start here for any new client.

### Pattern 1 — New Lead Capture & Nurture
**Problem:** Leads come in from website forms, ads, and referrals — then fall through the cracks
**System:**
```
Form submission / Ad lead / Referral intake
  → GHL contact created + tagged [new-lead]
  → Make.com: Pull contact data → Send to Claude for personalized welcome message
  → GHL: Send SMS + email within 5 minutes of form submit
  → GHL Workflow: Day 1, 3, 7 follow-up sequence if no response
  → If appointment booked → tag [appointment-scheduled] → stop nurture sequence
  → If no response after 7 days → tag [cold-lead] → move to long-term nurture
```

### Pattern 2 — Appointment Reminder & Confirmation
**Problem:** No-shows cost practices $150–$300 per missed slot
**System:**
```
Appointment created in GHL calendar
  → Make.com: 72hr before → Send confirmation SMS/email
  → Make.com: 24hr before → Send reminder SMS + prep instructions
  → Make.com: 2hr before → Final reminder SMS
  → If no confirmation response → alert front desk via Slack/email
  → Post-appointment: 2hr after → Send review request (Google / Healthgrades)
```

### Pattern 3 — Review Request Automation
**Problem:** Most practices only ask for reviews inconsistently and manually
**System:**
```
Appointment status → "Completed" in GHL
  → 2–4 hour delay
  → GHL Workflow: Send personalized review request SMS
  → If no action after 24hr → Send email version
  → If no action after 48hr → Remove from sequence (never over-ask)
  → Positive review detected (via GBP webhook) → Tag contact [reviewer] → Add to referral list
```

### Pattern 4 — Content Publishing Automation
**Problem:** Consistent content publishing requires manual effort every week
**System:**
```
Content calendar trigger (Airtable or scheduled)
  → Make.com: Pull content from Airtable → Send to Claude for final polish/optimization
  → Claude: Return optimized content with SEO metadata
  → Make.com: Post to GHL blog + social scheduler + email draft
  → Notify Victor via email/Slack: "Content published — review here"
```

### Pattern 5 — AI-Powered Intake & Triage
**Problem:** Intake forms generate leads but require manual review and routing
**System:**
```
Patient/Lead intake form submitted (GHL)
  → Make.com: Extract form data → Send to Claude with triage prompt
  → Claude: Categorize urgency (urgent/routine/information-only), identify best physician/service match, draft personalized response
  → Make.com: Update GHL contact with Claude's categorization + notes
  → Route to appropriate pipeline stage
  → Send personalized response to patient (from Claude draft, approved or auto-sent based on category)
```

### Pattern 6 — Full Business Digitization (Flagship)
**Problem:** A practice's entire operation is manual — scheduling, follow-up, content, reporting, billing prep, team comms
**System:** Combination of Patterns 1–5 + custom modules for their specific workflow
**Build approach:** Discovery → workflow map → priority automation stack → phased build (highest ROI first)

---

## 4. Make.com Scenario Design Framework

When designing a new Make.com scenario:

**Step 1: Map the workflow first**
Before touching Make.com, draw the flow on paper (or in Notion/Miro):
- Trigger event
- Each step in sequence
- Decision branches (if/else conditions)
- Error paths
- Final output / success state

**Step 2: Identify the modules needed**
Make.com modules for PMD's common stack:
- `GHL: Watch Contacts` — trigger on new/updated contacts
- `GHL: Create/Update Contact` — write back to CRM
- `GHL: Add Tag / Remove Tag` — segment contacts
- `HTTP: Make a Request` — any API not natively supported
- `Anthropic: Create a Message` (or HTTP to Anthropic API) — invoke Claude
- `Airtable: Create/Update Record` — log to operations database
- `Gmail / GHL Email: Send Email` — outbound communications
- `Slack: Create Message` — internal team alerts
- `Tools: Set Variable / Iterator / Array Aggregator` — data manipulation
- `Flow Control: Router / Filter` — conditional branching

**Step 3: Build the happy path first**
Get the primary flow working end-to-end before adding error handling, edge cases, or conditional branches.

**Step 4: Add error handling**
- Use Make.com's built-in error handler on each critical module
- For API calls: set retry policy (2–3 retries with delay)
- For missing data: use `ifempty()` fallback or filter to stop the scenario gracefully
- Route errors to a notification (email/Slack) so you know immediately when something breaks

**Step 5: Test with real data**
Use a test contact in GHL — run the scenario manually. Verify every output. Check for:
- Data format mismatches (dates, phone number formats, field mappings)
- HTML encoding issues in message templates
- API rate limits

**Step 6: Document before you ship**
Every scenario that goes to production needs a one-page doc:
- What it does (plain English)
- What triggers it
- What systems it touches
- How to turn it off (for emergencies)
- Who to contact if it breaks

---

## 5. Claude Prompt Engineering for Automation

When Claude is embedded in a Make.com workflow, prompt quality determines output quality.

**Standard prompt structure for automation contexts:**
```
System: You are [role]. You are processing [type of input] for [organization name], a [description].

Context: [Any relevant background — the contact's history, the form they submitted, the content category]

Task: [Specific, single job — triage this lead, draft this response, categorize this content]

Output format: [Exact structure expected — JSON fields, plain text, specific sections]
Do NOT include any preamble or explanation. Return only the specified output.

Input: {{input_data_from_make}}
```

**Key rules for automation prompts:**
- Always specify output format precisely — automation can't parse conversational responses
- Use `temperature: 0` or `0.2` for classification/triage tasks, `0.7` for creative/content tasks
- Include a fallback instruction: "If you cannot determine [X], return [default value]"
- Test with edge cases: empty inputs, unusual characters, very long inputs, non-English text

---

## 6. GHL Automation Architecture

GHL workflows are the client-facing layer. Make.com handles the complex logic; GHL handles the triggers and communications.

**GHL Workflow design rules:**
- Every workflow needs a clear entry trigger and an exit condition
- Use tags for state management — a contact's tags represent their current status in your system
- Never leave a contact in a workflow indefinitely — always have a "remove from workflow" action
- Separate workflows by function: one workflow for lead nurture, one for appointment reminders, one for post-visit — don't chain everything into one mega-workflow

**GHL → Make.com integration patterns:**
- GHL Webhook → Make.com: Use "Watch for Events" trigger in Make (custom webhook URL pasted into GHL workflow)
- Make.com → GHL: Use GHL API (v1 or v2) via HTTP module — always authenticate with API key, not OAuth for production stability
- Data mapping: GHL uses `contact.id`, `contact.email`, `contact.phone`, `contact.tags` as primary identifiers

**Common GHL automation pitfalls:**
- Tag-based triggers fire on every tag addition — add a filter to check if the contact is already in-progress
- GHL's time delay steps don't account for business hours — if you need business-hour-aware delays, route through Make.com
- SMS character limits: GHL splits messages over 160 chars — test your templates at expected message lengths

---

## 7. Client Discovery Protocol

When beginning an AI Systems engagement (or scoping a proposal), run this 5-area discovery:

**Area 1 — Current State**
- Walk me through your typical day / week operationally
- What are the most repetitive manual tasks your team does?
- Where do things fall through the cracks most often?
- What tools do you currently use? (Get a full list)

**Area 2 — Pain Points**
- What's the single most painful part of running your operations?
- What would you eliminate tomorrow if you could?
- Where do you lose the most time? The most money?

**Area 3 — Vision**
- If your operations ran perfectly, what would that look like?
- What would you do with the time you'd recover?
- What does scale look like for you in 1–2 years?

**Area 4 — Technical Reality**
- Who manages your tech stack currently?
- Do you have someone internal who could be trained to manage systems? (Tier A vs B indicator)
- What platforms are you locked into? Any contracts?
- Any HIPAA or compliance constraints we need to design around?

**Area 5 — Decision**
- Who's involved in this decision?
- What does your budget range look like for something like this?
- What timeline are you working toward?

After discovery → route to `proposal-builder` with notes to generate the scoped proposal.

---

## 8. System Documentation Template

Every system PMD builds needs documentation delivered to the client. Use this template.

```
# [System Name] — Operating Guide

## What This System Does
[2–3 sentences in plain English]

## Trigger
[What starts the automation — be specific]

## What Happens Step by Step
1. [Step 1]
2. [Step 2]
...

## What the Client Sees
[What the end patient/customer/staff experiences]

## How to Turn It Off (Emergency Stop)
[Step-by-step — assume the person reading this is not technical]

## How to Make Changes
[Who to contact, what information to provide]

## Known Limitations
[Edge cases, things it doesn't handle, manual steps that remain]

## Performance Monitoring
[Where to check that it's working — GHL dashboard, Make.com execution log, etc.]

## Last Updated
[Date — Victor / PMD]
```
