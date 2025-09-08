# DataManager

**Responsibility:** per-player save/load, exposing a mutable table tree `pdata`.

**Shape (relevant branches):**
```lua
Quests = {
  Active = { [questId] = {
    stepIdx, stepKey, progress = { [objId] = number },
    vars = {},            -- baselines for delta objectives
    state = "active"|"claimable",
    expiresAt = 0,
    stepEndsAt = 0,
    mutatorsApplied = false,
    retries = {},
  }},
  Completed = { [questId] = unixTime },
  Cooldowns = { [questId] = unixTime },
  Availability = { [questId] = { availEndsAt = unixTime } },
},
Stats = {
  Leaderstats = { Coins = number, ... },
  Progress    = { Pickups = { Coins = number } },
}
```

DataManager provides `GetPlayerData(player)` used by `DataEditor`.
