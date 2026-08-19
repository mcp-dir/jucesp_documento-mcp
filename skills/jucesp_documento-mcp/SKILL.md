---
name: jucesp_documento-mcp
description: Skill da REST API do JUCESP: Download de Documento na MCP.AI: 1 endpoint em /api/jucesp_documento. Baixa um documento arquivado de uma empresa na JUCESP a partir do NIRE e do número de registro. Hospedado pela plataforma, sem credenciais, pague por consulta com crédito pré-pago. Autentique com workspace API key (sk_live) gerada em app.mcp.ai/settings/api-keys. Use quando o usuário pedir algo coberto pelos endpoints.
---

# JUCESP: Download de Documento — REST API skill

Você tem acesso à **JUCESP: Download de Documento** REST API na MCP.AI.

> Baixa um documento arquivado de uma empresa na JUCESP a partir do NIRE e do número de registro. Hospedado pela plataforma, sem credenciais, pague por consulta com crédito pré-pago.

## Base URL

```
https://api.mcp.ai/api/jucesp_documento
```

Todo endpoint é um **POST** na Base URL + o path abaixo. Os parâmetros vão no corpo JSON.

## Autenticação

Inclua em toda request:

```
Authorization: Bearer sk_live_...
Content-Type: application/json
```

> Gere sua chave em **https://app.mcp.ai/settings/api-keys** (workspace API key `sk_live_…`, não expira, revogável). Uma única chave serve pra todos os seus MCPs.

## Formato de resposta

```json
{ "ok": true, "tool": "<tool_id>", "result": <payload> }
```

## Exemplo cURL

```bash
curl -X POST https://api.mcp.ai/api/jucesp_documento/consultar \
  -H "Authorization: Bearer sk_live_..." \
  -H "Content-Type: application/json" \
  -d '{"nire":"...","registro":"..."}'
```

## Reportar problemas

Se um endpoint retornar erro, vazio ou dado inesperado, reporte (não desista calado): **POST /api/jucesp_documento/report** com `{ "message": "...", "context"?: "...", "conversation"?: [...] }`. Isso notifica o time da MCP.AI.

## Endpoints (1)

#### `jucesp_documento_consultar`

Baixa um documento arquivado de uma empresa na JUCESP a partir do NIRE e do número de registro. _(POST /api/jucesp_documento/consultar)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `login_cpf` | string | Não | Parâmetro de consulta "login_cpf". |
| `login_senha` | string | Não | Parâmetro de consulta "login_senha". |
| `pkcs12_cert` | string | Não | Parâmetro de consulta "pkcs12_cert". |
| `pkcs12_pass` | string | Não | Parâmetro de consulta "pkcs12_pass". |
| `nire` | string | Sim | Parâmetro de consulta "nire". |
| `registro` | string | Sim | Parâmetro de consulta "registro". |

---

Este MCP também funciona via **conexão MCP** (Claude / Cursor) em `https://api.mcp.ai/p_jucesp_documento` — veja o [README](../../README.md). A skill acima é pra consumir a **REST API** direto (agente próprio / código).
