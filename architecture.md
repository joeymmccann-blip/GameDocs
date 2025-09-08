# Architecture Overview

```
ServerScriptService/GameStuff
├─ DataManager/                 # Save/load & player data tree
│  ├─ DataManager.lua
│  ├─ DataEditor.lua            # Strict, path-based edits + boosted adds
│  └─ Utilities/
│     ├─ MathUtils.lua          # (Optional) InfiniteMath wrappers
│     └─ TableUtils.lua
│
├─ Events/
│  ├─ EventCaller.lua           # Simple pub/sub facade (Fire/Listen)
│  └─ (QuestEventListeners.lua) # Bridges pickup/currency deltas → Engine.Bump
│
├─ Players/Quests/
│  ├─ Catalog.lua               # Main quest list
│  ├─ CatalogLoader.lua         # Supports per-quest modules from folder
│  ├─ Rules.lua                 # Defaults (polling, day/week cutoff, etc.)
│  ├─ Engine.lua                # Accept → Progress → Complete
│  ├─ Mutators.lua              # World/UI toggles (prompt, spawns...)
│  └─ Binders.server.lua        # Wires listeners / availability emits
│
├─ Spawner/
│  └─ CollectableHandler.lua    # Coins, crates… awards & emits PickupCollected
│
└─ Services/
   ├─ GlobalLeaderboardService.lua
   └─ PublicLeaderstats.lua

ReplicatedStorage/
├─ BoostData/World1.lua         # Currency meta: paths, base values
├─ GuiRemotes/GuiPush           # Server → client prompt/dialog feed
├─ GuiEngine/GuiRouter.lua      # Send actions to server
└─ GuiProfiles/
   └─ QuestHub/
      ├─ TemplatesExtra.lua     # Visuals for prompts & dialogs
      └─ (profile modules)
```

**Data flow (high level)**

1. Player touches coin → `CollectableHandler` grants currency (via `DataEditor`) and fires `PickupCollected`.
2. `QuestEventListeners` turns pickup/currency deltas into `Engine.Bump` where applicable.
3. `Engine` updates per-step `entry.progress` and checks completion in `TickEvaluate`/`PollDeltas`.
4. `Mutators` push prompt/dialog updates to clients using `GuiPush` (RemoteEvent).
5. `GuiClientHandler` renders prompts/dialogs using `TemplatesExtra` and routes button clicks.
