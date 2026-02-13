# PXTEAMS

Welcome to the PXTEAMS GitHub organization — the home of all PX Inc repositories.

## Repository Naming Convention

All repositories follow **lowercase kebab-case** with a **product-first** naming pattern.

**Format:** `{product}-{functionality}` or `{category}-{name}`

| Pattern | Example | When to use |
|---|---|---|
| `{product}` | `local-portal` | Main product repo |
| `{product}-{feature}` | `local-portal-zipcode-finder` | Feature scoped to a product |
| `{category}-{name}` | `api-docs`, `frontend-coding-exercise` | Shared or cross-product resources |
| `{name}-demo` | `talkthread-demo`, `publisher-portal-demo` | Demo or proof-of-concept repos |
| `{name}-service` | `verification-service` | Standalone service repos |

**Rules:**

- Always use lowercase kebab-case (`this-format`, never `ThisFormat` or `this_format`)
- Do not prefix with `px-` — all repos are already under the PXTEAMS org
- Product name comes first, then the subfunctionality
- Use descriptive suffixes: `-service`, `-demo`, `-docs`
- Keep names concise

## PR & Commit Conventions

PR titles are recommended to follow the [Conventional Commits](https://www.conventionalcommits.org/) format. This can be enforced via the `PXTEAMS/actions/check-pr-title` action in a workflow.

```
type(scope): description
```

**Allowed types:** `feat`, `fix`, `docs`, `style`, `refactor`, `perf`, `test`, `build`, `ci`, `chore`, `revert`

**Examples:**

```
feat(auth): add SSO login flow
fix(tracking): resolve timeout on batch processing
docs: update API documentation
ci: add SonarCloud analysis step
```

Include the Jira ticket ID in the branch name or commit body to enable automatic linking.

## Shared GitHub Actions

Reusable actions are maintained in the [`actions`](https://github.com/PXTEAMS/actions) repository and referenced as:

```yaml
- uses: PXTEAMS/actions/{action-name}@v1
```

## CI/CD

All repositories should (eventually) use GitHub Actions for CI/CD. Workflows follow these conventions:

- Runner selection defaults to repo-level variable: `${{ vars.RUNNER_GROUP || 'ubuntu-latest' }}`
- Workflows use path-based filtering (via `dorny/paths-filter`) to avoid unnecessary builds in monorepo setups
- Azure authentication uses OIDC (federated credentials), not stored secrets
- Reusable workflows are stored in the respective repo under `.github/workflows/`

## Getting Started

1. Clone the repository you need
2. Check the repo's own `README.md` for setup instructions
3. Ensure you have access to the required Azure resources and GitHub secrets/variables
4. Follow PR conventions outlined above

