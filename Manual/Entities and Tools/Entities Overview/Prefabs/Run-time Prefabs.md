# Run-time Prefabs

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/26215402
- Page ID: 26215402
- Breadcrumb: Entities and Tools > Entities Overview > Prefabs > Run-time Prefabs
- Parent: Prefabs

## Content

##
Overview

Run-time prefabs are designed to expose the concepts of prefabs to the game (it has been an Editor-only concept so far).

In the example below we have a level for short multiplayer sessions and we will look at a building within this level which contains other objects.

The system is already built to work synchronized over network. Support for Designer objects is in beta stage.

##
Setup

1) Drag & drop the prefab as usual from the Database View. Note the naming convention used for the prefabs variations group.

2) A tool has been added to convert back and forth between Prefab and run-time prefab entity. Right click on the prefab and choose "Convert to Procedural Object".

3) Note how this now becomes an entity, containing all the prefab objects (see the postfix _prc has been added to the name). The entity fields are automatically filled in (entity library and current prefab selection).

Number of spawn is limiting the number of occurrences that this prefab can be spawned in the level (0 means no limit). This entity is now like a regular entity that can be manipulated even from FlowGraph etc.

4) This entity will now spawn at run-time.

You can simulate this by clicking on "Reload Script".

5) When you are done playing around, you can right click on the PRC and do "Convert to Prefab" and will convert back to the prefab in step 1.

Now you can continue editing as normal if you wish.

Make sure to leave it as a PRC entity (step 3) before you export the level. Otherwise the prefab will be exploded to single objects in the level, and will not be available as a runtime prefab in the game (won't be accessible to game logic)
Technical note
When you export to game a regular Editor Prefab, the single entities inside the prefabs are "exploded" into the level XML.

Thus the game and engine have no knowledge of the Editor Prefab concept. But when you export a run-time prefab entity instead, the level XML will now contain only the prefab entity proxy reference.

The corresponding XML prefab library will be loaded automatically. This allows the game to access the high level concept of prefabs at run-time.
