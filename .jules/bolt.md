## 2024-11-11 - [Extracted Dynamic Pattern Computations to Constants]
**Learning:** Found dynamic Pattern.compile strings inside high-frequency event handlers such as RenderLivingEvent and ClientChatReceivedEvent. This causes an O(N*M) performance bottleneck, allocating and computing regex AST repeatedly.
**Action:** Move all Pattern.compile initializations into private static final class variables, so that the regex trees are only generated once per class load.
