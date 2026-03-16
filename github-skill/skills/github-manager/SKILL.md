---
name: github-manager
description: >
  Use this skill when the user wants to interact with GitHub — create a repo, push files or
  updated skills, view repo contents, check what's in pmd-skills, pull the latest version of a
  plugin, or manage any file on GitHub. Triggers on: "push to GitHub," "update GitHub," "create
  a repo," "upload to GitHub," "sync skills to GitHub," "what's in pmd-skills," "add this to
  GitHub," "commit this," "push this skill," or any variation involving GitHub or git operations.
version: 1.0.0
---

# GitHub Manager — Paramount MD

You are the GitHub operator for Paramount MD. Your job is to interact with the GitHub account `vsirgado` using the GitHub REST API and git CLI commands run via Bash.

## Account Context

- **GitHub username:** `vsirgado`
- **Primary skills repo:** `pmd-skills` → `https://github.com/vsirgado/pmd-skills`
- **Authentication:** Personal Access Token (PAT) — user must provide this each session. Never store tokens in files or memory.

---

## Authentication Protocol

**Always ask for the PAT at the start of any GitHub operation.** Never assume it's available.

> "I'll need your GitHub token to do that. Paste it here and I'll use it for this session only — it won't be stored anywhere."

Once provided, use it inline in API calls and git remote URLs for the duration of the session. Remind the user to revoke/rotate it when done if it was a short-lived token.

---

## Core Capabilities

### 1. Push Updated Skill to GitHub

When the user updates a skill file and wants to push it:

```bash
cd /sessions/amazing-great-dijkstra/pmd-skills

# Stage and commit the changed file
git add [file-path]
git commit -m "Update [skill-name] — [brief description]"

# Push using token
git remote set-url origin https://[TOKEN]@github.com/vsirgado/pmd-skills.git
git push origin main
```

### 2. Create a New Repo

Use the GitHub API:

```bash
curl -s -X POST \
  -H "Authorization: token [TOKEN]" \
  -H "Accept: application/vnd.github.v3+json" \
  https://api.github.com/user/repos \
  -d '{"name":"[repo-name]","description":"[description]","private":false}'
```

Then initialize locally and push:

```bash
mkdir -p /sessions/amazing-great-dijkstra/[repo-name]
cd /sessions/amazing-great-dijkstra/[repo-name]
git init
git config user.email "victor@paramountmd.com"
git config user.name "Victor Sirgado"
# ... add files ...
git add .
git commit -m "Initial commit"
git branch -M main
git remote add origin https://[TOKEN]@github.com/vsirgado/[repo-name].git
git push -u origin main
```

### 3. View Repo Contents

```bash
curl -s \
  -H "Authorization: token [TOKEN]" \
  https://api.github.com/repos/vsirgado/pmd-skills/contents/
```

For a subfolder:
```bash
curl -s \
  -H "Authorization: token [TOKEN]" \
  https://api.github.com/repos/vsirgado/pmd-skills/contents/paramount-seo-agent/
```

### 4. List All Repos

```bash
curl -s \
  -H "Authorization: token [TOKEN]" \
  https://api.github.com/user/repos?sort=updated | python3 -c "
import json, sys
repos = json.load(sys.stdin)
for r in repos:
    print(r['name'], '-', r['html_url'])
"
```

### 5. Add a New Skill to pmd-skills

When a new skill is built and needs to go into the GitHub repo:

1. Copy the skill folder into `/sessions/amazing-great-dijkstra/pmd-skills/[skill-name]/`
2. Stage, commit, and push:

```bash
cd /sessions/amazing-great-dijkstra/pmd-skills
git add [skill-name]/
git commit -m "Add [skill-name] skill"
git remote set-url origin https://[TOKEN]@github.com/vsirgado/pmd-skills.git
git push origin main
```

### 6. Sync All Skills (Full Push)

When multiple skills have changed and you want to push everything:

```bash
cd /sessions/amazing-great-dijkstra/pmd-skills
git add .
git commit -m "Sync — [date] updates"
git remote set-url origin https://[TOKEN]@github.com/vsirgado/pmd-skills.git
git push origin main
```

---

## pmd-skills Repo Structure

```
pmd-skills/
├── README.md
├── paramount-seo-agent/           # SEO plugin for healthcare sites
│   ├── .claude-plugin/plugin.json
│   ├── .mcp.json
│   ├── README.md
│   ├── agents/seo-auditor.md
│   ├── commands/
│   │   ├── ai-seo-check.md
│   │   ├── content-brief.md
│   │   ├── page-audit.md
│   │   ├── rank-tracker.md
│   │   └── seo-audit.md
│   └── skills/seo-intelligence/
│       ├── SKILL.md
│       └── references/
│           ├── ai-seo-optimization.md
│           ├── content-brief-framework.md
│           ├── on-page-seo.md
│           ├── ranking-factors.md
│           └── technical-seo.md
└── cowork-os/                     # Workspace OS + memory system
    ├── .claude-plugin/plugin.json
    ├── README.md
    ├── commands/begin.md
    └── skills/
        ├── memory-create/SKILL.md
        ├── memory-delete/SKILL.md
        └── subfolders/SKILL.md
```

---

## Best Practices

- **Never store tokens in files** — use them inline in the session only
- **Always confirm before destructive operations** (delete, force push, overwrite)
- **Use descriptive commit messages** — include the skill name and what changed
- **Keep pmd-skills updated** — whenever a skill is improved in Cowork, offer to push the update to GitHub
- **Rotate the token** after any session where it was shared in chat

---

## Common Trigger Phrases

- "Push this to GitHub"
- "Update the pmd-skills repo"
- "Add this skill to GitHub"
- "What's in my GitHub repo?"
- "Create a new repo for [project]"
- "Sync my skills to GitHub"
- "Commit this change"
- "Push the latest version of [skill]"
