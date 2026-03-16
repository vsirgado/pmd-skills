# PMD Skills

Custom Claude Cowork plugins built by **Victor Sirgado / Paramount MD**.

Paramount MD is a digital marketing and content development company specializing in healthcare practices and medical experts.

---

## Plugins

### PMD Custom Builds

| Plugin | Description |
|--------|-------------|
| [`paramount-seo-agent`](./paramount-seo-agent/) | SEO intelligence for healthcare sites — audits, rank tracking, content briefs, Notion sync |
| [`cowork-os`](./cowork-os/) | Workspace OS — session init, persistent memory, subfolder creation |
| [`github-skill`](./github-skill/) | Interact with GitHub from Cowork — create repos, push files, sync skills |

### Downloaded & Tracked

| Plugin | Source | Description |
|--------|--------|-------------|
| [`superpowers`](./superpowers/) | [obra/superpowers](https://github.com/obra/superpowers) | Core skills library — TDD, debugging, collaboration patterns, git worktrees |
| [`claude-mem`](./claude-mem/) | [thedotmack/claude-mem](https://github.com/thedotmack/claude-mem) | Auto-captures session context and injects relevant memory into future sessions |
| [`ui-ux-pro-max`](./ui-ux-pro-max/) | [nextlevelbuilder/ui-ux-pro-max-skill](https://github.com/nextlevelbuilder/ui-ux-pro-max-skill) | UI/UX design intelligence — 50 styles, 9 stacks, 50+ font pairings |
| [`awesome-claude-skills`](./awesome-claude-skills/) | [travisvn/awesome-claude-skills](https://github.com/travisvn/awesome-claude-skills) | Curated reference list of the best Claude skills across the community |

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
