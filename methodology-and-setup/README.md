# 🧠 AI Agent Improvement/Testing Methodology  

> **Setup and Methodoloty - Start Here**  
> This is the setup to integrate safeguards, checks, and iterative improvements using **GitHub Copilot Pro** with the **GPT-5.0** model.
> Based on Josh Madakor’s Cyber Range Baseline AI Agent Model

---

## 🧩 Overview  

Every following section includes actionable guidance aligned with **PLAN → APPROVAL → EDIT → KEEP → TEST → REVIEW → COMMIT → PUSH → TAG** workflow.  
Each instruction corresponds to a **WORKING and COMPLETE** `@copilot-agent` prompt block ready for copy/paste into VS Code.

---

## ⚙️ Development Environment Setup  

1. **Install VS Code.**  
2. **Install GitHub Copilot Extension.**  
3. **Enable Copilot Agent Mode** — allows Copilot to reason across multiple files.  
4. *(Optional)* Subscribe to Copilot Pro ($10/mo) for **GPT-5.0** access.  
5. Ensure your AI project lives on a **local drive** (not OneDrive / Google Drive) for proper Git handling.

---

## 🌐 Connect Local Git Project to GitHub  

1. **Verify repository status**
   ```bash
   git status
   ```
   Confirms version control and lists modified files.

2. **Stage and commit changes**
   ```bash
   git add .
   git commit -m "feat(time-window): integrate get_time_window helper, enforce model consistency, and remove deprecated models"
   ```

3. **Create new GitHub repository**
   - Go to GitHub → **New Repository**  
   - Example name: `Custom_AI_Threat_Hunt_Agent`  
   - Leave README / .gitignore / license unchecked  
   - Copy your HTTPS URL (e.g. `https://github.com/YOURNAMEHERE/Custom_AI_Threat_Hunt_Agent.git`)

4. **Link local and remote**
   ```bash
   git remote add origin https://github.com/YOURNAMEHERE/Custom_AI_Threat_Hunt_Agent.git
   git branch -M master
   git push -u origin master
   ```

5. **Verify success**
   - Refresh the repo on GitHub.  
   - Confirm all project files are visible.  

6. **Future updates**
   ```bash
   git add .
   git commit -m "describe your change"
   git push
   ```

---

## 🛡️ Git Safety & Restore Points  

Initialize Git and capture a clean snapshot before any major change:  
```bash
git init
git add .
git commit -m "Safe baseline before AI fixes"
```

View snapshots:  
```bash
git log --oneline
```

Restore safely:  
```bash
git revert <commit-id>        # Soft revert a specific change  
git reset --hard <commit-id>  # Full rollback to earlier state
```

---

## 🤖 Copilot Commit Discipline  

Follow your **SOP:**  
> PLAN → APPROVAL → EDIT → KEEP → TEST → REVIEW → COMMIT → PUSH → TAG  

### 🧠 Let Copilot Learn Your Project  

1. Create `.github/copilot-instructions.md` *(contains your SOP and rules).*  
2. Create `.vscode/settings.json` to auto-load it each session.

Example `settings.json`:  
```json
{
  "github.copilot.chat.startupCommands": [
    "@copilot-agent Please read .github/copilot-instructions.md and follow all listed SOP steps for any new edits."
  ]
}
```

**Result:**  
- Every time VS Code launches, Copilot Chat automatically reads your instructions.  
- It performs a **read-only repository scan** to build context — no files are edited.  
- Your behavioral guardrails and workflow rules are applied automatically.

✅ **No manual startup needed.**

---

## 🔄 Manual Context Refresh  

Whenever you update project structure or SOP instructions, simply run:  
```
@copilot-agent Please read .github/copilot-instructions.md and follow all listed SOP steps for any new edits.
```

Copilot will:
1. Re-read your `.github/copilot-instructions.md` rules.  
2. Rebuild its internal project map (read-only).  
3. Re-apply workflow behavior and safety logic.

Think of this as pressing a **“Refresh Context”** button — *no code changes occur.*

---

## 🧩 Summary  

| Category | Purpose |
|:----------|:---------|
| **Safeguards** | Protect codebase integrity via Git snapshots & commit SOP. |
| **Agent Improvements** | Incrementally upgrade logic with Copilot-assisted patches. |
| **OWASP LLM Hardening** | Reduce model exposure to prompt injection & leakage. |
| **MITRE ATLAS Mapping** | Align detection & response with adversarial behaviors. |

This methodology ensures **stability first**, **security always**, and **auditability throughout** — while letting your Agent evolve responsibly through GPT-powered automation.

---

## 📌 Author

**Peter Van Rossum**  
🔗 [LinkedIn](https://www.linkedin.com/in/vanr)  
💻 [GitHub](https://github.com/SecOpsPete)   
Version 1.0 · © 2025 SecOpsPete Labs · For educational and research use.

---
