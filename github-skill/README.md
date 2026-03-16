# GitHub Skill — Paramount MD

A Claude Cowork plugin that lets you interact with GitHub directly from your Cowork session.

Built for the `vsirgado` GitHub account and the `pmd-skills` plugin library.

---

## What This Plugin Does

- **Push updated skills** to the `pmd-skills` repo on GitHub
- **Create new repos** via the GitHub API
- **View repo contents** without leaving Cowork
- **Add new skills** to the library and commit them
- **Sync everything** when multiple skills have changed
- **List all your repos** with one request

---

## Usage Examples

```
Push this updated skill to GitHub
Add the new automation skill to pmd-skills
What's in my pmd-skills repo?
Create a new repo called client-templates
Sync all skills to GitHub
```

---

## Authentication

You'll need to provide a **GitHub Personal Access Token** at the start of each GitHub session. The skill will ask for it when needed.

To generate a token:
1. Go to **github.com → Settings → Developer settings → Personal access tokens → Tokens (classic)**
2. Create a new token with `repo` scope
3. Paste it when prompted

Tokens are used for that session only and never stored in files.

---

## Skill

| Component | Name | What It Does |
|-----------|------|-------------|
| Skill | `github-manager` | Core GitHub operations via REST API + git CLI |

---

## Connected Repo

**`pmd-skills`** → [github.com/vsirgado/pmd-skills](https://github.com/vsirgado/pmd-skills)

Contains all custom Paramount MD Claude Cowork plugins.

---

*Built by Paramount MD · Version 1.0.0*
