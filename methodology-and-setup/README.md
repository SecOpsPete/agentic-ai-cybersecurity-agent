# 🧠 AI Agent Improvement / Testing Methodology  
### Setup and Methodology  
This is the complete standard operating procedure (SOP) for integrating safeguards, version control, and iterative AI agent improvements using **GitHub Copilot Pro** with the **GPT‑5.0 model**, based on **Josh Madakor’s Cyber Range Baseline AI Agent Model**.

---

## 🧩 Overview  
This methodology follows a structured sequence to ensure every AI‑assisted modification is documented, testable, reversible, and auditable.

### **PLAN → APPROVAL → EDIT → KEEP → TEST → REVIEW → COMMIT → PUSH → TAG**

Each stage below outlines the exact operational flow for integrating and verifying Copilot‑driven changes within the AI Agent repository.

---

## 🧠 PLAN — Define the Objective
1. Identify what change or safeguard is being introduced (e.g., new guardrail, prompt enforcement, inference logic).  
2. Record the rationale in your GitHub issue or development notes.  
3. Ensure Copilot understands project scope and intended modification before editing.

---

## ✅ APPROVAL — Prepare and Confirm Readiness
1. Review the current repository state.  
2. Verify no unstaged or unsaved edits exist:
   ```bash
   git status
   ```
3. If this is a new feature or logic refactor, tag a **pre‑edit snapshot** for rollback safety:
   ```bash
   git add .
   git commit -m "snapshot: baseline before Copilot edit"
   ```

---

## ✏️ EDIT — Controlled Copilot Modification
1. Activate **GitHub Copilot Agent Mode** or Copilot Chat in VS Code.  
2. Instruct Copilot using natural‑language prompts referencing this SOP.  
3. After Copilot proposes changes:
   - Review the diff (`Ctrl+Shift+G` → “Compare Changes” in VS Code).  
   - Accept or reject suggestions manually.  
4. After approval, stage all changes for temporary save:
   ```bash
   git add .
   git commit -m "snapshot: reviewed Copilot proposal before testing"
   ```

---

## 🧷 KEEP — Preserve Stable State
Once the code compiles and runs without errors:
```bash
git add .
git commit -m "snapshot: working build before functional testing"
```
This creates a stable fallback before validation begins.

---

## 🧪 TEST — Validate Functionality
1. Run all unit or functional tests.  
2. Execute manual verification for expected outputs.  
3. For Copilot logic or guardrail changes, validate:  
   - Dry‑run behavior (non‑interactive safe mode).  
   - Expected logs and confirmations appear in sequence.  
4. Only proceed to review once test outcomes meet baseline criteria.

---

## 🔍 REVIEW — Inspect, Compare, and Verify File Integrity
Before committing final code, confirm that **only intentional files** were modified.  
This protects against accidental commits of logs, cache, or compiled files.

```bash
git diff --name-only
```
✅ Confirms exactly which files changed since the last commit.

Example safe transition from REVIEW → COMMIT:
```powershell
git diff --name-only
git add _main.py EXECUTOR.py
git commit -m "feat(isolation): restore two-tier guardrail prompts before lookup; add DEVICE_INFERRED and audit logs"
```
This verification step was standardized after the **Guardrail Prompt Restoration & Audit Logging Update** to ensure full traceability and control.

---

## 💾 COMMIT — Record Verified Changes
1. Use clear, structured commit messages:
   ```bash
   git commit -m "fix: validated Copilot improvement in isolation workflow"
   ```
2. Avoid committing temporary logs or `.pyc` files — commit only reviewed source and documentation changes.

---

## ☁️ PUSH — Publish to Remote Repository
Once the local commit is complete and verified:
```bash
git push
```
Confirms successful synchronization with GitHub and updates project history.

---

## 🏷️ TAG — Version and Snapshot for Rollback
Create versioned checkpoints for stable, verified milestones.

### Examples
**Manual snapshot tag:**
```bash
git tag -a snapshot-post-change -m "Verified Copilot improvement"
git push --tags
```

**Feature-specific tag:**
```bash
git tag v1.3.0-guardrail-restore
git push --tags
```

Use tags as restore anchors — they make rollback, testing, and audits effortless.

---

## 🧠 Let Copilot Learn Your SOP Automatically
1. Create `.github/copilot-instructions.md` containing this entire SOP.  
2. Add `.vscode/settings.json` to load instructions automatically at startup.

**Example settings.json**
```json
{
  "github.copilot.chat.startupCommands": [
    "@copilot-agent Please read .github/copilot-instructions.md and follow all listed SOP steps for any new edits."
  ]
}
```

Each time VS Code launches, Copilot will re‑apply these workflow standards before editing any files.

---

## 🔄 Manual Context Refresh
When you modify your SOP or restructure your repository, refresh Copilot’s context manually:
```
@copilot-agent Please re-read .github/copilot-instructions.md and rebuild project context before continuing.
```
This ensures new rules are respected before Copilot resumes editing.

---

## 📌 Author
**Peter Van Rossum**  
[LinkedIn](https://www.linkedin.com) · [GitHub](https://github.com/SecOpsPete)  
**Version 1.3 · © 2025 SecOpsPete Labs · For educational and research use**


