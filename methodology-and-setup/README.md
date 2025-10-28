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

### 🧩 GitHub Sync Verification 

### Purpose  
Verify synchronization between local (`master`) and remote (`origin/master`).  

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

## 🧩 GitHub Sync Verification — Guardrail Isolation Commit

### Purpose  
To verify that local commits made after the **guardrail isolation and audit-logging fixes** are properly synchronized with the remote repository (`origin/master`) and reflected on GitHub.

---

## ✅ Step-by-Step Verification Process

### **Step 1 — Check Current Branch**
Ensure you are working on the correct branch before pushing any updates.
```powershell
git branch
```
**Expected output:**
```
* master
```
*(The asterisk indicates the active branch.)*

---

### **Step 2 — Confirm Remote Repository**
Verify that the local repository is linked to the correct GitHub remote.
```powershell
git remote -v
```
**Expected output:**
```
origin  https://github.com/SecOpsPete/Custom_AI_Threat_Hunt_Agent.git (fetch)
origin  https://github.com/SecOpsPete/Custom_AI_Threat_Hunt_Agent.git (push)
```

---

### **Step 3 — Inspect Latest Local Commit**
View your most recent commit to confirm the expected guardrail fix.
```powershell
git log -1
```
**Example output:**
```
commit 482250efb5b4af7490059260f0d47d49xxxxxxxx (HEAD -> master, tag: snapshot-post-guardrail-isolation-fix)
Author: Peter Van Rossum <email@email.com>
Date:   Mon Oct 27 16:41:24 2025 -0700

    feat(isolation): show guardrail prompts before MDE lookup; treat inferred device as host-scoped; add audit logs
```

---

### **Step 4 — Compare Local vs Remote**
Check the latest commit on the remote (`origin/master`) to confirm whether it lags behind.
```powershell
git log origin/master -1
```
**Example output:**
```
commit 98fae383d9098614517d2fd620a12xxxxxxxxxx (tag: v1.4.1, origin/master, origin/HEAD)
Author: Peter Van Rossum <email@email.com>
Date:   Fri Oct 17 21:57:11 2025 -0700
```
➡️ *If the remote commit hash differs from your local (`482250e...`), it means the new fix has not yet been pushed.*

---

### **Step 5 — Push Latest Commit**
Synchronize the local master branch with the remote.
```powershell
git push origin master
```
**Example output:**
```
Total 0 (delta 0), reused 0 (delta 0), pack-reused 0 (from 0)
To https://github.com/SecOpsPete/REPO-NAME.git
   98faxxx..482xxxx  master -> master
```
✅ *This confirms your guardrail isolation commit has been successfully uploaded.*

---

### **Step 6 — Verify on GitHub**
Navigate to your repository:  
[https://github.com/SecOpsPete/REPO-NAME](https://github.com/SecOpsPete/REPO-NAME)

- Click **Code → Commits**  
- Confirm the latest entry:
  ```
  feat(isolation): show guardrail prompts before MDE lookup; treat inferred device as host-scoped; add audit logs
  ```
  appears with today’s date and your username.

---

### **Step 7 — Confirm Tag Synchronization**
Check that your release tag for this verified snapshot appears on GitHub.

```powershell
git tag --list
```
Expected to include:
```
snapshot-post-guardrail-isolation-fix
```

If missing remotely:
```powershell
git push --tags
```

Then verify under:
> **GitHub → Releases → Tags → `snapshot-post-guardrail-isolation-fix`**

---

### ✅ Final Verification Outcome
- `master` branch fully synced with `origin/master`  
- Commit `482250e` (Guardrail Isolation Fix) visible on GitHub  
- Tag `snapshot-post-guardrail-isolation-fix` published under Releases  

This confirms your repository’s **guardrail, audit-logging, and isolation logic** are preserved in the remote master history.

---

**Author:** *Peter Van Rossum*  
**Project:** *Custom AI Threat Hunt Agent*  
**Last Verified:** *October 27, 2025 – Version v1.4.2 (Guardrail Isolation Fix Sync)*


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



