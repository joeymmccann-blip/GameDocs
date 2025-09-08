# TemplatesExtra.lua

Two components used by the client:

## `PromptBubble(opts)`
- World-anchored billboard prompt with text + button.
- `opts.anchorInstance` (Model/BasePart), `opts.text`, `opts.name`

## `DialogScreen(opts)`
- Simple bottom-center dialog panel with a text body and a horizontal button row.
- Buttons are filled dynamically by the client using the quest dialog spec.
- Style constants are at the top of the module so you can change colors/padding without changing behavior.
