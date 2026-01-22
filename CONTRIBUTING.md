# Contributing

Thanks for contributing to **edge-telemetry-agent-go**!

This is a Go-based telemetry agent intended to run on Linux (eventually BeagleBone Black). The goals are reliability, clean boundaries, and testability.

## Changelog and decisions (required)
- **Update `CHANGELOG.md` on every push** (at minimum the `Unreleased` section).
- For major decisions (collector strategy, buffering/storage, retry policy, transport/auth), **add/update an ADR** in `docs/decisions/`.

## Prerequisites
- Go 1.22+ recommended

## Setup
Optional local environment:
```bash
cp .env.example .env
```

## Run locally
```bash
go run ./cmd/edge-agent
```

## Testing
```bash
go test ./...
```

## Formatting
All code must be gofmt clean:
```bash
gofmt -w .
```

## Project conventions

### Recommended layout
- `cmd/edge-agent` — main entrypoint
- `internal/collector` — metrics collectors
- `internal/sender` — HTTP client + retry/backoff
- `internal/storage` — buffering (SQLite later)
- `internal/config` — settings loading

### Reliability guidelines
- Use `context` for cancellation/timeouts.
- Network calls should have timeouts and retries with backoff.
- Avoid global mutable state.

### Testing style
- Prefer table-driven tests when appropriate.
- Keep collectors deterministic (inject time/IO if needed).

## Documentation
- Update `README.md` for config/env changes.
- Update `docs/architecture.md` for data flow changes.
- Add ADRs under `docs/decisions/` for major choices.

## Commit message guidelines
Use clear, imperative messages:
- "Add uptime collector"
- "Implement sender retry backoff"
- "Add unit tests for collectors"

## Pull requests
- Include summary + how to verify locally.
- Add/update tests for behavior changes.
- Keep changes focused and reviewable.
