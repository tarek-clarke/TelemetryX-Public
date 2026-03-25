# Supported Platforms & Hardware

TelemetryX is designed for the modern cross-platform landscape, ensuring high-performance telemetry regardless of your OS or GPU vendor.

## Operating Systems

| OS | Status | Metrics Source |
|----|--------|----------------|
| **Windows 10/11** | Stable | WMI, PDH, NVML, ADLX |
| **Linux (Ubuntu, Arch)** | Stable | sysfs, procfs, hwmon, NVML |
| **SteamOS (Steam Deck)** | Verified | sysfs, Vulkan |
| **macOS (Intel & M-Series)** | Beta | Mach APIs, Metal Performance Counters |

## GPU Vendors

### NVIDIA (GeForce, Quadro, RTX)
- **API**: NVML (NVIDIA Management Library).
- **Metrics**: Full support for Temperature, Power, Clocks, VRAM, and PCIE throughput.

### AMD (Radeon, Instinct)
- **API**: ADLX (AMD Display Library X).
- **Metrics**: High-frequency utilization, power tracking, and thermal hotspot monitoring.

### Intel (Arc, Iris Xe)
- **API**: Metrics Discovery API.
- **Metrics**: Detailed pipeline utilization and shader compilation tracking.

### Apple Silicon (M1, M2, M3)
- **API**: Metal Framework & IOKit.
- **Metrics**: VRAM pressure, GPU occupancy, and thermal states.

## Minimum Requirements
- **CPU**: 64-bit multi-core processor.
- **RAM**: 4GB+.
- **Graphics**: 
  - Vulkan 1.1+ (Recommended)
  - Metal 2.0+ (macOS)
  - DirectX 11+ (Windows)
  - OpenGL 3.3+
