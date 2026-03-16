# PMD Skills

Custom Claude Cowork plugins built by **Victor Sirgado / Paramount MD**.

Paramount MD is a digital marketing and content development company specializing in healthcare practices and medical experts.

---

## Plugins

### [`paramount-seo-agent`](./paramount-seo-agent/)
Superpowered SEO agent for Paramount MD. Audits pages, tracks rankings, generates content briefs, and syncs everything to Notion. Built specifically for healthcare and medical practice websites.

**Components:** 1 skill · 5 commands · 1 autonomous agent

### [`cowork-os`](./cowork-os/)
Workspace OS for Claude Cowork. Handles session initialization, persistent memory management, and structured subfolder creation.

**Components:** 3 skills · 1 command

---

## Installation

These plugins are designed for use with [Claude Cowork](https://claude.ai). To install:

1. Download the plugin folder
2. Open Claude Cowork → Settings → Plugins
3. Click **Install local plugin** and select the folder

---

## Structure

```
pmd-skills/
├── paramount-seo-agent/       # SEO intelligence + audit commands
│   ├── .claude-plugin/
│   ├── agents/
│   ├── commands/
│   └── skills/seo-intelligence/references/
└── cowork-os/                 # Workspace OS + memory system
    ├── .claude-plugin/
    ├── commands/
    └── skills/
```

---

*Built by [Paramount MD](https://paramountmd.com) · Version 1.0.0*
