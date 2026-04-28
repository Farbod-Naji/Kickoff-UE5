# Version Log

## V1.0.0  
_Initial Playable Football Prototype with Network Replication_

### Core Football Functionality

- Implemented basic match loop  
  - Two opposing goals (Left / Right)  
  - Ball actor with collision and physics simulation  
  - Goal detection via hitbox overlap  

- Implemented player interaction system  
  - Player focuses on Ball actor during movement  
  - Dash mechanic toward focused Ball actor  
  - Physics-driven interaction (intentionally unpolished prototype state)  

- Implemented scoring system  
  - Goal overlap triggers score event  
  - Visual goal reaction (frame color change)  
  - Animated goal movement using `MoveComponentTo`  

- Implemented team structure  
  - Introduced `E_Team {Left, Right}` enum for side ownership  

- Built controlled ball spawning  
  - GameMode validates active ball count before spawning  

### Network Replication & Duplication System

- Established authoritative server model  
  - Client overlap → `Run On Server` validation  
  - Server executes scoring logic  
  - `Multicast` propagates goal reaction visuals  
  - Prevented client-side score execution  

- Replicated gameplay state across instances  
  - `BP_Goal` randomized color reaction synchronized on all clients  
  - UI score updates replicated across server and client  
  - Goal animation state synchronized  

- Implemented deterministic team spawning (GameMode)  
  - Server player assigned to Left team  
  - Client player assigned to Right team  
  - Spawn logic executed only on authoritative instance  

- Implemented replicated team visuals  
  - Replaced player materials with Dynamic Material Instances on spawn  
  - Modified `M_Manniqune` to support clean runtime color overrides for `MI_Quinn`  
  - Assigned team color at runtime  
  - Replicated material parameter changes across server and client  

- Reduced expensive runtime lookups  
  - Minimized `Get All Actors Of Class` calls  
  - Cached actor references where appropriate  

----

# Dev Log (unreleased changes)

## V1.0.0-dev.1
_2026-04-28_
- optimized images by reducing resolution and converting to WebP for faster load times