# Game Systems Docs (Roblox / LuaU)

These notes describe the systems currently implemented in the project. They aim to be clear and practical rather than flashy. The focus is on how to read the code, how modules fit together, and how to extend them safely.

> Scope: quests, data layer, events, collectables, GUI prompts/dialogs, leaderboards, light spawning hooks, logging.
> Out of scope (not built yet): inventory, combat, crafting.

## Contents
- [Architecture](architecture.md)
- Data Layer: [`data/`](data/README.md)
- Events: [`events/`](events/README.md)
- Quests: [`quests/`](quests/README.md)
- Collectables: [`collectables/`](collectables/README.md)
- Touch / Triggers (generic): [`touch/`](touch/README.md)
- GUI: [`gui/`](gui/README.md)
- Spawning: [`spawning/`](spawning/README.md)
- Leaderboards: [`leaderboards/`](leaderboards/README.md)
- Automation & Resets: [`automation/`](automation/README.md)
- Logging: [`logging.md`](logging.md)
- Dev Checklist: [`dev-checklist.md`](dev-checklist.md)

## Quick Start
1. Open the place in Studio and start a server with 1 client.
2. Confirm server output shows *DataEditor Initialized* and *Quests Binders initialized*.
3. Talk to the ShopKeeper and run through **HELLO_NEIGHBOR_ADV**.
4. Pick up a coin to exercise `CollectableHandler` and quest bumps.

## Known Limitations (honest list)
- Quest cooldown gating may need additional checks in `Engine.CanAccept` for strict non-repeatable flows.
- `TouchDetection` exists but many pickups are handled directly by `CollectableHandler` touch.
- GUI prompt styling is simple; colors and spacing are configurable in `TemplatesExtra` and client.
- Cooldown/availability UX (hiding prompts) still being refined.
