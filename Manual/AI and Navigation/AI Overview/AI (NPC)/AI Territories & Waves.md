# AI Territories & Waves

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/25535416
- Page ID: 25535416
- Breadcrumb: AI and Navigation > AI Overview > AI (NPC) > AI Territories & Waves
- Parent: AI (NPC)

## Content

![Image](https://www.cryengine.com/docs/static/attachments/29933202)

## What are AI Territories and Waves

AI Territories and Waves (T/W) help Level Designers to control the number of active AIs (AI entities) at any time in the game using simple flowgraph logic. T/W should not be used for vehicle AI.

A Territory is a shape that defines an area. All AIs assigned to a Territory can be activated, deactivated, and spawned with a single flownode. Optionally, Waves are contained in Territories and allow independent AI activations inside a Territory.

T/W allow Level Designers a much easier and faster setup for AI in their levels and significantly speed up debugging AI flowgraph issues. Controlling AI with this system also helps designers to not exceed the maximum number of allowed active AIs. This is especially important on consoles.

## Sections

[What are AI Territories and Waves](#what-are-ai-territories-and-waves)[Sections](#sections)[Example Usecases](#example-usecases)[What is an Entity Pool?](#what-is-an-entity-pool)[AI Territories](#ai-territories)[AI Waves](#ai-waves)[AI Entity Properties](#ai-entity-properties)[How to set up AI Territories](#how-to-set-up-ai-territories)[How to set up AI Waves](#how-to-set-up-ai-waves)[Debugging Waves](#debugging-waves)[Debugging Entity Pools](#debugging-entity-pools)

### Example Usecases

AI Territories and Waves (T/W) help Level Designers to control the number of active AIs (AI entities) at any time in the game using simple flowgraph logic. T/W should not be used for vehicle AI.

A **Territory** is a shape that defines an area. All AIs assigned to a Territory can be activated, deactivated, and spawned with a single flownode. Optionally, ** Waves** are contained in Territories and allow independent AI activations inside a Territory.

T/W allow Level Designers a much easier and faster setup for AI in their levels and significantly speed up debugging AI flowgraph issues. Controlling AI with this system also helps designers to not exceed the maximum number of allowed active AIs. This is especially important on consoles.

A simple example of T/W usage would be:

- An action bubble is surrounded by a Territory.
- Each AI encounter is a single Wave.
- When the player enters the action bubble, its Territory is enabled and all Territories from other action bubbles are disabled. This ensures, that no unnecessary AIs are active.
- Inside the action bubble, the encounters are triggered as before, except that designers now need only one flownode to activate/deactivate an encounter instead of nodes for each AI instance. It's also not needed any more to deactivate all AIs manually on level start, because T/W and their assigned AIs are disabled from start automatically.
- The AI status is stored when a T/W gets disabled. When the player goes back to a previous AB that was disabled when he left it before, the same AIs will be active again.

### What is an Entity Pool?

It's a collection of empty slots with which an entity of a given type can be prepared from. It's a way to control the number of entities that exist in memory.

An entity pool is created by filling the slots with a specific number of "empty" entities of a given type - AI, vehicle, item, rigid body, etc... The intention is to reuse these slots over and over for all the entities of that type which exist in the world, bringing them into existence when they're needed and removing them when they're not so that others may be used in place. Where as before, a level may have created over 100 AI entities and only use 8 to 16 of them at a time. While only these that are being used are being drawn and updated, the other AI entities still exist in memory and are looked at by the game at various moments (such as saving and loading). When using a pool, we remove those excesses from memory by ensuring only 16 (or however large the pool is) ever exist in memory.

When an entity is set to go through an entity pool, it is not created when the level is loaded. Instead, the information specific to it is saved. When the entity is later needed during the progression of the game, the entity is **prepared** from the pool. When the entity is no longer needed, it is ** freed** back to the pool.

There is a hard limit to the number of entities which can exist in the pool. As an example, for Crysis 2, this number is 12 for the AI. That means if you try to prepare more than 12 AI from the pool, it will fail. The game will still continue to run, but no 13th AI will be created. You must be aware of your numbers and control them accordingly.
When an AI entity is marked as being created through the pool and it is used inside of an AI Wave, you do not need to manually prepare or free this AI! Instead, you only have to enable/spawn the AI Wave. All pooled AI entities inside that wave will then be prepared and enabled for you, resulting in consistent behavior as expected with AI Waves. Furthermore, if you disable the AI Wave, all pooled AI entities inside that wave will be freed. With this in mind, your existing Flowgraph for controlling the AI Wave should be sufficient enough to deal with the AI entities inside being pooled.

When an AI has been killed, the AI entity does not need to be freed right away. A dead AI is placed in a go-between state: it is still taking up a slot in the pool, but if a slot is desperately needed, the slot containing the dead AI will be automatically freed and used by the system. If there is more than 1 AI dead, the furthest one away from the player will be used instead. Dead AI does not need to be freed!

However, it is still a good idea to free any AI (by either disabling the AI Wave they are in or manually freeing them) when they are no longer needed, such as when the player has moved on to the next action bubble or entered a point in the level where he cannot backtrack any further. Doing so helps the system out, and that's a good thing.

### AI Territories

- AI Territories can be edited like AreaShapes.
- They should be placed around an area where the containing AIs can navigate.
- The *ActiveCount* and * BodyCount* outputs are useful to check whether it's necessary to respawn new AI.
- Overlapping Territories are possible. But be careful with automatically assigned AIs in this case.
- When a Territory is selected, all assigned AI are marked with a blue icon to quickly identify them.

**Properties:**

Property | Description
--- | ---
**Height** | Defines the height, if used as a 3D Territory 0 = infinite height (2D Territory)
**DisplayFilled** | Defines if the shape is drawn filled or not, like in AreaShapes
**Shape Parameters** | The Territory shape can be edited like AreaShapes. Waves need to be picked in the same way as triggers are picked from AreaShapes.
**Assigned AIs** | Displays the number of AIs which are assigned to this Territory
**Select Assigned** ** AIs** | By pressing this button, all assigned AIs will be selected, the Territory itself will be deselected

**Flownode:**

Input | Description
--- | ---
**Disable** | Disable the Territory
**Enable** | Enable the Territory
**Kill** | Kills all active AIs of this Territory
**Spawn** | (Re-)Spawn AIs assigned to this Territory (but not assigned to any Wave)
Output | Description
**ActiveCount** | Outputs the number of currently active AIs assigned to this Territory.
**BodyCount** | Outputs the number of killed AIs assigned to this Territory.
**Dead** | Fires when all AIs assigned to this Territory are dead (works also for respawned AIs).
**Disabled** | Fires when the Territory gets disabled (it doesn't fire on level start, although all Territories are disabled from start automatically).
**Enabled** | Fires when the Territory gets enabled.
**Spawned** | Fires when AIs are spawned via the *Spawn* input (if the Territory was disabled before, it gets enabled and the * Enabled* output fires as well).

### AI Waves

- Waves are linked to Territories like triggers are linked to shapes.
- To enable/spawn a Wave, its Territory must be enabled.
- The *ActiveCount* and * BodyCount* outputs are useful to check whether it's necessary to respawn new AIs.
- When a Wave is selected, all assigned AIs are marked with a green icon to quickly identify them

**Properties:**

- It's not possible to have more than one wave with the same name

Property | Description
--- | ---
**Assigned AIs** | Displays the number of AIs which are assigned to this Wave.
**Select Assigned AIs** | By pressing this button, all assigned AIs will be selected, the Wave entity itself will be deselected.

**Flownode:**

Input | Description
--- | ---
Disable | Disable the Wave
Enable | Enable the Wave
Kill | Kills all active AIs of this Wave
Spawn | (Re-)Spawn AIs assigned to this Wave
Output | Description
ActiveCount | Outputs the number of currently active AIs assigned to this Wave
BodyCount | Outputs the number of killed AIs assigned to this Wave
Dead | Fires when all AIs assigned to this Wave are dead (works also for re-spawned AIs)
Disabled | Fires when the Wave gets disabled (it doesn't fire on level start, although all Waves are disabled from start automatically)
Enabled | Fires when the Wave gets enabled
Spawned | Fires when AIs are spawned via the *Spawn* input (if the Wave was disabled before, it gets enabled and the * Enabled* output fires as well)

### AI Entity Properties

#### Territory & Wave

Property | Description
--- | ---
**Territory** | Assigns the AI to a Territory: - "<Auto>": The AI is automatically assigned to the Territory it is inside - "<None>": The AI is not assigned to any Territory (default) - *TerritoryName*: The AI can be manually assigned to any Territory of the level
**Wave** | Assigns the AI to a Wave: - "<None>": The AI is not assigned to any Wave (default) - *WaveName*: The AI can be manually assigned to a Wave of its Territory (The AI must be assigned to the Territory first, before Waves are selectable)

#### Entity pool - Marking an entity to go through a pool

To mark an entity as going through a pool, you need to tick its '**Created Through Pool**' property as true. This can be done either through the Archetype or on each individual entity via its Params on the Rollup Bar. The latter overrides the former's setting.

When the level is loaded in the [Launcher](/docs/static/engines/cryengine-3/categories/1638401/pages/1605722), the entity will be correctly setup to work with the pool if a pool exists to handle it. If not, the entity will be created as normal.

The '**HiddenInGame**' property can be used in conjunction. If this is not ticked (set to FALSE), the entity will be automatically prepared from the pool on level start. If ticked (set to TRUE), the entity will not be prepared until you explicitly call on it via Flowgraph (see below).

### How to set up AI Territories

- Add some AIs to the level.
- Add an *AITerritory* from * Entity/AI* to your level like an AreaShape.

- Select the AI and choose the Territory name in its properties.

- Select the *AITerritory* again and * Add Selected Entity* to your flowgraph
- Now you can easily enable, disable and spawn/re-spawn all AIs which are assigned to this Territory with just one flownode
- Territories and Waves are disabled from start by default. There is no need to trigger the disable input from a start node
- After adding, removing or editing a Territory shape, it's necessary to regenerate AI navigation

### How to set up AI Waves

- Add an *AIWave* entity from * Entity/AI* to your level (which is already set up with an AI Territory).

- Select the Territory which should contain the Wave and pick the Wave entity like you would pick a trigger with an AreaShape.

- Select the AI and choose the Wave name in the AI properties. Note that you have to assign them to a Territory first before you can select a Wave.

- Add the Wave to your flowgraph like you did with the Territory.
- Remember that the Territory has to be enabled before you can enable a Wave.

### Debugging Waves

```
ai_DebugDrawEnabledPuppets 1       Displays all enabled AIs and their Territories & Waves in the center of the screen
ai_DebugDrawTerritoriesAndWaves 1  Displays Territory & Wave below each AI (_ai_DebugDraw_ needs to be on)
ai_StatsDisplayMode 1              Not related to T/W but very useful to check the number of currently active AI
```

### Debugging Entity Pools

**How do I know if my level is prepared for Entity Pools?**

Simple! First, open your level in the game launcher. Once loaded, type the following into your console:

```
es_DebugPool 1
```

You will see a bunch of text appear in the top-left corner. One of the lines will mention "*Bookmarked Entities*" and have a count beside it.

If you know there are AI or other entities in your level which should have their "**Created Through Pool**" option ticked to true and this count is ** higher than 0**, then the level is prepared and ready to go!

If the count is **at 0**, then the level is not prepared for entity pooling. In such a case, try the following:

- Verify the archetype has the "**Created Through Pool**" option ticked to true if it should.
- Verify the entity's param on its rollup bar has the "**Created Through Pool**" option ticked to true if it is not an archetype and it should.
- Re-export your level.

**How do I know if the pool is full in my level?**

This may also interest you if you want to see how the entity pool is being utilized in your level. First, open your level in the game launcher. Once loaded, type the following into your console:

```
es_DebugPool 1
es_DebugPoolFilter AI
```

... where '*AI'* should be replaced with the name of the entity pool you want to test. The names of all pools will be visible if you keep "* es_DebugPoolFilter*" cleared.

What you should see is a bunch of text in the top-left corner of your screen. The pool's information and contents will be displayed.

The following are the useful bits to take from this output:

- Bookmarked Entities - Number of entities marked as being created through pools. It should be > 0 if you have AI in your level which should be marked.
- Pool *'Name'* - The entity pool whose information is about to follow, with its name listed. This name should be assigned to "*es_DebugPoolFilter*" to get more information about the pool, as mentioned above. The color highlight on this text means the following:
- **White** means the pool has no issues and is being used without any major concerns thus far.
- **Yellow** means the pool has reached its max capacity at some point during the level. It is a warning: the pool is still being used correctly, but we're at our limit! So be mindful.
- **Red** means the pool reached its max capacity and another entity was trying to be prepared from the pool. The pool could not comply, so the entity was not prepared.
- Not In Use - The current number of slots in the entity pool which are not in use. In this case, *15* slots are free for AI to use.
- In Use - The current number of slots in the entity pool which are currently being used. In this case, *1* slot is being used.
- Below this output, the AI who are currently prepared from the pool and exist will be shown, followed by their EntityId.
- Pool Definitions - The entity classes which exist in the pool. In this case, the AI pool is shown to work with all the Alien classes and the HumanGrunt class.
- Max count (size of the pool) is displayed here on the first line.
- The color highlight of the class name displays information about how that class has been used with the pool. On PC, this color will change.
- **White** means no entities have been prepared from the pool yet of that class type.
- **Green** means at least one has been prepared and all so far have been prepared successfully.
- **Red** means at least one has been prepared but it failed when being prepared.
