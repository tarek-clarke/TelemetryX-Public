# TelemetryX Roadmap

The evolution of TelemetryX is driven by performance, accuracy, and platform coverage.

## v0.1.0 — The Core Alpha (Current)
- [x] Multi-platform telemetry engine.
- [x] Initial GPU collectors (NVIDIA, AMD, Apple).
- [x] Vulkan and Metal rendering layers.
- [x] Canonical schema normalization.
- [x] Binary logging system (`.txlog`).

## v0.5.0 — The Stability Update
- [ ] Full DirectX 12 (DXGI) injection support.
- [ ] Intel Metrics Discovery API integration.
- [ ] Profile auto-detection system for Steam AppIDs.
- [ ] Refined bottleneck heuristic engine.
- [ ] Customizable TOML-based UI themes.

## v1.0.0 — Production Release (Coming Soon)
- [ ] Steam Store release.
- [ ] Full Steam Deck (SteamOS) optimized UI.
- [ ] ML Auto-Correction for new driver versions.
- [ ] Post-Session Analysis Tool (view `.txlog` files).
- [ ] Advanced "Overlay Editor" widget.

## Long-Term Vision
- **Remote Dashboard**: A separate companion app (mobile/web) to view telemetry without an overlay (optional, opt-in).
- **VR/AR HUDs**: Injecting telemetry into OpenXR pipelines for VR enthusiasts.
- **Frame-Generation Analysis**: Specific metrics for DLSS 3 and FSR 3 frame-gen performance.
