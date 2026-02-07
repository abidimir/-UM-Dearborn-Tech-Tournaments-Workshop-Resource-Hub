## About This Resource

This repository was created for the **AIC x GDGC Tech Tournament 2026** at the University of Michigan-Dearborn. It's designed to help students build practical technical skills in Git, Docker, backend development, and machine learning—whether you're participating in the tournament or just looking to learn.

The materials are beginner-friendly but move quickly. You don't need prior experience, but you should be comfortable learning new tools independently. Each section includes hands-on labs and links to external resources if you want to go deeper.

**Organized by:**
- *Mir Abidi*
- *Jack Wagner*
- *Sumia Saleh*
- *Husniyah Alam*

---

## Setting Up Your Environment

This guide will help you set up your development environment. By the end, you'll have all the tools needed to work through the workshops and build your own projects.

**Time estimate:** 30-60 minutes (depending on your internet connection and familiarity with installations)

---

## What You'll Need

### Software to Install

| Tool | What it's for | Download |
|------|---------------|----------|
| **Git** | Version control—track changes to your code and collaborate with others | [git-scm.com](https://git-scm.com/downloads) |
| **Python 3.10+** | Programming language we'll use for backend and ML work | [python.org](https://www.python.org/downloads/) |
| **Docker Desktop** | Run applications in containers—consistent environments everywhere | [docker.com](https://www.docker.com/products/docker-desktop/) |
| **VS Code** (recommended) | Code editor with great extensions for Python, Docker, and Git | [code.visualstudio.com](https://code.visualstudio.com/) |

### Accounts to Create

| Service | What it's for | Sign up |
|---------|---------------|---------|
| **GitHub** | Host your code, collaborate on projects | [github.com](https://github.com/join) |
| **Kaggle** | ML competitions and datasets | [kaggle.com](https://www.kaggle.com/account/login?phase=startRegisterTab) |

---

## Installation Guides

### Git

**Windows:**
1. Download the installer from [git-scm.com](https://git-scm.com/downloads)
2. Run the installer—the default options are fine for most users
3. Open a new terminal (Command Prompt or PowerShell) and verify:
   ```bash
   git --version
   ```
   You should see something like `git version 2.43.0`

**macOS:**
1. Open Terminal and run:
   ```bash
   git --version
   ```
2. If Git isn't installed, you'll be prompted to install Command Line Tools—follow the prompts
3. Alternatively, install via [Homebrew](https://brew.sh/): `brew install git`

**Linux (Ubuntu/Debian):**
```bash
sudo apt update
sudo apt install git
git --version
```

After installing, configure your identity (use the email associated with your GitHub account):
```bash
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"
```

---

### Python

**Windows:**
1. Download Python 3.10+ from [python.org](https://www.python.org/downloads/)
2. **Important:** Check the box that says "Add Python to PATH" during installation
3. Open a new terminal and verify:
   ```bash
   python --version
   ```

**macOS:**
1. macOS comes with Python, but it's often outdated. Install a newer version:
   ```bash
   brew install python@3.11
   ```
2. Verify:
   ```bash
   python3 --version
   ```

**Linux (Ubuntu/Debian):**
```bash
sudo apt update
sudo apt install python3 python3-pip python3-venv
python3 --version
```

> **Note for macOS/Linux users:** You may need to use `python3` and `pip3` instead of `python` and `pip`. To check which command works, try both `python --version` and `python3 --version`.

---

### Docker Desktop

1. Download Docker Desktop for your OS from [docker.com](https://www.docker.com/products/docker-desktop/)
2. Run the installer and follow the prompts
3. **Windows users:** You may be prompted to enable WSL 2 (Windows Subsystem for Linux)—follow the instructions provided
4. Start Docker Desktop
5. Open a terminal and verify:
   ```bash
   docker --version
   docker compose version
   ```

> **Heads up:** Docker Desktop must be running for Docker commands to work. You'll see the Docker whale icon in your system tray/menu bar when it's active.

---

### VS Code (Recommended)

1. Download from [code.visualstudio.com](https://code.visualstudio.com/)
2. Install these extensions (click the Extensions icon in the sidebar or press `Ctrl+Shift+X`):
   - **Python** (by Microsoft)
   - **Docker** (by Microsoft)
   - **GitLens** (by GitKraken)
   - **Jupyter** (by Microsoft)

---

## Verify Your Setup

Run these commands to confirm everything is installed correctly:

```bash
# Git
git --version

# Python (try both if unsure)
python --version
python3 --version

# Pip (Python package manager)
pip --version
pip3 --version

# Docker
docker --version
docker compose version
```

### Quick Python Test

Create a simple test to ensure Python and pip work together:

```bash
# Create a test directory
mkdir python-test
cd python-test

# Create a virtual environment
python -m venv venv

# Activate it
# Windows:
venv\Scripts\activate
# macOS/Linux:
source venv/bin/activate

# Install a package
pip install requests

# Test it
python -c "import requests; print('Python is working!')"

# Deactivate when done
deactivate

# Clean up
cd ..
rm -rf python-test
```

### Quick Docker Test

```bash
docker run hello-world
```

You should see a message that starts with "Hello from Docker!"

---

## What's Next?

Once your environment is set up, you're ready to dive into the workshops:

1. **[Git and Docker](../02-git-and-docker/)** — Version control and containerization fundamentals
2. **[APIs and Backend Development](../03-apis-and-backend/)** — Build web APIs with Python
3. **[Machine Learning and Kaggle](../04-machine-learning/)** — Train models and compete on Kaggle
4. **[Presenting Projects](../05-presenting-projects/)** — Communicate your work effectively

---

## Troubleshooting

Having issues? Check the [Troubleshooting Guide](./TROUBLESHOOTING.md) for solutions to common problems.

---

## Additional Resources

- [Git Documentation](https://git-scm.com/doc)
- [Python Official Tutorial](https://docs.python.org/3/tutorial/)
- [Docker Getting Started Guide](https://docs.docker.com/get-started/)
- [VS Code Documentation](https://code.visualstudio.com/docs)