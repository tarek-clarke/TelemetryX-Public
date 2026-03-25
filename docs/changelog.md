# Changelog

All notable changes to the TelemetryX project will be documented in this file.

## [Unreleased]

### Added
- Multi-platform Core Engine (C17).
- Lock-free SPSC ring buffer for telemetry distribution.
- Vulkan and Metal injection layers.
- Metric collectors for NVIDIA, AMD, Intel, and Apple Silicon.
- ML-driven semantic metric normalization.
- TOML-based profile management.
- Binary logging (`.txlog`).

### Improved
- Near-zero-overhead vertex batching in GAL.
- High-precision timing in PAL across Windows/Linux/macOS.

### Fixed
- Primary architecture and cross-platform build system.
