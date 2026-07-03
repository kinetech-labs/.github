# Kinetech Labs — GitHub metadata and CI templates

This repository stores GitHub metadata, issue/PR templates, and reusable workflows used across Kinetech Labs projects.

What’s included

- .github/workflows/common-setup.yml — reusable workflow for checkout + Node/Go setup
- .github/workflows/ci.yml — CI workflow (calls `common-setup`, runs lint/test/build depending on project files)
- .github/workflows/security-scan.yml — security scanning (govulncheck for Go, npm audit for Node)
- .github/workflows/code-quality.yml — code-quality checks
- .github/ISSUE_TEMPLATE, CODE_OF_CONDUCT.md, CONTRIBUTING.md, SECURITY.md, etc.

Behavior notes

- Workflows detect project type by the presence of `package.json` (Node/React/Next) or `go.mod` (Go).
- Direct pushes to `main` are blocked by a `guard` job; enable branch protection in repo settings for stronger enforcement.
- Shared setup is implemented as a reusable workflow (`common-setup.yml`) to avoid duplication.

Local testing

You can test actions locally using `act` (https://github.com/nektos/act) or run individual tools locally:

```bash
# Run Go vulnerability check locally (requires Go 1.21+)
go install golang.org/x/vuln/cmd/govulncheck@latest
govulncheck ./...

# Run npm audit for Node projects
npm ci
npm audit --audit-level=moderate
```

Contributing

If you add language-specific steps, prefer updating `common-setup.yml` so callers inherit the change. Keep workflows idempotent and defensive (check for `package.json` / `go.mod` before running language tooling).

Branch protection

To fully prevent direct pushes to `main`, enable branch protection rules in repository settings and require pull requests + status checks.
