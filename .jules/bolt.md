## 2023-11-20 - [Pattern compilation in high-frequency events]
 **Learning:** [Dynamic compilation of regular expressions using `Pattern.compile()` within high-frequency event handlers like `onChat` and `RenderLivingEvent` introduces unnecessary object allocations and CPU overhead in this Forge mod codebase.]
 **Action:** [Always pre-compile `Pattern` objects as `private static final` fields at the class level instead of dynamically inside events.]
