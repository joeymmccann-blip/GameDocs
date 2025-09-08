# Catalog.lua (examples)

```lua
return {
  {
    id = "HELLO_NEIGHBOR_ADV",
    title = "Hello Neighbor",
    autoAccept = false,
    autoClaim  = false,
    steps = {
      step1 = {
        id = "Step_DoObjective",
        objectives = {
          { id="collect", type="pathDelta",
            path={"Stats","Progress","Pickups","Coins"}, amount=3, label="collect 3 Coins" },
        },
        mutators = {
          { id="TalkBubble_Active", type="guiPrompt",
            target={ kind="part", path="Workspace/NPCs/ShopKeeper01" },
            visibleIf = "inStep:step1",
            onEnter = { template="PromptBubble", text="{action} to talk",
              action={ type="openDialog", dialogId="ACTIVE_GATE" } },
            onExit = { hide=true } },
        },
      },
      step2 = { id = "Step_TurnIn", objectives = {} },
    },
    ui = { dialogs = { /* see repo for full spec */ } },
    rewards = { currency = { Coins = 100 } },
    cooldownSec = 900, -- example gate
  },
}
```

**Per-quest modules**
If you prefer modular quests, place modules under `ServerScriptService/.../Players/Quests/CatalogParts/` and enable `CatalogLoader` to merge them, so `Catalog.lua` stays tidy.
