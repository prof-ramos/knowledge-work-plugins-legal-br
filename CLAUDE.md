# CLAUDE.md — Plugin Jurídico (Brasil)

## Visão Geral

Plugin Claude (pt-BR) para automação de fluxos jurídicos brasileiros. Oferece comandos e skills para revisão contratual, triagem de NDAs, checagem de conformidade LGPD, avaliação de risco jurídico, respostas padronizadas e briefings de reuniões. Funciona no Claude (Cowork/Claude Code) e integra ferramentas externas via conectores MCP.

**Versão:** 0.2.0
**Idioma:** Português (pt-BR) — todo conteúdo voltado ao usuário deve ser em pt-BR
**Autor:** prof-ramos

> **Aviso importante:** este plugin auxilia fluxos jurídicos, mas **não presta consultoria jurídica**. Todo output deve ser revisado por profissional habilitado.

## Estrutura do Repositório

```
.
├── CLAUDE.md                  # Este arquivo — guia do projeto para assistentes de IA
├── README.md                  # Guia rápido (pt-BR)
├── PRD.md                     # Documento de requisitos do produto
├── CONNECTORS.md              # Especificações de conectores MCP
├── .claude-plugin/
│   └── plugin.json            # Metadados do plugin (nome, versão, descrição)
├── .mcp.json                  # Configuração de servidores MCP
├── commands/                  # Comandos de usuário (YAML frontmatter + markdown)
│   ├── review-contract-br.md  # /review-contract-br — revisão contratual com playbook
│   ├── triage-nda-br.md       # /triage-nda-br — triagem de NDA (verde/amarelo/vermelho)
│   ├── vendor-check-br.md     # /vendor-check-br — status contratual por fornecedor
│   ├── brief-br.md            # /brief-br — briefing jurídico (diário/tema/incidente)
│   └── respond-br.md          # /respond-br — respostas padronizadas a partir de templates
└── skills/                    # Componentes reutilizáveis de conhecimento (YAML frontmatter + markdown)
    ├── contract-review-br/SKILL.md
    ├── nda-triage-br/SKILL.md
    ├── lgpd-compliance/SKILL.md
    ├── legal-risk-assessment-br/SKILL.md
    ├── canned-responses-br/SKILL.md
    └── meeting-briefing-br/SKILL.md
```

## Arquitetura

Este é um **plugin somente de documentação** — sem código compilado, sem sistema de build, sem dependências de runtime. O plugin inteiro consiste em arquivos markdown com YAML frontmatter que definem comandos e skills para o sistema de plugins do Claude.

### Conceitos-chave

- **Comandos** (`commands/*.md`): Pontos de entrada do usuário, invocados como slash commands. Cada arquivo possui YAML frontmatter com `description` e `argument-hint`, seguido de especificações de workflow e output.
- **Skills** (`skills/*/SKILL.md`): Componentes de conhecimento reutilizáveis usados pelos comandos. Cada um possui YAML frontmatter com `name` e `description`, seguido de checklists, frameworks e princípios.
- **Playbook** (`.claude/legal-br.local.md`): Arquivo local específico da organização (não commitado) contendo posições padrão, faixas aceitáveis, gatilhos de escalonamento, templates de redação e matrizes de risco.
- **Conectores MCP**: Integrações agnósticas a ferramentas, referenciadas via placeholders `~~categoria` (ex.: `~~cloud storage`, `~~chat`, `~~CLM`).

### Relação entre comandos e skills

Comandos orquestram fluxos de trabalho e usam skills como blocos de construção. Por exemplo, `/review-contract-br` utiliza as skills `contract-review-br`, `lgpd-compliance` e `legal-risk-assessment-br`.

## Convenções de Formato de Arquivo

### Arquivos de comando (`commands/*.md`)

```yaml
---
description: Descrição curta em pt-BR
argument-hint: "<dica de uso>"
---

# /nome-do-comando

[Etapas do workflow, formato de saída, regras]
```

### Arquivos de skill (`skills/*/SKILL.md`)

```yaml
---
name: nome-da-skill
description: O que a skill faz, em pt-BR
---

# Skill — Nome de Exibição

[Princípios, checklists, frameworks, formato de saída]
```

