# 🧠 AI Agent Improvement / Testing Methodology  

## 🧩 Overview  
This methodology provides a complete, structured SOP for AI agent improvements using **GitHub Copilot Pro** with **GPT‑5.0**, based on **Josh Madakor’s Cyber Range Baseline AI Agent Model**.  

**Workflow:**  
### PLAN → APPROVAL → EDIT → TEST → REVIEW & COMMIT → PUSH → TAG  

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

## 🧠 PLAN — Define the Objective  
1. Identify what change is being introduced (guardrail, prompt enforcement, etc.).  
2. Record rationale in issues or dev notes.  
3. Ensure Copilot understands project scope.  

---

## ✅ APPROVAL — Confirm Readiness 

Before initiating any Copilot-assisted modification or edit phase, verify that the repository is in a **clean, stable state**.  
This ensures a reliable rollback point and maintains full traceability throughout your workflow.

---

### 🧭 Context Validation (Copilot Initialization)

Before proceeding with baseline verification, ensure that **GitHub Copilot’s project context** is properly initialized.  
This step ensures that Copilot follows your structured workflow rules during the upcoming edit session.

Create or confirm the presence of this file inside your `.github` directory:

**`.github/copilot-instructions.md`**
```markdown
# ⚙️ Copilot Agent Instructions

These instructions tell GitHub Copilot how to behave in this project.  
They are safe to load automatically — nothing here edits your files by itself.

---

## 🧠 1. Read-Only Context Scan (Automatic)

@copilot-agent  
Before doing any code edits, scan all files in this workspace **in read-only mode**.

Your goal is to understand how the project is structured — not to change anything.

During the scan:
- Look at all Python modules and what they do  
- Note any configuration or JSON files  
- Read the `.github` folder for context  
- Identify the project’s main entry point(s)

After scanning, summarize:
- Major modules and their purposes  
- Important configuration files  
- How modules depend on one another  

Then respond with:  
> “Context loaded successfully. Ready for safe operations.”

---

## ⚙️ 2. Standard Behavior Rules

- Always confirm a **safe snapshot commit** before making code changes.  
- Propose a **clear commit message** before applying edits.  
- Never modify more than one file at a time unless I confirm.  
- Wait for explicit approval before running any `git` commands.  
- Treat this as part of an **AI Threat-Hunting Agent** codebase — be precise and auditable.  
- Follow **PEP 8**, preserve inline comments, and keep docstrings concise.  
- Use **read-only analysis first**; perform edits only after I approve.  
- Summarize planned changes clearly before executing them.

```

### 🔁 3. Reload Command (Manual Use)

When modifying SOP or repo structure:

```bash
@copilot-agent Please re-read .github/copilot-instructions.md and rebuild project context before continuing.
```

This ensures Copilot always reloads your latest workflow context before editing.

### 🧩 Repository Verification

**1. Review repository status:**
```bash
git status
```
Confirm that there are no untracked or unintended edits. The working directory should be clean before proceeding.

**2. Create a pre-edit snapshot for rollback safety:**
```bash
git add .
git commit -m "snapshot: baseline before Copilot edit"
```
This snapshot captures the last verified baseline — serving as a restore point in case Copilot-generated or manual edits cause instability.

---

### 🎯 Key Goals During APPROVAL

- ✅ Verify repo integrity and cleanliness before entering edit mode.  
- 🧠 Preserve a rollback-ready snapshot that can be restored safely if needed.  
- 🧩 Maintain an unbroken version history consistent with your structured workflow.  
- 📘 Ensure all baselines are tagged or referenced clearly for later review or comparison.  
- 🧭 Confirm Copilot context is active and synchronized with `.github/copilot-instructions.md`.  

---

## ✏️ EDIT — Controlled Copilot Modification

Use **Copilot Agent Mode** or **Copilot Chat** in VS Code to guide intelligent code changes through natural‑language prompts aligned with this SOP. This phase emphasizes **controlled, human‑supervised modification** — where Copilot acts as an assistant, *not* an autonomous editor.

