---
description: Gerar briefing jurídico em pt-BR (diário/tema/incidente), usando conectores MCP quando disponíveis
argument-hint: "daily | incidente | tema <consulta>"
---

# /brief-br

## Modos

- `/brief-br daily` — pendências, prazos contratuais, solicitações recentes, alertas LGPD
- `/brief-br incidente` — checklist rápido para incidente de segurança/LGPD (triagem e próximos passos)
- `/brief-br tema <consulta>` — briefing sobre um tema (com fontes quando conectores/web estiverem disponíveis)

## Observações

- Sempre explicitar **fontes consultadas** e **limitações** quando não houver conectores.
- Incidente LGPD: produzir checklist e minuta de comunicação interna (não enviar automaticamente).
