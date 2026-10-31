## 2024-10-31 - Regex Compilation in Render Loops
**Learning:** Discovered `Pattern.compile` being executed inside `RenderLivingEvent` (specifically in `MiscFeatures.java`), which runs every frame for every entity. This causes severe FPS drops and object churn due to constant regex recompilation in one of the hottest paths of the application.
**Action:** Always pre-compile `Pattern` objects as `static final` fields, especially when used in render, tick, or chat events.
