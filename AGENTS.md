# AGENTS.md

Guidance for coding agents and contributors working in this repository.

## Project overview

- Project: **Go Report Card** (`github.com/gojp/goreportcard`)
- Language: **Go** (module currently targets `go 1.24.2`)
- Main entrypoint: `main.go`
- Key packages: `check/`, `download/`, `handlers/`, `vault/`, `tools/`

## Setup and common commands

Run all commands from repository root:

- Build everything:
  - `make build`
- Run lint suite:
  - `make lint`
- Run tests with coverage:
  - `make test`
- Start the app locally:
  - `GRC_DATABASE_PATH=./db make start`
- Install local tooling used by this repo:
  - `make install`

## Change guidelines

- Keep changes minimal and scoped to the task.
- Prefer updating existing code paths over introducing new abstractions unless necessary.
- Do not modify vendored code under `vendor/` unless explicitly required.
- Avoid changing fixtures in `check/testdata/` unless the task needs it.
- When modifying behavior, add or update tests close to the changed package.

## Code style and quality

- Follow standard Go formatting and style (`gofmt`, `go vet`, `staticcheck`).
- Keep functions small and readable; avoid deeply nested branching where possible.
- Return contextual errors where they improve diagnosability.
- Preserve existing package boundaries and naming conventions.

## Validation before submitting changes

For code changes, run:

1. `make lint`
2. `make test`
3. `make build`

For docs-only updates, lint/tests are optional but recommended when touching behavior references.

## Notes for agents

- Respect any unrelated local changes already present in the working tree.
- Never rewrite git history unless explicitly asked.
- If you add new dependencies, use current stable releases and keep `go.mod`/`go.sum` consistent.
