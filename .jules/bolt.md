## 2026-10-20 - [O(N*M) Rendering Optimization]
**Learning:** Calling `getLoadedEntityList()` inside `RenderLivingEvent` causes massive O(N*M) performance bottlenecks due to per-entity per-frame evaluation.
**Action:** Always prefer caching entities in `TickEvent.ClientTickEvent` or processing bounded queries. Avoid iterating over all loaded entities in any render loop.
