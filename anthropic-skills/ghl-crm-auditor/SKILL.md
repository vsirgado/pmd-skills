---
name: ghl-crm-auditor
description: >
  Build, configure, and operate a Self-Healing GoHighLevel CRM Audit System using Make.com and the Anthropic API. Use this skill whenever the user mentions auditing GHL contacts, cleaning up a CRM, building a Make scenario for GoHighLevel, connecting Claude to GHL via API, setting up contact health scoring, or automating CRM cleanup. Also trigger when the user says things like "run the audit", "check the CRM", "clean up contacts", "fix my GHL", or "set up the auditor". This skill covers the full build from API connection through audit output — use it proactively any time GoHighLevel + automation + AI are mentioned together.
---

# GHL CRM Auditor Skill

A step-by-step system for building and operating an AI-powered GoHighLevel CRM audit and cleanup pipeline using Make.com and Claude (Anthropic API).

---

## System Overview

**Architecture:**
```
GHL API → Make.com Iterator → Claude (Anthropic API) → Notion Output
```

**What it does:**
- Pulls all contacts from a GHL sub-account
- Loops through each contact
- Sends contact data to Claude for analysis
- Claude returns a health score, issues list, and recommended action
- Results output to a Notion database for review

---

## Credentials Required

| Credential | Where to Get It | Notes |
|---|---|---|
| GHL Sub-Account JWT Token | GHL Sub-Account → Settings → Private Integrations | Select contact/tag/opportunity scopes |
| GHL Agency JWT Token | GHL Agency View → Settings → Private Integrations | For location-level access |
| GHL Location ID | GHL Sub-Account → Settings → Business Info → Location ID | |
| Anthropic API Key | console.anthropic.com → API Keys | Must have credit balance |
| Notion Integration Token | notion.so → Settings → Integrations | |

**Security:** Never ask the user to paste credentials into chat. Always instruct them to enter directly into Make.com connection fields or keychain.

---

## Make.com Scenario Structure

### Module 1 — HTTP: Pull GHL Contacts
- **Type:** HTTP → Make a Request
- **Auth:** API Key (Bearer token, in header)
- **URL:** `https://services.leadconnectorhq.com/contacts/`
- **Method:** GET
- **Headers:**
  - `Authorization`: `Bearer {GHL_SUB_ACCOUNT_JWT}`
  - `Version`: `2021-07-28`
- **Query Parameters:**
  - `locationId`: `{LOCATION_ID}`
  - `limit`: `100`
- **Pagination Type:** URL or link-based
  - Items path: `contacts`
  - Next page URL path: `meta.nextPageUrl`
  - Page size parameter name: `limit`
  - Page size parameter value: `100`

### Module 2 — Iterator
- **Array:** `{{1.data.contacts[]}}`
- Loops through each contact one at a time

### Module 3 — HTTP: Send to Claude
- **Type:** HTTP → Make a Request
- **Auth:** No authentication (API key in header)
- **URL:** `https://api.anthropic.com/v1/messages`
- **Method:** POST
- **Headers:**
  - `x-api-key`: `{ANTHROPIC_API_KEY}`
  - `anthropic-version`: `2023-06-01`
  - `content-type`: `application/json`
- **Body content type:** application/json
- **Body input method:** JSON string
- **Body content:**
```json
{
  "model": "claude-sonnet-4-20250514",
  "max_tokens": 1024,
  "messages": [
    {
      "role": "user",
      "content": "You are a CRM auditor for a healthcare marketing agency. Analyze this contact and flag issues. Check for: missing email, missing phone, missing tags, missing source, unassigned owner. Return a JSON object with: contact_id, contact_name, issues (array of strings), health_score (0-100), recommended_action. Contact data: ID={{3.id}} Name={{3.contactName}} Email={{3.email}} Phone={{3.phone}} Tags={{3.tags}} Source={{3.source}} Owner={{3.assignedTo}}"
    }
  ]
}
```

