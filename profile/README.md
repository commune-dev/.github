[![PyPI version](https://img.shields.io/pypi/v/commune-mail?color=blue&label=commune-mail)](https://pypi.org/project/commune-mail/)
[![PyPI Downloads](https://img.shields.io/pypi/dm/commune-mail?label=python%20installs%2Fmo&color=blue)](https://pypi.org/project/commune-mail/)
[![npm version](https://img.shields.io/npm/v/commune-ai?color=red&label=commune-ai)](https://www.npmjs.com/package/commune-ai)
[![npm Downloads](https://img.shields.io/npm/dm/commune-ai?label=node%20installs%2Fmo&color=red)](https://www.npmjs.com/package/commune-ai)
[![Smithery](https://smithery.ai/badge/commune)](https://smithery.ai/server/commune)
[![Status](https://img.shields.io/website?url=https%3A%2F%2Fstatus.commune.email&label=API&up_message=operational&down_message=degraded&color=green)](https://status.commune.email)
[![License: MIT](https://img.shields.io/badge/license-MIT-yellow.svg)](https://github.com/commune-dev/commune-python/blob/main/LICENSE)

## Commune — Email & SMS Infrastructure for AI Agents

Give your AI agent a real inbox and phone number. Production-grade email and SMS for LangChain, CrewAI, OpenAI Agents SDK, Claude, and MCP.

```
pip install commune-mail    # Python
npm install commune-ai      # TypeScript / Node.js
uvx commune-mcp             # Claude Desktop / Cursor / Windsurf
```

---

Commune handles the infrastructure so your agent can send and receive email like a real person.

- Each agent gets its own dedicated inbox (`@yourdomain.com` or `@agents.commune.email`)
- Inbound emails fire webhooks instantly with HMAC signing and automatic retries
- Replies stay threaded in Gmail, Outlook, and Apple Mail — no extra work
- Search across your entire inbox history using natural language
- Structured extraction lets you auto-parse email fields to JSON without an extra LLM call
- Inbound content goes through prompt injection analysis before it touches your agent
- Provision real phone numbers and handle two-way SMS alongside email
- Self-hostable — the full backend is open source

---

### Get started in 60 seconds

```python
from commune import CommuneClient

client = CommuneClient(api_key="comm_...")
inbox = client.inboxes.create(local_part="support")
print(inbox.address)  # → support@agents.commune.email

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

**[Get your API key →](https://commune.email)**

---

*[commune.email](https://commune.email) · [Docs](https://commune.email/docs) · [Status](https://status.commune.email)*
