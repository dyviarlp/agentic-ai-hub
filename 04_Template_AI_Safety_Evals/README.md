# 🛡️ Template 04: AI Safety Evals & Security Auditor (2026)

> **Specialty:** Lead AI Safety Evaluator & Red Team Security Specialist  
> **Author:** Juan Armando Rodríguez Pérez  
> **Auditing Scope:** Prompt Injections, LLM Jailbreaks, OWASP MASVS & Firebase Security Rules  
> **Native MCPs:** `filesystem/search`, `evaluation-tools`, `github`  
> **Paradigm:** Doubt-Driven CoT, Factual Consistency & Quantifiable Evidence Gates

---

## 🏛️ Architecture Principles

1. **Doubt-Driven CoT & Red Teaming:**
   - Adversarial probing of prompt injection vectors, jailbreak robustness, and schema bypass vulnerabilities.
2. **Anti-Hallucination Auditing:**
   - Verifiable factual consistency checks against canonical sources and regulatory frameworks.
3. **Cloud & Mobile Security Audits:**
   - Granular Firestore (`firestore.rules`) and Cloud Storage rules auditing.
   - CORS validation, CSP security headers, and R8 obfuscation checks.
4. **Deterministic Evidence Scoring:**
   - Quantifiable Safety Scores (0-100%) and actionable vulnerability remediations.

---

## 📦 Directory Structure

```text
04_Template_AI_Safety_Evals/
├── .agents/
│   ├── memory/
│   │   ├── 01_vulnerabilities_registry.md
│   │   ├── 02_mitigations_playbook.md
│   │   ├── 03_llm_evals_benchmarks.md
│   │   ├── 04_cloud_rules_hardening.md
│   │   └── 05_masvs_mobile_security.md
│   ├── skills/
│   │   ├── red-teaming-guardrails/
│   │   ├── security-and-hardening/
│   │   └── truthfulness-evaluator/
│   ├── AGENTS.md
│   └── project_manifest.json
└── README.md
```

---

## 🚀 Drop-In Activation

To activate this agent template in any AI/security audit repository:
```bash
cp -r 04_Template_AI_Safety_Evals/.agents /path/to/your-audit-project/
```
