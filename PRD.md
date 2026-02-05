# PRD (Plugin) — Automação de Fluxos Legais (Brasil)

**Versão:** 0.1 (rascunho inicial)

Este PRD descreve o **escopo plugin-first** (commands/skills/playbook + MCP). Não descreve uma plataforma SaaS com backend próprio.

## 1. Visão

Criar um plugin em pt-BR para acelerar fluxos jurídicos recorrentes no Brasil (contratos/NDAs/LGPD), padronizando outputs e reduzindo tempo de triagem e primeira revisão.

## 2. Metas

- Reduzir tempo de primeira revisão (contrato/NDA) com checklist + playbook.
- Aumentar consistência (padrões de cláusulas e gatilhos de escalonamento).
- Garantir cobertura mínima de LGPD quando houver tratamento de dados pessoais.

## 3. Não-metas

- Não substituir revisão humana.
- Não prometer atualização normativa/jurisprudencial automática sem conectores/fontes.
- Não realizar assinatura ICP-Brasil diretamente (fora do escopo do plugin, salvo via MCP dedicado).

## 4. Personas

- Jurídico interno (contratos/comercial)
- Privacidade/LGPD
- Paralegal/analista jurídico
- Escritório pequeno/médio

## 5. Funcionalidades (commands)

### 5.1 `/review-contract-br`

**Entrada:** arquivo/URL/texto.

**Contexto coletado:** papel (contratante/contratada), prazo, foco, dados pessoais (sim/não), valor/criticidade.

**Saída:** resumo executivo + top issues + análise por cláusula + sugestões de redação + estratégia.

**Severidade:** VERDE/AMARELO/VERMELHO.

### 5.2 `/triage-nda-br`

Checklist NDA BR + classificação VERDE/AMARELO/VERMELHO + sugestões de ajustes.

### 5.3 `/vendor-check-br`

Se conectores disponíveis, buscar acordos e consolidar status (NDA/MSA/DPA/SOW).

### 5.4 `/brief-br`

Briefing diário/tema/incidente (incl. incidente LGPD com checklist).

### 5.5 `/respond-br`

Respostas padronizadas com templates do playbook.

## 6. Playbook local

Arquivo recomendado: `.claude/legal-br.local.md`

Conteúdo mínimo:
- posições padrão por cláusula
- ranges aceitáveis
- gatilhos de escalonamento
- templates de redação
- matriz de risco

## 7. Riscos e mitigação

- Alucinação em referências legais → exigir citações verificáveis quando houver fonte; sinalizar incerteza.
- Dados sensíveis → minimizar retenção; orientar usuário.

## 8. Roadmap

- MVP: `/review-contract-br` + `/triage-nda-br` + playbook.
- Fase 2: `/respond-br` + `/brief-br`.
- Fase 3: `/vendor-check-br` com MCP.
