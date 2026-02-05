---
description: Gerar resposta padronizada em pt-BR a partir de templates/playbook (com escalonamento quando necessário)
argument-hint: "<tipo-de-demanda>"
---

# /respond-br

Gera respostas padronizadas (e-mails/mensagens internas) com base em templates definidos no playbook local.

## Exemplos de tipos

- `pedido-dpa-lgpd`
- `pedido-nda`
- `pedido-revisao-contrato`
- `resposta-area-negocio-risco`
- `solicitacao-titular-lgpd`

## Regras

- Se o playbook não existir, usar padrões gerais e **marcar como rascunho**.
- Se houver gatilho de risco alto (VERMELHO), orientar escalonamento.
