---
description: Consultar e consolidar status de acordos por fornecedor (NDA/MSA/DPA/SOW) em pt-BR (via conectores MCP quando disponíveis)
argument-hint: "[nome do fornecedor]"
---

# /vendor-check-br

Consolida o status de relacionamento contratual com um fornecedor.

## Workflow

1) Receber o nome do fornecedor
2) Se houver conectores MCP, pesquisar em:
   - ~~CLM (se existir)
   - ~~cloud storage (pastas de contratos)
   - ~~office suite (e-mail/anexos)
   - ~~chat (pedidos e contexto)
   - ~~project tracker (tarefas/matters)
3) Listar contratos encontrados (tipo, status, datas críticas)
4) Identificar lacunas (ex.: há MSA mas falta DPA e existe tratamento de dados)

## Saída (formato)

- Visão geral do relacionamento
- Acordos encontrados (com datas e localização)
- Lacunas e alertas (LGPD, vencimentos, renovação automática)
- Próximos passos recomendados
