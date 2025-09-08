# QuestEventListeners

Translates gameplay events into `Engine.Bump` calls.

- On `PickupCollected`:
  ```lua
  Engine.Bump(player, { type = "collectItem", tag = payload.tag })
  ```

- On `StatChanged` (currency path deltas):
  If the changed path matches a currency in BoostData, delta quests are re-evaluated by `Engine.PollDeltas` (which reads baselines + current values).

Include this file under `ServerScriptService.GameStuff.Players.Quests` and load it with your binders.
