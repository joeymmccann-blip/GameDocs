# BoostData

World catalogs that define currencies and their canonical `path`.

Example:
```lua
currencies = {
  Coins = {
    name = "Coins",
    path = { "Stats","Leaderstats","Coins" },
    BaseValue = 1,
    BaseXp = 1,
  },
  XpBase = { name = "XpBase", path = { "Stats","Progress","XpBase" } },
}
```
