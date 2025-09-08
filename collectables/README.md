# Collectables

[`CollectableHandler.lua`](collectable_handler.md) manages physical pickups like Coins/Crates.

- Resolves currencies from `ReplicatedStorage/BoostData/*`.
- Awards via `DataEditor.AddStat` using the currency's `path`.
- Optionally applies `BaseXp` to `XpBase` if present.
- Always fires:
  ```
  EventCaller.Fire("PickupCollected", player, { tag = "...", amount = 1, ... })
  ```
