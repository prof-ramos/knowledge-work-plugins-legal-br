---
name: admin-law-federal-br
description: Apoio a consultorias jurídicas internas de órgãos federais em PAD (processo administrativo disciplinar) e pareceres/consultas jurídicas, com checklists, roteiros e estrutura de parecer.
---

# Skill — Direito Administrativo Federal (Brasil)

## Propósito

Apoiar consultorias jurídicas internas de ministérios, autarquias e fundações públicas federais em duas frentes:

1. **PAD / Processo Administrativo** — triagem, classificação e roteiro de condução
2. **Parecer / Consulta Jurídica** — estrutura formal e checklist de análise

> **Aviso:** esta skill produz rascunhos para revisão por profissional habilitado. Não substitui parecer formal nem configura consultoria jurídica.

## Base normativa

- **CF/88** — princípios da administração pública (art. 37 e correlatos)
- **Lei 8.112/1990** — regime jurídico dos servidores federais (PAD, direitos, deveres, penalidades)
- **Lei 9.784/1999** — processo administrativo no âmbito federal (prazos, recursos, nulidades, motivação)
- **Lei 14.133/2023** — nova lei de licitações (manifestação jurídica obrigatória, art. 53 e correlatos)
- **LC 73/1993 + Lei 13.327/2016** — organização da AGU e carreiras jurídicas (referência contextual)
- **Manual de PAD — CGU/CRG** (edição nov/2025) — referência operacional para condução de processos disciplinares

### Jurisprudência de referência

- **Súmula 635/STJ** — prazo prescricional em PAD
- **Súmula 650/STJ** — taxatividade das hipóteses de demissão (art. 132, Lei 8.112/1990)

> Citar jurisprudência apenas quando houver fonte confiável; caso contrário, sinalizar como hipótese para validação.

---

## Módulo 1 — PAD / Processo Administrativo

### Princípios

- Sempre indicar o rito adequado com base na gravidade do fato
- Verificar prescrição antes de qualquer recomendação de instauração
- Sinalizar vícios que possam gerar nulidade (contraditório, ampla defesa, motivação)
- Seguir as orientações do Manual de PAD da CGU/CRG como referência operacional

### Classificação do fato

| Gravidade | Exemplos | Rito recomendado |
|---|---|---|
| **Leve** | Atrasos, descumprimento pontual de dever funcional | Sindicância (arts. 143-145, Lei 8.112) |
| **Média** | Acumulação ilícita, abandono de cargo, inassiduidade habitual | PAD Sumário (arts. 133-134, Lei 8.112) |
| **Grave** | Improbidade, corrupção, lesão aos cofres públicos, insubordinação grave | PAD Ordinário (arts. 148-182, Lei 8.112) |

### Checklist — Fases do PAD

#### Instauração
- [ ] Portaria de instauração (autoridade competente, membros da comissão, prazo)
- [ ] Publicação no DOU / boletim interno
- [ ] Verificação de impedimento/suspeição dos membros

#### Instrução
- [ ] Notificação do servidor (citação válida)
- [ ] Oitiva de testemunhas
- [ ] Diligências e perícias (se necessárias)
- [ ] Juntada de documentos

#### Defesa
- [ ] Intimação para apresentar defesa escrita
- [ ] Prazo: 10 dias (prorrogável por igual período) — art. 161, Lei 8.112
- [ ] Defensor dativo (se revel) — art. 164, Lei 8.112
- [ ] Vista dos autos garantida

#### Relatório
- [ ] Conclusão fundamentada da comissão
- [ ] Indicação de materialidade e autoria
- [ ] Sugestão de penalidade (se for o caso)

#### Julgamento
- [ ] Autoridade competente para julgar (art. 141, Lei 8.112)
- [ ] Prazo de 20 dias (art. 167, Lei 8.112)
- [ ] Fundamentação do julgamento (especialmente se divergir do relatório)

### Prescrição (Lei 8.112, art. 142)

| Penalidade | Prazo prescricional |
|---|---|
| Advertência | 180 dias |
| Suspensão | 2 anos |
| Demissão / Cassação / Destituição | 5 anos |

> **Atenção:** Súmula 635/STJ — o prazo prescricional conta da ciência do fato pela autoridade competente para instaurar o PAD.

### Penalidades (art. 127, Lei 8.112)

1. Advertência
2. Suspensão
3. Demissão
4. Cassação de aposentadoria/disponibilidade
5. Destituição de cargo em comissão / função de confiança

