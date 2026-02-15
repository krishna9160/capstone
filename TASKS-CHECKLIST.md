
# Tasks Checklist (33 Tasks → 50 points)

> Replace `krishna5170/capstone` with your repo if different.

## Task 1
Submit: README URL with CI badge
- URL: `https://github.com/krishna5170/capstone/blob/main/README.md`

## Task 2
Submit: `user-story.md` URL
- URL: `https://github.com/krishna5170/capstone/blob/main/user-story.md`

## Task 3–6, 8–12, 18, 20, 24, 25, 27, 28, 33
Submit screenshots from your GitHub **Projects** board:
- Create a Project (Kanban) → add issues from user stories
- Columns: New Issues, Ice Box, Product Backlog, Sprint Backlog, In Progress, Done (or similar)
- Label stories with **Enhancement**/**Technical Debt** where required
- Assign to sprints and add estimates; move cards to Done when achieved
- Filenames must match exactly as requested

## Task 7
Submit: `setup.cfg` URL
- URL: `https://github.com/krishna5170/capstone/blob/main/setup.cfg`
- Contains nosetests, coverage, flake8, pylint configs

## Tasks 13–17 (REST cURL)
Save outputs to files (copy the exact output from terminal):
- `rest-create-done`, `rest-list-done`, `rest-read-done`, `rest-update-done`, `rest-delete-done`

## Task 19
Submit terminal logs for CI success:
- In Actions → a successful run → **View raw logs** → paste into `ci-workflow-done`

## Task 21
Submit: `ci-build.yaml` URL
- URL: `https://github.com/krishna5170/capstone/blob/main/.github/workflows/ci-build.yaml`
- Must include checkout → lint → nosetests (this repo does)

## Task 22
Submit: `app/__init__.py` URL with **Talisman** security headers
- URL: `https://github.com/krishna5170/capstone/blob/main/app/__init__.py`

## Task 23
Submit: `security-headers-done` file content (nosetests output after enabling CORS)
- Run: `nosetests -v > security-headers-done 2>&1`

## Task 26
Submit: JSON printed when launching app on port **8080**
- `curl -s http://127.0.0.1:8080/ > kube-app-output`

## Task 29
Submit: Dockerfile URL
- URL: `https://github.com/krishna5170/capstone/blob/main/Dockerfile`

## Task 30
Submit: `kube-images` content
- `docker images | grep customer-accounts > kube-images`

## Task 31
Submit: `kube deploy-accounts` content
- `kubectl -n customer-accounts get deploy,po,rs,svc -o wide > "kube deploy-accounts"`

## Task 32 (Tekton logs)
- Apply `tekton/` pipeline
- Run a `PipelineRun`
- Capture logs into `pipelinerun.txt`

