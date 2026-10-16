## 2024-05-24 - [RenderLivingEvent Loop Bottleneck]
**Learning:** Hooking into `RenderLivingEvent` and iterating over `world.loadedEntityList` inside of it creates an O(N*M) performance bottleneck, as `RenderLivingEvent` is called for every rendered entity on every single frame. This can cause massive lag in populated areas like hubs or dungeons.
**Action:** Always move broad, full-world entity iterations to `TickEvent.ClientTickEvent` to run at most 20 times per second, instead of per-frame per-entity. Keep render loops tight and localized.
