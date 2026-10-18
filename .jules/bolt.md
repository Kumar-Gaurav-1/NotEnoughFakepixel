## 2024-05-24 - [Avoid getLoadedEntityList in Render Events]
**Learning:** Iterating over `mc.theWorld.getLoadedEntityList()` inside `RenderLivingEvent` causes severe O(N*M) performance bottlenecks. This is because the render event fires for every entity every frame, and time checks like `getTotalWorldTime() % 5 == 0` still remain true for multiple frames per tick, running the heavy scan hundreds of times.
**Action:** Move global entity scans to `TickEvent.ClientTickEvent` to ensure they only run once per tick.
