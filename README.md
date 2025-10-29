Dev-Sec-Ops Project

Security Scan Report:

📄 DevSecOps Vulnerability Report

Tool: Trivy
Target: newsletter-webapp-backend:latest
Date: July 25, 2025
Candidate: Deep Ochhane
🚨 Summary of Findings:
🔐 OS-Level (Alpine Image):

    4 High-severity OpenSSL vulnerabilities

        CVE-2024-12797: Handshake validation failure

        CVE-2024-6119: DoS via X.509 name checks

    Mitigation Suggestion: Use updated base image (alpine:3.20.3) or OpenSSL patch version.

📦 Node.js Package Vulnerabilities:

    1 Critical:

        CVE-2025-23061 (Mongoose): Search injection

    5 High:

        body-parser, cross-spawn, path-to-regexp, others

    Mitigation Suggestion:

        Upgrade dependencies listed in package.json to recommended secure versions.

        Use tools like npm audit fix or npm-check-updates.

🛠 Action Plan:

    ❗ Flagged CRITICAL issue in Mongoose must be patched in production before public release.

    🟡 For development/testing pipelines, vulnerability reporting can be set to warn only for High but must block on Critical.

✅ What Was Implemented:

    Trivy integrated in GitHub Actions.

    Vulnerability scan gates enabled for image and Dockerfile.

    Workflow fails on CRITICAL vulnerabilities.

    Full transparency using open-source scan tooling.

🧠 Production Hardening Suggestions:

    Use distroless or slim images instead of Alpine.

    Pin package versions in package-lock.json.

    Use SBOM scanning with Trivy or CycloneDX.

    Enable GitHub Dependabot or npm audit CI job.

    🔒 Semgrep detected default root user usage in Dockerfiles.
Fix was intentionally not applied in this project due to runtime dependencies, but flagged for future production hardening.

📌 Semgrep Security Scan Summary

Tool: Semgrep
Findings:

backend/Dockerfile: no USER specified — runs as root.

frontend/Dockerfile: no USER specified — runs as root.
Impact: Running containers as root can lead to container breakout if exploited.
Recommendation: Specify a non-root user via USER instruction in Dockerfile.
Status: Documented. Fix is deferred in this evaluation project.

🔄 Pull Request Workflow Update

We have introduced multiple Pull Request (PR) templates for this repository to improve code review quality and ensure that all required details are provided when raising a PR.

📌 What Changed

Added a .github/PULL_REQUEST_TEMPLATE/ folder in the repo.

Created two separate PR templates:

frontend_pr.md → For UI/UX or client-side changes.

backend_pr.md → For API, database, or server-side changes.

🚀 How It Works

When you create a new Pull Request, GitHub will now show a “Choose a template” dropdown.

You can pick the correct template based on your work:

Frontend PR Template → For UI changes, styling, components, etc.

Backend PR Template → For API, DB schema, server logic, etc.

Fill in the required details before submitting for review.

✅ Action for Team

Always select the correct PR template when creating a PR.

Ensure ClickUp task links and Acceptance Criteria are completed.

This update will help us test how GitHub shows the dropdown template selection on new PRs.

### Now we are ready to check out template:

* it is actually working or not?
* Let's do it.
* testing PR status
  
