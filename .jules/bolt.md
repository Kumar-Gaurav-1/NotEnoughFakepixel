## 2024-06-25 - Minecraft 1.8.9 Tick Loop Optimization
**Learning:** In Minecraft 1.8.9 Forge mods, code executing on every `ClientTickEvent` (20 times per second) must absolutely minimize object allocation. Using Java 8 Streams and `Collectors.toList()` inside these hot loops creates excessive short-lived objects (lambdas, wrappers, iterators), leading to frequent minor GC pauses which cause observable lag spikes in-game.
**Action:** Always replace Java Streams with traditional `for` loops and pre-sized `ArrayList`s when optimizing code that runs in standard game tick/render events.

## 2024-06-25 - Redundant Scoreboard Parsing
**Learning:** Scoreboard parsing is an expensive operation often performed every tick by multiple features independently. Some features, like `SlayerTimer`, only need to check the scoreboard to detect when an event *starts*, but continue parsing it every tick even after the event is active.
**Action:** Add early returns (`if (isActive) return;`) in tick event handlers that only need to trigger once per event cycle to skip expensive redundant state checks.
