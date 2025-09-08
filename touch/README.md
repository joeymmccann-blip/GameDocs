# TouchDetection (generic)

A generic trigger router that normalizes `Touched/TouchEnded` → `onEnter/onStay/onActivate/onLeave` for handlers. Useful where you want hold-to-activate or cooldowns.

Current pickups use direct `CollectableHandler` touch for simplicity, but `TouchDetection` is kept for future interactions (e.g., doors, levers).
