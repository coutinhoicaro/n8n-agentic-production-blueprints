# 🤖 Enterprise n8n Workflow Blueprints & AI Agents

<div align="center">

[![Platform](https://img.shields.io/badge/Orchestrator-n8n%20Enterprise-EA4B71?style=for-the-badge&logo=n8n&logoColor=white)](https://n8n.io/)
[![LangChain](https://img.shields.io/badge/Agentic-LangChain%20Nodes-1C3C3C?style=for-the-badge&logo=langchain&logoColor=white)](https://docs.n8n.io/integrations/builtin/cluster-nodes/root-nodes/n8n-nodes-langchain.agent/)
[![Models](https://img.shields.io/badge/LLMs-Claude%203.5%20Sonnet%20%7C%20GPT--4o-D97706?style=for-the-badge&logo=anthropic&logoColor=white)](https://anthropic.com/)
[![Database](https://img.shields.io/badge/State-PostgreSQL%20%7C%20Redis-336791?style=for-the-badge&logo=postgresql&logoColor=white)](https://www.postgresql.org/)
[![License](https://img.shields.io/badge/License-MIT-black?style=for-the-badge)](LICENSE)

<br>

**Production-Tested Agentic Workflows & Event-Driven Automation Blueprints**  
*Modular n8n JSON templates integrating LangChain reasoning agents, self-healing retries, webhook routing, and enterprise database transactions.*

</div>

---

## 📌 Executive Summary

Building enterprise automations often degrades into fragile, unmaintainable scripts.

This repository provides **battle-tested, production-ready n8n blueprints** implementing modern agentic design patterns: tool calling, structured memory buffers, deterministic routing branches, and database transaction logging.

---

## 🏗️ Architecture: Agentic Workflow Execution

```mermaid
flowchart LR
    subgraph Ingress ["1. Ingress & Triggers"]
        WEBHOOK["HTTP Webhook / Event Stream"] --> VALIDATE["JSON Schema Sanitization"]
    end

    subgraph AgenticCore ["2. LangChain Agent Reasoning"]
        VALIDATE --> AGENT["LangChain Agent Node (Claude 3.5 / GPT-4o)"]
        AGENT <--> MEMORY["Buffer Window Memory"]
        AGENT <--> TOOLS["Tool Definitions (DB Query, HTTP Call)"]
    end

    subgraph Persistence ["3. Storage & Escalation"]
        AGENT --> ROUTE{"Decision Matrix"}
        ROUTE -- "High Intent" --> DB[("PostgreSQL Transaction")]
        ROUTE -- "Urgent" --> ALERT["Real-Time Dispatch (Slack / Telegram / SIEM)"]
    end

    style WEBHOOK fill:#1e293b,stroke:#3b82f6,stroke-width:2px,color:#fff
    style AGENT fill:#1e293b,stroke:#8b5cf6,stroke-width:2px,color:#fff
    style DB fill:#1e293b,stroke:#10b981,stroke-width:2px,color:#fff
    style ALERT fill:#1e293b,stroke:#e11d48,stroke-width:2px,color:#fff
```

---

## 📦 Blueprint Catalog

| Blueprint | Category | Key Integrations | Description |
| :--- | :--- | :--- | :--- |
| **`lead_triage_rag_agent.json`** | AI Lead Intelligence | LangChain Agent, Claude 3.5 Sonnet, PostgreSQL | Evaluates incoming lead payloads via LLM tools and persists structured intent records. |
| **`security_quarantine_webhook.json`** | Edge Threat Response | Webhooks, Cloudflare Workers, PostgreSQL | Ingests real-time security alerts from edge routers and executes dynamic IP quarantine actions. |

---

## 🚀 How to Import and Deploy

1. In your **n8n instance** (Cloud or Self-Hosted), navigate to **Workflows**.
2. Click **Add Workflow** ➔ **Import from File**.
3. Select the desired `.json` blueprint from the [`workflows/`](workflows/) directory.
4. Set up your environment credentials in the n8n Credential Manager:
   * **Anthropic / OpenAI API Keys**
   * **PostgreSQL Connection String**
5. Activate the workflow and test with sample webhook triggers.

---

## 📂 Repository Structure

```
n8n-agentic-production-blueprints/
├── workflows/
│   ├── lead_triage_rag_agent.json          # AI Lead Triage & Database Insertion Workflow
│   └── security_quarantine_webhook.json    # Edge Security Alert Ingestion Pipeline
├── LICENSE                                 # MIT License
└── README.md                               # Architecture Catalog & Import Guide
```

---

## 📄 License
Distributed under the **MIT License**. See `LICENSE` for details.
