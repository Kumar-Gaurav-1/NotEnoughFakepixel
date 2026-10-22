## BOLT'S JOURNAL
## 2026-10-22 - [Render Event Bottleneck]
 **Learning:** [Iterating over `getLoadedEntityList()` inside a render event (like `RenderLivingEvent`) triggers logic per entity rendered, per frame. This results in $O(N \times M)$ overhead, drastically lowering frame rates.]
 **Action:** [Use `TickEvent.ClientTickEvent` (with `event.phase == TickEvent.Phase.START` check) for logic that only needs to evaluate occasionally instead of tying it to the render loop.]
