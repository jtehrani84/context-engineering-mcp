# Slack Post Draft — Context Engineering Part 3: MCP Servers

## For: #ai-club + #tmt-solutions

---

Hey {channel} — Part 3 of the context engineering series. Part 1 was memory (teaching Claude to remember). Part 2 was the AgentScript case study (same model, same question, wildly different answers). This one is about connections.

:electric_plug: Teaching Claude to Connect: MCP Servers :electric_plug:

Memory gave Claude a brain. But a brain without hands is just a journal. It can remember that your customer has 900 Slack seats ramping to 1,000 — but it can't look that up itself. You're still the middleman, copy-pasting from Org62 into the chat window.

MCP (Model Context Protocol) is the open standard from Anthropic that fixes this. It gives Claude direct access to external systems — your CRM, your code repos, your Slack channels, your documentation — through a standardized interface. Think USB-C for AI: one protocol, any capability.

I'm running 9 servers with 120+ tools. Some highlights:
• **Slack MCP** — Claude searches channels, reads threads, drafts messages, creates canvases. No more "can you check what Sarah said in #deal-reviews last week?"
• **GitHub MCP** — PRs, code search, issue management. Claude reviews diffs, creates branches, pushes code.
• **Meridian (custom)** — 40 tools wrapping our intelligence platform + corporate CRM. Account briefs, pipeline data, installed products, competitive intel. This is the crown jewel.

The interesting part: these servers compose without coupling. Claude is the integration layer — like the Unix pipe `|` operator. "Pull the Roblox account brief from Meridian, check what the AE said in Slack last week, and draft a prep doc" becomes one prompt that hits three servers. No integration code. No middleware. The LLM decides which tools to call and synthesizes the results.

The case study in the write-up is about connecting to corporate Salesforce (Org62) — where the standard integration path doesn't exist for individual SE tooling. No Connected App, no OAuth, no JWT, no API credentials. We built around the constraint using the sf CLI as a local bridge — and now Claude has full read access to pipeline, contacts, contracts, installed products, and consumption data across every account variant.

I also cover the "Two Data Planes" insight — why Slack MCP and CRM tools aren't redundant even though they both surface account information. Slack captures unstructured signal (team dynamics, competitive intel, sentiment). CRM captures structured records (exact products, pricing, renewal dates). Same account, completely different intelligence. You need both.

Part 3 — https://jtehrani84.github.io/context-engineering-mcp/
Part 2 — https://jtehrani84.github.io/context-engineering-agentscript/
Part 1 — https://jtehrani84.github.io/claude-context-architecture/
