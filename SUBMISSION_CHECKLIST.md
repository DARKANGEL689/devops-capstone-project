# DevOps Capstone Project - Final Submission Checklist & Artifact Guide

This repository contains the organized submission artifacts for the **DevOps Capstone Project** (IBM / Coursera).

---

## 📌 Submission Options Overview

| Feature | Option 1: AI Graded Submission | Option 2: Peer Graded Submission |
| :--- | :--- | :--- |
| **Grading Speed** | Instant / Automated by AI Autograder | 2–5 days (depends on peer reviews) |
| **Naming Strictness** | **Extremely Strict** (exact file names & extensions) | Moderate (clear screenshots required) |
| **Output File Formats** | Raw text/logs without extensions for some (`rest-create-done`, etc.) | `.jpg` screenshots for most outputs |
| **Best For** | Fast grade turnaround, clean automated verification | If you captured terminal screenshots instead of raw text logs |

---

## 📋 Master Deliverables Checklist (Option 1: AI Graded)

### 1. Public GitHub URLs (Must be public repos)
- [ ] **Item 1:** Public GitHub URL of `README.md` (with project title & GitHub Actions Build badge) *(2 pts)*
- [ ] **Item 2:** Public GitHub URL of `user-story.md` (template in `.github/ISSUE_TEMPLATE/` or `.github/`) *(1 pt)*
- [ ] **Item 7:** Public GitHub URL of `setup.cfg` (nosetests, coverage, flake8, pylint config) *(1 pt)*
- [ ] **Item 21:** Public GitHub URL of `ci-build.yaml` (GitHub Actions workflow) *(4 pts)*
- [ ] **Item 22:** Public GitHub URL of `init.py` / `__init__.py` (Talisman & CORS headers) *(1 pt)*
- [ ] **Item 29:** Public GitHub URL of `Dockerfile` (Docker build instructions) *(2 pts)*

---

### 2. Screenshots (`.png` or `.jpeg` / `.jpg`)
Place these in the `screenshots/` directory:

- [ ] **Item 3:** `Planning-userstories-done.png` — User stories in "New Issues" column *(1 pt)*
- [ ] **Item 4:** `planning-productbacklog-done.png` — Stories listed under "Ice Box" column *(1 pt)*
- [ ] **Item 5:** `planning-labels-done.png` — Stories labeled `Technical Debt` or `Enhancement` *(1 pt)*
- [ ] **Item 6:** `planning-kanban-done.png` — Stories in "Sprint Backlog" *(1 pt)*
- [ ] **Item 8:** `rest-techdebt-done.png` — "Setting up development environment" in "Done" *(1 pt)*
- [ ] **Item 9:** `read-accounts.png` — "Read an account from the service" in "Done" *(1 pt)*
- [ ] **Item 10:** `list-accounts.png` — "List all accounts in the service" in "Done" *(1 pt)*
- [ ] **Item 11:** `update-accounts.png` — "Update an account in the service" in "Done" *(1 pt)*
- [ ] **Item 12:** `delete-accounts.png` — "Delete an account from the service" in "Done" *(1 pt)*
- [ ] **Item 18:** `sprint2-plan.png` — Two new Sprint 2 user stories under Sprint Backlog *(1 pt)*
- [ ] **Item 20:** `ci-kanban-done.png` — CI automation story moved to "Done" *(1 pt)*
- [ ] **Item 24:** `security-kanban-done.png` — Security story moved to "Done" *(1 pt)*
- [ ] **Item 25:** `sprint3-plan.png` — Three user stories added to Sprint 3 Backlog *(1 pt)*
- [ ] **Item 27:** `kube-docker-done.png` — Docker containerization story moved to "Done" *(1 pt)*
- [ ] **Item 28:** `kube-kubernetes-done.png` — Kubernetes deployment story moved to "Done" *(1 pt)*
- [ ] **Item 33:** `cd-pipeline-done.png` — CD pipeline automation story moved to "Done" *(1 pt)*

---

### 3. Command Output / Log Files
Place these in the `outputs/` directory:

- [ ] **Item 13:** `rest-create-done` — cURL command and output for CREATE (POST /accounts) *(2 pts)*
- [ ] **Item 14:** `rest-list-done` — cURL command and output for LIST (GET /accounts) *(2 pts)*
- [ ] **Item 15:** `rest-read-done` — cURL command and output for READ (GET /accounts/{id}) *(2 pts)*
- [ ] **Item 16:** `rest-update-done` — cURL command and output for UPDATE (PUT /accounts/{id}) *(2 pts)*
- [ ] **Item 17:** `rest-delete-done` — cURL command and output for DELETE (DELETE /accounts/{id}) *(2 pts)*
- [ ] **Item 19:** `ci-workflow-done` — Terminal output of successful GitHub Actions workflow steps *(2 pts)*
- [ ] **Item 23:** `security-headers-done` — Complete nosetests output passing with CORS/Talisman *(1 pt)*
- [ ] **Item 26:** `kube-app-output` — JSON response when application runs on port 8080 *(1 pt)*
- [ ] **Item 30:** `kube-images` — Terminal output of `docker images` showing accounts image *(2 pts)*
- [ ] **Item 31:** `kube-deploy-accounts` — Output of `kubectl get all` (deployments, pods, replica sets, svc) *(2 pts)*
- [ ] **Item 32:** `pipelinerun.txt` — Complete logs of Tekton PipelineRun *(5 pts)*

---

## 🛠️ Exact Commands to Generate Output Files (Reference)

If you need to regenerate or verify any output file from your lab environment, use these standard commands:

### REST API cURL Outputs
```bash
# 1. CREATE
curl -i -X POST -H "Content-Type: application/json" -d '{"name":"John Doe","email":"john@example.com","address":"123 Main St","phone_number":"555-1234","date_joined":"2023-01-01"}' http://localhost:8000/accounts > rest-create-done

# 2. LIST
curl -i -X GET http://localhost:8000/accounts > rest-list-done

# 3. READ (replace 1 with your created account ID)
curl -i -X GET http://localhost:8000/accounts/1 > rest-read-done

# 4. UPDATE
curl -i -X PUT -H "Content-Type: application/json" -d '{"name":"John Doe Updated","email":"john_new@example.com","address":"456 Elm St","phone_number":"555-5678","date_joined":"2023-01-01"}' http://localhost:8000/accounts/1 > rest-update-done

# 5. DELETE
curl -i -X DELETE http://localhost:8000/accounts/1 > rest-delete-done
```

### Security & Tests Output
```bash
nosetests -v --with-spec --spec-color > security-headers-done
```

### Kubernetes & Docker Outputs
```bash
# Port 8080 App Output
curl -s http://localhost:8080/ > kube-app-output

# Docker Images Output
docker images > kube-images

# Kubernetes Deployment Info
kubectl get all > kube-deploy-accounts
```

### Tekton Pipeline Logs
```bash
tkn pipelinerun logs --last > pipelinerun.txt
```
