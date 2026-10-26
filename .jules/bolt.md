## 2025-01-24 - [RenderLivingEvent loadedEntityList bottleneck]
**Learning:** Iterating over `world.loadedEntityList` within high-frequency render events like `RenderLivingEvent` or `RenderEntityModelEvent` causes severe O(N*M) performance bottlenecks where N is rendered entities and M is total loaded entities. Caching with time-based checks inside render events is a code smell.
**Action:** Use `TickEvent.ClientTickEvent` (checking `event.phase == TickEvent.Phase.START`) for once-per-tick caching instead. Always clear the cache immediately to prevent ghost entity rendering and memory leaks.
