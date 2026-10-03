## 2023-11-20 - Java Pattern Compilation Anti-pattern
**Learning:** Avoid compiling regular expressions `Pattern.compile()` within frequently triggered event listeners, like Forge's `ClientChatReceivedEvent`. This causes high, continuous CPU overhead. Similarly, prefer simple `StringBuilder` loops over Java 8 Streams (`.chars().filter()...`) in hot rendering paths for fewer allocations.
**Action:** Extract patterns into `private static final Pattern` class fields and initialize them once. Use basic loops when iterating through strings in high-frequency methods.
