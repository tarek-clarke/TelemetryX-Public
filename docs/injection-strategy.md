# Injection Strategy

TelemetryX must enter the game's rendering pipeline to display its overlay. Since we support multiple OSs and Graphics APIs, we employ a multi-pronged injection strategy tailored for each.

## 1. Vulkan (Implicit Layer)
This is our cleanest and most stable injection method.
- **How it works**: TelemetryX is registered as a "Vulkan Implicit Layer" in the system registry or via environment variables.
- **The Hook**: We intercept the `vkQueuePresentKHR` call. Before the frame is presented to the screen, we record our overlay commands into a secondary command buffer and merge it with the game's primary queue.
- **Advantage**: Zero risk of "hooking" errors and full compatibility with Steam Deck/Proton.

## 2. DirectX 11/12 (DXGI Hook)
Essential for the vast majority of Windows games.
- **How it works**: We perform a VTable hook on the `IDXGISwapChain::Present` method. 
- **The Hook**: When the game calls `Present`, we pause, perform our GAL draw calls, and then resume the original call.
- **Advantage**: High performance and support for most modern AAA titles.

## 3. Metal (macOS Swizzling)
TelemeteryX provides first-class support for Apple Silicon.
- **How it works**: We use Objective-C Method Swizzling on the `MTLCommandBuffer`'s `presentDrawable:` method.
- **The Hook**: We inject our rendering pass before the drawable is committed to the display.
- **Advantage**: Native performance on M1/M2/M3 chips without requiring application restarts.

## 4. OpenGL (LD_PRELOAD / Interposition)
- **Linux**: We use `LD_PRELOAD` to intercept `glXSwapBuffers`.
- **Windows**: We hook `wglSwapBuffers` via a trampoline function.
- **Advantage**: Legacy support for older titles and emulators.

## Anti-Cheat Compatibility
We prioritize being "Anti-Cheat Friendly":
- **No Memory Tampering**: We do not touch game-specific memory (actors, logic, coordinates).
- **No DLL Hijacking**: We avoid name-collision injection methods (e.g., placing a fake `dxgi.dll` in the game folder).
- **Whitelisting**: We actively work with EAC and BattlEye to ensure the TelemetryX signature is recognized as a performance tool.
