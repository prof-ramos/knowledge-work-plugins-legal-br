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

- `contract-review-br`
- `nda-triage-br`
- `lgpd-compliance`
- `legal-risk-assessment-br`
- `canned-responses-br`
- `meeting-briefing-br`

## Estrutura

```
.
├── .claude-plugin/plugin.json
├── .mcp.json
├── CONNECTORS.md
├── PRD.md
├── commands/
└── skills/
```
