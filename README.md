# 🧠 Agentic AI Cybersecurity Agent
**An AI-powered autonomous threat-hunting model built in Python for next-generation SOC automation.**

---

## 🔍 Overview
The **Agentic AI Cybersecurity Agent** is an advanced AI model designed to autonomously hunt, analyze, and respond to security threats across enterprise-scale infrastructures.  <br>

Base model built in The Cyber Range classroom labs, customizations added with assistance from  **GitHub Copilot Pro** and developed in **Python**, this project integrates directly with **Microsoft Sentinel** and **Defender for Endpoint** via secure API connections to a **Cyber Range** cloud environment ingesting telemetry from over **1,000 endpoints and servers**.

Powered by **Kusto Query Language (KQL)**, the agent processes massive log datasets to detect Indicators of Compromise (IoCs) **300–500 times faster than a human analyst**.  <br>

When anomalies or threats are confirmed, it can simulate or recommend isolation of affected systems—with human oversight required to validate findings and approve remediation.

---

## 🧩 Security, Guardrails & Enhancements
This model incorporates a comprehensive set of AI security guardrails and resilience mechanisms, including:

- 🔐 **Password-protected isolation & remediation guardrails**  
- 🧹 **PII redaction and data sanitization**  

- 📊 **[Row/Byte Cap Enforcement](./row-byte-cap-rate-enforcement/README.md)**  
  Implements safety caps that limit row and payload size across all agent queries to maintain performance stability and prevent excessive token or memory usage. Automatically truncates results beyond 2,000 rows or 1 MB payload and logs structured warnings with colorized console feedback for analyst visibility.


- ⏱️ **[Time Window Enforcement](./time-window-input-restrictions/README.md)**  
  Standardizes query time ranges across all modules, enforcing analyst-approved lookback windows to optimize performance and maintain SOC best practices.


- 🧰 **Robust error handling and validation logic**

In addition, the agent is being expanded with:
- 🛡️ **OWASP LLM Top 10 Hardening**  
- 🗺️ **MITRE ATLAS threat-mapping**  

These enhancements align AI reasoning with adversarial behavior models, creating a **powerful, defensible framework for AI-driven cybersecurity automation**.

---

> *Developed by SecOpsPete — part of the Agentic AI initiative to merge cognitive automation with real-world cybersecurity defense.*
