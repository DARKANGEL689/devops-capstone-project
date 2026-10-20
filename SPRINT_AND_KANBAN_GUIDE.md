# DevOps Capstone Project: Sprint & Kanban Board Step-by-Step Guide

This guide walks you through setting up GitHub Projects/ZenHub, creating all user stories, taking the required screenshots, and executing the lab commands for **Option 1: AI Graded Submission**.

---

## 🗂️ Overview of Required Screenshots

| Step | Required Screenshot Filename | Description / What to show |
| :--- | :--- | :--- |
| **Lab 1** | `Planning-userstories-done.png` | All initial user stories listed in the **New Issues** column |
| **Lab 1** | `planning-productbacklog-done.png` | User stories moved to the **Ice Box** (Product Backlog) column |
| **Lab 1** | `planning-labels-done.png` | User stories labeled as `Technical Debt` or `Enhancement` |
| **Lab 1** | `planning-kanban-done.png` | Sprint 1 stories moved to the **Sprint Backlog** |
| **Lab 2** | `rest-techdebt-done.png` | "Setting up the development environment" story in **Done** |
| **Lab 2** | `read-accounts.png` | "Read an account from the service" story in **Done** |
| **Lab 2** | `list-accounts.png` | "List all accounts in the service" story in **Done** |
| **Lab 2** | `update-accounts.png` | "Update an account in the service" story in **Done** |
| **Lab 2** | `delete-accounts.png` | "Delete an account from the service" story in **Done** |
| **Lab 3** | `sprint2-plan.png` | The two new Sprint 2 user stories in **Sprint Backlog** |
| **Lab 3** | `ci-kanban-done.png` | "Automate CI checks using GitHub Actions" story in **Done** |
| **Lab 3** | `security-kanban-done.png` | "Add security headers and CORS support" story in **Done** |
| **Lab 4** | `sprint3-plan.png` | The three user stories added to Sprint 3 under **Sprint Backlog** |
| **Lab 4** | `kube-docker-done.png` | "Containerize the service using Docker" story in **Done** |
| **Lab 4** | `kube-kubernetes-done.png` | "Deploy the service to Kubernetes" story in **Done** |
| **Lab 5** | `cd-pipeline-done.png` | "Automate CD deployment with Tekton" story in **Done** |

---

## 🚀 Sprint 1: Planning & REST API

### 1. GitHub Board Setup
1. On GitHub, go to your repository `devops-capstone-project`.
2. Click **Projects** -> **New project** -> Select **Board** template.
3. Configure the following columns:
   - `New Issues`
   - `Ice Box`
   - `Sprint Backlog`
   - `In Progress`
   - `Review/QA`
   - `Done`

### 2. User Stories to Create
Create these issues using the user story template (`user-story.md`):

1. **Title:** `Setting up the development environment`
   - **Label:** `Technical Debt`
2. **Title:** `Create an account in the service`
   - **Label:** `Enhancement`
3. **Title:** `Read an account from the service`
   - **Label:** `Enhancement`
4. **Title:** `List all accounts in the service`
   - **Label:** `Enhancement`
5. **Title:** `Update an account in the service`
   - **Label:** `Enhancement`
6. **Title:** `Delete an account from the service`
   - **Label:** `Enhancement`

### 3. Screenshot Capture Checklist (Sprint 1)
- **`Planning-userstories-done.png`**: When all 6 issues are in the **New Issues** column.
- **`planning-productbacklog-done.png`**: Move all 6 issues into the **Ice Box** column.
- **`planning-labels-done.png`**: Show issues with visible labels `Technical Debt` and `Enhancement`.
- **`planning-kanban-done.png`**: Move Sprint 1 issues into the **Sprint Backlog** column.

---

## ⚡ Sprint 2: CI Pipeline & Security

### 1. New User Stories
Add these 2 stories to your board:
1. **Title:** `Automate CI checks using GitHub Actions`
   - **Label:** `Enhancement`
2. **Title:** `Add security headers and CORS support`
   - **Label:** `Enhancement`

### 2. Screenshot Capture Checklist (Sprint 2)
- **`sprint2-plan.png`**: Show both stories in the **Sprint Backlog**.
- **`ci-kanban-done.png`**: Move "Automate CI checks using GitHub Actions" to **Done**.
- **`security-kanban-done.png`**: Move "Add security headers and CORS support" to **Done**.

---

## 🐳 Sprint 3: Containerization & Kubernetes

### 1. New User Stories
Add these 3 stories to your board:
1. **Title:** `Containerize the service using Docker`
   - **Label:** `Enhancement`
2. **Title:** `Deploy the service to Kubernetes`
   - **Label:** `Enhancement`
3. **Title:** `Create Kubernetes deployment and service manifests`
   - **Label:** `Technical Debt`

### 2. Screenshot Capture Checklist (Sprint 3)
- **`sprint3-plan.png`**: Show all 3 stories in the **Sprint Backlog**.
- **`kube-docker-done.png`**: Move "Containerize the service using Docker" to **Done**.
- **`kube-kubernetes-done.png`**: Move "Deploy the service to Kubernetes" to **Done**.

---

## 🔄 Sprint 4: Tekton CD Pipeline

### 1. New User Story
Add:
1. **Title:** `Automate CD deployment with Tekton`
   - **Label:** `Enhancement`

### 2. Screenshot Capture Checklist (Sprint 4)
- **`cd-pipeline-done.png`**: Move "Automate CD deployment with Tekton" to **Done**.

---

## 📝 Output Files Generation Reference

In your lab terminal, run these commands and save the exact output into your `outputs/` folder:

### 1. REST cURL Outputs
```bash
# Start your service (make run or honcho start or python -m flask run -p 8000)

# CREATE
curl -i -X POST -H "Content-Type: application/json" -d '{"name":"John Doe","email":"john@example.com","address":"123 Main St","phone_number":"555-1234","date_joined":"2023-01-01"}' http://localhost:8000/accounts > rest-create-done

# LIST
curl -i -X GET http://localhost:8000/accounts > rest-list-done

# READ (Account ID 1)
curl -i -X GET http://localhost:8000/accounts/1 > rest-read-done

# UPDATE (Account ID 1)
curl -i -X PUT -H "Content-Type: application/json" -d '{"name":"Jane Doe","email":"jane@example.com","address":"456 Elm St","phone_number":"555-5678","date_joined":"2023-01-01"}' http://localhost:8000/accounts/1 > rest-update-done

# DELETE (Account ID 1)
curl -i -X DELETE http://localhost:8000/accounts/1 > rest-delete-done
```

### 2. CI & Security Outputs
```bash
# CI Workflow Terminal Log
# Copy the full terminal log from GitHub Actions or local flake8 + nosetests run to:
ci-workflow-done

# Security Headers & CORS Test Run
nosetests -v --with-spec --spec-color > security-headers-done
```

### 3. Docker & Kubernetes Outputs
```bash
# Test application running on port 8080
curl -s http://localhost:8080/ > kube-app-output

# Docker Images
docker images > kube-images

# Kubernetes Deployment Status
kubectl get all > kube-deploy-accounts
```

### 4. Tekton Pipeline Output
```bash
tkn pipelinerun logs --last > pipelinerun.txt
```
