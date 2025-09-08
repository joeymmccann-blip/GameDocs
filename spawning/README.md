# Spawning / World Binds

- Example file `BindWorld1Updates.lua` enables/disables spawn sets and connects upgrade purchases or other world-specific counters.
- Mutators can toggle spawn sets and tagged gates while a step is active:
  ```lua
  { type="spawnSet", id="FarmCrates", onEnter="enable", onExit="disable" }
  ```
