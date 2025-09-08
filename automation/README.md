# Automation & Resets

**Daily/Weekly gates**
- `Engine` uses a UTC cutoff hour (`Rules.DayCutoffUTC`) to decide day rollover.
- Availability reset modes: `reset="day" | "week"` checked in `EvaluateAvailability`.

**Cooldowns**
- `cooldownSec` per quest places a unix timestamp into `Quests/Cooldowns[questId]` on completion.
- Checked inside `CanAccept`/`EvaluateAvailability` to hide/disable until elapsed.