### Module 4 — Notion: Add Row to Database
- **Type:** Notion → Create a Database Item
- **Database:** GHL CRM Audit (pre-created in Notion)
- **Fields to map:**
  - `Contact Name` → `{{3.contactName}}`
  - `Contact ID` → `{{3.id}}`
  - `Health Score` → parsed from Claude response
  - `Issues` → parsed from Claude response
  - `Recommended Action` → parsed from Claude response
  - `Date Audited` → `{{now}}`

---

## GHL API Field Reference

These are the exact field names returned by the GHL contacts API:

| Field | GHL API Key |
|---|---|
| Contact ID | `id` |
| Full Name | `contactName` |
| First Name | `firstName` |
| Last Name | `lastName` |
| Email | `email` |
| Phone | `phone` |
| Tags | `tags` (array) |
| Source | `source` |
| Assigned Owner | `assignedTo` |
| Location ID | `locationId` |
| Date Added | `dateAdded` |
| Date Updated | `dateUpdated` |
| Country | `country` |
| Type | `type` |

---

## Notion Database Schema

Create a Notion database called `GHL CRM Audit` with these columns:

| Column | Type |
|---|---|
| Contact Name | Title |
| Contact ID | Text |
| Health Score | Number |
| Issues | Text |
| Recommended Action | Text |
| Date Audited | Date |
| Sub-Account | Text |

---

## Audit Criteria

Claude evaluates each contact against these criteria:

| Check | Flag If |
|---|---|
| Missing email | `email` is empty |
| Missing phone | `phone` is empty |
| No tags | `tags` array is empty |
| No source | `source` is empty |
| Unassigned | `assignedTo` is empty |
| Missing name | `contactName` is empty |

**Health Score Guide:**
- 90-100: Clean contact, no issues
- 70-89: Minor issues, low priority
- 45-69: Multiple missing fields, medium priority
- 0-44: Critical issues, urgent action required

---

## Weekly Automation Schedule

Once the scenario is working:
1. In Make.com, set the schedule to **Every Monday at 8:00 AM**
2. The system will automatically audit all contacts weekly
3. Results accumulate in Notion with date stamps
4. Review the Notion database weekly to action fixes

---

## Common Errors & Fixes

| Error | Cause | Fix |
|---|---|---|
| 401 Unauthorized | Wrong or missing API key | Re-enter Bearer token in header |
| 422 Invalid JWT | Using old-style API key | Create a Private Integration JWT token |
| Token not authorized for scope | Agency token used for contacts | Create sub-account level token with contact scopes |
| Credit balance too low | Anthropic account unfunded | Add credits at console.anthropic.com → Billing |
| toJSON not found | Make doesn't support toJSON | Use `toString()` or map fields individually |
| Contact data coming through empty | Iterator variable wrong | Use `{{3.fieldName}}` not `{{3.value.fieldName}}` |
| Pagination missing value | Page size value not set | Set Page size parameter value to `100` |

---

## Phase Roadmap

| Phase | Status | Description |
|---|---|---|
| Phase 1 — Audit | ✅ Built | Pull contacts → Claude analysis → Notion output |
| Phase 2 — Auto-Fix | 🔜 Next | Auto-tag untagged contacts, assign owners, flag duplicates |
| Phase 3 — Alerts | 🔜 Future | Real-time Slack/email alerts when new issues detected |
| Phase 4 — Multi-Account | 🔜 Future | Loop across all Paramount MD client sub-accounts |

---

## Current Build Status (Paramount MD)

- **Sub-account:** Paramount MD (locationId: `33l120d4J3Ctd1aaDmVc`)
- **Total contacts:** 2,219
- **Make scenario:** GHL CRM Auditor v1 (3 modules live)
- **Modules complete:** HTTP (GHL) ✅ | Iterator ✅ | HTTP (Claude) ✅
- **Pending:** Notion output module
- **Output destination:** Notion database (not yet created)
