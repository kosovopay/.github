# Contributing to KosovoPay

Thanks for taking the time to contribute. This file is the org-wide default; an individual
repo may add its own `CONTRIBUTING.md` that takes precedence.

## Ways to contribute

- 🐞 **Report bugs** — open an issue in the relevant repo with a minimal reproduction.
- 💡 **Suggest features** — open a feature-request issue describing the problem first, then your idea.
- 📖 **Improve docs** — typo and clarity fixes are always welcome.
- 🔧 **Send code** — see the licensing note below.

## Licensing note — read before sending a PR

Our SDKs ship under **two different licenses**:

| Repo | License | Code contributions |
|---|---|---|
| [`go-sdk`](https://github.com/kosovopay/go-sdk) | **MIT** | ✅ Pull requests welcome |
| [`php-sdk`](https://github.com/kosovopay/php-sdk), [`python-sdk`](https://github.com/kosovopay/python-sdk), [`dotnet-sdk`](https://github.com/kosovopay/dotnet-sdk) | **KosovoPay License 1.0** (source-available, no redistribution/modification) | Issues & proposals welcome; code changes are **by invitation** |

By submitting a pull request you certify you wrote the contribution (or have the right to
submit it) and license it to KosovoPay under the repository's license.

## Pull-request checklist

- [ ] One focused change per PR.
- [ ] All checks green (lint, static analysis, tests) — every repo runs CI on PRs.
- [ ] Tests added/updated for behavior changes.
- [ ] Public API changes are documented.
- [ ] Commit messages are clear; the PR description explains the *why*.

## Local quality gates

Each SDK documents its commands in its README. In short:

| Language | Lint | Types/Static | Test |
|---|---|---|---|
| PHP | `pint` | `phpstan` | `pest` |
| Python | `ruff` | `mypy` | `pytest` |
| Go | `gofmt` | `go vet` | `go test` |
| .NET | `dotnet format` | build warnings | `dotnet test` |

## Conduct

Be professional, respectful, and constructive. Spam, harassment, or abuse gets you blocked.
