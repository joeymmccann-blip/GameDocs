# EventCaller

Simple facade with one of these signatures (implementation may vary):
```lua
EventCaller.Fire(name, ...)
EventCaller.Listen(name, callback)
-- or EventCaller.On / Subscribe / Connect (the code defers to what's available)
```

**Common events**
- `StatChanged` (from DataEditor)
- `PickupCollected` (from CollectableHandler)
- Quest bus: `QuestAccepted`, `QuestStepAdvanced`, `QuestCompleted`, `QuestClaimable`, `QuestAbandoned`, `QuestVisibility`
- GUI feed: server emits prompt/dialog changes to clients via `GuiPush` RemoteEvent.