### 🧠 **How the EDIT Phase Works**

I use the **browser version of ChatGPT** to craft clear, natural-language prompts that align with my **planning objectives**, then paste them directly into **GitHub Copilot** inside VS Code. This step is strictly **planning-driven**, not coding — in accordance with the SOP file Copilot reads during the **APPROVAL** stage. After each edit cycle is *kept* (snapshot preserved), I manually instruct Copilot to **re-read** the `.github/copilot-instructions.md` file to refresh its operational context.  

**The process involves an iterative rhythm of:**
> ✏️ **Prompt → 🔍 Review → 💾 Keep → ⏭️ Proceed**

Copilot applies changes in small, controlled phases, allowing for multiple rounds of review and verification before moving forward.  
This ensures every modification remains **auditable, reversible, and intentional** within the Agentic AI workflow.

---

### 🧭 **Where to Review Changes**

You can review changes in **VS Code** or the **terminal**, but the goal here isn’t deep Git control — it’s simply to confirm that Copilot’s proposed edits make sense and don’t introduce errors.

#### 🧩 In VS Code (Recommended)
- Open the **Source Control** sidebar (`Ctrl + Shift + G`).  
- Click each modified file to view the **before/after diff**.  
- Read through the changes from top to bottom.  
- If something looks off, undo or edit it manually.  
- When the file looks correct, **save your work**.

#### 💻 In the Terminal (Optional Quick Check)
Use these commands if you prefer verifying file changes from the terminal:
```bash
git status           # Shows which files changed
git diff             # Shows what changed inside those files
```
---

### 🧪 Pre-Review Safety Checks

Before accepting any Copilot proposal or staging changes:

1. **Confirm only intended files show as modified**
   ```bash
   git status
   ```
2. **Filter out noise** (pyc, logs, cache). Ensure `.gitignore` includes:
   ```
   __pycache__/
   *.pyc
   logs/
   .pytest_cache/
   .venv/
   .DS_Store
   ```

---

### 🔍 Review and Validation Workflow

After Copilot proposes changes, review the updated file directly in **VS Code’s main editor**.  
You do **not** need to stage individual code blocks — focus instead on confirming that the overall logic, comments, and structure align with your intent.

1. **Read through the modified file** from top to bottom.  
2. **Confirm Copilot’s summary or rationale** matches what you requested.  
3. **Undo any unintended changes** using `Ctrl+Z` or the file’s history panel.  
4. **KEEP and run** the file once to ensure syntax and behavior are stable.  
5. When satisfied, take a **snapshot** (`git add . && git commit -m "snapshot: reviewed Copilot proposal"`) before testing.

> 💡 *The focus here is review and validation — not granular code staging.*  
> The goal is to confirm that Copilot’s modifications are safe, purposeful, and aligned with your AI Agent objectives.


### 🧠 Edit Principles

Each change should be:
- **Clearly explained** by Copilot (ask it to summarize its plan and expected effects).
- **Focused** on a single logical improvement or bug fix.
- **Reviewed manually** for correctness, security, and adherence to project conventions.
- **Traceable** — rationale captured in commit message or inline comment where helpful.

---

## 🧪 **TEST — Validate Functionality (Query-Based AI Testing)**

This phase confirms that the AI Agent produces expected and consistent results in response to natural-language queries.  
The focus here is *practical functional testing* — verifying that your agent correctly interprets, processes, and responds according to design.

**Typical workflow:**
```bash
# Run the AI Agent interactively
python _main.py

# Enter representative test queries
> "I'm worried that brute force logon attempts have occurred on [DEVICE_NAME] recently."
> "Check sign-ins for john.smith@example.com and the IP 45[.]76[.]122[.]108 in the last 24 hours."
> "I am concerned that unauthorized logon attempts have tried to access [DEVICE_NAME] in the last many days from impossible travel location."
```

