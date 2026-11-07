
## $(date +%Y-%m-%d) - [Compiling regular expressions inside ClientChatReceivedEvent]
**Learning:** In Minecraft Forge modding, parsing chat messages is extremely frequent. Compiling `Pattern.compile()` on the fly inside event listeners like `ClientChatReceivedEvent` or `TickEvent` creates significant overhead because `Pattern.compile` is an expensive operation that shouldn't be executed for every chat message or tick. This can cause micro-stutters and frame drops.
**Action:** Always pre-compile `Pattern` objects as `private static final` fields at the class level instead of instantiating them dynamically inside frequently called event methods.
