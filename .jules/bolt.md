## 2024-11-04 - [Event Loop Iteration vs Render Loop Iteration]
**Learning:** Checking for loaded entities in `RenderWorldLastEvent` (`world.loadedEntityList`) scales linearly every frame and bottlenecks performance drastically compared to running it in `TickEvent.ClientTickEvent`.
**Action:** Moving non-visual logic out of the render loop (which ticks every frame) and into the game tick loop (which ticks at a fixed 20 TPS) improves framerate reliability without changing observed behavior.
