# Directory Structure

While TelemetryX is closed-source, we believe in technical transparency. Below is the high-level architecture of the private implementation.

## Project Tree

```text
TelemetryX/
├── src/
│   ├── platform/       # OS abstraction (threads, time, dynlib)
│   ├── core/           # Engine, schema, ring buffers, normalization
│   ├── collectors/     # Hardware-specific (NVML, ADLX, Intel MD, Mach)
│   ├── gal/            # Graphics Abstraction Layer (Vulkan, Metal, GL)
│   ├── ml/             # Normalization logic (Embedder, Similarity)
│   ├── overlay/        # Compositor, Widgets, Text rendering
│   ├── inject/         # Injection hooks (Vulkan layer, DXGI, OpenGL)
│   └── main.c          # Launcher entry point
│
├── tests/              # Unit and integration tests
├── profiles/           # Default TOML overlay configs
├── tools/              # Post-session log analysis tools (Python/C)
└── docs/               # Internal technical design specs
```

## Module Descriptions

- **`platform/`**: The glue that makes TelemetryX truly cross-platform.
- **`core/`**: The "brains" of the system—handling data flow and canonical schema mapping.
- **`collectors/`**: The "senses"—talking to hardware drivers at low level.
- **`gal/`**: The "graphics card"—efficiently drawing the overlay.
- **`ml/`**: The "translator"—mapping new vendor metrics automatically.
- **`overlay/`**: The "interface"—rendering the dashboard you see in-game.
- **`inject/`**: The "gateway"—how TelemetryX enters the game process.
