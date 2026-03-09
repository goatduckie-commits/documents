# OpenClaw Integration

Integrate Linkup with [OpenClaw](https://openclaw.ai) to give your self-hosted agent real-time web search via the [clawhub](https://clawhub.ai) skill registry.

---

## Prerequisites

- OpenClaw installed and running ([quick start](https://docs.openclaw.ai/start/getting-started))
- A Linkup API key — get one at [app.linkup.so](https://app.linkup.so)
- `clawhub` CLI: `npm i -g clawhub`

---

## Installation

Install the Linkup skill from clawhub:

```bash
clawhub install linkup-search
clawhub list  # verify
```

Alternatively, ask your OpenClaw agent directly:

> "Install the Linkup skill from clawhub."

The skill will be available at the next session start. No restart required if the skills watcher is enabled.

The skill is available at [clawhub.ai/shauryajain21/linkup-search](https://clawhub.ai/shauryajain21/linkup-search).

---

## Configuration

Add your API key to `openclaw.json`:

```json
{
  "skills": {
    "entries": {
      "linkup-search": {
        "enabled": true,
        "env": {
          "LINKUP_API_KEY": "your-api-key-here"
        }
      }
    }
  }
}
```

This scopes the key to the skill, which is preferable for multi-agent setups over using a `.env` file.

---

## How It Works

OpenClaw injects the skill's instructions into the system prompt at session start. The agent calls Linkup when a query requires current information, instead of relying on training data.

A typical call looks like:

```json
POST https://api.linkup.so/v1/search
{
  "q": "Stripe payment processing fees 2025",
  "depth": "standard",
  "outputType": "sourcedAnswer"
}
```

Linkup returns a structured, source-cited answer. The agent reasons over the result and formats the reply.

**Depth selection:**
- `standard` — optimized for latency. Use for single-fact lookups.
- `deep` — higher recall, multi-source synthesis. Use for company research, competitive analysis, or page extraction.

---

## Usage Examples

| Query | Depth |
|---|---|
| "What is Vercel's current free tier limit?" | standard |
| "Compare Vercel and Netlify pricing" | deep |
| "Summarize OpenAI's last 3 press releases" | deep |
| "Funding history and team size of Acme Corp" | deep |

---

## Related

- [Linkup API reference](https://docs.linkup.so/api-reference/search)
- [Prompting guide](https://docs.linkup.so/documentation/get-started/prompting)
- [OpenClaw docs](https://docs.openclaw.ai)
