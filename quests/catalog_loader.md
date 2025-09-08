# CatalogLoader.lua

Purpose: allow a mixed approach — keep a small curated `Catalog.lua`, and merge in additional quests from a folder when present.

**Rules**
- Only ModuleScripts returning a single quest table or an array of quests.
- Duplicate `id` is ignored unless `preferFolder = true` is set in loader options.

**Usage**
```lua
local Catalog = require(script.Parent.Catalog)
local Loader  = require(script.CatalogLoader)
local merged  = Loader.Merge(Catalog, script.Parent:FindFirstChild("CatalogParts"))
return merged
```
