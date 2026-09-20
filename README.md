# ### DevSecOps Security Pipeline

A robust, automated **DevSecOps Security Pipeline** designed to integrate continuous security testing directly into your software development lifecycle. This repository serves as an automated "Shift-Left" security blueprint, embedding secrets detection and vulnerability scanning gates directly into GitHub Actions. 

### 🚀 Repository Structure

The project currently contains the following core components: 

* **.github/workflows/**: Holds the automated security guardrails that audit code modifications. 

  * **secrets_scan.yaml**: Dedicated configuration checking for hardcoded credentials and tokens.
  * **security.yaml**: Infrastructure and vulnerability scanner tracking code flaws.
* **app.py**: The primary Python-based application serving as the code asset under test.
* **Dockfile**: The container blueprint configuration utilized to package and deploy the software ecosystem.

### 🛡️ DevSecOps Automated Guardrails

Your security pipeline runs automatically on every push event and leverages industry-standard scanning tools to enforce security gates: 

### 1. Secrets & Credentials Leaks (secrets_scan.yaml)

* **Tool Used:** **Gitleaks** (gitleaks/gitleaks-action@v2)
* **Objective:** Scans the repository to identify and intercept exposed API keys, private certificates, cloud provider tokens, and passwords.
* **Mechanism:** Configured with fetch-depth: 0 to pull the complete, historic git commit timeline, ensuring historical codebase leaks are detected.

### 2. Static Vulnerability Scanning (security.yaml)

* **Tool Used:** **Aqua Security Trivy** (aquasecurity/trivy-action@master)
* **Objective:** Conducts static application security testing (SAST) and software composition analysis (SCA) to check for configuration flaws and out-of-date packages.
* **Mechanism:** Configured with scan-type: 'fs' to inspect the local filesystem and set with a strict exit-code: '1'. This acts as a hard quality gate that intentionally **breaks the build** if any **CRITICAL** or **HIGH** severity flaws are identified.

### ⚙️ Getting Started & Local Emulation

### Prerequisites

* A GitHub account with active repository Actions runner permissions.
* (Optional) Local installation of Docker to build and debug your application environment.

### Local Initialization

To review the core software configuration or test dependencies locally: 

1. Clone the repository: 

bash

git clone https://github.com/junmw/devsecops-security-pipeline.git
cd devsecops-security-pipeline

Use code with caution.
2. Build the local container structure (Note: Ensure your filename matches Dockfile): 

bash

docker build -f Dockfile -t devsecops-pipeline-app .

Use code with caution.
3. Spin up the application container: 

bash

docker run -p 5000:5000 devsecops-pipeline-app

Use code with caution.

### 📝 License

This project is licensed under the MIT License - see the LICENSE file for details.
