
# Unreal Multiplayer Football Prototype

A small Unreal Engine prototype focused on building a basic football match and layering multiplayer replication on top of it.

The goal of this project was to understand authoritative server architecture, RPC flow, and gameplay-state synchronization.

![Gameplay Screenshot](Images/Kickoff.png)

## Core Gameplay

- Two opposing goals (Left / Right)
- Physics-driven ball actor
- Dash mechanic toward focused ball
- Goal detection via hitbox overlap
- Score-triggered goal reaction (color + movement)
- GameMode-controlled ball spawning

## Multiplayer Implementation

- Authoritative server model  
  - Client overlap → `Run On Server` validation  
  - Server executes scoring logic  
  - `Multicast` propagates visual reactions  

- Deterministic team spawning  
  - Server = Left team  
  - Client = Right team  

- Replicated visuals  
  - Goal color reaction synchronized  
  - UI score updates replicated  
  - Dynamic Material Instances used for team colors  

- Reduced runtime lookups  
  - Minimized `Get All Actors Of Class`  
  - Cached references where appropriate  


---

See `VersionLog.md` for iteration history.



