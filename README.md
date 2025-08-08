# 🗂️ Git Version Control Workflow

---

## 📌 Overview

This project demonstrates the implementation of Git best practices in a DevOps context. It covers initializing a Git repository, creating and managing multiple branches (`main`, `dev`, `feature`), committing changes with meaningful messages, using pull requests to merge feature branches safely, tagging stable releases, and automating YAML validation using GitHub Actions.

---

## 🛠️ Tech Stack

| Tool          | Purpose                                  |
|---------------|------------------------------------------|
| Git           | Version control and branching            |
| GitHub        | Remote repo + pull request workflows     |
| Kubernetes    | Container orchestration                   |
| YAML          | Manifest configuration format             |
| GitHub Actions| CI automation for YAML validation        |

---

## ⚙️ Project Structure & Workflow

### Branching Strategy

- `main`: Stable production-ready code
- `dev`: Development integration branch
- `feature/add-ingress`: Feature branch for ingress resource

### YAML Manifests

Located in the `manifests/` directory:

- `namespace.yaml`: Defines Kubernetes namespace  
- `deployment.yaml`: Deploys NGINX pods  
- `service.yaml`: Exposes NGINX as a service  
- `ingress.yaml`: Adds ingress for routing traffic  

---

## 🔁 Git Workflow Summary

| Step | Git Command(s) | Purpose                                      |
|-------|----------------|----------------------------------------------|
| 1️⃣    | `git init`<br>`git remote add origin`       | Initialize repo and connect to GitHub         |
| 2️⃣    | `git add .`<br>`git commit -m`               | Stage and commit files                         |
| 3️⃣    | `git branch -M main`<br>`git checkout -b dev`<br>`git checkout -b feature/add-ingress` | Create & switch between branches               |
| 4️⃣    | `git push -u origin <branch>`                 | Push branches to GitHub                        |
| 5️⃣    | Pull Request (via GitHub UI)                   | Merge feature branches into dev, then main    |
| 6️⃣    | `git tag -a v1.0 -m "First release"`<br>`git push origin v1.0` | Tag stable release and push tag                |
| 7️⃣    | `.gitignore` file                              | Exclude temp/log files                          |
| 8️⃣    | GitHub Action (YAML Lint)                      | Automate YAML syntax validation                 |

---

## 🧠 Git Concepts in DevOps

| Concept         | Command / Action                  | Why It’s Used in DevOps                      |
|-----------------|---------------------------------|---------------------------------------------|
| Branching       | `git checkout -b branch-name`   | Isolate features or fixes                    |
| Pull Requests   | GitHub UI → Compare & Merge      | Enable code review and safe merges           |
| Tagging         | `git tag -a v1.0`               | Mark stable releases for CI/CD pipelines     |
| `.gitignore`    | List patterns like `*.log`, `*.tmp` | Keep repository clean and portable          |
| GitHub Actions  | Workflow `.github/workflows/validate-yaml.yml` | Auto-check YAML syntax on every push        |
| Collaboration   | Merging via PRs                 | Simulate team workflow with peer reviews    |

---

## 🧪 How to Reproduce This Project

```bash
# Initialize repo and add remote
git init
git remote add origin git@github.com:<your-username>/<repo-name>.git

# Add files and commit
git add .
git commit -m "Initial commit with Kubernetes manifests"

# Create branches and push
git branch -M main
git push -u origin main
git checkout -b dev
git push -u origin dev
git checkout -b feature/add-ingress
git push -u origin feature/add-ingress

# Tag release and push tag
git checkout main
git tag -a v1.0 -m "First release with NGINX deployment"
git push origin v1.0

```

## 📁 Project Directory Structure

```

K8sDeploymentManifests-DevOpsTask4/
├── manifests/
│   ├── namespace.yaml
│   ├── deployment.yaml
│   ├── service.yaml
│   └── ingress.yaml
├── docs/
│   └── task\_documentation.md
├── .github/
│   └── workflows/
│       └── validate-yaml.yml
├── .gitignore
├── README.md

```


## ⚙️ GitHub Actions CI

A GitHub Action was set up to validate all YAML files in the repo to catch syntax errors early.

**File:** `.github/workflows/validate-yaml.yml`

```yaml
name: Validate YAML

on:
  push:
    paths:
      - '**/*.yaml'
      - '**/*.yml'

jobs:
  yaml-lint:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - name: Install yamllint
        run: sudo apt-get install -y yamllint
      - name: Lint YAML files
        run: yamllint .
```

---

## 🧠 What I Learned

* Creating and managing multiple Git branches in a structured workflow
* How to use pull requests for merging and collaboration
* Writing and organizing Kubernetes manifests
* Tagging releases for version control
* Automating YAML validation with GitHub Actions
* Importance of `.gitignore` in preventing unwanted files in version control
* Real-world DevOps project structure using Git & GitHub

---

## ✅ Task Checklist

* [x] Initialized and pushed Git repo
* [x] Created `main`, `dev`, and feature branches
* [x] Committed Kubernetes manifests
* [x] Used pull requests for merging branches
* [x] Tagged first release as `v1.0`
* [x] Added a `.gitignore` file
* [x] Created GitHub Action for YAML validation
* [x] Documented all steps in `docs/task_documentation.md`
* [x] Added `README.md`

---
