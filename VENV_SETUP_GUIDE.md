# Virtual Environment Setup Guide for Building LLM Applications

## What is a Virtual Environment?

A Python virtual environment is an isolated Python installation on your system. It allows you to:
- Install packages specific to a project without affecting your system Python
- Keep different projects' dependencies separate
- Avoid version conflicts between projects
- Maintain reproducibility across different machines

## Why Use Virtual Environments?

When you install packages globally, they go into your system Python. If two projects need different versions of the same package, you'll have conflicts. Virtual environments solve this by creating isolated "sandboxes" for each project.

## Creating and Managing Virtual Environments

### Windows (CMD)

**Create a virtual environment:**
```cmd
python -m venv env_chXX
```

**Activate the virtual environment:**
```cmd
.\env_chXX\Scripts\activate
```

**Deactivate the virtual environment:**
```cmd
deactivate
```

### Windows (PowerShell)

**Create a virtual environment:**
```powershell
python -m venv env_chXX
```

**Activate the virtual environment:**
```powershell
.\env_chXX\Scripts\Activate.ps1
```

**Deactivate the virtual environment:**
```powershell
deactivate
```

### macOS / Linux (Bash/Zsh)

**Create a virtual environment:**
```bash
python -m venv env_chXX
```

**Activate the virtual environment:**
```bash
source ./env_chXX/bin/activate
```

**Deactivate the virtual environment:**
```bash
deactivate
```

---

## Chapter-Specific Setup

Replace `XX` with the chapter number (01, 02, 03, etc.).

### Chapter 1

```bash
# Windows CMD/PowerShell
python -m venv env_ch01
.\env_ch01\Scripts\activate

# macOS/Linux
python -m venv env_ch01
source ./env_ch01/bin/activate
```

### Chapter 2

```bash
# Windows CMD/PowerShell
python -m venv env_ch02
.\env_ch02\Scripts\activate

# macOS/Linux
python -m venv env_ch02
source ./env_ch02/bin/activate
```

### Chapter 3

```bash
# Windows CMD/PowerShell
python -m venv env_ch03
.\env_ch03\Scripts\activate

# macOS/Linux
python -m venv env_ch03
source ./env_ch03/bin/activate
```

### Chapter 4

```bash
# Windows CMD/PowerShell
python -m venv env_ch04
.\env_ch04\Scripts\activate

# macOS/Linux
python -m venv env_ch04
source ./env_ch04/bin/activate
```

---

## Switching Between Environments

### To switch from one environment to another:

**Step 1: Deactivate the current environment**
```bash
deactivate
```

**Step 2: Activate the new environment**

Windows CMD/PowerShell:
```cmd
.\env_chXX\Scripts\activate
```

macOS/Linux:
```bash
source ./env_chXX/bin/activate
```

---

## Installing Packages

Once your virtual environment is activated (you should see `(env_chXX)` in your terminal prompt), install packages using:

```bash
pip install package_name
```

For example, to install groq:
```bash
pip install groq
```

---

## Using Venvs in Positron

After activating a virtual environment in the terminal, you must also select it in Positron:

1. Click the Python interpreter selector in the bottom-right corner
2. Select "Enter interpreter path" or look for your venv in the list
3. Browse to `./env_chXX/bin/python` (macOS/Linux) or `./env_chXX/Scripts/python.exe` (Windows)
4. The notebook kernel will use this environment for all code execution

---

## Checking Your Active Environment

**Verify which Python is active:**
```bash
which python          # macOS/Linux
where python          # Windows
```

**Check installed packages:**
```bash
pip list
```

**See the venv directory:**
```bash
echo $VIRTUAL_ENV      # macOS/Linux
echo %VIRTUAL_ENV%     # Windows CMD
$env:VIRTUAL_ENV       # Windows PowerShell
```

---

## Quick Reference

| Task | Windows (CMD) | macOS/Linux |
|------|---------------|------------|
| Create | `python -m venv env_chXX` | `python -m venv env_chXX` |
| Activate | `.\env_chXX\Scripts\activate` | `source ./env_chXX/bin/activate` |
| Deactivate | `deactivate` | `deactivate` |
| Check active | `echo %VIRTUAL_ENV%` | `echo $VIRTUAL_ENV` |

---

## Troubleshooting

### "No module named 'groq'" after installation

This means the notebook kernel is using a different Python environment than where you installed `groq`. You need to:

1. Activate the correct venv in the terminal
2. Install packages there: `pip install groq`
3. Switch the Positron kernel to use that venv (click the Python version in the bottom-right corner)

### Virtual environment not activating

- Check that the path is correct
- On Windows, you may need to enable script execution: `Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser`
- On macOS/Linux, ensure the file has execute permissions: `chmod +x ./env_chXX/bin/activate`
