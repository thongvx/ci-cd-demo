# ci-cd-demo

Flask app + Calculator module with a CI/CD pipeline on a GitHub Self-hosted Runner.

Pipeline (`.github/workflows/ci-cd.yml`), triggered on every push:

1. **Code Quality Check** – flake8
2. **Run Unit Tests** – pytest + coverage (uploaded as `coverage-report` artifact)
3. **Build Docker Image** – `ci-cd-demo:latest`
4. **Deploy to localhost** – container `python-app` on port 5001 
5. **Build Summary**

## Run locally

```bash
python3 -m venv .venv
.venv/bin/pip install -r requirements.txt -r requirements-dev.txt
.venv/bin/flake8 app.py src/ tests/ --max-line-length=120
.venv/bin/python -m pytest tests/ -v
```

Runner machine requirements: `python3`, Docker (daemon running), `curl`.
