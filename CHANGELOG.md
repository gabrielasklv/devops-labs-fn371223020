# Changelog
## [0.4.0]
### Added
- `compose.yaml` with `app` and `db` (PostgreSQL 17) services
- Healthcheck on db; app waits for it (`depends_on: service_healthy`)
- Named volume `db-data` for persistent notes
- `.env.example` with required variables
- Adminer under the `tools` profile
- Runbook section "Run with Compose"

## Unreleased

- Initial template: notes API with health and version endpoints.
