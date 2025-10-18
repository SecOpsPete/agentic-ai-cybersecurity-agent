# 🧠 Agentic AI Cybersecurity Agent
**An AI-powered autonomous threat-hunting model built in Python for next-generation SOC automation.**

---

## 🔍 Overview
The **Agentic AI Cybersecurity Agent** is an advanced AI model designed to autonomously hunt, analyze, and respond to security threats across enterprise-scale infrastructures.  <br>

Base model built in The Cyber Range classroom labs, customizations added with assistance from  **GitHub Copilot Pro** and developed in **Python**, this project integrates directly with **Microsoft Sentinel** and **Defender for Endpoint** via secure API connections to a **Cyber Range** cloud environment ingesting telemetry from over **1,000 endpoints and servers**.

Powered by **Kusto Query Language (KQL)**, the agent processes massive log datasets to detect Indicators of Compromise (IoCs) **300–500 times faster than a human analyst**.  <br>

When anomalies or threats are confirmed, it can simulate or recommend isolation of affected systems—with human oversight required to validate findings and approve remediation.

---

- 🛡️ **[Password-Protected Isolation & Remediation Guardrails](./password-protected-isolation-remediation-guardrails/README.md)**  
  Adds a pre-isolation security layer that operates before the standard “Isolate VM (y/n)” prompt, requiring password authentication to confirm authorization. Ensures only approved analysts can execute isolation while maintaining audit logs, dry-run protection, and colorized event summaries for full visibility.
  

- 🔒 **[PII Redaction Framework](./pii-redaction/README.md)**  
  Obfuscates sensitive data such as email addresses by default and includes optional toggles for usernames and IPs to meet stricter privacy needs without limiting analyst visibility. Configuration changes are made easily within `GUARDRAILS.py` by toggling redaction settings from `False` to `True`.


- 📊 **[Row/Byte Cap Enforcement](./row-byte-cap-rate-enforcement/README.md)**  
  Implements safety caps that limit row and payload size across all agent queries to maintain performance stability and prevent excessive token or memory usage. Automatically truncates results beyond 2,000 rows or 1 MB payload and logs structured warnings with colorized console feedback for analyst visibility.


- ⏱️ **[Time Window Enforcement](./time-window-input-restrictions/README.md)**  
  Standardizes query time ranges across all modules, enforcing analyst-approved lookback windows to optimize performance and maintain SOC best practices.

- 🧭 **Confidence-based threat classification logic**

- 🧰 **Robust error handling and validation logic**

In addition, the agent is being expanded with:
- 🛡️ **OWASP LLM Top 10 Hardening**  
- 🗺️ **MITRE ATLAS threat-mapping**  

These enhancements align AI reasoning with adversarial behavior models, creating a **powerful, defensible framework for AI-driven cybersecurity automation**.

---

> *Developed by SecOpsPete — part of the Agentic AI initiative to merge cognitive automation with real-world cybersecurity defense.*
