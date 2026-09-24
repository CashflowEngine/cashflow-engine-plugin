# CashFlow Engine plugin

Connects your AI to the [CashFlow Engine](https://cashflowengine.io) strategy library,
portfolio analytics and Hunter solver, so you can ask for them in your own words.

It bundles the hosted CashFlow Engine MCP server with a skill that tells the agent how
to use it, so setup is one install and a sign-in instead of pasting a server URL and a
client ID by hand.

## What it does

- Search a library of backtested options strategies and read a strategy's detail.
- Measure a portfolio you assemble: performance, correlation, drawdown, buying power.
- Run Monte Carlo simulations and the Hunter solver against constraints you set.
- Load and save your own portfolios and Hunter settings.
- Produce an OptionsApp import file, with schedules disabled.

## What it does not do

It cannot place a trade, connect to a broker, or move money. It reads analytics and
saves your own research. Enabling anything in OptionsApp is a separate step you
perform yourself.

## Install

**Cursor / Grok Bot** — install "CashFlow Engine" from the marketplace, then complete
the browser sign-in when prompted.

**Any MCP client, manually** — point it at `https://cashflow-mcp-production.up.railway.app/mcp`.
Setup guides for Claude, Claude Code, Codex, Cursor and Gemini CLI are in the app under
**Connect your AI**.

You sign in with your normal CashFlow Engine login. Enter your credentials only on the
CashFlow Engine sign-in page, never into an AI chat. Check the account shown on the
approval screen before approving, and revoke access any time under
**Account & subscription → Connected apps**.

Available on all active plans. Which features you can reach follows your plan.

## Every number is a backtest

Hypothetical backtested performance. Past performance does not predict future results.
Options trading involves substantial risk of loss. AI can misinterpret results,
historical selection can overfit, and actual losses can exceed historical or simulated
losses. Stops do not guarantee execution prices. Nothing this connector returns is a
live result, a fill, or a forecast, and nothing in it is investment advice.

Results you request and your saved research are shared with the AI provider you choose
and subject to its data policy.

## Contents

| Path | What it is |
|---|---|
| `mcp.json` | The hosted MCP server plus its public OAuth client ID (PKCE, no secret) |
| `skills/cashflow-engine/SKILL.md` | How the agent should use the connector |
| `.cursor-plugin/plugin.json` | Cursor marketplace manifest |
| `.grok-plugin/plugin.json` | Grok Build marketplace manifest |

MIT licensed. Operated by AI Momentum LLC.
