# AI Engineering Learning Project - Setup & Instructions

This guide covers how to set up, activate, and work on this project from any machine (Windows, macOS, or Linux) when pulling/cloning from GitHub.

---

## 1. Prerequisites

Make sure the machine has:
- **Git**: [git-scm.com](https://git-scm.com/)
- **Python 3.10+** (Recommended: Python 3.12+): [python.org](https://www.python.org/)

---

## 2. First-Time Setup on Any New Machine

When cloning this repository to a new computer, the `.venv` folder is intentionally not included (it is ignored by Git). Follow these steps to set up your environment:

### Step 1: Open Terminal in Project Directory
Navigate to your project root folder:
```bash
cd ai-engineering-learn
```

### Step 2: Create a Fresh Virtual Environment
```bash
# Windows / Git Bash / macOS / Linux
python -m venv .venv
```
*(On macOS/Linux you may need `python3 -m venv .venv`)*

### Step 3: Activate the Virtual Environment

- **Windows (Git Bash)**:
  ```bash
  source .venv/Scripts/activate
  ```
- **Windows (PowerShell)**:
  ```powershell
  .\.venv\Scripts\Activate.ps1
  ```
- **macOS / Linux**:
  ```bash
  source .venv/bin/activate
  ```

> **Verification**: When activated, you will see `(.venv)` displayed on the left side of your terminal line.

### Step 4: Install Dependencies
If a `requirements.txt` file exists:
```bash
pip install -r requirements.txt
```

---

## 3. Daily Workflow (Working on the Tutorial)

Every time you open your terminal to continue the tutorial:

1. **Activate the environment**:
   ```bash
   source .venv/Scripts/activate
   ```
2. **Install new packages** as required by your tutorial:
   ```bash
   pip install <package-name>
   ```
3. **Save your dependencies** before committing code:
   ```bash
   pip freeze > requirements.txt
   ```
4. **Deactivate** when finished (optional):
   ```bash
   deactivate
   ```

---

## 4. Git Best Practices

Before pushing code to GitHub, ensure:
- Never commit `.venv/` or `.env` (files containing API keys).
- Always commit `requirements.txt` so other machines know what packages to install.

### Standard Git Workflow:
```bash
# Check changed files
git status

# Stage your code changes and requirements.txt
git add .

# Commit your changes
git commit -m "Add tutorial lesson exercises"

# Push to GitHub
git push origin main
```

---

## 5. Troubleshooting Common Git Bash & Windows Issues

### Issue: `python3: command not found` or redirects to Microsoft Store
On Windows, Python installs as `python.exe` by default. In Git Bash, make sure your `~/.bashrc` includes:
```bash
export PATH="/c/Users/$USER/AppData/Local/Programs/Python/Python312:/c/Users/$USER/AppData/Local/Programs/Python/Python312/Scripts:$PATH"
alias python3="python"
alias pip="python -m pip"
```
Reload config:
```bash
source ~/.bashrc
```

### Issue: PowerShell execution policy error when activating venv
If PowerShell displays `running scripts is disabled on this system`, run:
```powershell
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser
```
Then run `.\.venv\Scripts\Activate.ps1` again.