## Convenções Principais

### Classificação de risco

Todas as avaliações de risco usam um sistema de três níveis:
- **VERDE**: Aceitável; sem impacto material
- **AMARELO**: Negociar; impacto moderado; existem alternativas padrão
- **VERMELHO**: Escalar; potencial impacto relevante (financeiro, reputacional, regulatório, operacional)

### Escopo jurídico brasileiro

O plugin prioriza padrões legais brasileiros:
- **LGPD** (Lei 13.709/2018) — proteção de dados, incidentes, operadores/suboperadores
- **Código Civil** — práticas contratuais (multas, juros/correção, foro/arbitragem)
- **CDC** — proteção ao consumidor quando aplicável (cláusulas abusivas)
- Jurisprudência: citar apenas quando houver fonte confiável via conectores; caso contrário, sinalizar como hipótese para validação

### Diretrizes de conteúdo

- Todo texto voltado ao usuário em **pt-BR**
- Sempre sinalizar incerteza explicitamente — nunca fabricar referências legais
- Sempre incluir **próximos passos** e **gatilhos de escalonamento** nos outputs
- Minimizar retenção de dados sensíveis
- Exigir citações verificáveis ao referenciar fontes jurídicas
- Marcar outputs como rascunho quando templates do playbook não estiverem disponíveis

## Conectores MCP

O plugin é **agnóstico a ferramentas**. Placeholders nos arquivos referenciam categorias, não produtos específicos:

| Placeholder | Exemplos |
|---|---|
| `~~cloud storage` | Box, SharePoint, Google Drive, Egnyte |
| `~~office suite` | Microsoft 365, Google Workspace |
| `~~chat` | Slack, Teams |
| `~~project tracker` | Jira, Confluence, Asana |
| `~~CLM` | Contract Lifecycle Management (opcional) |
| `~~CRM` | Sistema CRM (opcional) |
| `~~e-signature` | Plataforma de assinatura eletrônica (opcional) |
| `~~github reader` | Zread MCP Server (opcional) |

A configuração fica em `.mcp.json`. Atualmente configurados: `chat` (placeholder) e `zread` (leitor GitHub da Z.AI).

## Fluxo de Desenvolvimento

### Não há etapas de build, teste ou lint

Este projeto não possui código para compilar, testes para rodar, nem configuração de linter. Todo o conteúdo é markdown.

### Adicionar um novo comando

1. Criar `commands/<nome-do-comando>.md` com YAML frontmatter (`description`, `argument-hint`)
2. Adicionar o heading do comando como `# /<nome-do-comando>`
3. Documentar etapas do workflow, formato de saída e regras
4. Atualizar `README.md` listando o novo comando

### Adicionar uma nova skill

1. Criar `skills/<nome-da-skill>/SKILL.md` com YAML frontmatter (`name`, `description`)
2. Adicionar o heading como `# Skill — Nome de Exibição`
3. Documentar princípios, checklists e formato de saída
4. Atualizar `README.md` listando a nova skill

### Atualizar metadados do plugin

Editar `.claude-plugin/plugin.json` — incrementar `version` ao fazer mudanças significativas.

## Roadmap

- **MVP (atual):** `/review-contract-br` + `/triage-nda-br` + playbook
- **Fase 2:** `/respond-br` + `/brief-br`
- **Fase 3:** `/vendor-check-br` com conectores MCP

## Lembretes Importantes para Assistentes de IA

1. **Idioma:** Sempre produzir conteúdo em pt-BR para este plugin
2. **Não é consultoria jurídica:** Incluir disclaimers; outputs são auxílios, não parecer jurídico
3. **Sem segredos no git:** Nunca commitar chaves de API ou credenciais (usar variáveis de ambiente)
4. **Playbook é local:** `.claude/legal-br.local.md` é específico da organização e não deve ser commitado
5. **Agnóstico a ferramentas:** Usar placeholders `~~categoria`, nunca hardcodar nomes de ferramentas em comandos/skills
6. **Integridade de citações:** Nunca fabricar referências legais; sinalizar incerteza quando fontes não estiverem disponíveis
7. **Mudanças mínimas:** Este é um plugin de documentação — manter arquivos focados e concisos
