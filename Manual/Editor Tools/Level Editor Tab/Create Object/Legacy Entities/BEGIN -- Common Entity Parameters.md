# BEGIN -- Common Entity Parameters

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/29796951
- Page ID: 29796951
- Breadcrumb: Editor Tools > Level Editor Tab > Create Object > Legacy Entities > BEGIN -- Common Entity Parameters
- Parent: Legacy Entities

## Content

## Overview

Many objects inside Sandbox will share properties that are applicable to the object so this will expand beyond the scope of just Entities.

This article also contains links to pages that describe the properties of specific entities and groups of entities included with the CryENGINE SDK.

### Standard Parameters

The Standard Parameters pane is where you can adjust standard parameters like the name of your object or the currently selected layer.

The text box at the top of the pane allows you to enter a new name for your object, the default name given is "ObjectTypeX". In the screen shot below, "Rifle1" is displayed, as this is the first Rifle entity to be placed in the world.

![Image](https://www.cryengine.com/docs/static/attachments/56000602)

Some entities have color schemes applied by default, depending on their type. The colored box next to the text box opens the color editor window. This can be used to give particular entities a color scheme of your choosing, if you'd wish to customize this.

Clicking the Browse icon next to the Layer field opens the Select Layer window, allowing you to place your object in the appropriate layer. The text to the right of the layer button tells you which layer is currently selected.

For more information on this, see the [Level Explorer](../../Level%20Explorer.md) documentation.

![Image](https://www.cryengine.com/docs/static/attachments/56000604)

**Parameters** | **Description**
--- | ---
**Name** | Name of the entity.
**Color** | The color that distinguishes the entity on the Level Explorer panel.
**Material** | Clicking the Browse button next to this field will reveal a browser where you can select a material for the entity.
**Minimum Graphics** | When set, the selected object only appears in game detail settings of the desired value and above. (i.e. when set to medium spec, the object will not appear in low spec, but will appear in medium spec, high spec and above). The default minimal spec is Any.

### Entity Params

Modifying the Entity Params enables effects such as wind and shadow to be added to an object and also toggle options such as hiding the object in-game.

**Parameter** | **Description**
--- | ---
**Outdoor Only** | When set, the object will not be render when inside a visarea.
**Cast Shadow MinSpec** | When set, this object will cast a shadow on the selected quality setting and above.
**LodRatio** | Defines how far from the current camera position that different Level Of Detail models for the object are used.
**ViewDistRatio** | Defines how far from the current camera position that the object will be rendered.
**HiddenInGame** | When set, this object will not be shown in pure game mode. Useful for debugging or prototyping in Sandbox.
**Receive Wind** | When set, this object will be influenced by any wind setup in your level.
**RenderNearest** | Used to eliminate z-buffer artifacts when rendering in first person view.
**NoStaticDecals** | If this is set to true, decals will not be rendered on this object.
**Created Through Pool** | This is mostly used on AI entities for memory optimization.

#### Shared Entity Params

There are many cases where parameters will be inherited from higher level scripts such as EntityUtils.lua. Below are some common parameters which you may find in various entities.

Parameter | Description
--- | ---
**CanBreakOthers** | If true entity can apply damage to other breakable objects.
**Faction** | Entity faction (see [Factions](/docs/static/engines/cryengine-3/categories/1638401/pages/13205553)).
**HeavyObject** | **Deprecated**
**InteractLargeObject** | If true, players can trigger large object interactions (such as grab and kick) with the entity.
**Pickable** | If true, players can "grab" or pick the object up (see [Pickable Objects](../../../../Asset%20Prep%20(External)/Asset%20Exporting%20Overview/Geometry%20Creation%20Overview/Interactive%20Geometry/Pickable%20Objects.md)).
**Resting** | If true the object will not spawn in a physically 'awake' state. Instead it will wait until being physically interacted with first. This parameter would be used in the case where you have a floating object you wish to fall (or not) when entering the game.
**Serialize** | If true entity will load/save it’s state.
**SmartObjectClass** | Specifies the smart object type of the object (see [Smart Objects](../../../../Asset%20Prep%20(External)/Asset%20Exporting%20Overview/Geometry%20Creation%20Overview/Interactive%20Geometry/Smart%20Objects.md)).
**Usable** | If true entity is usable by players (see [Adding Usable Support on an Entity](/docs/static/engines/cryengine-3/categories/1638401/pages/1933360)).
**UseMessage** | If **useable** is true this message will be displayed when players are in range. Can be a [localized string](../../../../User%20Interface%20(HUD%20Menu)/UI%20Overview/Localization%20System.md) such as @use_object.
Health |
**Invulnerable** | Object does not receive damage, but will register "Hit" output when applicable.
**MaxHealth** | Health of the entity, how much damage can it take before being considered "Dead" and triggering the output.
**OnlyEnemyFire** | Will only take damage from enemy ([Faction](/docs/static/engines/cryengine-3/categories/1638401/pages/13205553)-based) fire, only if a faction is set.
RenderProxyOptions |
**AnimateOffScreenShadow** | If true, animate the shadow of off-screen objects. By default, objects in the shadow pass do not get added to the active list. This flag changes that behavior. If an object with this flag is rendered in shadow pass, it is kept active for another 8 frames. This allows the shadows of off-screen objects to continue to move along with animations which would otherwise freeze still.
MultiplayerOptions |
**Networked** | If true physics will be simulated on the server and serialized over the network, otherwise they will be simulated on the client.

### Material Layers

**DEPRECATED**

### Entity Properties

The Entity Properties pane is different for each entity as each entity offers different parameters. Please reference individual entity pages for more information.

### Miscellaneous Entity Parameters

This pane contains parameters related to entity scripting and other useful entity functions.

**Parameters** | **Description**
--- | ---
**Edit Script** | Clicking the Edit Script button opens the script file in your [associated program](../../../../CRYENGINE%20-%20Getting%20Started/For%20New%20CRYENGINE%20Users/CRYENGINE%20V%20Basics/Customizing%20CRYENGINE%20Sandbox/Changing%20Sandbox%20Preferences.md) and allows you to modify the script for the selected entity. The script file location is shown above this and the Reload Script button. Clicking the '**>**' button will give you more options related to this file.
**Reload Script** | Click the Reload Script to implement any changes made to the script. This is particularly useful for reviewing Particle Effects as reloading it activates it again.
**Entity Archetype** | If the entity is an Entity Archetype, the name of this Entity Archetype will appear on the button and clicking will open the archetype in the [DataBase View](../../../DataBase%20View.md).
**Create** | Create a new Flow Graph. For more information on flow graphs, please see the [Flow Graph](../../../Flow%20Graph/How%20to%20Use%20Flow%20Graph.md) documentation.
**List** | List Flow Graphs that the selected entity is associated with.
**Remove** | If a Flow Graph was created on this entity, you can remove/delete that Flow Graph via this button.
**Sequence** | If the entity is being used in a Track View sequence the name of the sequence will be displayed here. Clicking on the button will also open up the sequence in the Track View Window.
**Save State** | This saves the physical state of a selected entity (when AI/Physics in turned on). This can be useful for placing physical props realistically around the world without having to manually rotate and align their positions.
**Clear State** | Clears any saved physical state.

### Entity Links

The Entity Links pane displays entities linked to the main entity. Creating an entity link is essentially making a dynamic link which can be referenced in LUA script.

So, for example, if you have a Mission Objective entity you can create a link that can be easily referenced in LUA that tracks a given number of entities on the map.

Or, maybe you have an Explosion Trigger that is linked to multiple entities that when activated will kill all these linked entities.

![Image](https://www.cryengine.com/docs/static/attachments/56000605)

To pick a target, click the **Pick** button and then select the desired entity to create a link. You can select multiple entities one at a time while the button is still active.

The Pick Target button will glow while it's active. Once you're done with selection, press ESC or click the button again to deactivate it.

### Entity Property Panes

The following property panes are only visible for certain entities, however, they are standard panes that function the same regardless of which entity they are modifying.

#### Attached Entities

The Attached Entities pane enables you to create links to other objects in the perspective viewport.

This pane sometimes appears combined with the Shape Parameters pane but it's functionality remains the same.

**Option** | **Description**
--- | ---
**Pick** | Links two objects, click an object that you would like to link with another object and click the Pick button and finally your desired object. You will visually see the link in the perspective viewport and see the object name in the target window.
**Remove** | Removes a link between two objects, click the desired object in the Target window and click Remove.
**Select** | Selects an object from the Target window. Double-clicking the object name in the Target window will also select the object.

#### Shape Parameters

The Shape Parameters pane allows you to edit the area of effect for a shape and create links to other objects in the perspective viewport.

**Parameters** | **Description**
--- | ---
**Num Points** | Num Points relates to the number of points the shape contains in the perspective viewpoint.
**Edit Shape** | Clicking the Edit Shape button turns on the shape editing mode and allows you to edit the selected shape.
**Use Transform Gizmo** | When in editing mode, checking the Use Transform Gizmo check box will turn on the Transform Gizmo helper.
**Reverse Path** | The Reverse Path button is used with objects like AIPath and when clicked will reverse the AI path. The arrow on screen will point in the opposite direction to show the new path direction.
**Split** | Press the Split button and click two parts of your shape to split your shape and create a new independent shape.
**Reset Height** | This button will flatten the shape and all other points to the height of the selected point.
**Pick** | Links a shape to an object, click a shape that you would like to link another object and click the Pick button and finally your desired object. You will visually see the link in the perspective viewport and see the object name in the target window.
**Remove** | Removes a link between the selected shape and an object, click the desired object in the Target window and click Remove.
**Select** | Selects an object from the Target window. Double-clicking the object name in the Target Window will also select the object.

[Standard Parameters](#standard-parameters)[Entity Params](#entity-params)[Material Layers](#material-layers)[Entity Properties](#entity-properties)[Miscellaneous Entity Parameters](#miscellaneous-entity-parameters)[Entity Links](#entity-links)[Entity Property Panes](#entity-property-panes)
