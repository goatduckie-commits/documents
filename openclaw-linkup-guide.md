# Add Real-Time Web Search to Your OpenClaw Agent with Linkup

LLMs have a training cutoff. For agents handling current data — news, pricing, company intelligence — this creates a retrieval gap. This guide connects OpenClaw to Linkup's search API to close it.

## Prerequisites

- OpenClaw installed ([docs](https://docs.openclaw.ai))
- Linkup API key from [app.linkup.so](https://app.linkup.so)
- clawhub CLI: `npm i -g clawhub`

---

## Setup

### 1. Install the skill

```bash
clawhub install linkup-search
clawhub list  # verify
```

You can also ask your OpenClaw agent directly: *"Install the Linkup skill from clawhub."*

### 2. Configure your API key

```json
{
  "skills": {
    "entries": {
      "linkup-search": {
        "enabled": true,
        "env": { "LINKUP_API_KEY": "your-api-key-here" }
      }
    }
  }
}
```

### 3. Start a new session

Skills load at session start. Open a new chat — the agent will now call Linkup for queries that require current data.

---

## How It Works

The skill injects retrieval instructions into the system prompt. The agent selects depth based on query complexity and sends a POST to `https://api.linkup.so/v1/search`:

```json
{
  "q": "Stripe payment processing fees 2025",
  "depth": "standard",
  "outputType": "sourcedAnswer"
}
```

Linkup returns a structured answer with cited sources. The agent formats and returns it to the user.

**Depth selection:** `standard` for single-fact lookups; `deep` for multi-source synthesis or page extraction.

---

## Usage Patterns

| Query type | Depth | Example |
|---|---|---|
| Current fact | standard | "What is Vercel's current free tier limit?" |
| Competitive comparison | deep | "Compare Vercel vs Netlify pricing" |
| Multi-source synthesis | deep | "Summarize OpenAI's last 3 press releases" |
| Company profile | deep | "Funding, team size, and product of Acme Corp" |
