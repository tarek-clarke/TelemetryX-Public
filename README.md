# TelemetryX

**Cross-Platform Performance Telemetry Overlay for Windows, Linux, and macOS.**

TelemetryX is a high-performance, near-zero overhead performance telemetry overlay designed for enthusiasts, gamers, and developers. It unifies hardware metrics from NVIDIA, AMD, Intel, and Apple Silicon into a single, canonical performance model.

---

## Key Features

- **Near-Zero Overhead**: Built with C17 and lock-free SPSC ring buffers for minimal CPU/GPU impact.
- **Vulkan-First Architecture**: Low-latency rendering with fallbacks for Metal and OpenGL.
- **Unified Telemetry Schema**: A single model for over 80+ hardware and software metrics.
- **ML-Assisted Normalization**: Uses lightweight on-device embeddings to map disparate vendor counters to a canonical schema.
- **Advanced Bottleneck Attribution**: Heuristic analysis for GPU, CPU, VRAM, and I/O stalls.
- **Platform Agnostic**: First-class support for Windows (WMI/PDH), Linux (sysfs/proc), and macOS (Mach/Metal).

## Documentation

Comprehensive documentation of the project structure and subsystems:

- **Architecture Overview**: [docs/architecture.md](docs/architecture.md)
- **Telemetry Engine**: [docs/telemetry-engine.md](docs/telemetry-engine.md)
- **ML Normalization**: [docs/normalization-pipeline.md](docs/normalization-pipeline.md)
- **Graphics Abstraction Layer**: [docs/overlay-renderer.md](docs/overlay-renderer.md)
- **Injection Strategy**: [docs/injection-strategy.md](docs/injection-strategy.md)
- **Roadmap**: [docs/roadmap.md](docs/roadmap.md)

## Repository Status

**TelemetryX is a closed-source project.** This repository serves as the public documentation hub, community issue tracker, and release portal. The proprietary implementation is maintained in a private core repository.

---

## Community

- **Bug Reports**: Please use the [Bug Report Template](.github/ISSUE_TEMPLATE/bug_report.md).
- **Feature Requests**: Open an issue using the [Feature Request Template](.github/ISSUE_TEMPLATE/feature_request.md).
- **Performance Issues**: Submit a [Performance Report](.github/ISSUE_TEMPLATE/performance_issue.md).

## Privacy and Data

TelemetryX is strictly **offline-by-design**. It contains no networking code and never "phones home." All telemetry data is processed and stored locally on your device.

See [Privacy and Data Handling](docs/privacy-and-data.md) for more details.

---

## License

This documentation and the TelemetryX public-facing project are licensed under the MIT License. See [LICENSE](LICENSE) for details.
