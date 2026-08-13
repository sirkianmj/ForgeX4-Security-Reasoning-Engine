<div align="center">

# 🛡️ ForgeX4 Security Reasoning Engine

[![Proprietary License](https://img.shields.io/badge/License-Proprietary-red.svg)](#-license)
[![Platform](https://img.shields.io/badge/Platform-n8n-FF6600.svg?logo=n8n&logoColor=white)](#)
[![AI Engine](https://img.shields.io/badge/AI-Google_Gemini-4285F4.svg?logo=google&logoColor=white)](#)
[![Logic](https://img.shields.io/badge/Logic-JavaScript-F7DF1E.svg?logo=javascript&logoColor=black)](#)

*An autonomous, zero-maintenance intelligence pipeline engineered for high-assurance vulnerability triage and automated publishing.*

</div>

---

## 🚀 Overview

The **ForgeX4 Security Reasoning Engine** is a proprietary backend architecture designed to eliminate manual vulnerability monitoring. It acts as an autonomous intelligence pipeline that ingests raw global threat telemetry, applies deterministic risk modeling, and orchestrates LLMs for deep technical extraction. 

Designed for high-assurance environments, the system enforces strict algorithmic governance (a multi-stage Quality Gate) before routing validated intelligence to production deployment.

> **Note:** This repository serves as a **technical showcase** of complex autonomous system design, API orchestration, and backend automation.

---

## 🧠 Core Architecture Flow

The pipeline is built on **n8n** and executes via a 6-hour autonomous cron schedule. It leverages a custom temporal state perimeter, deterministic JavaScript algorithms, and Google Gemini via LangChain.

```mermaid
graph TD
    %% Styling
    classDef trigger fill:#FF6600,stroke:#333,stroke-width:2px,color:#fff;
    classDef ingest fill:#4285F4,stroke:#333,stroke-width:2px,color:#fff;
    classDef compute fill:#F4B400,stroke:#333,stroke-width:2px,color:#111;
    classDef ai fill:#0F9D58,stroke:#333,stroke-width:2px,color:#fff;
    classDef deploy fill:#DB4437,stroke:#333,stroke-width:2px,color:#fff;
    classDef gate fill:#8E24AA,stroke:#333,stroke-width:2px,color:#fff;

    %% Nodes
    A([6-Hour Schedule])
    B1(CISA RSS Feed)
    B2(NVD API 2.0)
    C{Temporal State Memory}
    D[Deterministic Risk Engine]
    E{AI Analysis Gate}
    W1((Wait: Rate Limit))
    F[Gemini Security Analyst]
    G[Editorial Ranking Engine]
    H{LinkedIn Content Gate}
    W2((Wait: Rate Limit))
    I[LangChain Content Gen]
    J[Content Quality Gate]
    K{Deployment Switch}
    L([LinkedIn Production])
    M([Ntfy HTTP Alert])

    %% Connections
    A --> B1
    A --> B2
    B1 --> C
    B2 --> C
    C -- "Novel IDs Only" --> D
    D --> E
    E -- "Score >= 60" --> W1
    W1 --> F
    F --> G
    G --> H
    H -- "Top 5 Posts" --> W2
    W2 --> I
    I --> J
    J --> K
    K -- "PASS" --> L
    K -- "REVIEW / REJECT" --> M

    %% Class Assignments
    class A trigger;
    class B1,B2 ingest;
    class C,D,W1,G,W2,J compute;
    class F,I ai;
    class E,H,K gate;
    class L,M deploy;
