# Troubleshooting

Common issues and fixes encountered during setup. If your problem isn't listed here, try searching the error message online or ask for help.

---

## Git Issues

### "git is not recognized" or "command not found: git"

**Cause:** Git isn't installed or isn't in your system PATH.

**Fix:**
- **Windows:** Reinstall Git and make sure to select "Add to PATH" during installation. Then open a **new** terminal window.
- **macOS:** Run `xcode-select --install` to install Command Line Tools.
- **Linux:** Run `sudo apt install git` (Ubuntu/Debian) or `sudo dnf install git` (Fedora).

### "Please tell me who you are" error

**Cause:** Git doesn't know your identity yet.

**Fix:** Run these commands with your information:
```bash
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"
```

### Authentication failed when pushing to GitHub

**Cause:** GitHub no longer accepts password authentication for Git operations.

**Fix:** Set up a Personal Access Token or SSH key:
1. Go to GitHub → Settings → Developer settings → Personal access tokens → Tokens (classic)
2. Generate a new token with `repo` scope
3. Use this token as your password when prompted

Or set up SSH keys: [GitHub SSH Guide](https://docs.github.com/en/authentication/connecting-to-github-with-ssh)

---

## Python Issues

### "python is not recognized" or "command not found: python"

**Cause:** Python isn't installed or isn't in your system PATH.

**Fix:**
- **Windows:** Reinstall Python and check "Add Python to PATH" during installation. Open a **new** terminal.
- **macOS/Linux:** Try `python3` instead of `python`. If that doesn't work, install Python via your package manager.

### `python` runs Python 2.x instead of 3.x

**Cause:** Your system has both Python 2 and Python 3 installed.

**Fix:** Use `python3` explicitly:
```bash
python3 --version
pip3 install package-name
```

### "pip is not recognized" or "No module named pip"

**Cause:** pip isn't installed or isn't in PATH.

**Fix:**
```bash
# Try pip3 first
pip3 --version

# If that doesn't work, install pip
python3 -m ensurepip --upgrade

# Or on Linux
sudo apt install python3-pip
```

### "Permission denied" when installing packages

**Cause:** Trying to install packages globally without admin rights.

**Fix:** Use a virtual environment (recommended) or user install:
```bash
# Option 1: Virtual environment (recommended)
python3 -m venv venv
source venv/bin/activate  # macOS/Linux
venv\Scripts\activate     # Windows
pip install package-name

# Option 2: User install
pip install --user package-name
```

### "No module named venv"

**Cause:** The venv module isn't installed (common on some Linux distributions).

**Fix (Ubuntu/Debian):**
```bash
sudo apt install python3-venv
```

---

## Docker Issues

### "docker: command not found"

**Cause:** Docker isn't installed or Docker Desktop isn't running.

**Fix:**
1. Make sure Docker Desktop is installed
2. Start Docker Desktop (look for the whale icon in your system tray/menu bar)
3. Wait a minute for it to fully start, then try again

### "Cannot connect to the Docker daemon"

**Cause:** Docker Desktop isn't running.

**Fix:**
1. Open Docker Desktop
2. Wait for it to say "Docker is running"
3. Try your command again

### Docker Desktop won't start on Windows

**Cause:** WSL 2 isn't installed or enabled.

**Fix:**
1. Open PowerShell as Administrator
2. Run: `wsl --install`
3. Restart your computer
4. Try starting Docker Desktop again

### "image not found" or "pull access denied"

**Cause:** Typo in image name, or trying to pull a private image.

**Fix:**
- Check the image name for typos
- Make sure you're using the correct image name from Docker Hub
- If it's a private image, log in with `docker login`

### Docker commands are very slow on macOS/Windows

**Cause:** Docker Desktop uses a virtual machine, which adds overhead.

**Fix:** This is somewhat expected, but you can:
- Allocate more resources to Docker (Docker Desktop → Settings → Resources)
- Use smaller base images (e.g., `python:3.11-slim` instead of `python:3.11`)

---

## VS Code Issues

### Extensions not working

**Fix:**
1. Make sure you've installed the extension (check Extensions sidebar)
2. Reload VS Code (Ctrl+Shift+P → "Reload Window")
3. Check if the extension requires additional setup

### Python interpreter not found

**Cause:** VS Code doesn't know which Python to use.

**Fix:**
1. Press `Ctrl+Shift+P` (or `Cmd+Shift+P` on Mac)
2. Type "Python: Select Interpreter"
3. Choose your Python installation or virtual environment

### Terminal uses wrong shell

**Fix:**
1. Press `Ctrl+Shift+P`
2. Type "Terminal: Select Default Profile"
3. Choose your preferred shell

---

## General Tips

### "Permission denied" errors

- **Windows:** Run your terminal as Administrator
- **macOS/Linux:** Don't use `sudo` unless necessary. If you must, understand why.

### Commands work in one terminal but not another

- Changes to PATH require opening a **new** terminal window
- Some installations require a system restart

### Still stuck?

1. Copy the exact error message
2. Search for it online (Stack Overflow usually has answers)
3. Ask for help—include:
   - Your operating system
   - The exact command you ran
   - The complete error message

---

## Useful Links

- [Git Documentation](https://git-scm.com/doc)
- [Python Documentation](https://docs.python.org/3/)
- [Docker Documentation](https://docs.docker.com/)
- [VS Code Documentation](https://code.visualstudio.com/docs)
- [Stack Overflow](https://stackoverflow.com/)
