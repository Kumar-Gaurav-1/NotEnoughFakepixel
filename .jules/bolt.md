
## 2026-10-28 - [Performance Issue] Over-iterating getLoadedEntityList in render events
**Learning:** Iterating over `mc.theWorld.getLoadedEntityList()` or `world.loadedEntityList` within render events (`RenderLivingEvent`, `RenderWorldLastEvent`) causes severe O(N) or O(N*M) performance bottlenecks in large worlds since these events fire repeatedly on every frame.
**Action:** Use `TickEvent.ClientTickEvent` (checking for `event.phase == TickEvent.Phase.START` or modulo division over total world time to run sporadically) to cache entities and clear cache when necessary instead of pulling the list inside render calls, OR use bounded queries like `getEntitiesWithinAABB` where practical.
