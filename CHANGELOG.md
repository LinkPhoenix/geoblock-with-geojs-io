# Changelog

All notable changes to this project will be documented in this file.

The format is based on Keep a Changelog, and this project follows Semantic Versioning.

## [1.0.4] - 2026-03-08

### Changed
- Updated `go.mod` to `go 1.26.1` (latest stable Go release as of 2026-03-08).
- Updated CI Go version in `Quality` workflow to `1.26.1` to keep checks aligned with the module version.

## [1.0.2] - 2026-03-08

### Added
- Added `trustForwardedHeaders` configuration to control whether `X-Forwarded-For` and `X-Real-IP` are trusted.
- Added `failClosedIfNoIP` configuration to explicitly deny/allow requests when no client IP can be resolved.
- Added GitHub Actions workflows for quality checks and automatic latest release creation on `vX.Y.Z` tags.
- Added deterministic unit tests for IP resolution fallback, trust settings, and config validation.

### Changed
- Added fallback to `RemoteAddr` when forwarded headers are not used or not present.
- Normalized country codes from configuration, API, and header input to uppercase.
- Updated plugin metadata sample config to include new IP resolution security options.

### Fixed
- Fixed potential HTTP response body leak when GeoJS API returns non-200 responses.
- Fixed timeout logging behavior when `ignoreAPITimeout` is disabled.
- Fixed monthly refresh behavior to also honor `ignoreAPITimeout`.
- Fixed allowed IP range logging to use `logAllowedRequests`.
- Updated README author and plugin registry version example.

## [1.0.3] - 2026-03-08

### Fixed
- Normalized repository files to LF line endings to avoid hidden CRLF mismatches in CI.
- Hardened `Quality` workflow module/import consistency check by stripping `\r` before comparison.

## [1.0.1] - 2026-03-08

### Added
- Added Traefik plugin metadata `iconPath` pointing to `.assets/logo.png`.

### Changed
- Published patch release `v1.0.1` as the new latest release.

## [1.0.0] - 2026-03-08

### Added
- Initial public release of `GeoBlock With GeoJS.io` Traefik middleware plugin.
- Country whitelist/blacklist support with GeoJS.io lookup.
- Optional request bypass with `excludedPathPatterns`.
- Optional custom country source header support with `ipGeolocationHttpHeaderField`.
- Optional response enrichment with `X-IPCountry` when `addCountryHeader` is enabled.
- Optional on-disk cache persistence and configurable log file target.

### Changed
- Rebranded plugin metadata and documentation to `GeoBlock With GeoJS.io`.
- Updated module and import path to `github.com/linkphoenix/geoblock-with-geojs-io`.
- Standardized local Traefik and Docker examples to use the new module path.

### Fixed
- Replaced fatal startup exits with explicit errors returned by plugin initialization.
- Added default cache size handling when not explicitly configured.
- Added strict validation for invalid `allowedIPAddresses` entries.
- Added backward-compatible support for legacy `blacklist` key while documenting `blackListMode`.
- Added tests for nil config and invalid allowed IP address cases.
