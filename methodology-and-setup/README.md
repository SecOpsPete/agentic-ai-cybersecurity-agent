# 🧠 AI Agent Improvement / Testing Methodology  
### Setup and Methodology – Start Here  
This is the complete standard operating procedure (SOP) for integrating safeguards, version control, and iterative AI agent improvements using **GitHub Copilot Pro** with the **GPT-5.0 model**, based on **Josh Madakor’s Cyber Range Baseline AI Agent Model**.

---

## 🧩 Overview
Every section below aligns with the official workflow:  

**PLAN → APPROVAL → EDIT → KEEP → TEST → REVIEW → COMMIT → PUSH → TAG**

Each step includes actionable guidance and Copilot-ready prompt blocks.

---

## ⚙️ Development Environment Setup
1. **Install VS Code**  
2. **Install GitHub Copilot Extension**  
3. **Enable Copilot Agent Mode** (for reasoning across multiple files)  
4. *(Optional)* Subscribe to **Copilot Pro ($10/mo)** for GPT-5.0 access.  
5. **Ensure your AI project is local** (e.g., `C:\Users\peter\AI_Agent\`) — not on OneDrive or Google Drive, to prevent Git file-locking issues.

---

## 🌐 Connect Local Git Project to GitHub
**1. Verify Git status**
```bash
git status
```
Shows whether version control is active and lists modified files.

**2. Stage and commit initial changes**
```bash
git add .
git commit -m "Initial commit – AI Agent baseline"
```

**3. Create a new GitHub repository**
- Go to GitHub → *New Repository*
- Example: `Custom_AI_Threat_Hunt_Agent`
- Leave README / .gitignore / license unchecked  
- Copy the HTTPS URL (e.g., `https://github.com/YOURNAME/Custom_AI_Threat_Hunt_Agent.git`)

**4. Link local and remote**
```bash
git remote add origin https://github.com/YOURNAME/Custom_AI_Threat_Hunt_Agent.git
git branch -M main
git push -u origin main
```

**5. Verify success**
- Refresh the repo on GitHub  
- Confirm all project files are visible  

**6. Future updates**
```bash
git add .
git commit -m "describe your change"
git push
```

---

## 🛡️ Git Safety & Restore Points
Before any major change, create a safe snapshot:

```bash
git add .
git commit -m "Safe baseline before AI fixes"
```

**View snapshots:**
```bash
git log --oneline
```

**Restore safely:**
```bash
git revert <commit-id>        # Soft revert a specific change  
git reset --hard <commit-id>  # Full rollback to earlier state
```

---

## 💾 Snapshots & Tagging Discipline
Use **tags** to label stable states or major checkpoints:

```bash
git tag -a snapshot-pre-copilot-fix -m "Checkpoint before Copilot isolation logic fix"
git push --tags
```

Tags act as **named save points** you can revert to or reference later.

---

## 🤖 Copilot Commit Discipline
Follow your SOP strictly:

> **PLAN → APPROVAL → EDIT → KEEP → TEST → REVIEW → COMMIT → PUSH → TAG**

Always create a pre-edit commit before letting Copilot modify your code:
```bash
git commit -am "Checkpoint before Copilot edit"
```

After successful testing:
```bash
git commit -am "Fix: normalize verdict and confidence comparison"
git push
```

---

## 🧠 Let Copilot Learn Your Project
1. Create `.github/copilot-instructions.md` containing your SOP and workflow rules.  
2. Add `.vscode/settings.json` to auto-load instructions each session.

**Example settings.json:**
```json
{
  "github.copilot.chat.startupCommands": [
    "@copilot-agent Please read .github/copilot-instructions.md and follow all listed SOP steps for any new edits."
  ]
}
```

Result:  
Each time VS Code launches, Copilot automatically reads your SOP and applies those rules before editing any files.

---

## 🔄 Manual Context Refresh
When you change your SOP or repo structure, tell Copilot to refresh context:

```
@copilot-agent Please re-read .github/copilot-instructions.md and rebuild project context before continuing.
```

This reinitializes Copilot’s project awareness without changing code.

---

## 📌 Author
**Peter Van Rossum**  
[LinkedIn](https://www.linkedin.com) · [GitHub](https://github.com/SecOpsPete)  
**Version 1.0 · © 2025 SecOpsPete Labs · For educational and research use**
