# Connectors (MCP)

Este plugin é **agnóstico a ferramentas**. Nos arquivos, usamos placeholders do tipo `~~categoria`.

Exemplos:
- `~~cloud storage` → Box / SharePoint / Google Drive / Egnyte
- `~~office suite` → Microsoft 365 / Google Workspace
- `~~chat` → Slack / Teams
- `~~project tracker` → Jira / Confluence / Asana

## Categorias sugeridas para este plugin

- Chat: `~~chat`
- Cloud storage: `~~cloud storage`
- Office suite: `~~office suite`
- Project tracker: `~~project tracker`
- CLM: `~~CLM` (opcional)
- CRM: `~~CRM` (opcional)
- E-signature: `~~e-signature` (opcional)
- GitHub/Open-source reader: `~~github reader` (via **Zread MCP Server**, opcional)

> Observação: integrações específicas do Brasil (ex.: SEI, SAJ, eproc) **não são garantidas** no plugin puro; podem exigir MCP servers dedicados.

## Zread MCP Server (Z.AI) — leitura de repositórios GitHub

O **Zread MCP Server** permite que clientes compatíveis (Claude Code, Cline etc.) acessem e analisem repositórios open-source do GitHub via MCP.

Ferramentas típicas expostas:
- `search_doc` — busca docs, issues/PRs recentes e contexto do repo
- `get_repo_structure` — lista estrutura de diretórios/arquivos
- `read_file` — lê arquivo específico

Exemplo (Claude Code):

```bash
claude mcp add -s user -t http zread https://api.z.ai/api/mcp/zread/mcp --header "Authorization: Bearer <ZAI_API_KEY>"
```

> Importante: **não** commitar chaves no git. Use variáveis de ambiente/secret store.
