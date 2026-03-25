# Canonical Metric Schema

TelemetryX uses a unified schema to represent performance data across all hardware vendors. This ensures that UI widgets and logs remain consistent regardless of whether you're using an NVIDIA, AMD, Intel, or Apple GPU.

## Schema Philosophy
1. **Normalization**: All vendor-specific counters are mapped to a canonical ID.
2. **Standard Units**: Temperature in Celsius, Power in Watts, Clocks in MHz.
3. **High Fidelity**: Support for 80+ distinct performance and system metrics.

## Key Metric Groups

### 1. GPU Metrics (`GPU_`)
- `GPU_LOAD`: Percentage of GPU time spent processing.
- `GPU_TEMP`: Thermal reporting for the primary sensor.
- `GPU_VRAM_USED`: Total video memory in use (MB).
- `GPU_CORE_CLOCK`: Current operating frequency (MHz).
- `GPU_POWER_DRAW`: Real-time power consumption (W).

### 2. CPU Metrics (`CPU_`)
- `CPU_TOTAL_LOAD`: Aggregate load across all cores.
- `CPU_TEMP`: Processor package temperature.
- `CPU_POWER`: Core or Package power draw.

### 3. Frame Metrics (`FRM_`)
- `FRM_FPS`: Average frames per second.
- `FRM_TIME`: Frame latency (ms).
- `FRM_STALL_IO`: Detection of disk-related frame stalls.

### 4. System & Memory (`SYS_`)
- `SYS_RAM_USED`: System memory utilization.
- `SYS_SWAP_USED`: Virtual memory pressure.
- `SYS_PCI_BANDWIDTH`: Data throughput over the PCI-E bus.

## Extending the Schema
While the schema is currently fixed in the core engine, community requests for new metrics (e.g., specific AltiVec or AVX counters) can be submitted as [Feature Requests](.github/ISSUE_TEMPLATE/feature_request.md).
