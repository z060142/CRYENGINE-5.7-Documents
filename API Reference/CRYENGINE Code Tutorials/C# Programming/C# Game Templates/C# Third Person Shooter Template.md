# C# Third Person Shooter Template

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/29791358
- Page ID: 29791358
- Breadcrumb: CRYENGINE Code Tutorials > C# Programming > C# Game Templates > C# Third Person Shooter Template
- Parent: C# Game Templates

## Content

The Third Person Shooter template is a simple example of a Third Person Shooter to get you started. The template shows you how to:

-
Use action maps to receive input from the user.

-
Delegate functionality to another EntityComponent.

-
Control animations on a character.

-
Set up physics for characters.

-
Receiving collision messages.

-
Using surface types to handle interactions between entities.

[#general-setup](
General Setup
)
[#action-maps](
Action Maps
)
[#character-animator](
Character Animator
)
[#character-physics](
Character Physics
)
[#collision-messages](
Collision Messages
)
[#material-effects](
Material Effects
)
Related Content:

-
[/docs/static/engines/cryengine-5/categories/23756813/pages/26875052](
C# API Reference
)

-
[/docs/static/engines/cryengine-5/categories/23756813/pages/29791112](
C# Programming
)

##
General Setup

When you launch the template in the GameLauncher it will first load the Example map. This is done by adding a map-command to the game.cryproject file of the project, which can execute several console variables and console commands on startup. Once the map is loaded, the
**
Player
**
 component handles all the user input and translates it to actions in the game. The
**
Player
**
 class initializes itself in two steps. First in
**
OnInitialize
**
 which is called after the map is done loading. The next part of initialization is done in
**
OnGameplayStart
**
 which is called every time when the Sandbox moves into play-mode, or in the case of the GameLauncher after all
**
OnInitialize
**
 methods have been called. Once the game is running the engine will call
**
OnUpdate
**
 every frame which will update all the gameplay logic.

##
Action Maps

Instead of using the
[/docs/static/engines/cryengine-5/categories/28704771/pages/29448891](
Input
)
 class to receive the input from the user, this template uses
[/docs/static/engines/cryengine-5/categories/23756813/pages/23306384](
action maps
)
. Action maps makes it easier to change the controls later on without having to rewrite the code. In C#, this is achieved by using the
[/docs/static/engines/cryengine-5/categories/28704771/pages/29448762](
ActionHandler
)
 class. To use the
**
ActionHandler
**
, you need to initialize it by providing the path to the .xml-file that contains the action map, and the name of the action map that needs to be loaded. Once the
**
ActionHandler
**
 is initialized, you can add handlers to specific actions by calling
[/docs/static/engines/cryengine-5/categories/28704771/pages/29448762](
AddHandler
)
 with the name of the action and a delegate that gets called when the action is triggered.

More details on how to set up an action map can be found on the
[/docs/static/engines/cryengine-5/categories/23756813/pages/23306384](
Setting Up Controls and Action Maps page
)
.

```

`
private void InitializeInput()
{
  var actionHandler = new ActionHandler(InputActionMapUrl, InputActionMapName);
  actionHandler.AddHandler("shoot", OnFireWeaponPressed);
}

private void OnFireWeaponPressed(string name, InputState state, float value)
{
  if(state == InputState.Pressed)
  {
    Weapon.Fire();
  }
}

protected override void OnRemove()
{
    _actionHandler?.Dispose();
}
`

```

When a component uses the ActionHandler, it should always dispose of it when it's done using it. A common place to do this is in the
**
OnRemove
**
 method, which is automatically called when the entity is removed.

##
Character Animator

The
**
CharacterAnimator
**
 is an
[/docs/static/engines/cryengine-5/categories/28704771/pages/29448894](
EntityComponent
)
 which makes it easier to setup and manage an animated character from C#. The
**
CharacterAnimator
**
 is automatically added to the player entity in the
**
OnInitialize
**
 method of the
**
Player
**
 component. The
**
CharacterAnimator
**
 has several properties that need to be set before it can be used. These properties can be set in the inspector by selecting the player entity. The required properties are:

-
**
`
AnimationDatabase
`
**
: The path to the
[/docs/static/engines/cryengine-5/categories/23756816/pages/23308472](
 Animation Database (.adb) file
)
.

-
**
`
ControllerDefinition
`
**
: The path to the
[/docs/static/engines/cryengine-5/categories/23756816/pages/23308471](
Controller Definition (.xml) file
)
.

-
**
`
MannequinContext
`
**
: The name of the
[/docs/static/engines/cryengine-5/categories/23756816/pages/23308438](
context
)
 to load from the Controller Definition file.

-
**
`
StartFragmentName
`
**
: The name of the
[/docs/static/engines/cryengine-5/categories/23756816/pages/23308429](
 fragment
)
 that the
**
CharacterAnimator
**
 should start in.
While in game-mode the animations can be controlled by setting the values of
[/docs/static/engines/cryengine-5/categories/28704771/pages/29448764](
MotionParameterIds
)
 and
[/docs/static/engines/cryengine-5/categories/28704771/pages/29448773](
AnimationTags
)
.
The value of
a
**
MotionParameterId
**
 can be set directly by calling
