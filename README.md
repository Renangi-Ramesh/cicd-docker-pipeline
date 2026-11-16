# Dockerized Python CI/CD Pipeline (Learning Copy)

This repository is an imported learning copy of an open-source example. It is retained for study and hands-on experimentation; it should not be presented as an entirely original project.

## Original source and attribution

- Original repository: https://github.com/Hacker3S/cicd-docker-pipeline
- Original author: Shawn Sreeju Sampath (Hacker3S)
- Original licence: MIT — see [LICENSE](LICENSE) if present in the source history/repository.

Please review the original repository and its licence before redistributing or publishing modifications.

## What the example demonstrates

- Python Flask application and pytest tests
- Docker image build
- GitHub Actions workflow
- Docker Hub image publishing using repository secrets
- Container smoke test against a health endpoint

## Run locally

```bash
python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
python app.py
```

Run tests:

```bash
pytest -v
```

Run with Docker:

```bash
docker build -t ci-cd-learning-app .
docker run --rm -p 5000:5000 ci-cd-learning-app
curl http://localhost:5000/health
```

## GitHub Actions configuration

The workflow in `.github/workflows/ci-cd.yml` expects these repository Actions secrets:

- `DOCKERHUB_USERNAME`
- `DOCKERHUB_TOKEN`

Do not add credentials directly to workflow files. Review the workflow and configure secrets before enabling image publishing. The deployment job in this example runs a container smoke test on the GitHub-hosted runner; it is not a deployment to an AWS EC2 instance.

## Current status

This is a study copy. I have added repository hygiene rules, but the tracked virtual environment/cache content still needs removal and the workflow has not been verified in this account. Do not treat the pipeline as passing until you run it from the Actions tab and review its logs.

## Learning goals

- Understand test → build → publish → smoke-test stages
- Practice GitHub Actions job dependencies and secrets
- Extend the workflow with a properly secured AWS deployment after validating the base pipeline

---
Maintained as a learning copy by Ramesh Renangi. Original project credit remains with Shawn Sreeju Sampath / Hacker3S.
