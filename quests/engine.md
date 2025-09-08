# Engine.lua

Central state machine.

## Accept
- Creates `Active[questId]` with `stepIdx=1`, `progress={}`, `vars=baselines`.
- Applies step mutators (UI/world effects) and emits `QuestAccepted`.
- Hides pre-accept surfacing via `QuestVisibility` events.

## Bump & Deltas
- `Engine.Bump(player, {type="collectItem", tag="Coins"})`
  Increments matching objectives up to their `amount`.
- `Engine.PollDeltas(player)`
  Recomputes `"currencyDelta"`/`"pathDelta"` from baselines.

## Timers
- Per-step timer: `timerSec` + `startTimerWhen` (`"enterStep"` or `"firstBump"`).
- Failure policy: `retryStep` (with `maxRetries`) or `failQuest` → `Abandon`.

## Completion
- When all objectives in a step are satisfied: advance to next step.
- If no next step:
  - If `autoClaim=false`, marks entry `state="claimable"` and emits `QuestClaimable`.
  - Else, grants `rewards`, moves to `Completed`, starts cooldown if configured, and emits `QuestCompleted`.

## Availability
- Absolute window (`startAt/endAt`), rolling window (`windowSec`), daily/weekly reset, and `cooldownSec` checks in `CanAccept`/`EvaluateAvailability`.
