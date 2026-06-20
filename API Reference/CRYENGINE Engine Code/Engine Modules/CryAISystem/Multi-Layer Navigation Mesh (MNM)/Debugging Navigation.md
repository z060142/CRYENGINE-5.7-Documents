# Debugging Navigation

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/24281245
- Page ID: 24281245
- Breadcrumb: CRYENGINE Engine Code > Engine Modules > CryAISystem > Multi-Layer Navigation Mesh (MNM) > Debugging Navigation
- Parent: Multi-Layer Navigation Mesh (MNM)

## Content

Ensure to have the cvar ai_debugDraw set to 1 in order for other cvars to show their debug information:

```
ai_debugDraw 1
```

### Debugging the NavMesh

CVar/Command | Values | Description
--- | --- | ---
ai_debugMNMAgentType | e. g. "`MediumSizedCharacters`" | specifies the name of the Agent type for which to draw the NavMesh
ai_debugDrawNavigation | 0/1/2/3/4/5 | draws the NavMesh with additional information (triangles, islands, etc.) depending on the value of this cvar
ai_DebugDrawNavigationWorldMonitor | 0/1 | draws red bounding boxes whenever the NavMesh gets regenerated due to world changes
ai_MNMAllowDynamicRegenInEditor | 0/1 | if enabled, regenerates the NavMesh whenever switching between edit and game mode in Sandbox to ensure the NavMesh is up-to-date when all affecting objects are reverted to their initial state
ai_MNMDebugAccessibility | 0/1 | if enabled, draws areas that are disconnected from other areas in red
ai_MNMProfileMemory | 0/1 | if enabled, draws information about the current memory usage, number of triangles, etc. of the NavMesh on a per-Agent basis

### Debugging Pathfinding and Pathfollowing

CVar/Command | Values | Description
--- | --- | ---
ai_DrawPath | "`none`", "` all`", (desired entity name) | draws line-segments and path node numbers along the found path that is about to get traversed
ai_DrawPathFollower | 0/1 | draws debug information about the look-ahead position to follow while traversing the whole path
ai_DebugPathfinding | 0/1 | prints some information about the start/end points of the found path to the console