**Key validation points:**
- ✅ Confirm the agent executes the correct internal logic paths for each query.  
- 🧠 Verify outputs align with expected structure (e.g., JSON format, console output, or log entries).  
- 🔍 Inspect logs for errors, latency spikes, or unintended responses.  
- 🧩 Continue only after responses are validated against expected behavior and confidence logic.

**Example prompt validation checklist:**
- “Does the model respond to malformed or ambiguous input gracefully?”  
- “Are the results consistent with the intended time-window and confidence parameters?”  
- “Do structured outputs match your defined schema or formatting conventions?”
---

## 💾🔍 REVIEW & COMMIT — Final Verification and Commit

This phase represents the **culmination of the AI Agent improvement workflow** — where verified, intentional changes are finalized and recorded into version control. After completing testing and confirming that all Copilot-assisted modifications behave as intended, this step ensures the repository reflects a **clean, auditable, and logically consistent state**.

---

### 🧭 Purpose

The goal of REVIEW & COMMIT is to perform one last **structured audit** before officially writing changes to the project history.  
This is where you pause to confirm that every change introduced since your last baseline serves a clear purpose, meets your planning objectives, and preserves stability.  
Unlike previous snapshot phases, this is your **final, authoritative commit** — the version that becomes part of your permanent Git history.

---

### 🧩 Typical Workflow

```bash
# 1. Review all modifications made since the last verified snapshot
git diff

# 2. Stage only the verified, intentional files
git add .

# 3. Confirm staged changes are correct and contain no noise or temporary files
git diff --cached

# 4. Perform the official commit with a descriptive, action-oriented message
git commit -m "feat: finalized Copilot improvements and verified build integrity"
```

---

### 🔍 Manual Verification Checklist

Before performing the commit, confirm the following:

- ✅ **Functional Validation** — All tests have passed, and the AI Agent performs as expected.  
- 🧠 **Intent Verification** — Each file modified directly relates to your planned improvement (no stray changes).  
- 🔍 **Repository Cleanliness** — Ensure no `.pyc`, `.log`, `__pycache__/`, `.pytest_cache/`, or environment-specific artifacts remain.  
- 🧩 **Documentation Consistency** — Confirm that README, comments, or inline docstrings reflect the latest state of the project.  
- 🧾 **Commit Clarity** — The message should describe *what* changed and *why*, following a consistent convention (e.g., `feat:`, `fix:`, `refactor:`).

---

### 🧠 Example Commit Message Guidelines

Use descriptive, plain-language commit messages that clearly capture what was verified and why it matters.  
You don’t need to follow developer prefixes like `feat:` or `fix:` — just make the purpose and scope clear.

**Examples:**
| Type | Example |
|------|----------|
| `snapshot:` | `snapshot: verified Copilot improvement to input validation sequence` |
| `update:` | `update: reviewed and stabilized AI Agent workflow after testing` |
| `docs:` | `docs: updated SOP section for REVIEW & COMMIT phase` |
| `security:` | `security: validated input handling and confirmed guardrail enforcement` |
| `config:` | `config: adjusted environment settings and re-verified Copilot context` |

> 💡 Tip: Think of each commit message as an **audit log entry** — it should tell the story of *why* this version exists.

For the record, developer-style commit messages would look something like this:

| Type | Example |
|------|----------|
| `feat:` | `feat: integrated validated Copilot logic for input guardrails` |
| `fix:` | `fix: resolved context refresh timing issue in Copilot agent loop` |
| `refactor:` | `refactor: reorganized agent validation flow for clarity and maintainability` |
| `docs:` | `docs: updated SOP references and agentic workflow instructions` |


---

### 🎯 Key Goals During REVIEW & COMMIT

- ✅ Confirm the project compiles, runs, and behaves as expected post-edit.  
- 🧠 Verify that all changes align precisely with planning objectives and Copilot’s intended logic.  
- 🔍 Eliminate any noise or temporary artifacts from the commit scope.  
- 🧾 Preserve auditability with clear, structured commit messages.  
- 📘 Ensure repository integrity and prepare for the **PUSH** and **TAG** phases that follow.

