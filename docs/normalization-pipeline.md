# Normalization Pipeline

A key challenge in cross-platform telemetry is that every vendor (NVIDIA, AMD, Intel, Apple) uses different names and units for the same metric. The TelemetryX Normalization Pipeline solves this.

## The Three-Stage Process

### 1. Deterministic Match (Override Table)
Most common metrics (e.g., `NV_GPU_TEMP`, `AMD_HOTSPOT_TEMP`) are mapped in an O(1) hash table. If a match is found, normalization rules are applied immediately.

### 2. Semantic Mapping (ML Fallback)
When a new driver or hardware is released with unknown metric names, TelemetryX uses a lightweight ML model:
- **Embedder**: Converts the metric name (e.g. "Core_Voltage_Aux") into a semantic vector.
- **Similarity Search**: Compares the vector against the canonical schema.
- **Auto-Mapping**: The system "learns" the mapping and caches it in the runtime override table.

### 3. Unit Standardization
All data is converted to standardized international units:
- **Temperature**: Celsius (°C)
- **Power**: Watts (W) or Milliwatts (mW)
- **Clock**: Megahertz (MHz)
- **Memory**: Megabytes (MB)
- **Latency**: Milliseconds (ms)

## Handling Counters vs. Gauges

- **Gauges**: (Temperature, Load) Stored as raw values.
- **Counters**: (Bytes Sent, Frame Count) The pipeline calculates the **Delta** between polls to provide meaningful "per second" or "per frame" rates.

## Validation Layer

Before a metric reaches the UI, it passes through a validation check:
- **Range Check**: Clamping values to realistic bounds (e.g. 0-100% load).
- **Quality Flags**: Marking data as "Stale" or "Invalid" if a collector fails, preventing erratic UI behavior.
