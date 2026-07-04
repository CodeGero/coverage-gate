# Coverage Gate — Enforce Code Coverage

[![Marketplace](https://img.shields.io/badge/Marketplace-coverage--gate-green)](https://github.com/marketplace/actions/coverage-gate)
[![Version](https://img.shields.io/badge/version-1.0.0-green)](https://github.com/CodeGero/coverage-gate/releases)

**Enforce coverage thresholds on every PR.** Fail if coverage drops below your minimum.

---

## Quick Start

```yaml
- uses: CodeGero/coverage-gate@v1
  with:
    github-token: ${{ secrets.GITHUB_TOKEN }}
    min-coverage: 80
```

## How It Works

1. Reads your coverage report (coverage.xml, .coverage, or coverage.json)
2. Extracts the overall coverage percentage
3. Fails the build if coverage drops below your threshold
4. Posts a PR comment with the coverage change (premium)

## Full CI Config

```yaml
name: Test & Coverage
on: [pull_request]
jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - run: pip install pytest pytest-cov
      - run: pytest --cov=. --cov-report=xml
      - uses: CodeGero/coverage-gate@v1
        with:
          github-token: ${{ secrets.GITHUB_TOKEN }}
          min-coverage: 80
```

## Inputs

| Input | Default | What it does |
|-------|---------|-------------|
| `github-token` | *required* | For PR comments |
| `min-coverage` | `80` | Minimum coverage % |
| `coverage-file` | `coverage.xml` | Path to report |
| `fail-on-drop` | `true` | Fail if coverage drops |

## Premium

https://kryptorious.gumroad.com/l/jbvet — Historical trends, PR diff comments, Slack alerts.

MIT License
