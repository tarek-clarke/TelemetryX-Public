# Frequently Asked Questions (FAQ)

### Q: Is TelemetryX Open Source?
**A:** No, the core engine and implementation are proprietary (Closed Source). This repository serves as the public documentation hub and community issue tracker.

### Q: Does TelemetryX impact game performance?
**A:** Our goal is near-zero overhead. Because we use lock-free data structures and batch our rendering into a single draw call, the impact is typically less than 0.5% in most AAA titles.

### Q: Why is there no Networking code?
**A:** Privacy and stability. Performance telemetry should be local. By having no network stack, we ensure your data never leaves your machine and the app remains incredibly lean.

### Q: Does it work with Anti-Cheat?
**A:** We design TelemetryX to be anti-cheat friendly. We avoid DLL hijacking and memory tampering. We are actively working with major AC vendors (EAC, BattlEye) to ensure compatibility.

### Q: Can I customize the UI?
**A:** Yes! TelemetryX uses a TOML-based profiling system. You can change colors, positions, and graph styles by editing your local profile files.

### Q: How do I request a new Metric?
**A:** Please use the [Feature Request](.github/ISSUE_TEMPLATE/feature_request.md) template in this repository.
