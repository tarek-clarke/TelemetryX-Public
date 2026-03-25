# Privacy & Data Handling

TelemetryX is built with a **Privacy-First** philosophy. As a performance tool, your data belongs to you, and we take extreme measures to ensure it stays on your machine.

## 1. Zero-Network Policy
**TelemetryX does not have any code for networking.**
- No `socket()` calls.
- No HTTP/HTTPS libraries.
- No background update checks or cloud sync.
- TelemetryX is 100% offline-ready.

## 2. On-Device Processing
All data processing, including the ML-assisted normalization and bottleneck analysis, happens entirely on your local CPU and GPU.
- **Machine Learning**: We use small, on-device ONNX models. No data is sent to a server for inference.
- **Logging**: If you enable binary logging (`.txlog`), the files are stored only in your user directory.

## 3. What We Collect (Locally)
TelemetryX only collects hardware-level performance data:
- GPU/CPU utilization and thermals.
- Memory usage.
- Disk and Network latency (via OS counters, not by sniffing traffic).
- Frame timing and refresh rates.

**We DO NOT collect**:
- Personally Identifiable Information (PII).
- Search history or browser data.
- Game-specific actions or keystrokes (beyond the overlay toggle hotkey).

## 4. Crash Reports
In the event of a crash, a local dump file may be generated. **You** are in control of whether you share this file via our community issue tracker for troubleshooting. No data is sent automatically.

## 5. Third-Party Libraries
We use a small set of open-source, community-vetted libraries (`lz4`, `toml-c`, `stb`) that have been audited to ensure they do not perform any hidden network activity.
