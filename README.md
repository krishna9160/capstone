
# Customer Accounts Microservice (Capstone)

![CI](https://github.com/krishna5170/capstone/actions/workflows/ci-build.yaml/badge.svg)

A simple **Customer Accounts** microservice built with **Flask** to satisfy the capstone evaluation tasks:

- RESTful APIs (CRUD for customer accounts)
- **User stories** template (`user-story.md`) and sprint planning guidance
- **CI with GitHub Actions** (linting + **nosetests** + coverage) → status badge above
- **Security headers with Flask-Talisman** and **CORS**
- **Docker** container (exposes port **8080**)
- **Kubernetes** manifests (Deployment/Service/Ingress, port 8080)
- Optional: **Docker publish** workflow to GHCR

> This repo is prepared to let you answer **all 33 tasks**.

---

## Quick Start (Local)

```bash
python3 -m venv .venv && source .venv/bin/activate
pip install -r requirements.txt
export FLASK_ENV=development
python wsgi.py  # Serves on http://127.0.0.1:8080
```

Swagger-like docs are not included; use curl commands below.

Healthcheck:
```bash
curl -s http://127.0.0.1:8080/health
```

---

## API Endpoints
- `POST   /accounts` – Create an account
- `GET    /accounts` – List all accounts
- `GET    /accounts/<id>` – Read an account
- `PUT    /accounts/<id>` – Update an account
- `DELETE /accounts/<id>` – Delete an account
- `GET    /health` – Service health
- `GET    /` – App info (used for Task 26 JSON output)

### Example cURL (for Tasks 13–17)
Save these outputs to the requested files.

```bash
# Create (Task 13 → save to rest-create-done)
curl -s -X POST http://127.0.0.1:8080/accounts   -H 'Content-Type: application/json'   -d '{"name":"Alice","email":"alice@example.com","balance":100.5,"status":"active"}'

# List (Task 14 → rest-list-done)
curl -s http://127.0.0.1:8080/accounts

# Read (Task 15 → rest-read-done) – replace 1 with created id
curl -s http://127.0.0.1:8080/accounts/1

# Update (Task 16 → rest-update-done)
curl -s -X PUT http://127.0.0.1:8080/accounts/1   -H 'Content-Type: application/json'   -d '{"balance":200}'

# Delete (Task 17 → rest-delete-done)
curl -s -X DELETE http://127.0.0.1:8080/accounts/1 -i
```

---

## Tests (nosetests)
```bash
nosetests -v --with-coverage --cover-package=app
```

For Task 23 (security headers + CORS), run:
```bash
nosetests -v > security-headers-done 2>&1
```

---

## Docker
```bash
docker build -t customer-accounts:local .
docker run -p 8080:8080 customer-accounts:local
```
Then visit <http://127.0.0.1:8080/> (Task 26 expects JSON when app launches on port 8080).

---

## Kubernetes
Apply manifests (update image if pushing to GHCR):
```bash
kubectl apply -f kubernetes/namespace.yaml
kubectl apply -f kubernetes/deployment.yaml
kubectl apply -f kubernetes/service.yaml
# Optional ingress if you have an ingress controller
kubectl apply -f kubernetes/ingress.yaml
```

Get details for Task 31:
```bash
kubectl -n customer-accounts get deploy,po,rs,svc -o wide > "kube deploy-accounts"
```

Task 30 (images):
```bash
docker images | grep customer-accounts > kube-images
```

---

## CI (GitHub Actions)
- Workflow file: `.github/workflows/ci-build.yaml`
- Tasks 1, 19, 21 use this workflow.

To produce Task 19 output:
1. Open a successful workflow run → **View raw logs** → copy all
2. Save as a text file named `ci-workflow-done`

---

## Security
- **Flask-Talisman** sets security headers (see `app/__init__.py`).
- **CORS** enabled for all origins (for demo) in `app/__init__.py`.

---

## Planning Artifacts
- **User stories template** in `user-story.md` (Task 2).
- Create a **GitHub Projects (Kanban)** board to manage issues and sprints. Use the screenshot tasks as a checklist:
  - Task 3: move all new issues to **New Issues** then capture
  - Task 4: put selected items in **Ice Box** and capture
  - Task 5: add labels **Technical Debt** / **Enhancement** and capture
  - Task 6: move stories to **Sprint Backlog**, assign to Sprint 1 with estimates and assignees, capture
  - Task 8–12, 18, 20, 24, 25, 27, 28, 33: move relevant stories to **Done** and capture

---

## What to Submit per Task (Checklist)
See the file `TASKS-CHECKLIST.md` for exact, step-by-step instructions and links to generate each artifact.

---

## License
MIT
