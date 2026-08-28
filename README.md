# 🏛️ Enterprise Agentic AI Hub & Multi-Agent Architecture

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Architecture](https://img.shields.io/badge/Architecture-Deterministic_Loop_Engineering-orange.svg)](#-deterministic-loop-engineering-framework)
[![Domain Blueprints](https://img.shields.io/badge/Blueprints-4_Production_Templates-success.svg)](#-curated-modular-domain-blueprints)
[![MCP Protocol](https://img.shields.io/badge/MCP-Model_Context_Protocol_Ready-8A2BE2.svg)](#-curated-modular-domain-blueprints)
[![Safety & Compliance](https://img.shields.io/badge/Security-OWASP_MASVS_%26_AI_Safety-red.svg)](#4-04_template_ai_safety_evals)
[![Author](https://img.shields.io/badge/Author-Juan_Armando_Rodríguez_Pérez-0A66C2?logo=linkedin&logoColor=white)](https://www.linkedin.com/in/juan-rodriguez-dev-ai)

> **Enterprise Multi-Agent Framework (2026)**  
> **Author:** Juan Armando Rodríguez Pérez — *Applied AI & Full-Stack Systems Engineer*  
> **Architecture Repository:** [https://github.com/dyviarlp/agentic-ai-hub](https://github.com/dyviarlp/agentic-ai-hub)

---

## 🧭 Overview

The **Enterprise Agentic AI Hub** is a curated catalog of **production-grade AI Agent Blueprints** designed for high-stakes software engineering, cloud infrastructure, career branding, and AI safety auditing. 

Unlike generic prompt templates, these blueprints are engineered around **Formal State Machine Loops**, **Native MCP (Model Context Protocol) Integration**, **Zero-Click Dynamic Intent Routing**, **Doubt-Driven Chain-of-Thought (CoT)**, and **Shift-Left Automated Quality Assurance**.

---

## 🔄 Deterministic Loop-Engineering Framework

Every agent operating within this framework executes under an immutable state machine designed to prevent infinite loops, hallucinated resolutions, and blind retry patterns.

```mermaid
flowchart TD
    A([🎯 User Intent / Task Input]) --> B[🧠 1. THINK: Deconstruct & Doubt-Driven CoT]
    B --> C[⚡ 2. ACT: Execute Atomic MCP Tool / Code Action]
    C --> D[👁️ 3. OBSERVE: Capture Runtime Output / AST / Logs]
    D --> E[⚖️ 4. EVALUATE: Validate Against Ground Truth]
    E -->|Validation Passed| F{🛡️ EVIDENCE GATE}
    E -->|Validation Failed| G[🔄 MUTATE PLAN: Next attempt MUST change the hypothesis]
    G --> B
    F -->|Tests 100% Green & Verified| H([✅ Deliver Verified Result])
```

### ⚡ The Immutable Engineering Principle
> **"The next attempt MUST change the plan."**  
> If a test, build, or evaluation fails, the agent is strictly prohibited from repeating the same action or assuming transient behavior without introducing a new structural hypothesis or root-cause patch.

---

## 📦 Curated Modular Domain Blueprints

This repository hosts 4 specialized, sanitized, privacy-clean agent templates ready for drop-in use:

| Blueprint | Domain & Core Stack | Native MCP Servers | Elite Skills Active | Key Capabilities |
| :--- | :--- | :--- | :--- | :--- |
| [**`01_Template_Mobile_Flutter`**](./01_Template_Mobile_Flutter) | Flutter 3.5+, Riverpod 3.x, Android API 34–37, Firebase | `firebase`, `google_maps_platform`, `flutter/dart`, `github` | `superpowers`, `andrej-karpathy-skills`, `agent-skills`, `impeccable`, `ponytail` | Clean Architecture, In-Memory Safe Storage, 120fps Impeller, Shift-Left QA (100% test pass) |
| [**`02_Template_Web_Fullstack`**](./02_Template_Web_Fullstack) | Next.js, React, TypeScript, Astro, Vercel Serverless | `chrome-devtools`, `modern-web-guidance`, `visualization`, `github` | `react-best-practices`, `ui-ux-pro-max`, `taste-skill`, `modern-web-guidance`, `chrome-devtools` | Author-Grade UI/UX, Core Web Vitals (LCP < 2s, INP < 200ms), WCAG AA a11y, strict TS contracts |
| [**`03_Template_Career_HR`**](./03_Template_Career_HR) | Playwright Headless PDF, ATS Parser, Python, LinkedIn Sync | `playwright/python`, `web-search/url-reader`, `github` | `anthropic-skills`, `marketingskills`, `humanizer`, `cognitive-doc-design`, `cv-ats-optimizer` | Deterministic 2-page A4 PDF rendering, strict NDA compliance, 360° Profile Synchronization |
| [**`04_Template_AI_Safety_Evals`**](./04_Template_AI_Safety_Evals) | Python Evals, Prompt Injection Testing, OWASP MASVS | `filesystem/search`, `evaluation-tools`, `github` | `matt-pocock-skills`, `red-teaming-guardrails`, `truthfulness-evaluator`, `security-and-hardening` | Red-teaming batteries, jailbreak probing, anti-hallucination auditing, granular Firestore/CORS security |

---

## 📂 Repository Structure

```text
agentic-ai-hub/
├── 01_Template_Mobile_Flutter/
│   ├── .agents/
│   │   └── AGENTS.md                  # Mobile Flutter agent instructions & constraints
│   └── README.md                      # Architecture deep dive & Flutter QA blueprint
│
├── 02_Template_Web_Fullstack/
│   ├── .agents/
│   │   └── AGENTS.md                  # Fullstack Web agent rules & Web Vitals directives
│   └── README.md                      # Next.js/React & Serverless guidelines
│
├── 03_Template_Career_HR/
│   ├── .agents/
│   │   └── AGENTS.md                  # Tech recruiter & career strategy agent instructions
│   └── README.md                      # Headless Playwright PDF & ATS optimization manual
│
├── 04_Template_AI_Safety_Evals/
│   ├── .agents/
│   │   └── AGENTS.md                  # AI safety, red teaming & security audit directives
│   └── README.md                      # Guardrail evaluation & MASVS compliance guide
│
├── .gitignore
├── LICENSE
└── README.md                          # Master Hub Documentation (This file)
```

---

## 🚀 Quickstart: Integrating Blueprints into Your Project

Adopting any blueprint in your target project takes **one command**. The agentic IDE (Antigravity IDE, Claude Code, Cursor, Windsurf, Gemini CLI, Cline) will immediately discover `.agents/AGENTS.md` at the workspace root:

### 1. Flutter Mobile Project
```bash
cp -r 01_Template_Mobile_Flutter/.agents /path/to/your-flutter-project/
```

### 2. Web Fullstack Project
```bash
cp -r 02_Template_Web_Fullstack/.agents /path/to/your-web-project/
```

### 3. Career & Document Strategy
```bash
cp -r 03_Template_Career_HR/.agents /path/to/your-career-workspace/
```

### 4. AI Safety & Security Evals
```bash
cp -r 04_Template_AI_Safety_Evals/.agents /path/to/your-audit-workspace/
```

---

## 🛡️ Privacy, Zero-Leakage & Safety Guarantee

All templates in this hub are **100% sanitized and virgin**:
- ❌ **Zero Hardcoded Secrets / API Keys:** All environments require dynamic `.env` configuration.
- ❌ **Zero Private Telemetry:** No personal identifiable information (PII) or confidential client data.
- ✅ **Strict NDA Compliance:** Frameworks focus strictly on engineering architecture and public evaluation standards.

---

## 👤 Author & Connect

**Juan Armando Rodríguez Pérez**  
*Applied AI & Full-Stack Systems Engineer*  
*Specialized in Fault-Tolerant Mobile/Web Platforms, Agentic AI Systems & Algorithmic Safety.*

- 💼 **LinkedIn:** [linkedin.com/in/juan-rodriguez-dev-ai](https://www.linkedin.com/in/juan-rodriguez-dev-ai)
- 🌐 **Live Production Showcase:** [mascotia-demo.web.app](https://mascotia-demo.web.app)
- 🐙 **GitHub Profile:** [github.com/dyviarlp](https://github.com/dyviarlp)

---

## 📄 License

This project is licensed under the [MIT License](LICENSE) — feel free to use and adapt it for personal or commercial agentic systems with attribution.
