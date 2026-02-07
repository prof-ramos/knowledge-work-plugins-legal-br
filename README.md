# Plugin Jurídico (Brasil) — Automação de Fluxos Legais

Plugin de produtividade jurídica (pt-BR) para uso em **Cowork/Claude** e também no **Claude Code**.

Foco: acelerar revisão contratual, triagem de NDAs e geração de respostas/briefings padronizados **no contexto legal brasileiro**, com atenção especial a **LGPD**, práticas contratuais locais e playbooks da organização.

> **Aviso importante:** este plugin auxilia fluxos jurídicos, mas **não presta consultoria jurídica**. Todo output deve ser revisado por profissional habilitado.

## Instalação (placeholder)

> Ajustar quando o pacote estiver publicado como plugin.

## Quick start

1) Configure o playbook local (ex.: `.claude/legal-br.local.md`) com posições padrão, faixas aceitáveis e gatilhos de escalonamento.
2) Conecte ferramentas via MCP (ver [CONNECTORS.md](CONNECTORS.md)).
3) Use os comandos.

## Comandos

- `/review-contract-br` — Revisão contratual com playbook BR
- `/triage-nda-br` — Triagem de NDA (verde/amarelo/vermelho)
- `/vendor-check-br` — Status contratual por fornecedor (se conectores estiverem disponíveis)
- `/brief-br` — Briefing jurídico (diário/tema/incidente)
- `/respond-br` — Respostas padronizadas (templates)

## Skills

### Skills jurídicas (pt-BR)

- `contract-review-br` — revisão contratual (Brasil) orientada por playbook
- `nda-triage-br` — triagem de NDA com checklist brasileiro
- `lgpd-compliance` — checklist LGPD para contratos
- `legal-risk-assessment-br` — framework de classificação de risco jurídico
- `canned-responses-br` — templates e respostas padronizadas
- `meeting-briefing-br` — preparação de reuniões jurídicas
- `admin-law-federal-br` — direito administrativo federal (PAD e pareceres jurídicos)

### Skills de produtividade (terceiros)

- `ms-office-suite:pdf` — processamento de PDFs (leitura, criação, merge, formulários, OCR)
- `ms-office-suite:docx` — criação, edição e análise de documentos Word
- `ms-office-suite:pptx` — criação e edição de apresentações PowerPoint
- `ms-office-suite:xlsx` — criação, edição e análise de planilhas Excel
- `internal-comms` — comunicações internas (3P updates, newsletters, FAQs)
- `content-research-writer` — assistente de pesquisa e redação de conteúdo
- `family-history-research` — planejamento de pesquisa genealógica e história familiar

## Estrutura

```
.
├── .claude-plugin/plugin.json
├── .mcp.json
├── CONNECTORS.md
├── PRD.md
├── commands/
└── skills/
    ├── contract-review-br/         # Skills jurídicas (pt-BR)
    ├── nda-triage-br/
    ├── lgpd-compliance/
    ├── legal-risk-assessment-br/
    ├── canned-responses-br/
    ├── meeting-briefing-br/
    ├── admin-law-federal-br/
    ├── ms-office-suite:pdf/        # Skills de produtividade (terceiros)
    ├── ms-office-suite:docx/
    ├── ms-office-suite:pptx/
    ├── ms-office-suite:xlsx/
    ├── internal-comms/
    ├── content-research-writer/
    └── family-history-research/
```
