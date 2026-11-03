## 2026-11-03 - Pre-compile Pattern objects in frequently executed code paths
**Learning:** Compiling regular expressions (`Pattern.compile()`) inside frequently executed code paths (such as `ClientChatReceivedEvent` / `onChat` listeners) causes unnecessary CPU overhead and object allocations (increasing Garbage Collection pressure).
**Action:** Always pre-compile `Pattern` objects as `private static final` fields.
