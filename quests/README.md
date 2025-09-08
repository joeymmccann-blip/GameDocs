# Quests

Files:
- [`Catalog.lua`](catalog.md) – list of quests (supports `collectItem`, `currencyDelta`, `pathDelta`, etc.).
- [`CatalogLoader.lua`](catalog_loader.md) – optionally load per-quest modules from a folder and merge into the main Catalog.
- [`Engine.lua`](engine.md) – accept → progress → complete, timers, availability, cooldowns.
- [`Mutators.lua`](mutators.md) – world/UI side-effects while a step is active.
- `Binders.server.lua` – wires visibility + listeners on boot.

**Progress model**
Each active quest keeps `progress[objId] = number`. The engine treats an objective as complete when `progress >= amount`.

**Two ways progress moves:**
- **Bumps** (`Engine.Bump`) for count-based objectives: `collectItem`, `talkToNPC`, `reachRegion`, etc.
- **Poll deltas** (`Engine.PollDeltas`) for `"currencyDelta"`/`"pathDelta"`; uses baseline snapshot on accept.
