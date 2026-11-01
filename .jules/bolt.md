## 2024-05-19 - [Render Loop Pattern Compilation]
**Learning:** Compiling regex patterns (`Pattern.compile()`) inside high-frequency render loops (like `RenderLivingEvent.Specials.Pre`) was discovered, causing unnecessary object creation and compilation overhead multiple times per frame per entity.
**Action:** Always inspect high-frequency event handlers (`RenderLivingEvent`, `TickEvent`) and move any `Pattern.compile` or expensive initialization calls to `private static final` fields at the class level.