**
SetMotionParameter
**
with the
**
MotionParameterId
**
and the required value. A
**
MotionParameterId
**
describes the basic
parameters of a character, such as movement speed and turning angle. Based on the values of the parameters the right animation will be blended in.
**
AnimationTags
**
 first need to be found by calling
**
FindTag,
**
with the name of the tag. Once the tag is found it can be used to call
**
SetAnimationTag
**
. The value of an
**
AnimationTag
**
can only be set to
**
`
true
`

**
or
**
`
false
`
**
. An
**
AnimationTag
**
 describes the state of a character, such as walking, rotating or aiming. More than one
**
AnimationTag
**
 can be set to
**
`
true
`
**
 at once.

In the template, the
**
PlayerAnimations
**
 class handles the calls to the
**
CharacterAnimator
**
. It keeps track of the movement and actions of the player and every frame
**
 PlayerAnimations
**
**

**
calculates the values for both the
**
MotionParameterIds
**
 and
**
AnimationTags
**
`
,
`
 and sends them to the
**
CharacterAnimator
**
.
`
**

**
`

##
Character Physics

Instead of physicalizing the player as a rigid type, this time it will be physicalized as a living type. The living type inherits from the rigid type, but is specialized for walking entities. Physicalizing the entity as living also enables it to be moved by calling
[/docs/static/engines/cryengine-5/categories/28704771/pages/29448917](
Move
)
 on the
[/docs/static/engines/cryengine-5/categories/28704771/pages/29448917](
PhysicsObject
)
 of the entity. The
**
Move
**
 method gives more control over the movement of the entity than
**
Impulse
**
, which works better for moving the player around.

To physicalize an entity as living, the entity is physicalized with
[/docs/static/engines/cryengine-5/categories/28704771/pages/29448908](
LivingPhysicalizeParams
)
 as the parameters. This parameter has two important properties which will define the physics settings for the player: the
[/docs/static/engines/cryengine-5/categories/28704771/pages/29448948](
PlayerDynamicsParameters
)
 and the
[/docs/static/engines/cryengine-5/categories/28704771/pages/29448947](
PlayerDimensionsParameters
)
.

-
The
**
 PlayerDimensions
**
**

**
parameter describes everything that's connected to the size, shape and pivot of the collider.

-
The
**
PlayerDynamics
**
 parameter describes how the entity reacts to physics actions, for example how much control the entity has while in the air, and the mass of the entity.
The shape of the collider can be either a capsule or a cylinder shape. For this template a capsule shaped collider is used instead of a cylinder because it has a low chance of getting stuck and moves smoothly over uneven terrain.

##
Collision Messages

Whenever a physicalized entity hits another physicalized entity, a message is sent to the
[/docs/static/engines/cryengine-5/categories/28704771/pages/29448894](
EntityComponents
)
 on the entity. To receive these messages the
[/docs/static/engines/cryengine-5/categories/28704771/pages/29448894](
OnCollision
)
 method needs to be overridden. The message will include a
[/docs/static/engines/cryengine-5/categories/28704771/pages/29448904](
CollisionEvent
)
 which contains information about the collision, such as the collision objects involved in the collision and the point of impact of the collision. The
**
OnCollision
**
 message can be used to have actions happen on collision. For example, the
**
Bullet
**
 class in the template overrides the
**
OnCollision
**
 method to destroy the bullet as soon as it hits something. But instead of destroying the bullet it's also possible to change it's trajectory, to make it bounce off of the collider it hit.

##
Material Effects

For the bullet collisions in the template, a material effect has been set up. The occurrence of the effect is specified in the
[/docs/static/engines/cryengine-5/categories/23756816/pages/23308243](
MaterialEffects.xml
)
 file. This file is located in the
**
Assets\Libs\MaterialEffects
**
 folder. To modify the file, you can open the file using a program such as Microsoft Excel or OpenOffice Calc. By default the Material Effects are set up as in the example below. This setup invokes the
**
collision:bullet_hit
**
 effect when a bullet collides with another bullet or a concrete entity.

 |
mat_concrete

 |
mat_bullet

 |

mat_bullet

 |
collision:bullet_hit

 |
collision:bullet_hit

 |

The actions that belong to
**
collision:bullet_hit
**
 are defined in the file
**
collision.xml
**
, which is located in Assets\Libs\MaterialEffects\FXLibs. This file can be opened in a normal text-editor like Notepad++. This file defines all currently registered collision effects. By default there is only one effect defined which is the
**
bullet_hit
**
 effect that's referenced in the
**
MaterialEffects.xml
**
 file. Once the
**
bullet_hit
**
 effect is invoked, it will activate an audio trigger with the name
**
bullet_impact
**
 which is defined in the Sandbox. The audio trigger can be adjusted in the Sandbox in the
[/docs/static/engines/cryengine-5/categories/23756816/pages/23308254](
Audio Controls Editor,
)
 found under the Tools menu.

More in-depth information about the features of Material Effects can be found in
[/docs/static/engines/cryengine-5/categories/23756816/pages/23308243](
_Audio & Physics 5.5.2
)
.
