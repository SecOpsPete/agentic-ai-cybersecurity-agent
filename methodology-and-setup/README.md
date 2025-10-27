# 🧠 AI Agent Improvement / Testing Methodology  
### Setup and Methodology 
This is the complete standard operating procedure (SOP) for integrating safeguards, version control, and iterative AI agent improvements using **GitHub Copilot Pro** with the **GPT-5.0 model**, based on **Josh Madakor’s Cyber Range Baseline AI Agent Model**.

---

## 🧩 Overview
This methodology aligns with the structured workflow:

**PLAN → APPROVAL → EDIT → KEEP → TEST → REVIEW → COMMIT → PUSH → TAG**

Each section provides actionable steps to ensure every Copilot-assisted improvement is versioned, reversible, and auditable.

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

## 🛡️ Git Safety, Snapshots, and Tagging Discipline

Maintaining stable save points is critical when using AI-assisted code generation.  
This section combines safety snapshots, commit practices, and tagging into a single, practical workflow.

### 🩵 Why Snapshots Matter
Snapshots act as **restore points** — each one preserves your project at a safe state before or after major edits. They ensure every Copilot modification is reversible.

### 🩵 When to Create Snapshots (Granular Timing)
Use this sequence during each Copilot improvement cycle:

1. **Pre‑Edit Snapshot** – *Before Copilot edits*  
   ```bash
   git add .
   git commit -m "snapshot: baseline before Copilot change"
   ```  
   Protects your current code from unintended AI edits.

2. **Post‑Review Snapshot** – *After approving Copilot’s proposed change*  
   ```bash
   git add .
   git commit -m "snapshot: reviewed Copilot proposal before testing"
   ```  
   Captures exactly what Copilot changed and what you approved.

3. **Post‑Test Commit & Tag** – *After confirming success*  
   ```bash
   git add .
   git commit -m "fix: applied and verified Copilot improvement"
   git push
   git tag -a snapshot-post-change -m "Verified Copilot improvement"
   git push --tags
   ```  
   Marks the verified, stable state in both local and remote history.

### 🩵 Viewing and Restoring Snapshots
If something breaks or you need to inspect history:

```bash
git log --oneline         # View commit history
git checkout <commit-id>  # Temporarily view a prior state
git reset --hard <commit-id>  # Fully revert to earlier snapshot
```

Tags (e.g., `snapshot-post-change`) let you instantly return to known‑good builds without losing history.

---

## 🤖 Copilot Commit Discipline
Follow your SOP precisely to maintain integrity and traceability:

> **PLAN → APPROVAL → EDIT → KEEP → TEST → REVIEW → COMMIT → PUSH → TAG**

Before each AI edit:
```bash
git commit -am "Checkpoint before Copilot edit"
```
After successful testing:
```bash
git commit -am "Fix: verified Copilot logic change"
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
Each time VS Code launches, Copilot automatically reads your instructions and applies them before editing any files.

---

## 🔄 Manual Context Refresh
When you change your SOP or repo structure, tell Copilot to refresh context:

```
@copilot-agent Please re-read .github/copilot-instructions.md and rebuild project context before continuing.
```
This reinitializes Copilot’s project awareness without altering code.

---

## 📌 Author
**Peter Van Rossum**  
[LinkedIn](https://www.linkedin.com) · [GitHub](https://github.com/SecOpsPete)  
**Version 1.1 · © 2025 SecOpsPete Labs · For educational and research use**
