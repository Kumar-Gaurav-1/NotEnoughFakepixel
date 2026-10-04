## 2024-05-15 - [MiscFeatures Pattern Compile Optimization]
**Learning:** Compiling regex patterns in a per-frame or high-frequency render method (like onRenderLivingSpecialsPre) is extremely bad for performance due to object allocation and CPU overhead.
**Action:** Always extract `Pattern.compile()` to a `private static final Pattern` field when used in high-frequency event handlers, especially render loops.
