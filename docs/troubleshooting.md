# Troubleshooting

Having issues with TelemetryX? This guide covers the most common problems and their solutions.

## 1. Overlay Not Appearing
- **Is the application running?** Check your task manager/activity monitor for `telemetryx-launcher`.
- **API Support**: Ensure your game is running on a supported API (Vulkan, DirectX 11/12, Metal, or OpenGL).
- **Injection Mode**: Try disabling other overlays (Steam, Discord, Afterburner) to check for hooking conflicts.

## 2. Low Performance / Stuttering
- **Check Poll Rate**: In your `default.toml` profile, ensure `poll_interval_ms` is not set too low (recommended: 16-33ms).
- **Logger Overhead**: If you are recording `.txlog` files, ensure you are writing to a fast SSD, not a mechanical drive or network storage.

## 3. Missing GPU Metrics
- **Driver Version**: Ensure you have the latest drivers from NVIDIA, AMD, or Intel.
- **Permission Errors**: On Linux, some sensors in `/sys/class/hwmon` require specific user permissions. Run the `setup_permissions.sh` script (see local tools).

## 4. Crash on Startup
- **Log Files**: Check the `telemetryx-error.log` in your user directory.
- **Reporting**: If the crash persists, please submit a [Bug Report](.github/ISSUE_TEMPLATE/bug_report.md) with your log file attached.

## 5. macOS Specifics (Metal)
- **App Sandbox**: If your game is from the Mac App Store, macOS may block the TelemetryX injection layer. We recommend using the "Companion Window" mode for sandboxed apps.
