# Documentation project instructions

## About this project

- Public documentation for Cashd, published at `docs.trycashd.com`
- Built on [Mintlify](https://mintlify.com). Pages are MDX with YAML frontmatter
- Configuration lives in `docs.json`
- Use the Mintlify MCP server, `https://mcp.mintlify.com`, to edit content and settings via MCP
- Use the Mintlify docs MCP server, `https://www.mintlify.com/docs/mcp`, to query information about using Mintlify via MCP

## Audiences

| Tab | Reader | Assumes |
|---|---|---|
| Merchants | Business owner, finance, store operations | No engineering knowledge |
| Providers | Loyalty programme commercial lead | No engineering knowledge |
| Integration | Engineers building against the Merchant API | Working knowledge of HTTP APIs |

A page belongs to one audience. Do not mix technical detail into the Merchants
or Providers tabs beyond a link into Integration.

## Terminology

- **Consumer** or **customer** — the person paying with Cashd. Not "user".
- **Merchant** — a business accepting Cashd. Not "vendor" or "partner" when the merchant is meant specifically.
- **Provider** — a loyalty programme whose points fund Cashd wallets. Not "issuer" in partner-facing content.
- **Partner** — either a merchant or a provider, where the statement applies to both.
- **Transaction** — a debit against a consumer wallet. Not "payment" or "charge" in API contexts.
- **Wallet** — the consumer's SAR balance in Cashd. A merchant-operated balance is a **merchant wallet** or **store credit**, never just "wallet".
- **Halala** — the integer money unit. 1 SAR = 100 halala. Money fields are `*_halalas`.
- **Merchant discount** — the percentage deducted at settlement. Not "commission", not "interchange", in partner-facing content.
- **Void** — reversing a transaction through the API. Not "refund" or "cancel".
- **Session** — a hosted-checkout session. Not "checkout" alone.

## Style preferences

- Use active voice and second person ("you")
- Keep sentences concise — one idea per sentence
- Use sentence case for headings
- Bold for UI elements: Click **Settings**
- Code formatting for file names, commands, paths, error codes, and field names
- State facts and requirements. Do not explain the reasoning behind a design
  decision unless the reader must act on it
- No filler, no rapport, no meta-commentary about the documentation itself
- Money always in halala for API values, with the SAR equivalent in prose where
  it aids comprehension
- Every consumer-facing string referenced in docs exists in Arabic and English.
  Note the requirement where a partner must render it

## Content boundaries

Publish:

- How to accept Cashd, commercially and operationally
- How to integrate against the Merchant API
- Error codes reachable by a partner or surfaced to a consumer
- Anything already stated in a merchant or provider agreement

Never publish:

- Internal runbooks, SOPs, or operational procedures
- Infrastructure, cluster, deployment, or monitoring detail
- Provider or merchant names not already public, and any commercial terms
  specific to one partner
- Credit risk positions, revenue recognition policy, breakage assumptions, or
  any internal accounting treatment
- Internal ticket identifiers, pull request numbers, or repository paths
- Fraud controls, rate-limit values, or velocity thresholds beyond what a
  partner must implement against
- Unreleased functionality

This repository is public. `.mintignore` excludes a file from the published
site, not from the repository. Anything committed is public.

## Error pages

`integration/errors/<code>` is a route contract. The backend emits
`doc_url: https://docs.trycashd.com/integration/errors/<code>` on every error
response. A new error code requires a page in the same release. Do not rename or
move these paths without changing the backend constant.
