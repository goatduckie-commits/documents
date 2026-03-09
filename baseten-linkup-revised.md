# Give Open-Source LLMs Real-Time Knowledge with Baseten + Linkup

---

We're thrilled to announce our partnership with **Baseten** — the inference platform powering production AI products at scale.

Open-source models are closing the gap with proprietary ones. But they all share the same blind spot: **they can't see the live web.**

---

#### The Problem

A model like GPT-OSS 120B, served on Baseten, can reason, write, and call tools. But ask it what happened yesterday, and it's stuck in its training data.

Think about using your phone with airplane mode permanently enabled. You have access to everything already downloaded — but nothing new, nothing current. That's essentially how LLMs operate without real-time web access. **Incredibly capable. Operating with an outdated map of a rapidly changing world.**

Linkup fixes that in a single API call.

---

#### Why Baseten

[Baseten](https://baseten.co) is the inference platform behind AI products. Deploy any open-source model — Llama, DeepSeek, GPT-OSS — as a production-ready API with **serverless GPU scaling** and no infrastructure to manage.

- **Serverless & scalable** — pay per minute, scale to zero or to thousands of replicas
- **Function calling built in** — models can decide when to use tools, not just what to say
- **Enterprise-ready** — SOC 2 Type II, HIPAA-compliant, custom SLAs

Backed by **$285M+ in funding at a $2.15B valuation**, Baseten powers teams like Abridge, Captions, Clay, and Writer.

---

#### Why Linkup

Linkup is web search built specifically for AI. Not a list of links — **structured, source-backed content optimized for LLM consumption.**

- **Multiple search depths** — Standard for simple facts, Deep for multi-step research, Fast (beta) for latency-sensitive tasks, and Deep Research (beta) for comprehensive reports
- **Source attribution** — every result comes with URLs and snippets for grounding
- **Privacy-first** — zero data retention, GDPR/CCPA/SOC 2 Type II compliant

Since launching in late 2024, Linkup has scaled to **tens of thousands of customers** — from AI-native startups like Artisan to global enterprises like KPMG. On OpenAI's SimpleQA benchmark, **Linkup ranks #1 with a 91% F-score**, the highest factual accuracy of any web-connected system.

---

#### How It Works Together

In two steps, you can give any open-source model live web access.

**Step 1:** Select a model on Baseten.

**Step 2:** Define a `search_web` tool powered by Linkup.

The model decides when it needs live information. When it does, Linkup handles the retrieval:

```
User → "What are the latest books on logic?"
       ↓
GPT-OSS 120B (Baseten) → decides to call search_web
       ↓
Linkup API → returns structured results from the live web
       ↓
GPT-OSS 120B → synthesizes a grounded, cited answer
```

**The model handles reasoning. Linkup handles retrieval. Baseten handles infrastructure.** Each does what it does best.

---

#### The Bigger Picture

At Linkup, our mission is simple: **give AI models instant access to the world's facts — fresh, trusted, and source-backed — so they can reason, decide, and create with confidence.**

Partnering with Baseten extends that mission to the open-source ecosystem. Developers get the **flexibility of open-source** with the **freshness users expect** — in under 100 lines of Python.

Grounding open-source models in real-time data is no longer a complex engineering project. It's a tool call.

**[Try the full tutorial →](https://docs.linkup.so)**
