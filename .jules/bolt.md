## 2024-10-21 - [RenderEvent Entity Iteration Anti-Pattern]
**Learning:** [Iterating over all loaded entities during render events (like `RenderLivingEvent`) is a massive O(N*M) bottleneck in Minecraft Forge mods, firing for every rendered entity per frame.]
**Action:** [Always move logic that iterates over world entities (like detecting armor stands) to `TickEvent.ClientTickEvent` checking for `TickEvent.Phase.START`, so it runs a fixed 20 times per second instead of scaling linearly with frame rate and entity count.]
