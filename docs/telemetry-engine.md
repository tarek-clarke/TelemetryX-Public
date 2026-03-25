# Telemetry Engine

The Telemetry Engine is the central hub for data collection and distribution in TelemetryX.

## Data Collection Model

The engine operates on a push-pull model:
1. **Pull**: The engine polls registered `Collectors` at a high frequency (default 16.6ms intervals).
2. **Push**: Collected samples are packed into `TxMetricSample` structs and pushed into a lock-free SPSC ring buffer.
3. **Subscribe**: UI widgets or the binary logger subscribe to the buffer to receive updates without blocking the collection loop.

## The Ring Buffer

Wait-free and lock-free concurrency is critical for near-zero overhead.
- **Capacity**: Pre-allocated to store thousands of latest samples.
- **Ordering**: Strictly chronological to ensure accurate frametime graphs.
- **Performance**: Pushing a sample takes ~15-30 nanoseconds on modern CPUs.

## Metric Schema

All metrics are converted to a **Canonical Schema** to ensure a consistent experience regardless of hardware.

### Key Metrics Tracked
- **Frame Rate (FPS)**
- **Frame Time (ms)**
- **GPU Utilization (%)**
- **GPU Clock (MHz)**
- **GPU Temperature (°C)**
- **VRAM Usage (MB)**
- **CPU Utilization (%)**
- **I/O Disk Latency (ms)**
- **Network Ping (ms)**

## Optimization Techniques

- **C17 Implementation**: Direct access to hardware APIs with minimal abstraction cost.
- **SIMD-Friendly Structures**: Data is packed to maximize cache hits during batch normalization.
- **Instruction Level Parallelism**: The poll loop is designed to be lean, allowing the CPU to execute collection calls in parallel where possible.
