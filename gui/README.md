# GUI: Prompts & Dialogs

**Server → Client channel**
- RemoteEvent: `ReplicatedStorage.GuiRemotes.GuiPush`
- Payloads:
  - `promptUpsert`: `{ key, questId, mutatorId, target, text, dialog?, tokenMap? }`
  - `promptClear`: `{ key }`
  - `dialogUpsert` / `dialogClear` (not always used)

**Client**
- `GuiClientHandler` receives, creates/upserts UI using `TemplatesExtra` components.
- Clicks are routed via `GuiRouter` with attributes (e.g., `Gui_ProfileKey="QuestHub"`, `Gui_OnClick="AcceptQuest"`).

**Templates**
- [`TemplatesExtra.lua`](templates_extra.md) defines the visuals for world prompts (BillboardGui) and screen dialogs.
- Colors & padding are easy to tweak without changing structure.
