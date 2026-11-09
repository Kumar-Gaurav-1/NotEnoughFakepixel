## 2025-01-20 - Pattern Compilation Anti-Pattern
**Learning:** Found multiple instances where regular expressions are compiled dynamically (`Pattern.compile()`) inside high-frequency events like `RenderLivingEvent` and `ClientChatReceivedEvent`. This creates a new Pattern object on every frame or chat message, causing significant performance overhead and object churn.
**Action:** Extract all `Pattern.compile` calls inside methods to `private static final Pattern` fields at the class level to ensure they are compiled only once.
