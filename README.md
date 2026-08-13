# ForgeX4 Security Reasoning Engine (Sovereign Sentinel)

An autonomous, zero-maintenance intelligence pipeline engineered for high-assurance vulnerability triage. Built on n8n, this framework ingests raw threat telemetry, applies deterministic risk modeling, orchestrates Google Gemini for technical extraction, and enforces algorithmic governance before routing intelligence to production environments.

## ⚙️ Core Architecture

The Sovereign Sentinel pipeline is designed to eliminate manual vulnerability monitoring by automating the entire intelligence lifecycle from ingestion to publication.

*   **Ingestion Layer:** Continuously polls the CISA Security Advisories RSS feed and the NIST National Vulnerability Database (NVD) API for real-time threat data.
*   **Temporal State Management:** Implements a custom memory perimeter with $O(1)$ lookups to strictly prevent duplicate processing of vulnerability records across execution cycles.
*   **Deterministic Risk Assessment:** A custom JavaScript engine that calculates priority scores based on CVSS metrics, exploitability vectors, and temporal data.
*   **AI Security Analyst:** Orchestrates Google Gemini (3.5 Flash Lite) via LangChain to perform deep technical extraction, enforcing strict JSON output schemas to guarantee factual grounding and eliminate hallucinations.
*   **Content Quality Gate:** An algorithmic governance engine that evaluates structural integrity, security depth, technical specificity, and originality.
*   **Autonomous Routing:** 
    *   `[PASS]`: High-fidelity, top-scoring intelligence is autonomously published to LinkedIn via OAuth2 integration.
    *   `[REVIEW]`: Edge-cases and anomalies are routed via raw HTTP POST requests to `ntfy.sh` for instant human-in-the-loop push notifications.

## 🚀 Installation & Deployment

This architecture is built for self-hosted or cloud environments running **n8n**.

### Prerequisites
1.  **n8n Instance** (v2.33+ recommended)
2.  **Google Gemini API Key**
3.  **LinkedIn Developer App** (Configured for OAuth2 with OpenID Connect scopes)
4.  **ntfy.sh Endpoint** (For receiving push notifications)

### Setup Instructions
1.  Download the `forgex4-sentinel.json` file from this repository.
2.  Open your n8n workspace, navigate to the workflows dashboard, and select **Import from File**.
3.  Upload the JSON file to generate the workflow canvas.
4.  Configure the credential nodes:
    *   Add your Google Gemini API key to the Language Model nodes.
    *   Authenticate the LinkedIn node using your OAuth2 App credentials.
5.  Update the `ntfy.sh` HTTP Request node with your preferred secret topic URL.
6.  Activate the 6-Hour Schedule Trigger and toggle the workflow to **Active**.

## 🛡️ License

Copyright (c) 2026 Kian Mansouri Jamshidi. All rights reserved. 

This code is provided for portfolio viewing and educational purposes only. No permission is granted to use, modify, or distribute this software without explicit authorization.

---
**Architected by Kian Mansouri Jamshidi**  
*Founder & Software Architect, ForgeX4*
