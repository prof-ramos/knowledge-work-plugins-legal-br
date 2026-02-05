# CLAUDE.md — Plugin Jurídico (Brasil)

## Project Overview

A Claude plugin (pt-BR) for automating Brazilian legal workflows. It provides commands and skills for contract review, NDA triage, LGPD compliance checks, legal risk assessment, canned responses, and meeting briefings. The plugin runs within Claude (Cowork/Claude Code) and integrates with external tools via MCP connectors.

**Version:** 0.2.0
**Language:** Portuguese (pt-BR) — all user-facing content must be in pt-BR
**Author:** prof-ramos

> **Critical disclaimer:** This plugin assists legal workflows but does NOT provide legal advice. All outputs must be reviewed by a qualified legal professional.

## Repository Structure

```
.
├── CLAUDE.md                  # This file — project guide for AI assistants
├── README.md                  # Quick-start guide (pt-BR)
├── PRD.md                     # Product requirements document
├── CONNECTORS.md              # MCP connector specifications
├── .claude-plugin/
│   └── plugin.json            # Plugin metadata (name, version, description)
├── .mcp.json                  # MCP server configuration
├── commands/                  # User-facing slash commands (YAML frontmatter + markdown)
│   ├── review-contract-br.md  # /review-contract-br — contract review with playbook
│   ├── triage-nda-br.md       # /triage-nda-br — NDA triage (green/yellow/red)
│   ├── vendor-check-br.md     # /vendor-check-br — vendor agreement status
│   ├── brief-br.md            # /brief-br — legal briefing (daily/topic/incident)
│   └── respond-br.md          # /respond-br — standardized responses from templates
└── skills/                    # Reusable skill components (YAML frontmatter + markdown)
    ├── contract-review-br/SKILL.md
    ├── nda-triage-br/SKILL.md
    ├── lgpd-compliance/SKILL.md
    ├── legal-risk-assessment-br/SKILL.md
    ├── canned-responses-br/SKILL.md
    └── meeting-briefing-br/SKILL.md
```

## Architecture

This is a **documentation-only plugin** — no compiled code, no build system, no runtime dependencies. The entire plugin consists of markdown files with YAML frontmatter that define commands and skills for the Claude plugin system.

### Key concepts

- **Commands** (`commands/*.md`): User-facing entry points invoked as slash commands. Each file has YAML frontmatter with `description` and `argument-hint`, followed by workflow and output specifications.
- **Skills** (`skills/*/SKILL.md`): Reusable knowledge components that commands draw upon. Each has YAML frontmatter with `name` and `description`, followed by checklists, frameworks, and principles.
- **Playbook** (`.claude/legal-br.local.md`): Organization-specific local file (not committed) containing default positions, acceptable ranges, escalation triggers, drafting templates, and risk matrices.
- **MCP connectors**: Tool-agnostic integrations referenced via `~~category` placeholders (e.g., `~~cloud storage`, `~~chat`, `~~CLM`).

### How commands and skills relate

Commands orchestrate user workflows and use skills as building blocks. For example, `/review-contract-br` relies on `contract-review-br`, `lgpd-compliance`, and `legal-risk-assessment-br` skills.

## File Format Conventions

### Command files (`commands/*.md`)

```yaml
---
description: Short description in pt-BR
argument-hint: "<usage hint>"
---

# /command-name

[Workflow steps, output format, rules]
```

### Skill files (`skills/*/SKILL.md`)

```yaml
---
name: skill-name
description: What the skill does, in pt-BR
---

# Skill — Display Name

[Principles, checklists, frameworks, output format]
```

## Key Conventions

### Risk classification

All risk assessments use a three-tier system:
- **VERDE** (green): Acceptable, no material impact
- **AMARELO** (yellow): Negotiate, moderate impact, standard alternatives exist
- **VERMELHO** (red): Escalate, significant financial/reputational/regulatory/operational impact

### Brazilian legal scope

The plugin prioritizes Brazilian legal standards:
- **LGPD** (Lei 13.709/2018) — data protection, incidents, operators/sub-operators
- **Código Civil** — contractual practices (penalties, interest/adjustment, jurisdiction/arbitration)
- **CDC** — consumer protection when applicable (abusive clauses)
- Jurisprudence: only cite when a reliable source is available via connectors; otherwise mark as hypothesis for validation

### Content guidelines

- All user-facing text in **pt-BR**
- Always signal uncertainty explicitly — never fabricate legal references
- Always include **next steps** and **escalation triggers** in outputs
- Minimize sensitive data retention
- Require verifiable citations when referencing legal sources
- Mark outputs as drafts when playbook templates are not available

## MCP Connectors

The plugin is **tool-agnostic**. Placeholders in files reference categories, not specific products:

| Placeholder | Examples |
|---|---|
| `~~cloud storage` | Box, SharePoint, Google Drive, Egnyte |
| `~~office suite` | Microsoft 365, Google Workspace |
| `~~chat` | Slack, Teams |
| `~~project tracker` | Jira, Confluence, Asana |
| `~~CLM` | Contract Lifecycle Management (optional) |
| `~~CRM` | CRM system (optional) |
| `~~e-signature` | E-signature platform (optional) |
| `~~github reader` | Zread MCP Server (optional) |

Configuration lives in `.mcp.json`. Currently configured: `chat` (placeholder) and `zread` (Z.AI GitHub reader).

## Development Workflow

### There is no build, test, or lint step

This project has no code to compile, no tests to run, and no linter configuration. All content is markdown.

### Adding a new command

1. Create `commands/<command-name>.md` with YAML frontmatter (`description`, `argument-hint`)
2. Add the command heading as `# /<command-name>`
3. Document workflow steps, output format, and rules
4. Update `README.md` to list the new command

### Adding a new skill

1. Create `skills/<skill-name>/SKILL.md` with YAML frontmatter (`name`, `description`)
2. Add the skill heading as `# Skill — Display Name`
3. Document principles, checklists, and output format
4. Update `README.md` to list the new skill

### Updating plugin metadata

Edit `.claude-plugin/plugin.json` — bump `version` when making significant changes.

## Roadmap

- **MVP (current):** `/review-contract-br` + `/triage-nda-br` + playbook
- **Phase 2:** `/respond-br` + `/brief-br`
- **Phase 3:** `/vendor-check-br` with MCP connectors

## Important Reminders for AI Assistants

1. **Language:** Always produce content in pt-BR for this plugin
2. **No legal advice:** Include disclaimers; outputs are aids, not counsel
3. **No secrets in git:** Never commit API keys or credentials (use environment variables)
4. **Playbook is local:** `.claude/legal-br.local.md` is org-specific and should not be committed
5. **Tool-agnostic:** Use `~~category` placeholders, never hardcode specific tool names in commands/skills
6. **Citation integrity:** Never fabricate legal references; signal uncertainty when sources are unavailable
7. **Minimal changes:** This is a documentation plugin — keep files focused and concise
