[![PyPI version](https://img.shields.io/pypi/v/commune-mail?color=blue&label=commune-mail)](https://pypi.org/project/commune-mail/)
[![PyPI Downloads](https://img.shields.io/pypi/dm/commune-mail?label=python%20installs%2Fmo&color=blue)](https://pypi.org/project/commune-mail/)
[![npm version](https://img.shields.io/npm/v/commune-ai?color=red&label=commune-ai)](https://www.npmjs.com/package/commune-ai)
[![npm Downloads](https://img.shields.io/npm/dm/commune-ai?label=node%20installs%2Fmo&color=red)](https://www.npmjs.com/package/commune-ai)
[![Smithery](https://smithery.ai/badge/commune)](https://smithery.ai/server/commune)
[![Status](https://img.shields.io/endpoint?url=https%3A%2F%2Fapi.commune.email%2Fstatus%2Fshield&label=API)](https://commune.email/status)
[![License: MIT](https://img.shields.io/badge/license-MIT-yellow.svg)](https://github.com/commune-dev/commune-python/blob/main/LICENSE)

## Commune — Email & SMS Infrastructure for AI Agents

Give your AI agent a real inbox and phone number. Production-grade email and SMS for LangChain, CrewAI, OpenAI Agents SDK, Claude, and MCP.

```
pip install commune-mail    # Python
npm install commune-ai      # TypeScript / Node.js
uvx commune-mcp             # Claude Desktop / Cursor / Windsurf
```

---

### What you can build

| Use Case | Description |
|----------|-------------|
| **Customer support agent** | Agent reads inbound tickets at `support@yourcompany.com`, classifies intent, replies in thread |
| **Hiring pipeline** | Outreach sequences, screening, scheduling — all tracked per candidate per thread |
| **Sales automation** | Personalized cold email, follow-up sequences, lead qualification |
| **Investor updates** | Scheduled reports, portfolio alerts, LP communications |
| **Multi-agent coordination** | Agents hand off tasks to each other via email threads |

---

### Repositories

#### SDKs

| Repo | Description | Install | Version | Downloads |
|------|-------------|---------|---------|-----------|
| [commune-python](https://github.com/commune-dev/commune-python) | Python SDK | `pip install commune-mail` | [![PyPI](https://img.shields.io/pypi/v/commune-mail?label=%20&color=blue)](https://pypi.org/project/commune-mail/) | [![PyPI DL](https://img.shields.io/pypi/dm/commune-mail?label=%20)](https://pypi.org/project/commune-mail/) |
| [commune-js](https://github.com/commune-dev/commune-js) | TypeScript / Node.js SDK | `npm install commune-ai` | [![npm](https://img.shields.io/npm/v/commune-ai?label=%20&color=red)](https://www.npmjs.com/package/commune-ai) | [![npm DL](https://img.shields.io/npm/dm/commune-ai?label=%20)](https://www.npmjs.com/package/commune-ai) |

#### Tools and Integrations

| Repo | Description | Install | Installs |
|------|-------------|---------|---------|
| [commune-mcp](https://github.com/commune-dev/commune-mcp) | MCP server for Claude Desktop, Cursor, Windsurf | `uvx commune-mcp` | [![Smithery](https://smithery.ai/badge/commune)](https://smithery.ai/server/commune) |
| [n8n-nodes-commune](https://github.com/commune-dev/n8n-nodes-commune) | n8n community node | `npm install n8n-nodes-commune` | [![npm DL](https://img.shields.io/npm/dm/n8n-nodes-commune?label=%20)](https://www.npmjs.com/package/n8n-nodes-commune) |

#### Examples and Learning

| Repo | Description |
|------|-------------|
| [commune-cookbook](https://github.com/commune-dev/commune-cookbook) | Code recipes for LangChain, CrewAI, OpenAI Agents, Claude, n8n — with Jupyter notebooks |
| [commune-inbox-demo](https://github.com/commune-dev/commune-inbox-demo) | Demo app: AI-powered inbox with triage and LLM reply drafts |

#### Community and Discovery

| Repo | Description |
|------|-------------|
| [awesome-email-agents](https://github.com/commune-dev/awesome-email-agents) | Curated list of email & SMS tools, MCP servers, and patterns for AI agents |
| [agent-stack](https://github.com/commune-dev/agent-stack) | Curated registry of 50+ infrastructure tools for production AI agents |
| [awesome-agent-protocols](https://github.com/commune-dev/awesome-agent-protocols) | Curated list of protocols for AI agent communication |

#### Backend

| Repo | Description | License |
|------|-------------|---------|
| [commune](https://github.com/commune-dev/commune) | Open-source backend — self-hostable | [![License](https://img.shields.io/badge/license-BSL%201.1-orange.svg)](https://github.com/commune-dev/commune/blob/main/LICENSE) |

---

### Integration matrix

| Framework | Python | TypeScript | MCP | Cookbook |
|-----------|--------|------------|-----|----------|
| LangChain | ✅ | ✅ | — | ✅ |
| CrewAI | ✅ | — | — | ✅ |
| OpenAI Agents SDK | ✅ | ✅ | — | ✅ |
| Claude (tool_use) | ✅ | ✅ | ✅ | ✅ |
| Cursor | — | — | ✅ | — |
| Windsurf | — | — | ✅ | — |
| n8n | — | ✅ | — | ✅ |

---

### Platform capabilities

- **Dedicated inboxes** — each agent gets its own `@yourdomain.com` or `@agents.commune.email` address
- **Inbound webhooks** — emails fire webhooks instantly with HMAC signing and 8-retry delivery guarantee
- **Email threading** — RFC 5322 compliance; replies appear threaded in Gmail, Outlook, Apple Mail
- **Semantic search** — vector search across all inbox history with natural language queries
- **Structured extraction** — auto-parse email fields to JSON using per-inbox schemas (no extra LLM call)
- **SMS** — provision real phone numbers, two-way SMS, unified search with email
- **Prompt injection protection** — 6-layer analysis on inbound content before it reaches your agent
- **Self-hostable** — full backend source available; run on your own infrastructure

---

### Get started in 60 seconds

```python
from commune import CommuneClient

client = CommuneClient(api_key="comm_...")
inbox = client.inboxes.create(local_part="support")
print(inbox.address)  # → support@agents.commune.email

# Reply in thread — stays grouped in Gmail / Outlook
client.messages.send(
    to="user@example.com",
    text="Your ticket is resolved.",
    inbox_id=inbox.id,
    thread_id=thread_id,  # from webhook payload
)
```

```typescript
import { CommuneClient } from 'commune-ai';

const client = new CommuneClient({ apiKey: process.env.COMMUNE_API_KEY! });
const inbox = await client.inboxes.create({ localPart: 'support' });
console.log(inbox.address); // → support@agents.commune.email
```

**[Get your API key →](https://commune.email)**

---

*[commune.email](https://commune.email) · [Docs](https://commune.email/docs) · [Status](https://commune.email/status)*
