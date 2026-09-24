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

**Grok Bot** — in a chat, say: `Install the plugin from https://github.com/CashflowEngine/cashflow-engine-plugin`

**Claude Code**

```
claude plugin marketplace add CashflowEngine/cashflow-engine-plugin
claude plugin install cashflow-engine@cashflow-engine
claude mcp login cashflow-engine
```

**Gemini CLI**

```
gemini extensions install https://github.com/CashflowEngine/cashflow-engine-plugin
```

Then start Gemini CLI and run `/mcp auth cashflow-engine` yourself. Installing does
not sign you in.

**Cursor** — install "CashFlow Engine" from the marketplace once it is listed.

**Any other MCP client** — point it at `https://cashflow-mcp-production.up.railway.app/mcp`.
Setup guides for Claude, Cowork, Codex and the rest are in the app under
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

One repository, four vendors. Each reads a different manifest at its root, so they
cannot collide, and keeping them together is what stops a client ID drifting from
the redirect URI it must match.

| Path | Vendor |
|---|---|
| `mcp.json` + `.cursor-plugin/plugin.json` | Cursor and Grok Bot |
| `.grok-plugin/plugin.json` | Grok Build |
| `.claude-plugin/` + `claude-code-mcp.json` | Claude Code |
| `gemini-extension.json` | Gemini CLI |
| `skills/cashflow-engine/SKILL.md` | the skill, read by Cursor, Grok Bot and Claude Code |
| `GEMINI.md` | the same guidance in the form Gemini CLI loads |

Each manifest carries its own vendor's OAuth client ID. They are public by design
(PKCE, no secret), but they are **not interchangeable**: a client ID only works with
the redirect URI registered for it.

The server key is `cashflow-engine` everywhere except the Cursor and Grok Bot
manifest, which uses `CashFlow Engine`. That is deliberate. Those two label the
connector with the key, while the CLIs take it as an argument to a command such as
`claude mcp login` or `/mcp auth`, where a space would break it.

MIT licensed. Operated by AI Momentum LLC.
