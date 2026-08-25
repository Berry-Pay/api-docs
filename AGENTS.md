# Documentation project instructions

## About this project

- This is the public documentation site for the **Berry Pay API**, built on
  [Mintlify](https://mintlify.com).
- Pages are MDX files with YAML frontmatter. Configuration lives in
  `docs.json`.
- Content mirrors the actual API implementation in the sibling repo
  `berry-pay-api` (Bun + Hono + Drizzle). When the API changes, the source of
  truth is that repo's `src/routes/v1/*.ts` and `src/serializers/*.ts` — update
  these docs to match, not the other way around.
- Use the Mintlify MCP server, `https://mcp.mintlify.com`, to edit content and
  settings via MCP.
- Use the Mintlify docs MCP server, `https://www.mintlify.com/docs/mcp`, to
  query information about using Mintlify via MCP.

## Terminology

- "Lojista" / "produtor" — the merchant using the API (not "usuário" alone,
  which is ambiguous with Berry Pay's internal admin users).
- "Cupom", "oferta", "transação", "parcela" — keep these Portuguese terms;
  don't anglicize to "coupon", "offer", "transaction", "installment" in prose.
- JSON field names, HTTP methods, header names, and code samples stay in
  **English** always — they're the literal API contract, not prose. Only the
  surrounding explanation is in Portuguese.
- "Berry Pay" (two words, capital B and P) when referring to the company/platform.

## Style preferences

- All page content is in **Brazilian Portuguese (pt-BR)** — every current
  customer is Brazilian. This is a deliberate choice, not a placeholder.
- Use active voice and second person ("você").
- Keep sentences concise — one idea per sentence.
- Use sentence case for headings.
- Bold for UI elements: Click **Settings**.
- Code formatting for file names, commands, paths, and code references.
- Every endpoint page follows the same shape: short description, required
  scope, path/query/body params via `<ParamField>`, response shape via
  `<ResponseField>`/`<Expandable>`, then `<RequestExample>` +
  `<ResponseExample>` with a realistic (fake) example.

## Content boundaries

- Document the public `/v1` API only. Don't document `berry-pay-system`'s
  internal admin dashboard, its session-cookie-authenticated routes, or any
  endpoint not under `/v1`.
- Never document or imply the existence of `berry_fee` / `berry_net_profit`,
  raw gateway responses, `internal_gateway_*` fields, `ip_address`,
  `user_agent`, or anything else the API intentionally excludes from
  responses (see `berry-pay-api/src/serializers/transaction.ts` for the
  current list). If the API starts returning something new, check with the
  team before documenting it — some fields are excluded on purpose.
- API keys aren't self-serve yet (see `authentication.mdx`) — don't document
  a key-management UI/endpoint that doesn't exist.
