# DataEditor

Strict, path-based editing on the player's data table. All *mutations* require a table or slash path (no bare keys).

## Key API
```lua
DataEditor.AddStat(player, {"Stats","Leaderstats","Coins"}, 5)
DataEditor.SetStat(player, {"Stats","Leaderstats","Coins"}, 100)
DataEditor.SetValue(player, {"Quests","Active"}, {})
DataEditor.GetValue(player, {"Stats","Leaderstats","Coins"}) -- read

-- Boosted add: adds base then applies multiplier (BoostCore)
DataEditor.AddBoostedStat(player, {"Stats","Leaderstats","Coins"}, 10, opts)
```

## Events
Every successful write fires:
```
EventCaller.Fire("StatChanged", player, keyName, newValue, deltaInfo, { path = {...}, pathStr = "Stats/..." })
```

Used by quest delta logic and by leaderstats mirroring.

## Infinite Math
If `Utilities/MathUtils` provides `wrap/unwrap` and `operations`, `DataEditor` uses them so large numbers remain safe. If not present, it falls back to plain numbers.
