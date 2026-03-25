# Overlay Renderer (GAL)

The Graphics Abstraction Layer (GAL) is responsible for compositing and drawing the performance HUD over your active game without causing stuttering or significant FPS drop.

## Rendering Backends

TelemetryX selects the most efficient backend for your platform:

- **Vulkan**: Primary target. Implemented as a Vulkan 1.3 implicit layer.
- **Metal**: Optimized for Apple Silicon using native Metal command buffers.
- **DirectX**: High-performance hooks for DX11 and DX12.
- **OpenGL**: Minimal overhead interposition.

## Technical Innovations

### 1. Single Draw Call Batching
The entire overlay—graphs, bars, text, and icons—is converted into a single vertex buffer and drawn in a **single GPU command**. This minimizes driver overhead and prevents the overlay from competing for GPU resources with the game.

### 2. SDF Font Rendering
Instead of traditional bitmap fonts, we use **Signed Distance Fields (SDF)**. 
- **Crisp at any scale**: The HUD looks sharp on 1080p and 4K.
- **Efficient**: Text rendering requires zero GPU memory updates after the initial font atlas is loaded.

### 3. Glassmorphism Compositor
High-quality UI doesn't have to be slow. Our compositor uses pre-calculated blur approximations and semi-transparent quads to achieve a premium "glass" look with near-zero pixel shader cost.

## Coordinate System

- **Anchor-Based**: Position widgets relative to Top-Left, Top-Right, etc.
- **Resolution Scaling**: The overlay automatically scales based on the game's internal resolution to maintain readability.
- **Dynamic Opacity**: Per-widget opacity control to ensure the HUD never obscures critical game information.
