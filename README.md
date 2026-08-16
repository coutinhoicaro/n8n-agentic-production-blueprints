# 🤖 Enterprise n8n Workflow Blueprints & AI Agents

<div align="center">

[![Type](https://img.shields.io/badge/Project-Workflow%20%26%20Agent%20Blueprints-blue?style=for-the-badge)](https://github.com/coutinhoicaro/n8n-agentic-production-blueprints)
[![Platform](https://img.shields.io/badge/Platform-n8n-EA4B71?style=for-the-badge&logo=n8n&logoColor=white)](https://n8n.io/)
[![LangChain](https://img.shields.io/badge/Agentic-LangChain%20Nodes-1C3C3C?style=for-the-badge&logo=langchain&logoColor=white)](https://docs.n8n.io/integrations/builtin/cluster-nodes/root-nodes/n8n-nodes-langchain.agent/)
[![Database](https://img.shields.io/badge/Database-PostgreSQL-336791?style=for-the-badge&logo=postgresql&logoColor=white)](https://www.postgresql.org/)
[![License](https://img.shields.io/badge/License-MIT-black?style=for-the-badge)](LICENSE)

<br>

**Production-Tested n8n Workflows & AI Agent Blueprints**  
*Modular n8n JSON templates integrating LangChain reasoning nodes, webhook gateways, automated retries, and PostgreSQL database queries.*

</div>

---

## 📌 Overview

This repository shares **curated n8n workflow blueprints** that demonstrate how to connect webhooks, AI agents (Claude / GPT-4o), and databases in a maintainable, visual architecture.

---

## 🏗️ Example Architecture: Agentic Lead Routing

```mermaid
flowchart LR
    subgraph Ingress ["1. Webhook Ingress"]
        WEBHOOK["HTTP Webhook"] --> VALIDATE["Extract Lead Info"]
    end

    subgraph Reasoning ["2. AI Agent Node"]
        VALIDATE --> AGENT["LangChain Agent (Claude / GPT)"]
        AGENT <--> TOOLS["Database & Search Tools"]
    end

    subgraph Output ["3. Storage & Alerts"]
        AGENT --> ROUTE{"Qualification"}
        ROUTE -- "Qualified" --> DB[("Save to PostgreSQL")]
        ROUTE -- "Urgent" --> ALERT["Send Slack / Webhook Alert"]
    end

    style WEBHOOK fill:#1e293b,stroke:#3b82f6,stroke-width:2px,color:#fff
    style AGENT fill:#1e293b,stroke:#8b5cf6,stroke-width:2px,color:#fff
    style DB fill:#1e293b,stroke:#10b981,stroke-width:2px,color:#fff
    style ALERT fill:#1e293b,stroke:#e11d48,stroke-width:2px,color:#fff
```

---

## 📦 Blueprint Catalog

| Workflow File | Description | Integrations |
| :--- | :--- | :--- |
| **[`lead_triage_rag_agent.json`](workflows/lead_triage_rag_agent.json)** | Evaluates incoming lead payloads with LLM reasoning and saves qualified profiles to PostgreSQL. | n8n, LangChain, Claude, PostgreSQL |
| **[`security_quarantine_webhook.json`](workflows/security_quarantine_webhook.json)** | Receives security alerts from edge workers and logs events for IP quarantine. | n8n Webhook, PostgreSQL, Logic Nodes |

---

## 🚀 How to Import

1. In your **n8n instance**, go to **Workflows**.
2. Click **Add Workflow** ➔ **Import from File**.
3. Choose any `.json` file from the [`workflows/`](workflows/) folder.
4. Add your own database and LLM credentials in n8n's credential manager.

---

## 📄 License
Distributed under the **MIT License**. See `LICENSE` for details.
