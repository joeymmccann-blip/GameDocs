# CatalogLoader

Load inline quests + per-quest modules from a folder and merge (ensure unique ids).

```lua
local CatalogLoader = require(SSS.GameStuff.Players.Quests.CatalogLoader)
return CatalogLoader.Merge({ folder = script.Quests, list = { -- inline quests } })
```
