# Bie Daalt 14 — Integration & API Testing

## Overview
This repository contains Lab 14 for **Integration & API Testing** using:

- Postman Collection
- Postman Environment Variables
- Pre-request Script
- Test Scripts
- Newman CLI
- GitHub Actions CI

## Selected API
**JSONPlaceholder**

Base URL:

```text
https://jsonplaceholder.typicode.com
```

JSONPlaceholder is a free fake REST API for testing and prototyping. It supports GET, POST, PUT/PATCH, DELETE behavior without authentication.

## Repository Structure

```text
bie-daalt-14/
├── README.md
├── partA/
│   ├── SETUP.md
│   └── screenshot.png
├── postman/
│   ├── collection.json
│   ├── env.dev.json
│   └── env.ci.json
├── .github/
│   └── workflows/
│       └── api-tests.yml
├── reports/
│   └── api.html
└── REFLECTION.md
```

## Requirements Covered

- 8+ requests
- Happy GET
- GET by ID
- POST create
- PUT update
- PATCH update
- DELETE
- Error / negative case
- Chained request using variable from previous response
- 15+ assertions
- 5+ assertion types
- 1+ pre-request script
- Newman local execution
- GitHub Actions workflow

## How to Run Locally

Install Newman:

```bash
npm install -g newman newman-reporter-htmlextra
```

Run the collection:

```bash
newman run postman/collection.json -e postman/env.dev.json
```

Generate HTML report:

```bash
mkdir -p reports
newman run postman/collection.json -e postman/env.dev.json \
  --reporters cli,htmlextra \
  --reporter-htmlextra-export reports/api.html
```

## GitHub Actions

The workflow file is located at:

```text
.github/workflows/api-tests.yml
```

It runs Newman automatically on:

- push
- pull_request

The CI workflow also uploads the test report as an artifact.

## Environment Variables

`baseUrl` is defined in both:

```text
postman/env.dev.json
postman/env.ci.json
```

No real token or secret is used because JSONPlaceholder does not require authentication.

## Important Note

Before submitting, replace `partA/screenshot.png` with your own screenshot from Postman showing the first successful request.

Also make sure your GitHub repository has:

- At least 8 commits
- Commits across at least 3 different days
- At least 1 successful green GitHub Actions run
