# Documentation project instructions

## About this project

- Public documentation for Cashd, published at `docs.trycashd.com`
- Built on [Mintlify](https://mintlify.com). Pages are MDX with YAML frontmatter
- Configuration lives in `docs.json`
- Use the Mintlify MCP server, `https://mcp.mintlify.com`, to edit content and settings via MCP
- Use the Mintlify docs MCP server, `https://www.mintlify.com/docs/mcp`, to query information about using Mintlify via MCP

## Audience

Engineers building against the Merchant API. Assume working knowledge of HTTP
APIs. Commercial and operational onboarding content is out of scope for this
site.

## Terminology

- **Consumer** or **customer** — the person paying with Cashd. Not "user".
- **Merchant** — a business accepting Cashd. Not "vendor" or "partner" when the merchant is meant specifically.
- **Loyalty programme** — the points source funding a Cashd wallet. Never named in partner-facing content.
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

- How to integrate against the Merchant API
- Error codes reachable by a merchant or surfaced to a consumer
- Anything already stated in a merchant agreement

Never publish:

- Commercial, onboarding, or account-management content — this site is technical only
- Internal runbooks, SOPs, or operational procedures
- Infrastructure, cluster, deployment, or monitoring detail
- Loyalty programme or merchant names not already public, and any commercial
  terms specific to one merchant
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
