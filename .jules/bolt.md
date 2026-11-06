
## 2024-05-14 - [Optimize Pattern Compilation]
 **Learning:** [Compiling `Pattern` regexes on every tick or render event frame (like `RenderLivingEvent.Specials.Pre`) is a severe performance anti-pattern. This overhead compounds with the number of rendered entities.]
 **Action:** [Always pre-compile regexes as `private static final` fields at the class level instead of instantiating them within hot paths.]
