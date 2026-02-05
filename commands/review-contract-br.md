---
description: Revisar contrato (pt-BR) contra playbook — apontar desvios, sugerir redações e resumir riscos
argument-hint: "<arquivo ou texto do contrato>"
---

# /review-contract-br

Revisão contratual orientada por playbook brasileiro (inclui checagens LGPD quando aplicável).

## Workflow (alto nível)

1) Aceitar contrato (arquivo/URL/texto)
2) Coletar contexto (papel, prazo, foco, dados pessoais)
3) Carregar playbook local (`legal-br.local.md`)
4) Analisar cláusulas e classificar: VERDE/AMARELO/VERMELHO
5) Gerar sugestões de redação (pt-BR) e estratégia

## Output

- Resumo executivo
- Top issues
- Análise por cláusula (com citações do contrato)
- Sugestões de redação
- Próximos passos
