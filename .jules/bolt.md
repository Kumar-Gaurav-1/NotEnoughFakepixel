## 2026-10-17 - [O(N*M) Loop in Render Events]
**Learning:** Iterating over all loaded entities within per-entity render events (like RenderLivingEvent) causes O(N*M) performance bottlenecks and massive lag spikes when many entities are present.
**Action:** Always use TickEvent.ClientTickEvent (which runs once per tick) instead of render events for processing world entities globally.
