# TelemetryX Architecture

TelemetryX is built on a modular, performance-first architecture designed to minimize CPU and GPU overhead while providing high-frequency data collection.

## Core Design Principles

1. **Non-Blocking Data Path**: Use of Single-Producer, Single-Consumer (SPSC) lock-free ring buffers between data collection and rendering.
2. **Minimal Runtime Allocations**: Memory for the telemetry engine and ring buffers is pre-allocated at startup to prevent mid-frame stutters.
3. **Platform Abstraction**: A clean `platform/` layer that abstracts OS-specific thread, time, and dynamic library operations.
4. **Vendor Agnostic**: A plugin-based collector system that unifies NVIDIA, AMD, Intel, and Apple metrics.

## System Layers

### 1. Platform Abstraction Layer (PAL)
The PAL provides a consistent API for:
- High-precision timing (nanoseconds).
- Low-latency threading and atomics.
- Dynamic library loading for vendor SDKs (NVML, ADLX).
- Cross-platform file I/O for logging and profiles.

### 2. Telemetry Engine
The heart of TelemetryX. It manages:
- **Poll Loop**: Highly optimized loop running at user-defined frequency (default 60Hz).
- **Collector Registry**: Dynamically loads and polls active hardware collectors.
- **Ring Buffer**: Manages the flow of `TxMetricSample` data to subscribers.

### 3. Normalization Pipeline
Transforming disparate vendor data into a unified format:
- **Override Table**: O(1) matching for known vendor metrics.
- **ML Normalization**: Fallback using lightweight embeddings to map unknown strings to canonical IDs.
- **Sanitization**: Ensures all metrics are clamped to valid ranges and converted to standard units.

### 4. Graphics Abstraction Layer (GAL)
The rendering backend:
- **Vulkan-First**: Native support for Vulkan 1.3 implicit layers.
- **Batch Renderer**: Combines all overlay quads into a single draw call.
- **SDF Text Rendering**: Efficient, scale-independent text using signed distance fields.

### 5. Injection Layer
How TelemetryX enters your game:
- **Vulkan**: Implicit layer negotiation.
- **DirectX**: DXGI Present hooks.
- **Metal**: Objective-C method swizzling on present calls.
- **OpenGL**: Symbol interposition/LD_PRELOAD.
