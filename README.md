# Coverage Gate

Enforce a minimum code-coverage threshold on pull requests and fail when coverage drops.

## What it does
Parses a Cobertura `coverage.xml` (or `lcov`/`json` when present), compares the line-rate against `min-coverage`, optionally fails when coverage drops versus the base branch, and posts a PR comment with the result.

## Usage
```yaml
- uses: CodeGero/coverage-gate@v1
  with:
    github-token: ${{ secrets.GITHUB_TOKEN }}
    min-coverage: '80'
    coverage-file: 'coverage.xml'
    fail-on-drop: 'true'
```

## Inputs
| Input | Required | Default | Description |
|---|---|---|---|
| `github-token` | yes | — | Token for posting the coverage comment. |
| `min-coverage` | no | `80` | Minimum allowed line coverage (%). |
| `coverage-file` | no | `coverage.xml` | Path to the coverage report. |
| `fail-on-drop` | no | `true` | Fail the build if coverage drops below the base. |

## Generating the report
```bash
pip install coverage && coverage run -m pytest && coverage xml
```

## License
MIT — free to use. Premium support via [Gumroad](https://kryptorious.gumroad.com/l/jbvet).
