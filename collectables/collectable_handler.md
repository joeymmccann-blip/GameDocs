# CollectableHandler.lua

**How it works**
- Watches spawned collectable models/parts; connects `.Touched` once.
- Debounces per-instance to prevent multiple awards.
- Currency lookup order: `CollectionService` tag, then instance `Name`, matched (case-insensitive) to BoostData currency keys/names (with singular/plural fallback).

**Quest integration**
- `PickupCollected` payload includes `tag` and `tagLower`. Quest listeners map this to `Engine.Bump(... type="collectItem")`.

**Stats path**
- Coins example: `{"Stats","Leaderstats","Coins"}` from BoostData.World1.
- Progress counter example used by docs: `{"Stats","Progress","Pickups","Coins"}` for pathDelta.
