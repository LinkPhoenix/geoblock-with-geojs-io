# Changelog

All notable changes to this project will be documented in this file.

The format is based on Keep a Changelog, and this project follows Semantic Versioning.

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

