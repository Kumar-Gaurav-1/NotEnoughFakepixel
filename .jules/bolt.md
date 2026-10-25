## 2023-10-25 - [O(N*M) Rendering Bottlenecks]
**Learning:** Iterating over `mc.theWorld.getLoadedEntityList()` inside render events (e.g., `RenderLivingEvent.Pre<EntityLivingBase>`) causes an O(N*M) performance bottleneck, as the render event is fired per rendered entity per frame, running the iteration millions of times.
**Action:** Always move broad entity scans to `TickEvent.ClientTickEvent` (with a check for `event.phase == TickEvent.Phase.START`) so they only run once per tick rather than inside rendering loops.
