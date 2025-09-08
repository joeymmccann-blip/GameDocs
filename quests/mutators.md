# Mutators.lua

Lightweight side effects tied to quest/step state.

Supported types (as used in project):
- `guiPrompt`: server pushes prompt/dialog payload to clients via `GuiPush`.
- `spawnSet`: enable/disable groups.
- `toggleInstances`: set Visible/Collidable for tagged items.
- `uiHint`: simple on-screen hint (optional).

The server calls `Mutators.ApplyForStep(player, questId, stepDef)` when a step becomes active and `ClearForStep` when leaving.
