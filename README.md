# 🧠 Agentic AI Cybersecurity Agent
**An AI-powered autonomous threat-hunting model built in Python for next-generation SOC automation.**

---

## 🔍 Overview
The **Agentic AI Cybersecurity Agent** is an advanced AI model designed to autonomously hunt, analyze, and respond to security threats across enterprise-scale infrastructures.  <br>

Base model built in Josh Madakor's Cyber Range classroom labs, customizations added with assistance from  **GitHub Copilot Pro** and developed in **Python**, this project integrates directly with **Microsoft Sentinel** and **Defender for Endpoint** via secure API connections to a **Cyber Range** cloud environment ingesting telemetry from over **1,000 endpoints and servers**.

Powered by **Kusto Query Language (KQL)**, the agent processes massive log datasets to detect Indicators of Compromise (IoCs) **300–500 times faster than a human analyst**.  <br>

When anomalies or threats are confirmed, it can recommend actual isolation of affected systems—with human oversight required to validate findings and approve remediation.

- 📘 **[Methodology & Setup](https://github.com/SecOpsPete/agentic-ai-cybersecurity-agent/tree/main/methodology-and-setup)**  
  Provides the foundational workflow for improving and hardening the Agentic AI model.    
  **PLAN → VERIFY → EDIT → TEST → COMMIT → PUSH → TAG**
  <br>

<h3 align="center">🎬 Watch the Video:</h3>
<p align="center">
  <a href="https://www.youtube.com/watch?v=tms3dnZih4U&t=33s">
    <img src="https://img.youtube.com/vi/tms3dnZih4U/maxresdefault.jpg" width="400" alt="Watch the video">
  </a>
</p>

---

- 🛡️ **[Password-Protected Isolation & Remediation Guardrails](./password-protected-isolation-remediation-guardrails/README.md)**  
  Adds a pre-isolation security layer that operates before the standard “Isolate VM (y/n)” prompt, requiring password authentication to confirm authorization. Ensures only approved analysts can execute isolation while maintaining audit logs, dry-run protection, and colorized event summaries for full visibility.
  

- 🧠 **[Confidence-Based Threat Classification Logic](./threat-classification-logic/README.md)**  
  Introduces dual-field interpretation for *confidence* and *verdict* to eliminate false positives and clarify AI decisions.  
  Isolation and remediation are now triggered **only** when findings are both `malicious` and `high-confidence`, preserving guardrail and dry-run protections while improving analyst visibility.


- 🔒 **[PII Redaction Framework](./pii-redaction/README.md)**  
  Obfuscates sensitive data such as email addresses by default and includes optional toggles for usernames and IPs to meet stricter privacy needs without limiting analyst visibility. Configuration changes are made easily within `GUARDRAILS.py` by toggling redaction settings from `False` to `True`.


- 📊 **[Row/Byte Cap Enforcement](./row-byte-cap-rate-enforcement/README.md)**  
  Implements safety caps that limit row and payload size across all agent queries to maintain performance stability and prevent excessive token or memory usage. Automatically truncates results beyond 2,000 rows or 1 MB payload and logs structured warnings with colorized console feedback for analyst visibility.


- ⏱️ **[Time Window Enforcement](./time-window-input-restrictions/README.md)**  
  Standardizes query time ranges across all modules, enforcing analyst-approved lookback windows to optimize performance and maintain SOC best practices.
  

- 🧰 **[Validation Logic](https://www.youtube.com/watch?v=tms3dnZih4U&t=33s)**
  Cleaned up weaknesses in user input validation in the base AI Model. 


In addition, the agent is being expanded with:
- 🛡️ **OWASP LLM Top 10 Hardening**  
- 🗺️ **MITRE ATLAS threat-mapping (Adversarial Threat Landscape for Artificial-Intelligence Systems)**  

These enhancements align AI reasoning with adversarial behavior models, creating a **powerful, defensible framework for AI-driven cybersecurity automation**.

---

> *Developed by SecOpsPete — part of the Agentic AI initiative to merge cognitive automation with real-world cybersecurity defense.*
