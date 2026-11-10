## 2024-05-24 - [Pre-compile Regex Patterns in Hot Paths]
**Learning:** Compiling regular expressions (`Pattern.compile()`) inside frequently executed code paths (such as `RenderLivingEvent` render loops, tick events, or `ClientChatReceivedEvent` / `onChat` listeners) is a severe performance anti-pattern. This causes significant CPU overhead and generates excessive garbage.
**Action:** Always pre-compile `Pattern` objects as `private static final` fields.
