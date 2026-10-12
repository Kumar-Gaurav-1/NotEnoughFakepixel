## 2024-05-19 - [Repeated Regex Compilation in Render Events]
 **Learning:** Regular expressions were being compiled (`Pattern.compile()`) directly inside `RenderLivingEvent` methods, which fire on every entity render frame. This causes severe, continuous CPU and garbage collection overhead in a Minecraft mod.
 **Action:** Always look for and extract `Pattern.compile()` calls into `private static final Pattern` fields when they are found inside frequent event listeners or render loops.
