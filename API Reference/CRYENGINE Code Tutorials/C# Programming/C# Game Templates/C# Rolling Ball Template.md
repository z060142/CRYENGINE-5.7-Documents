# C# Rolling Ball Template

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/29791343
- Page ID: 29791343
- Breadcrumb: CRYENGINE Code Tutorials > C# Programming > C# Game Templates > C# Rolling Ball Template
- Parent: C# Game Templates

## Content

The Rolling Ball template is a simple game in which you can control a ball rolling around the level. The template shows you how to;

-
Use the
[EntityComponent](/docs/static/engines/cryengine-5/categories/28704771/pages/29448894)
 to modify the behavior of the entities in your game.

-
How to receive input from the Player.

-
How to use physics to move entities around.
[General Setup](#general-setup)
[Player](#player)
[PlayerView](#playerview)
[EntityProperties](#entityproperties)

##
General Setup

In the
[Blank template](C%23%20Blank%20Template.md)
, most of the work is done inside the
`
Game
`
 class, which is the starting point for the application. However, in the Rolling Ball template we have used a different approach to create the behavior.

The
`
Game
`
 class is now only used to register if the ESC-key is pressed (so that the application can be closed). Most of the logic is moved to the C# assets that can be accessed from the
**
Asset Browser
**
 in the Sandbox, with most of the heavy lifting happening in the
**
Player
**
class which is an
[EntityComponent](/docs/static/engines/cryengine-5/categories/28704771/pages/29448894)
. Since the
**
Player
**
 is an
**
EntityComponent
**
, it can be added to an Entity in the Sandbox. This is achieved by pressing
**
Components
**
 in the
**
Create Object
**
 window and then dragging the
**
Player
**
(new components will be in the General category by default) into your scene. If you already have an Entity ready for the player, you can also select the Entity and use the
**
Add Component
**
 button in the properties window to add the
**
Player
**
-component to the Entity.

##
Player

The
**
Player
**
 class is responsible for handling visuals, physics and the input of the player (in this case a ball that can roll around). Since the
**
Player
**
 is an
[EntityComponent](/docs/static/engines/cryengine-5/categories/28704771/pages/29448894)
, it can be added to an Entity in the level in the Sandbox from the
**
Add Component
**
 menu. The
**
Player
**
 will now be saved automatically whenever the level is saved, and if the game is launched it will be automatically set on the Entity with all of its properties set to the right value. The properties of the
**
Player
**
 are exposed by the
[EntityPropertyAttribute](/docs/static/engines/cryengine-5/categories/28704771/pages/29448914)
 which are explained in more detail in the
[EntityProperties](C%23%20Rolling%20Ball%20Template.md#C%23RollingBallTemplate-EntityProperties)
 chapter.

Once
instantiated,
the
**
Player
**
 class will set its visuals and physicalize itself. The visuals are handled by the
**
SetPlayerModel
**
 method, which calls
[LoadGeometry](/docs/static/engines/cryengine-5/categories/28704771/pages/29448766)
 and
[LoadMaterial](/docs/static/engines/cryengine-5/categories/28704771/pages/29448766)
 with the values that are set according to the
**
PlayerGeometryUrl
**
 and
**
PlayerMaterialUrl
**
. Once the visuals are rendered, it will
[Physicalize](/docs/static/engines/cryengine-5/categories/28704771/pages/29448897)
 itself by calling the
**
PrepareRigidbody
**
 method where it will set the
**
Mass
**
 of the entity and set the
[physicalization type](../../../CRYENGINE%20Engine%20Code/Engine%20Modules/CryPhysics/Physical%20entity%20types.md)
 to
**
Rigid
**
. Rigid means the object is solid and can move around. By setting it to rigid the
**
Player
**
 is able to move around and have collisions with other physicalized objects. If the
**
Mass
**
 is changed in the Sandbox or during runtime it will run
**
PrepareRigidbody
**
 again to update the
**
Mass
**
 of the
[PhysicsEntity](/docs/static/engines/cryengine-5/categories/28704771/pages/29448897)
.
For objects that shouldn't move around, the physicalization type should be set to
**
Static
**
.

The Player receives its update calls in
**
OnUpdate
**
, which is called every frame. The
[EntityComponent](/docs/static/engines/cryengine-5/categories/28704771/pages/29448894)
 has several virtual methods that can be overridden, such as
**
OnCollision
**
,
**
OnEditorGameModeChange
**
 and
**
OnTransformChanged
**
.

On each frame, the player's movement is handled by the
**
UpdateMovement
**
 method. First, the user-input is gathered through the
[Input](/docs/static/engines/cryengine-5/categories/28704771/pages/29448891)
 class. Next the forward direction of the camera is retrieved and transformed (so it will not point up or down). After the forward is calculated, the correct direction of the camera can be calculated using
[Vector3.Cross](/docs/static/engines/cryengine-5/categories/28704771/pages/29448783)
 in combination with the world's up direction. Once both the forward and the correct direction of the camera have been calculated, they can be used to add or subtract from the impulse direction (depending on the input that was retrieved earlier). Finally, the impulse direction is multiplied with the
**
FrameTime
**
 to make it framerate independent and the impulse is set to the
**
PhysicalEntity
**
's
**
Impulse
**
 property.

After updating the position of the
**
Player
**
 it will also update the camera's position. This is handled by the
**
PlayerView
**
 class which is explained in more detail in the
[PlayerView](C%23%20Rolling%20Ball%20Template.md#C%23RollingBallTemplate-PlayerView)
chapter.

##
PlayerView

The
**
PlayerView
**
 class is responsible for moving the camera to the correct position. However, because the
**
PlayerView
**
 is not an
**
EntityComponent
**
 it needs to receive its update calls from the
**
Player
**
 manually. Furthermore, the
**
PlayerView
**
 also uses the
**
Camera
**
 class to calculate and modify the camera position in a scene. It starts by getting the camera's rotation as yaw, pitch and roll values (x, y, and z axes). The yaw and pitch rotations are changed based on the mouse movement, while the roll rotation is completely removed. The angles are then set back to the rotation of the
**
Camera
**
. Finally, the forward direction of the
**
Quaternion
**
 is multiplied with the
**
ViewDistance
**
 and subtracted from the player's position to set the camera in the correct position.

Some interesting things to note regarding the
**
PlayerView
**
 class;

-
As it is not an
[EntityComponent](/docs/static/engines/cryengine-5/categories/28704771/pages/29448894)
it is unable to make use of the
[EntityPropertyAttribute](/docs/static/engines/cryengine-5/categories/28704771/pages/29448914)
.

-
As a result of 1. a decision was made to store the various properties that the
**
PlayerView
**
 uses in the
**
Player
**
 instead. This way settings can still be fine-tuned in the Sandbox.

##
EntityProperties

The
**
Player
**
 class has several properties that can be adjusted in the Sandbox. This is done by adding the
[EntityPropertyAttribute](/docs/static/engines/cryengine-5/categories/28704771/pages/29448914)
to the properties.

```

`
[EntityProperty(0, "Strength of the per-frame impulse when holding inputs")]
public float MoveImpulseStrength{ get; set; } = 800.0f;
`

```

In the template the following properties are already exposed.

-
**
`
Mass
`
**
 - Mass of the Player entity in kg.

-
**
`
MoveImpulseStrength
`
**
 - Strength of the per-frame impulse when holding inputs.

-
**
`
RotationSpeedYaw
`
**
 - Speed at which the Player rotates the camera yaw.

-
**
`
RotationSpeedPitch
`
**
 - Speed at which the Player rotates the camera pitch.

-
**
`
RotationLimitsMinPitch
`
**
 - Minimum limit to the camera pitch.

-
**
`
RotationLimitsMaxPitch
`
**
 - Maximum limit to the camera pitch.

-
**
`
ViewDistance
`
**
 - Determines the distance between the Player and camera.
All of these properties are float properties, but the
[EntityPropertyAttribute](/docs/static/engines/cryengine-5/categories/28704771/pages/29448914)
 can be used to expose a wide variety of types. By default it will assume the property's type is a primitive type (
**
`
int
`
**
,
**
`
float
`
**
,
**
`
string
`
**
,
**
`
bool
`
**
). By changing the first parameter in the
[EntityProperty](/docs/static/engines/cryengine-5/categories/28704771/pages/29448914)
 you can adjust how the value is represented in the Sandbox. For example, if you want to also expose the
**
PlayerGeometryUrl
**
 you could do it by using the default
**
[EntityPropertyType](/docs/static/engines/cryengine-5/categories/28704771/pages/29448761)
.Primitive
**
, but you can also choose to change it to
[EntityPropertyType](/docs/static/engines/cryengine-5/categories/28704771/pages/29448761)
**
.Geometry
**
. This will still create a text field, but it also gives you the option to open a file-browser to select a file to which the property should refer. For the
**
PlayerGeometryUrl
**
 this will look like the following code.

```

`
private string _playerGeometryUrl = "Objects/Default/primitive_sphere.cgf";

[EntityProperty(EntityPropertyType.Geometry, "Path where the player's geometry-file is located.")]
public string PlayerGeometryUrl
{
  get
  {
    return _playerGeometryUrl;
  }
  set
  {
    _playerGeometryUrl = value;
    //Initialize again so the geometry is reloaded.
    Initialize();
  }
}
`

```
