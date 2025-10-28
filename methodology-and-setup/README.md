# 🧠 AI Agent Improvement / Testing Methodology  

## 🧩 Overview  
This methodology provides a complete, structured SOP for AI agent improvements using **GitHub Copilot Pro** with **GPT‑5.0**, based on **Josh Madakor’s Cyber Range Baseline AI Agent Model**.  

**Workflow:**  
### PLAN → APPROVAL → EDIT → KEEP → TEST → REVIEW → COMMIT → PUSH → TAG  

Each stage ensures that AI‑assisted changes are versioned, testable, reversible, and auditable.  

---

## 💻 Local + GitHub Integration Setup (VS Code, Copilot, Repo Link)  

### ⚙️ Development Environment Setup  
1. **Install VS Code**  
2. **Install GitHub Copilot Extension**  
3. **Enable Copilot Agent Mode** (multi‑file reasoning)  
4. *(Optional)* Subscribe to **Copilot Pro ($10/mo)** for GPT‑5.0 access.  
5. **Keep your project local** (e.g., `C:\Users\peter\AI_Agent\`) — avoid OneDrive/Google Drive.  

---

### 🌐 Connect Local Git Project to GitHub  
1. **Verify Git status**
   ```bash
   git status
   ```

2. **Stage and commit initial changes**
   ```bash
   git add .
   git commit -m "Initial commit – AI Agent baseline"
   ```

3. **Create a GitHub repository**
   - Example: `Custom_AI_Threat_Hunt_Agent`
   - Copy HTTPS URL: `https://github.com/YOURNAME/Custom_AI_Threat_Hunt_Agent.git`

4. **Link local and remote**
   ```bash
   git remote add origin https://github.com/YOURNAME/Custom_AI_Threat_Hunt_Agent.git
   git branch -M main
   git push -u origin main
   ```

5. **Verify success**
   - Refresh GitHub to confirm file visibility  

---
---

## 🧠 PLAN — Define the Objective  
1. Identify what change is being introduced (guardrail, prompt enforcement, etc.).  
2. Record rationale in issues or dev notes.  
3. Ensure Copilot understands project scope.  

---

## ✅ APPROVAL — Confirm Readiness  
1. Review repo state and ensure no untracked edits:
   ```bash
   git status
   ```
2. Create a **pre‑edit snapshot** for rollback safety:
   ```bash
   git add .
   git commit -m "snapshot: baseline before Copilot edit"
   ```

---

## ✏️ EDIT — Controlled Copilot Modification  
1. Use **Copilot Agent Mode** or **Copilot Chat** in VS Code.  
2. Instruct Copilot using natural‑language prompts aligned with this SOP.  
3. Review and approve proposed diffs manually.  
4. Stage accepted edits:
   ```bash
   git add .
   git commit -m "snapshot: reviewed Copilot proposal before testing"
   ```

---

## 🧷 KEEP — Preserve Stable State  
Once code compiles and runs cleanly:  
```bash
git add .
git commit -m "snapshot: working build before functional testing"
```

---

## 🧪 TEST — Validate Functionality  
1. Run automated/unit tests.  
2. Verify manual behavior (dry‑run, safe mode, logs).  
3. Continue only after passing results.  

---

## 🔍 REVIEW — Inspect and Verify Integrity  
Before committing final code, confirm **only intended files** changed.  
```bash
git diff --name-only
```
Then stage only approved files:
```powershell
git add _main.py EXECUTOR.py
git commit -m "feat(isolation): restore two-tier guardrail prompts before lookup; add DEVICE_INFERRED and audit logs"
```

---

## 💾 COMMIT — Record Verified Changes  
1. Use clear, descriptive messages:
   ```bash
   git commit -m "fix: validated Copilot improvement in isolation workflow"
   ```
2. Avoid temporary or compiled artifacts (`.pyc`, logs).  

---

## ☁️ PUSH — Publish to Remote Repository  
Once verified locally:  
```bash
git push
```

---

### 🧩 GitHub Sync Verification — Guardrail Isolation Commit  

### Purpose  
Verify synchronization of **guardrail isolation and audit‑logging fixes** between local (`master`) and remote (`origin/master`).  

### Steps  
1. **Check Current Branch**
   ```powershell
   git branch
   ```
   Expected: `* master`  

2. **Confirm Remote Repository**
   ```powershell
   git remote -v
   ```

3. **Inspect Latest Local Commit**
   ```powershell
   git log -1
   ```

4. **Compare Local vs Remote**
   ```powershell
   git log origin/master -1
   ```

5. **Push Latest Commit**
   ```powershell
   git push origin master
   ```

6. **Verify on GitHub**
   - Open your repo and confirm the commit is visible with the correct timestamp.  

7. **Confirm Tag Synchronization**
   ```powershell
   git tag --list
   git push --tags
   ```

### ✅ Verification Outcome  
- Local and remote branches synced  
- Commit visible on GitHub  
- Tag published under **Releases**  

**Author:** *Peter Van Rossum*  
**Last Verified:** *October 27, 2025 – v1.4.2 (Guardrail Isolation Fix Sync)*  

---

## 🏷️ TAG — Version and Snapshot for Rollback  
Tag verified milestones:  

**Manual snapshot:**  
```bash
git tag -a snapshot-post-change -m "Verified Copilot improvement"
git push --tags
```

**Feature‑specific tag:**  
```bash
git tag v1.3.0-guardrail-restore
git push --tags
```

---

## 🧠 Let Copilot Learn Your SOP Automatically  
1. Create `.github/copilot-instructions.md` containing this SOP.  
2. Add `.vscode/settings.json`:  
   ```json
   {
     "github.copilot.chat.startupCommands": [
       "@copilot-agent Please read .github/copilot-instructions.md and follow all listed SOP steps for any new edits."
     ]
   }
   ```

---

## 🔄 Manual Context Refresh  
When modifying SOP or repo structure:  
```
@copilot-agent Please re-read .github/copilot-instructions.md and rebuild project context before continuing.
```

---

## 📌 Author  
**Peter Van Rossum**  
[LinkedIn](https://www.linkedin.com) · [GitHub](https://github.com/SecOpsPete)  
**Version 1.3 · © 2025 SecOpsPete Labs · For educational and research use**  



