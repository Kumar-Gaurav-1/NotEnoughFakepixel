## 2026-10-29 - [O(N*M) Render Loop Optimization]
**Learning:** Iterating over world.loadedEntityList inside Render events (like RenderLivingEvent) causes severe O(N*M) performance drops because the render event fires for every entity on screen, multiplying the loop cost.
**Action:** Move global entity lists iteration out of Render events. Use TickEvent.ClientTickEvent with event.phase == TickEvent.Phase.START to update state once per tick, or use bounded queries.
