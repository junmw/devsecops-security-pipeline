# DevSecOps Security Pipeline

An automated security pipeline designed to run continuous security tests directly inside your development workflow, using GitHub Actions to intercept leaks and scan for vulnerabilities.

### Repository Structure

*   **.github/workflows/**: Automated audit workflows (`secrets_scan.yaml`, `security.yaml`).
*   **app.py**: Primary Python test target application.
*   **Dockfile**: Container configuration.

### DevSecOps Automated Guardrails

1. **Secrets & Credentials Leaks (secrets_scan.yaml)**: Uses **Gitleaks** to catch exposed API keys and tokens across the git history.
2. **Static Vulnerability Scanning (security.yaml)**: Uses **Aqua Security Trivy** for SAST and SCA, failing the build on Critical or High severity flaws.

### Getting Started & Local Emulation

*   **Prerequisites**: GitHub account with Actions enabled; optional local Docker.
*   **Local Initialization**: Clone the repo, build via `docker build -f Dockfile -t devsecops-pipeline-app .`, and run on port 5000.
