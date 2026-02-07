# Git and Docker

This section covers two foundational tools for modern software development: **Git** for version control and **Docker** for containerization. These skills are essential whether you're working solo or on a team.

---

## Learning Objectives

By the end of this section, you will be able to:

- **Git:**
  - Initialize a repository and track changes to your code
  - Write clear commit messages
  - Create and merge branches
  - Push code to GitHub and collaborate with pull requests
  - Resolve basic merge conflicts

- **Docker:**
  - Understand what containers are and why they're useful
  - Build Docker images from a Dockerfile
  - Run and manage containers
  - Use Docker Compose for multi-container setups

---

## Contents

| File | Description |
|------|-------------|
| [GIT_CHEATSHEET.md](./GIT_CHEATSHEET.md) | Quick reference for common Git commands |
| [DOCKER_CHEATSHEET.md](./DOCKER_CHEATSHEET.md) | Quick reference for common Docker commands |
| [git_basics_lab.ipynb](./git_basics_lab.ipynb) | Hands-on lab: repositories, commits, and basic workflow |
| [git_branching_lab.ipynb](./git_branching_lab.ipynb) | Hands-on lab: branching, merging, and pull requests |
| [dockerizing_lab.ipynb](./dockerizing_lab.ipynb) | Hands-on lab: containerizing an application |
| [demo-app/](./demo-app/) | Sample Python application used in the Docker lab |

---

## Prerequisites

Before starting, make sure you have:

- [ ] Git installed (`git --version`)
- [ ] Docker Desktop installed and running (`docker --version`)
- [ ] A GitHub account
- [ ] A code editor (VS Code recommended)

See the [Getting Started guide](../01-getting-started/) if you need help with setup.

---

## Concepts Overview

### What is Git?

Git is a **version control system**—it tracks changes to your files over time. Think of it like unlimited undo/redo for your entire project, plus the ability to:

- See exactly what changed, when, and by whom
- Work on new features without breaking existing code
- Collaborate with others without overwriting each other's work
- Go back to any previous version of your project

Git is the industry standard. Virtually every software company uses it.

### What is Docker?

Docker lets you package your application and all its dependencies into a **container**—a lightweight, isolated environment that runs the same way everywhere.

**The problem Docker solves:** "It works on my machine" syndrome. Without containers:
- You install Python 3.11, your teammate has Python 3.9
- You're on Windows, the server runs Linux
- You have library version X, production has version Y

With Docker, you define your environment once, and it runs identically on any machine.

---

## Suggested Learning Path

1. **Read the Git Cheatsheet** — Familiarize yourself with the commands
2. **Complete Git Basics Lab** — Practice the fundamentals
3. **Complete Git Branching Lab** — Learn collaboration workflows
4. **Read the Docker Cheatsheet** — Understand container concepts
5. **Complete Dockerizing Lab** — Containerize the demo application

---

## External Resources

### Git

- [Pro Git Book](https://git-scm.com/book/en/v2) — Free, comprehensive guide (Chapters 1-3 cover the essentials)
- [Learn Git Branching](https://learngitbranching.js.org/) — Interactive visual tutorial
- [GitHub Skills](https://skills.github.com/) — Hands-on courses from GitHub
- [Oh Shit, Git!?!](https://ohshitgit.com/) — How to fix common Git mistakes

### Docker

- [Docker Getting Started Guide](https://docs.docker.com/get-started/)
- [Docker Curriculum](https://docker-curriculum.com/) — Beginner-friendly tutorial
- [Play with Docker](https://labs.play-with-docker.com/) — Practice Docker in your browser
- [Fireship: Docker in 100 Seconds](https://www.youtube.com/watch?v=Gjnup-PuquQ) — Quick video overview

---
