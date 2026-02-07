# Setup Checklist

A quick reference to make sure you have everything ready. See the [main README](./README.md) for detailed instructions.

---

## Software

- [ ] **Git** installed
  - [ ] `git --version` returns a version number
  - [ ] Configured username: `git config --global user.name "Your Name"`
  - [ ] Configured email: `git config --global user.email "your.email@example.com"`

- [ ] **Python 3.10+** installed
  - [ ] `python --version` or `python3 --version` returns 3.10 or higher
  - [ ] `pip --version` or `pip3 --version` works

- [ ] **Docker Desktop** installed and running
  - [ ] `docker --version` returns a version number
  - [ ] `docker compose version` returns a version number
  - [ ] `docker run hello-world` prints "Hello from Docker!"

- [ ] **VS Code** installed (recommended)
  - [ ] Python extension installed
  - [ ] Docker extension installed
  - [ ] GitLens extension installed
  - [ ] Jupyter extension installed

---

## Accounts

- [ ] **GitHub** account created
  - [ ] Verified email address
  - [ ] Can log in at [github.com](https://github.com)

- [ ] **Kaggle** account created
  - [ ] Can log in at [kaggle.com](https://www.kaggle.com)

---

## Quick Verification Commands

Copy and paste these into your terminal to verify your setup:

```bash
echo "=== Git ===" && git --version
echo "=== Python ===" && python3 --version || python --version
echo "=== Pip ===" && pip3 --version || pip --version
echo "=== Docker ===" && docker --version
echo "=== Docker Compose ===" && docker compose version
```

If all commands return version numbers (no errors), you're good to go!

---

## All Set?

Head to the first workshop: **[Git and Docker](../02-git-and-docker/)**