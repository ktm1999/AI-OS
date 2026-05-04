# Connections

Registry of every system the AIOS can reach. Filled by `/onboard` from Q4-Q7 answers; expanded over time as you wire new tools. `/audit` checks this file for domain coverage and freshness.

> **Note on `Mechanism = not yet connected`:** several tools below are already running on Louis's side (Powens, Plaid, n8n, the revenue Google Sheet, etc.). "Not yet connected" here means **the AIOS layer in this repo cannot reach them yet** — no MCP, no script in `scripts/`, no API ref in `references/`. Day 2+ work is to wire the highest-leverage ones.

| # | Domain | Tool | Mechanism | Auth | Last checked |
|---|---|---|---|---|---|
| 1 | Revenue / Financials | Google Sheet (single source of truth, fed by Powens + Plaid + n8n + custom APIs from banks, Alpaca, Interactive Brokers) | not yet connected | — | — |
| 2 | Customer interactions | Slack (Vestiaire, internal) + WhatsApp / iMessage / LinkedIn DMs / Messenger (external) | not yet connected | — | — |
| 3 | Calendar | Google Calendar (Vestiaire Workspace) + Outlook Calendar (Hotmail personal) | not yet connected | — | — |
| 4 | Communication | Gmail (louis.giuliani@vestiairecollective.com, Workspace) + Hotmail (louisgiuliani@hotmail.com, personal) | not yet connected | — | — |
| 5 | Project / task tracking | Jira (Vestiaire, internal tickets) + Microsoft To Do (personal: AVANTIR, real estate, algo, life — also used for notes) | not yet connected | — | — |
| 6 | Meeting intelligence | Google Meet (native recordings) | not yet connected | — | — |
| 7 | Knowledge / files | Google Drive (Vestiaire Workspace, work) + Google Drive (personal) + Notion (personal docs) | not yet connected | — | — |

**Mechanism options:** `mcp` (MCP server), `script` (Python/Bash hitting an API, in `scripts/`), `export` (CSV/JSON dump pipeline), `key+ref` (`.env` key + `references/{tool}-api.md` guide), `not yet connected`.

When you wire a new tool, also save `references/{tool}-api.md` capturing endpoints, auth flow, and common queries — researched-once-saved-forever.

## Day-2+ wiring suggestions (highest leverage first)

1. **Slack (Vestiaire)** — directly unlocks the #1 stated time-suck (Slack triage). MCP server exists.
2. **Google Drive + Google Meet (Vestiaire Workspace)** — meeting context + doc lookup. MCP available.
3. **Jira (Vestiaire)** — ticket context for Slack triage answers. MCP available.
4. **The revenue Google Sheet** — read-only API read + cache to a `references/revenue-sheet-schema.md`.
5. **Notion (personal)** — personal doc retrieval for AVANTIR / real estate / algo. MCP available.
6. **Gmail (Vestiaire) + Outlook (Hotmail)** — inbox triage + draft generation in voice.
7. **Microsoft To Do** — task surfacing.
