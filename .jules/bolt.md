## 2024-05-24 - Do not query all loaded entities in RenderLivingEvent
**Learning:** Querying mc.theWorld.getLoadedEntityList() or similar in RenderLivingEvent (or any render event) causes severe O(N*M) performance bottlenecks since it runs every frame for every entity being rendered.
**Action:** Use TickEvent.ClientTickEvent to update a cached list/map of entities periodically, or use event.entity directly if possible, or bounded queries.