> **Atenção:** Súmula 650/STJ — as hipóteses de demissão do art. 132 são taxativas.

### Nulidades e vícios mais comuns

- Ausência de notificação válida do servidor
- Cerceamento de defesa (prazo insuficiente, negativa de vista dos autos)
- Comissão com membro impedido ou suspeito
- Ausência de fundamentação no julgamento
- Desproporção entre fato e penalidade aplicada

### Gatilhos de escalonamento

- **VERMELHO — escalar para CGU:** indícios de improbidade administrativa, envolvimento de autoridade com foro privilegiado, repercussão pública relevante
- **VERMELHO — escalar para AGU:** dúvida sobre competência, necessidade de parecer vinculante, conflito entre órgãos
- **AMARELO — escalar para autoridade superior:** divergência entre relatório da comissão e julgamento, prescrição iminente, risco de nulidade processual

### Formato de saída — Triagem PAD

```
## Triagem — PAD

**Fato relatado:** [resumo do fato]
**Classificação preliminar:** Leve / Média / Grave
**Rito recomendado:** Sindicância / PAD Ordinário / PAD Sumário
**Base legal:** [artigos aplicáveis]

### Checklist de fases
- [ ] Instauração (portaria, comissão, publicação)
- [ ] Instrução (oitivas, diligências, perícias)
- [ ] Defesa (citação, prazo, vista dos autos)
- [ ] Relatório (conclusão da comissão)
- [ ] Julgamento (autoridade competente)

### Prazos
- Prazo do rito: [X dias, prorrogável por Y]
- Prescrição: [prazo aplicável + referência]

### Alertas
- [VERDE/AMARELO/VERMELHO] — [descrição e justificativa]

### Próximos passos
- [ações recomendadas]

### Gatilhos de escalonamento
- [quando escalar para CGU, AGU ou autoridade superior]
```

---

## Módulo 2 — Parecer / Consulta Jurídica

### Princípios

- Seguir a estrutura formal de pareceres adotada pela AGU e consultorias jurídicas federais
- Fundamentar em legislação e, quando disponível, jurisprudência verificável
- Sempre concluir com posição clara (aprovação, aprovação com ressalvas, rejeição)
- Classificar o risco da recomendação usando o sistema VERDE/AMARELO/VERMELHO

### Checklist de análise

Ao analisar qualquer consulta jurídica, verificar:

- [ ] **Competência** — o órgão/autoridade tem competência para o ato?
- [ ] **Legalidade** — o ato está conforme a legislação aplicável?
- [ ] **Constitucionalidade** — há conformidade com a CF/88 (especialmente art. 37)?
- [ ] **Motivação** — os motivos de fato e de direito estão explícitos? (art. 50, Lei 9.784)
- [ ] **Razoabilidade / Proporcionalidade** — a medida é adequada, necessária e proporcional?
- [ ] **Forma** — o ato segue a forma prescrita em lei?
- [ ] **Finalidade** — atende ao interesse público?
- [ ] **Manifestação em licitações** — se aplicável, verificar exigência do art. 53, Lei 14.133/2023

### Classificação de risco

- **VERDE** — sem óbice jurídico relevante; recomendar aprovação
- **AMARELO** — aprovação condicionada a ajustes; riscos moderados mitigáveis
- **VERMELHO** — óbice jurídico relevante; recomendar rejeição ou escalonamento para autoridade superior

### Formato de saída — Parecer Jurídico

```
## Parecer Jurídico — [Assunto]

**Processo:** [número/referência]
**Interessado:** [órgão/setor solicitante]
**Assunto:** [descrição]

### I — Ementa
[síntese da conclusão em 2-3 linhas]

### II — Relatório
[resumo dos fatos e do pedido]

### III — Fundamentação
[análise jurídica: competência, legalidade, constitucionalidade,
razoabilidade/proporcionalidade, referências normativas]

### IV — Conclusão
[posição recomendada + classificação de risco VERDE/AMARELO/VERMELHO]

### V — Encaminhamento
[próximos passos + quem deve aprovar/revisar]
```

---

## Regras gerais

1. Todo output em **pt-BR**
2. Nunca fabricar referências legais ou jurisprudenciais — sinalizar incerteza quando a fonte não estiver disponível
3. Sempre incluir **próximos passos** e **gatilhos de escalonamento**
4. Marcar outputs como **rascunho** quando o playbook local não estiver disponível
5. Seguir o sistema de classificação de risco VERDE/AMARELO/VERMELHO do plugin
