1. **Identify Performance Bottleneck**: `Pattern.compile()` is being called inside the `onChat` event handler in multiple files. `onChat` can be called very frequently, and compiling regular expressions dynamically is an expensive operation that should be avoided.
2. **Refactor `BossNotifier.java`**: Move `Pattern.compile()` to private static final fields.
3. **Refactor `AshfangHelper.java`**: Move `Pattern.compile()` to private static final fields.
4. **Refactor `ChocolateFactory.java`**: Move `Pattern.compile()` to private static final fields.
5. **Refactor `AbilityNotifier.java`**: Move `Pattern.compile()` to private static final fields.
6. **Refactor `Diana.java`**: Verify if `Pattern.compile()` can be improved (it's already a field, but maybe we can check). Oh wait, `Diana.java` has a dynamically compiled one? Let's check `Diana.java` line 54.
7. **Pre-commit Checks**: Run pre-commit instructions.
8. **Submit**: Create PR.
