1. **Analyze AshfangHelper.java**
   - Identify that `renderEntities` is called within the `RenderWorldLastEvent` which fires every frame.
   - Observe that `renderEntities` loops through `world.loadedEntityList` every frame. This is O(N) where N is the number of loaded entities, and can be severely detrimental to performance as noted in memory.

2. **Implement optimization**
   - Create a `List<Entity> cachedEntitiesToRender`.
   - Subscribe to `TickEvent.ClientTickEvent`. Ensure it only runs on `TickEvent.Phase.START` so we don't duplicate work.
   - Inside `onTick`, loop through `world.loadedEntityList` instead of in `renderEntities`, and populate `cachedEntitiesToRender` with entities that need to be rendered (Ashfang Minions, Blazing Souls). Also handle waypoints update and counters in this tick event rather than every frame.
   - Refactor `renderEntities` to only iterate over `cachedEntitiesToRender` and render them. This changes the O(N) operation per frame to O(M) where M is very small, and we only do O(N) 20 times a second instead of 60-144+ times a second.

3. **Verify Functionality**
   - Run tests using `./gradlew test` (or `./gradlew build`).

4. **Complete Pre-commit Steps**
   - Use `pre_commit_instructions` tool and complete required testing, formatting checks, and documentation.

5. **Create PR**
   - Title: `⚡ Bolt: [performance improvement]`
   - Description following Bolt guidelines.
