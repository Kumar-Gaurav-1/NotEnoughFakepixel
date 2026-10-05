## 2024-10-05 - Regex Compilation in Render Loop
**Learning:** `Pattern.compile()` is very expensive and was being called twice per entity per frame in `MiscFeatures.java` due to being inside a render event (`RenderLivingEvent.Specials.Pre`). This causes massive overhead (thousands of compilations per second).
**Action:** Always extract `Pattern.compile()` to static final fields, especially when used in high-frequency loops like render events or tick events.