---

### 🏁 Outcome

By the end of the REVIEW & COMMIT phase, your repository represents a **fully verified, production-grade checkpoint** in the AI Agent’s lifecycle.  
This version can be confidently pushed, tagged, and referenced as a **trusted baseline** for future iterations.

---

## ☁️ **PUSH — Publish to Remote Repository**

Once all changes are verified locally and committed, push the updates to your remote repository to synchronize your work with GitHub.

**Typical workflow:**
```bash
# Push committed changes to the remote branch
git push
```

**Key goals during PUSH:**
- ✅ Ensure local commits have passed review and testing.  
- ☁️ Keep the remote repository synchronized with your latest verified state.  
- 🔐 Confirm credentials or SSH keys are correctly configured before pushing.  
- 🧩 Maintain consistency between local and remote history to avoid merge conflicts.

**Purpose:**  
Finalize the workflow cycle by publishing your verified progress. This ensures your GitHub repository remains a reliable, up-to-date reflection of all validated development activity.

---
### 🏷️ **TAG — Version and Snapshot for Rollback**

Tagging creates immutable reference points in your repository history, allowing you to easily roll back or reference specific verified milestones.  
Use tags to mark major checkpoints, stable builds, or significant AI Agent improvements.

**Manual snapshot example:**
```bash
git tag -a snapshot-post-change -m "Verified Copilot improvement"
git push --tags
```

**Feature-specific version tag example:**
```bash
git tag v1.3.0-guardrail-restore
git push --tags
```

---

### 🔁 **Restoring from a Snapshot or Tag (Safe Rollback Procedure)**

When rolling back to a previously verified build or snapshot, always restore in a **non-destructive, auditable way.**  
This preserves your Git history while allowing you to recover the known good code state cleanly.

**1. List available snapshots (tags):**
```bash
git tag
```
View all checkpoints you’ve created (e.g., `snapshot-pre-change`, `snapshot-stable-build`, etc.).

**2. Create a new branch from the snapshot:**
```bash
git checkout -b restore-snapshot snapshot-pre-change
```
This pulls the snapshot into a **new working branch**, so your `main` or `master` branch remains untouched.

**3. Verify the code:**
Run your normal validation checks:
```bash
python EXECUTOR.py
```
or  
```bash
pytest
```
Confirm the snapshot runs as expected and that no corruption or dependency drift occurred.

**4. Merge the verified state back into main:**
Once you’re confident the snapshot is stable:
```bash
git checkout main
git merge restore-snapshot
```
This merges the verified build back into your main branch safely.

**5. Push the restored version to GitHub:**
```bash
git push
```
If you tagged this restored state as a new version (e.g., `snapshot-restored-<date>`), push the tags too:
```bash
git push --tags
```

**Key advantages of this approach:**
- Non-destructive (no `--hard` reset).  
- Maintains a full audit trail of what was restored and when.  
- Keeps all history intact and GitHub-safe.  
- Compatible with Copilot Agent Mode and your structured SOP workflow.

---

**Key goals during TAG:**
- ✅ Mark validated project states for future reference or rollback.  
- 🧠 Follow consistent versioning (e.g., `v1.2.3` or `snapshot-post-change`).  
- 📦 Ensure tags correspond to meaningful milestones — not just arbitrary commits.  
- 🔍 Confirm tags are successfully pushed and visible on GitHub under the *Releases* or *Tags* tab.

**Purpose:**  
Tags serve as version anchors, ensuring reproducibility and transparency across development stages. They represent clean, verified checkpoints in the Agentic AI workflow.

---

## 🧩 GitHub Sync Verification 

### Purpose  
To verify that local commits made after edits are properly synchronized with the remote repository (`origin/master`) and reflected on GitHub.

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

## 📌 Author  
**Peter Van Rossum**  
[LinkedIn](https://www.linkedin.com) · [GitHub](https://github.com/SecOpsPete)  
**Version 1.3 · © 2025 SecOpsPete Labs · For educational and research use**  



