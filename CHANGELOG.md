# Changelog

All notable changes to this project will be documented in this file.

---

## v1.0.0 - 2025-05-16 - Cory Close

### Changed
- Refactors kubesecrets into a single script (#1)

### Added
- Adds PR workflow (#1)
- Adds auto-bump workflow (#1)
- Adds release workflow (#1)
- Publishes release to homebrew tap (#1)

## v0.0.1 - 2023-12-05 - Cory Close 

Initial release of `kubesecrets`!

* Bash CLI for decoding and patching Kubernetes secrets
* Supports `kubectl`-based secret lookups, decoding, and base64 patching
* Features dry-run, interactive and stdin input modes
* Provides fallback resolution via environment variables
* Designed for use in CI, terminals, and workflows

---

