## 2024-05-19 - Regex Compilation in Render Loops
**Learning:** Found several instances where `Pattern.compile` is called inside render loops (like `RenderLivingEvent.Specials.Pre` in `MiscFeatures.java` and `RenderWorldLastEvent` / chat handlers in other files). This is a classic Java performance anti-pattern because regex compilation is expensive and render loops run on every frame.
**Action:** Always check render/tick loops for expensive object creations or method calls (like `Pattern.compile`). Hoist these to `private static final` fields at the class level.
