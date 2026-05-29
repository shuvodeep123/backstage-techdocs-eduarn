# Help Guide

Welcome to the Payment Service Help Guide.

This document provides troubleshooting steps, setup instructions, operational guidance, and common solutions for developers and DevOps teams working with the Payment Service.

---

# Table of Contents

1. Prerequisites
2. Local Development Setup
3. Running the Service
4. Running TechDocs
5. Common Errors
6. Troubleshooting
7. Deployment Help
8. FAQ
9. Useful Commands
10. Support Information

---

# Prerequisites

Before starting, ensure the following tools are installed:

* Node.js >= 18
* npm >= 9
* Python >= 3.10
* Docker
* Kubernetes CLI (`kubectl`)
* Git

---

# Local Development Setup

## Clone Repository

```bash id="oqgcr0"
git clone https://github.com/company/payment-service.git
```

## Navigate to Project

```bash id="jz6v8f"
cd payment-service
```

## Install Dependencies

```bash id="k6f4hs"
npm install
```

---

# Running the Service

## Start Development Server

```bash id="2ifg3r"
npm run dev
```

## Production Mode

```bash id="m5khh9"
npm start
```

---

# Running Backstage TechDocs

## Create Python Virtual Environment

```bash id="4vjlwm"
python3 -m venv venv
```

## Activate Virtual Environment

### Linux / macOS

```bash id="d2c4rd"
source venv/bin/activate
```

### Windows

```powershell id="m98pvk"
venv\Scripts\activate
```

---

## Install TechDocs Dependencies

```bash id="j4g5b9"
pip install mkdocs-techdocs-core
```

---

## Start Documentation Server

```bash id="1rfjlwm"
mkdocs serve
```

Open browser:

```text id="lzh2vc"
http://127.0.0.1:8000
```

---

# Common Errors

## Error: externally-managed-environment

### Cause

Python system environment is protected by Debian/Ubuntu.

### Solution

Use a virtual environment:

```bash id="g8mjlwm"
python3 -m venv venv
source venv/bin/activate
pip install mkdocs-techdocs-core
```

---

## Error: mkdocs command not found

### Solution

Activate virtual environment first:

```bash id="i7hy1f"
source venv/bin/activate
```

---

## Error: Port 8000 already in use

### Solution

Run on different port:

```bash id="f4dq1n"
mkdocs serve -a 127.0.0.1:9000
```

---

# Troubleshooting

## Documentation Not Loading

Check:

* `mkdocs.yml` exists
* `docs/index.md` exists
* `techdocs-core` plugin installed

---

## Broken Navigation

Verify navigation paths in `mkdocs.yml`.

Example:

```yaml id="zkl1b2"
nav:
  - Home: index.md
  - Help: help.md
```

---

## Build Failures

Run verbose build logs:

```bash id="kq7uv5"
mkdocs build --verbose
```

---

# Deployment Help

## Build Docker Image

```bash id="4e0n7y"
docker build -t payment-service .
```

---

## Run Docker Container

```bash id="f4f7yh"
docker run -p 3000:3000 payment-service
```

---

## Kubernetes Deployment

```bash id="qv0l5m"
kubectl apply -f k8s/
```

---

# FAQ

## Where are docs stored?

Documentation files are stored inside:

```text id="kp1vrf"
docs/
```

---

## How to add new documentation pages?

1. Create new `.md` file inside `docs/`
2. Add navigation entry in `mkdocs.yml`

Example:

```yaml id="n8ep49"
nav:
  - Home: index.md
  - Help: help.md
  - API: api.md
```

---

## How to publish docs to Backstage?

1. Push repository changes
2. Ensure `catalog-info.yaml` contains:

```yaml id="5ulw6w"
annotations:
  backstage.io/techdocs-ref: dir:.
```

---

# Useful Commands

## Install Dependencies

```bash id="mn7y7n"
npm install
```

## Run Tests

```bash id="a0w4p2"
npm test
```

## Build Project

```bash id="5by0r4"
npm run build
```

## Run TechDocs

```bash id="d2uwm9"
mkdocs serve
```

---

# Best Practices

* Keep documentation updated
* Use markdown formatting properly
* Add code examples
* Maintain architecture diagrams
* Keep troubleshooting guides current

---

# Support Information

## Teams

| Team          | Responsibility    |
| ------------- | ----------------- |
| Payments Team | Service ownership |
| DevOps Team   | Infrastructure    |
| Platform Team | Backstage support |

---

# References

* Backstage TechDocs
* MkDocs Documentation
* Kubernetes Documentation
* Docker Documentation

---

# Conclusion

This help guide provides operational and troubleshooting support for developers working with the Payment Service and Backstage TechDocs integration.
