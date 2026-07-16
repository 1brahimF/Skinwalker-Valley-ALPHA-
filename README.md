Skinwalker Valley

A survival horror game built in Roblox Studio, set in a foggy, procedurally generated forest inhabited by skinwalkers — shapeshifting entities from folklore that mimic voices and appearances to lure their prey.

Overview

No two runs are the same. Structures and trees regenerate at randomized points across the map each session, keeping the forest layout unpredictable while the fog and lighting keep visibility (and nerves) low.

Status: Work in Progress (ALPHA)

Implemented


Procedural structure generation — structures spawn at randomized points across the map each session, with weighted randomization for variety
Procedural tree generation — trees scatter across terrain using raycasting to detect ground level, with minimum-spacing logic to prevent overlap and randomized rotation per tree
Atmosphere — fog distance/color and lighting configured for horror tone
Hotbar/inventory system — in progress


Known Issues


PlayerSetup — syntax error, missing end (script does not currently compile)
StructureSpawner — math.random invalid interval error on line 30, likely a min/max range mismatch
DataStore calls fail in Studio testing (StudioAccessToApisNotAllowed) — expected until "Enable Studio Access to API Services" is turned on, or until published


Not Yet Started


Skinwalker AI — pathfinding, detection, chase behavior, and voice/appearance mimicry mechanic
Structure interiors / loot systems
Sound design (ambient forest, skinwalker audio cues, tension/jumpscare stings)
Full UI/UX pass (menus, HUD)


Project Structure

ServerScriptService/
├── Tree Gen              -- procedural tree scattering (raycast-based ground placement)
├── StructureSpawner       -- procedural structure generation at spawn points
├── PlayerSetup             -- player initialization (currently broken, needs fix)
├── HotbarController       -- inventory/hotbar system (in progress)

ServerStorage/
├── TreeModels             -- tree model prefabs used by Tree Gen
├── StructurePrefabs       -- structure prefabs used by StructureSpawner

Workspace/
├── Terrain
├── Structure(ALPHA)
├── StructureSpawnPoints
├── Invisible SpawnPoints

Tech Notes


Tree/structure placement uses Workspace:Raycast() to find terrain height at randomized X/Z coordinates
Tree models require their pivot point set to the trunk base (via Studio's Set Pivot tool) for correct ground placement — models without this will spawn floating or sunk into terrain
Spacing between generated objects is enforced via a minimum-distance check against previously placed positions


How to Test


Open in Roblox Studio
Run the game (Play or Server+Client test)
Tree Gen and StructureSpawner scripts execute on server start and populate the map
Check the Output window — the two known script errors above will appear but do not block generation


Roadmap


Fix PlayerSetup and StructureSpawner errors
Build skinwalker AI (movement, detection, mimicry)
Sound design pass
UI/UX pass
Playtesting and balancing generation density/spacing
