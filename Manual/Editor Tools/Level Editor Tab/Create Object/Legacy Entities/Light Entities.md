# Light Entities

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/29796937
- Page ID: 29796937
- Breadcrumb: Editor Tools > Level Editor Tab > Create Object > Legacy Entities > Light Entities
- Parent: Legacy Entities

## Content

##
Overview

The light entity is a dynamic real-time light that can be used to light a scene. For indoor areas it is essential to place proper lighting as the sun light does not light the interiors well. The light intensity of a light entity falls off linearly to the border of its radius.

Due to the increased calculation time for dynamic lights, you need to carefully place them in a scene. Deferred lights (as per default setting) are much more performance friendly but you should still use an amount within reason.

The Light entity can be found in
**
Create Object → Legacy Entities → Lights
**
.

##
Light Properties

**
Property
**

 |
**
Description
**

 |

**
Active
**

 |
Turns the light on/off.

 |

**
AttenuationBulbSize
**

 |
See
[/docs/static/engines/cryengine-5/categories/23756816/pages/29796937#LightEntities-falloff](
Attentuation and Falloff
)
 for more information. When using AmbientLights, setting this value to '0' reverts to the older, non-physical attenuation model.

 |

**
Radius
**

 |
Specifies how far from the source the light affects the surrounding area.

 |

**
Color
**

 |
 |

**
Diffuse
**

 |
Specify the RGB diffuse color of the light.

 |

**
DiffuseMultiplier
**

 |
Control the strength of the diffuse color.

 |

**
SpecularMultiplier
**

 |
Control the strength of the specular brightness.

 |

**
Options
**

 |
 |

**
AffectThisAreaOnly
**

 |
Set this parameter to false to make light cast in multiple visareas.

 |

**
AmbientLight
**

 |
Makes the light behave like an ambient light source, with no point of origin.

 |

**
AttenuationFalloffMax
**

 |
**
DEPRECATED (use BulbSize)

**
Controls the light fall-off. This can only be used for Ambient lights. Valid range between 0.0 and 1.0. See below for examples.

 |

**
deferred_clip_geom
**

 |
**
DEPRECATED (arbitrary light clip volumes not supported on Tiled shading, Light Boxes can still be used)
**

 |

**
DeferredClipBounds
**

 |
Specifies that the light is linked to a light box or light shape and to use the volume of the target area for clipping.

 |

**
FakeLight
**

 |
Disables light projection, useful for lights which you only want to have
[/docs/static/engines/cryengine-5/categories/23756816/pages/36869088](
Flare
)
 effects from.

 |

**
ForceDisableCheapLight
**

 |
Forces the engine to de-classify the light as a "CheapLight", which is a memory optimization done on export for Pure Game mode.

Lights are automatically de-classified as needed, based on whether they're used in a FG, trackview, etc, so this option should never need to be used, but provided as a fail-safe.

 |

**
IgnoresVisAreas
**

 |
Controls whether the light should respond to visareas.

 |

**
Projector
**

 |
 |

**
ProjectorFov
**

 |
Specifies the Angle on which the light texture is projected.

 |

**
ProjectorNearPlane
**

 |
Set the near plane for the projector, any surfaces closer to the light source than this value will not be projected on.

 |

**
Texture
**

 |
Here a texture can be specified that will be projected in the direction of the Y axis of the light entity.

A light projector texture must use the LightProjector CryTif preset, be 512*512px resolution, and contain no alpha channel.

 |

Shadows

 |

 |

**
CastShadows
**

 |
Makes the light cast a shadow based on the minimum selected config spec. "High" won't work on Low/Medium, for example. To ensure shadows are always cast, set the this to 'Low Spec'.

This setting is often confused as a 'Quality' setting for the shadows, it is not a quality setting. It's a method to control what system spec the shadows should be cast on.

With tiled shading, the amount of shadow-casting lights on screen is limited by default to '12'. This is because each 4 lights requires an additional 8MB of video memory for shadow texture mapping.

The limit can be controlled with the
**
r_ShadowCastingLightsMaxCount
**
 CVar.

 |

**
ShadowBias
**

 |
Moves the shadow cascade toward or away from the shadow-casting object.

 |

**
ShadowMinResPercent
**

 |
Specify, per-light, the percentage of the shadow pool the light should use for its shadows. Unless otherwise needed, "default" should be used for best performance vs quality.

 |

**
ShadowResolutionScale
**

 |

 |

**
ShadowSlopeBias
**

 |
Allows you to adjust the gradient (slope-based) bias used to compute the shadow bias.

 |

**
ShadowUpdateMinRadius
**

 |
Define the minimum radius from the light source to the player camera that the ShadowUpdateRatio setting will be ignored.

i.e; If set to 10 and the camera is less than 10m from the light source, the shadow will update normally. If further than 10m, the shadow will update as per ShadowUpdateRatio setting.

This will not work in Very High spec as Shadow Caching is disabled.
 |

**
ShadowUpdateRatio
**

 |
Define the update ratio for shadow maps cast from this light. The lower the value (example 0.01), the less frequent the updates will be and the more "stuttering" the shadow will appear.

This setting is enabled or disabled, depending on the ShadowUpdateMinRadius value and how far the player camera is from the light source.

This will not work in Very High spec as Shadow Caching is disabled.
 |

**
Shape
**

 |
 |

**
PlanarLight
**

 |
Used to turn the selected light entity into an Area Light. Was previously called "AreaLight".

To use Area/Planar Lights, ensure
**
r_DeferredShadingAreaLights
**
 is set to '1'.

 |

**
DiffuseSoftness
**

 |
**
DEPRECATED (3.7.0)
**

Control the softness of the projected texture (must use an alpha channel). Valid range between 0.0 and 1.0. See below for examples.

 |

**
LightFov
**

 |
**
DEPRECATED (3.7.0) - Use ProjectorFov instead
**

Control the size/shape of the cone or "Field of View" of the light projection.

 |

**
PlaneHeight
**

 |
Set the height of the Area Light shape.

 |

**
PlaneWidth
**

 |
Set the width of the Area Light shape.

 |

**
Texture
**

 |
**
DEPRECATED (3.7.0)
**

Specify a texture to be projected from the light. Texture must use an alpha channel if wanting to use diffuse softness.

 |

**
TextureReflection
**

 |
**
DEPRECATED (3.7.0)
**

Renders the texture in the reflection, as well as in the projection (see below for example).

 |

**
Style
**

 |
 |

**
AnimationPhase
**

 |
This will start the light animation, specified with the light style property, at a different point along the sequence.

This is typically used when you have multiply lights using the same animation in the same scene, using this property will make the animations play asynchronously.

 |

**
AnimationSpeed
**

 |
Specifies the speed at which the light animation should play.

 |

**
AttachToSun
**

 |
When enabled, sets the Sun to use the
[/docs/static/engines/cryengine-5/categories/23756816/pages/36869088](
Flare properties
)
 for this light.

 |

**
Flare
**

 |
Specify the path to the Flare Library item.

 |

**
FlareEnable
**

 |
Used by the
[/docs/static/engines/cryengine-5/categories/23756816/pages/36869088](
Flare Editor
)
 system.

 |

**
FlareFOV
**

 |
Control the FOV for the flare. This control needs to be enabled in the properties for the flare itself.

 |

**
LightAnimation
**

 |
Trackview sequence used to animate the light.

 |

**
LightStyle
**

 |
Specifies the a preset animation for the light to play. Styles are defined through Light.cfx shader. Valid values are 0-48. 40-48 are Testing/Debug styles.

 |

**
TimeScrubbingInTrackview
**

 |
 |

**
Rotation
**

 |
 |

**
X,Y,Z
**

 |
**
DEPRECATED
**

These values can be used to apply animated rotation to the light. Values range between 0-1.

 |

##
Negative Lights and Darkening Areas

In earlier revisions of CRYENGINE, lights had an option called "Negative Light". This system was removed in later revisions because a more solid implementation was introduced into the lighting system.

The idea here is to add darker/lower luminance light to the scene rather that "sucking out" the color and luminance by using negative lighting.

You can achieve better results now by using the Ambient Light option for your light. By using this option in conjunction with a dark Diffuse color, you can apply a "negative" light to your scene with much more precision and control.

3 Easy Steps:

-
Add a Light entity.

-
Select
**
Ambient
**
 in the Options properties.

-
Apply a Diffuse color of 2,2,2.
*
Important note: If you use 0,0,0, you won't get the desired effect.
*
You can also apply color to this negative light, not just pure black. This also mixes well with other lights placed on top in a positive light fashion, and negative lights also stack on top of each other for the blackest of blacks!

 |
 |
 |

Ambient Light Off
 |
Ambient Light On
 |
Additional Light Off
 |

##
Attenuation and Fall Off

Since CRYENGINE 3.6, we have changed our light entities so that the falloff curve is based on a physically correct model (
**
inverse square falloff
**
), meaning the light value falls off exponentially.

Light in the real world never completely falls off to 0. This poses a problem in our engine, since we don’t want to have lights with an infinite radius (performance, light leaking issues, etc), and we don’t want the light to cut off at the end of the radius since there will be a noticeable cull of the light (ugly).

To combat this, light begins to falloff
**
linearly
**
 from 80% to 100% of the radius value, which ensures that the light value reaches 0 before being culled.

**
AttenuationBulbSize
**
 is a value which combats the problem of lights in a 3d engine being infinitely small. This means that the light begins to fall off exponentially from the origin coordinates. AttenuationBulbSize fakes the size of the "light bulb", and thus acts as a radius for when the falloff should begin.

-
A value of
**
1
**
 means that the light is at full intensity within a 1 meter ball before it begins to falloff.

-
This value is very useful for ensuring that the
**
DiffuseMultiplier
**
 can remain at sane levels.
It becomes more important when there are objects that will be very close to the light entity. With a small
**
AttenuationBulbSize
**
, a nearby entity might look blown out because so much light energy is focused in such a small area before falling off rapidly.

When the
**
AttenuationBulbSize
**
 parameter is larger, the artist can use a lower
**
DiffuseMultiplier
**
 value, and thus have a much more natural level of light on nearby objects.

 |
 |

100 Bulb Size / No Falloff / Old System
 |
0.2 Bulb Size , Inverse Square Falloff, New System
 |

Similar to EnvironmentProbes, it is recommended that you do not change the
**
SpecularMultiplier
**
 value from
**
1
**
 on Light Entities because this will affect the diffuse/specular ratio of any object in the light’s radius and will then technically not be rendered in a physically correct way.

It’s worth noting that all the Cubemap related parameters here (AttenuationFalloffMax, SortPriority) are disabled and do not function, as only EnvironmentProbes should be used for cubemap management.

It’s also worth noting that the Area Light parameters do not function properly with our current physically based shading model.

##
Ambient Lights

The
**
Ambient
**
 flag behaves very differently from pre-3.6 versions of the engine. In the new workflow, ambient lights are simply multipliers for cubemap values.

For example, an ambient light with a DiffuseMultiplier of between 0 and 1 will
**
remove
**
 ambient light from the local cubemaps.

An ambient light with a DiffuseMultiplier value above 1 will
**
multiply
**
 the
**
local cubemap lighting.
**

-
Note that Ambient lights
**
cannot
**
 remove light provided by direct sources (ie, Sunlight, or non-ambient light entities)

-
Note that Ambient lights MUST have an
**
AttenuationBulbSize
**
value of 0, which ensures that the falloff model is
**
Linear
**
 and more visually appealing.
 |
 |

Non-Ambient
 |
Ambient
 |

##
Example Images

 |
 |
 |

AttenuationFalloffMax 0
 |
AttenuationFalloffMax 0.5
 |
AttenuationFalloffMax 1
 |

 |
 |

TextureReflection Off
 |
TextureReflection On
 |

 |
 |
 |

DiffuseSoftness 0
 |
DiffuseSoftness 0.5
 |
DiffuseSoftness 1
 |

 |
 |

SortPriority 0
 |
SortPriority 1
 |

##
DestroyableLight

The DestroyableLight entity is a special light with many additional properties enabling the setup of destroyable light settings including damage, explosion, sounds, and physics.

Two different models are specified for the base model and broken model.

To use the entity, simply place it in a level via
**
RollupBar -> Entities -> Lights -> DestroyableLight
**
.

 |
 |

The light entity before it is destroyed

 |
Destroyed, disabled and broken into pieces

 |

**
Property
**

 |
**
Description
**

 |

**
TurnedOn
**

 |
Turns the entity on/off.

 |

**
LightProperties_Base
**

 |
 |

**
Radius
**

 |
Specifies how far from the source the light affects the surrounding.

 |

**
UseThisLight
**

 |
Turns the Base_Light on/off.

 |

**
Color
**

 |
 |

**
Diffuse
**

 |
The diffuse color of the light can be specified here.

 |

**
DiffuseMultiplier
**

 |
To make the light brighter this diffuse multiplier can be used.

 |

**
HDRDynamic
**

 |
Specifies how much brighter than the default 255,255,255 white the light is. Sun light set in the Time of Day tool is 3 times brighter, for example.

 |

**
SpecularMultiplier
**

 |
Multiplies the specular color brighter, use to adjust brightness.

 |

**
Options
**

 |
 |

**
AffectThisAreaOnly
**

 |
Set this parameter to false to make lights other visarea.

 |

**
CastShadows
**

 |
Makes the light cast a shadow based on the config spec.

 |

**
DeferredLight
**

 |
Enables/disables the light as a deferred light.

 |

**
FakeLight
**

 |
Only applies corona effects but does not dynamically light the surroundings.

 |

**
GlowSubmatId
**

 |
GlowSubmatId is used to control the glow intensity of the destructible lights (for instance, destructible street light).

 |

**
IgnoreGeomCaster
**

 |
Used in conjunction with the Cast Shadows option. When Cast Shadows is set to true, setting this tick box will prevent the model attached to the light from obstructing the light.

 |

**
ViewDistRatio
**

 |
Value used to set the draw distance of the light.

 |

**
Projector
**

 |
 |

**
ProjectInAllDirs
**

 |
Makes the light shine omni-directionally.

 |

**
ProjectorFov
**

 |
Specifies the Angle on which the light texture is projected.

 |

**
ProjectorNearPlane
**

 |
ProjectNearPlane is used to clip the light projector from the light source, so the light doesn't affect certain objects near the light source.

 |

**
Texture
**

 |
Here a texture can be specified that will be projected in the direction of the y axis of the light entity.

 |

**
Style
**

 |
 |

**
AnimationPhase
**

 |
This will start the light animation, specified with the light style property, at a different point along the sequence.

This is typically used when you have multiply lights using the same animation in the same scene, using this property will make the animations play asynchronously.

 |

**
AnimationSpeed
**

 |
Specifies the speed at which the light animation should play.

 |

**
CoronaDistIntensityFactor
**

 |
Specifies how bright the corona effect is in the distance.

 |

**
CoronaDistFactor
**

 |
Specifies how big the corona effect is in the distance.

 |

**
CoronaScale
**

 |
Specifies how big the corona effect is.
**
NOTE:
**
 To apply a corona to a light entity you need to assign the light a suitable material and the material should use the Light.Flare shader.

 |

**
LightStyle
**

 |
Specifies the a preset animation for the light to play.

 |

Rotation

 |

 |

**
X,Y,Z
**

 |
**
DEPRECATED
**
 - These values can be used to apply animated rotation to the light. Values range between 0-1.

 |

**
Test
**

 |
 |

**
FillLight
**

 |
Obsolete.

 |

**
vDirection
**

 |
 |

**
X,Y,Z
**

 |
Change the direction of the entity light. Used with projector lights this defines which direction the light will be projected. Valid values are -1,0,1.

 |

**
vOffset
**

 |
 |

**
X,Y,Z
**

 |
Offset of the light from the pivot of the entity. This defines where the light entity will be spawned.

 |

 |

**
LightProperties_Destroyed
**

 |
 |

**
Radius
**

 |
Specifies how far from the source the light affects the surrounding.

 |

**
UseThisLight
**

 |
Turns the Destroyed_Light on/off.

 |

**
Color
**

 |
 |

**
Diffuse
**

 |
The diffuse color of the light can be specified here.

 |

**
DiffuseMultiplier
**

 |
To make the light brighter this diffuse multiplier can be used.

 |

**
HDRDynamic
**

 |
Specifies how much brighter than the default 256,256,256 white the light is. (sunlight set in the time of day window is for example 3 times brighter).

 |

**
SpecularMultiplier
**

 |
Multiplies the specular color brighter, use to adjust brightness.

 |

**
Options
**

 |
 |

**
AffectThisAreaOnly
**

 |
Set this parameter to false to make lights other visarea.

 |

**
CastShadows
**

 |
Makes the light cast a shadow based on the config spec.

 |

**
DeferredLight
**

 |
Enables/disables the light as a deferred light.

 |

**
FakeLight
**

 |
Only applies corona effects but does not dynamically light the surroundings.

 |

**
IgnoreGeomCaster
**

 |
Used in conjunction with the Cast Shadows option. When Cast Shadows is set to true, setting this tick box will prevent the model attached to the light from obstructing the light.

 |

**
GlowSubmatId
**

 |
Set which sub-material in the model material should be used as the glow material.

 |

**
UsedInRealTime
**

 |
Specifies if the light is a real-time light or not.

 |

**
ViewDistRatio
**

 |
Value used to set the draw distance of the light.

 |

**
Projector
**

 |
 |

**
ProjectInAllDirs
**

 |
Makes the light shine omni-directionally.

 |

**
ProjectorFov
**

 |
Specifies the Angle on which the light texture is projected.

 |

**
ProjectorNearPlane
**

 |
ProjectNearPlane is used to clip the light projector from the light source, so the light doesn't affect certain objects near the light source.

 |

**
Texture
**

 |
Here a texture can be specified that will be projected in the direction of the y axis of the light entity.

 |

**
Style
**

 |
 |

**
AnimationPhase
**

 |
This will start the light animation, specified with the light style property, at a different point along the sequence.

This is typically used when you have multiply lights using the same animation in the same scene, using this property will make the animations play asynchronously.

 |

**
AnimationSpeed
**

 |
Specifies the speed at which the light animation should play.

 |

**
CoronaDistIntensityFactor
**

 |
Specifies how bright the corona effect is in the distance.

 |

**
CoronaDistFactor
**

 |
Specifies how big the corona effect is in the distance.

 |

**
CoronaScale
**

 |
Specifies how big the corona effect is.

 |

**
LightStyle
**

 |
Specifies the frequency at which the light is blinking.

 |

Rotation

 |

 |

**
X,Y,Z
**

 |
**
DEPRECATED
**
 - These values can be used to apply animated rotation to the light. Values range between 0-1.

 |

**
Test
**

 |
 |

**
FillLight
**

 |
Obsolete.

 |

**
NegativeLight
**

 |
This will make the light object actually remove light from an area. Can be used to darken specific areas.

 |

**
vDirection
**

 |
 |

**
X,Y,Z
**

 |
Change the direction of the entity. This defines which direction the entity will be faced.

 |

**
vOffset
**

 |
 |

**
X,Y,Z
**

 |
Offset of the pivot of the entity. This defines where the entity will be spawned.

 |

 |

**
Entity Properties
**

 |
 |

**
Faction
**

 |
Select which AI faction the entity belongs to.

 |

**
Pickable
**

 |
When set, the object can be picked up.

 |

**
Usable
**

 |
When set, the object will activate when actioned by the player.

 |

**
UseMessage
**

 |
When an object is marked as usable this text will appear on the screen to indicate the player what to do with it, or what happens when you interact with it.

 |

**
Breakage
**

 |
 |

**
ExplodeImpulse
**

 |
Sets the impulse with which the destruction particles will be spawned.

 |

**
LifeTime
**

 |
Sets the lifetime of the destruction particles.

 |

**
SurfaceEffects
**

 |
When disabled no destruction particles will be spawned.

 |

**
Damage
**

 |
 |

**
DamageThreshhold
**

 |
Damage below the threshold set here will be ignored.

 |

**
Explode
**

 |
Determines whether or not the entity should explode. True/False.

 |

**
Health
**

 |
Health of the entity, how much damage can it take before exploding/breaking.

 |

**
PlayerOnly
**

 |
If true the light can only be damaged by players.

 |

**
DamageMultipliers
**

 |
 |

**
Bullet
**

 |
Multiplies the damage inflicted by bullets.

 |

**
Collision
**

 |
Multiplies the damage inflicted by collisions.

 |

**
Explosion
**

 |
 |

**
Damage
**

 |
Damage dealt to nearby objects.

 |

**
Decal
**

 |
Decal being projected to the ground, on explosion.

 |

**
Delay
**

 |
Time to wait until the effect is played.

 |

**
Effect
**

 |
Name of the effect to be played if the object is destroyed.

 |

**
EffectScale
**

 |
Size of the effect.

 |

**
HoleSize
**

 |
Size of the hole being cut into objects around the explosion.

 |

**
MinPhysRadius
**

 |
Lower boundary of the explosion falloff effects for physical objects that are not players/AI.

 |

**
MinRadius
**

 |
Lower boundary of the explosion falloff effects for players/AI.

 |

**
PhysRadius
**

 |
Upper boundary of the explosion falloff effects for physical objects that are not players/AI.

 |

**
Pressure
**

 |
Used for physical simulation of the explosion.

 |

**
Radius
**

 |
Upper boundary of the explosion falloff effects for players/AI.

 |

**
TerrainHoleSize
**

 |
Obsolete.

 |

**
DelayEffect
**

 |
 |

**
Effect
**

 |
A particle effect.

 |

**
HasDelayEffect
**

 |
If selected the effect will be played with delay.

 |

**
Params
**

 |
 |

**
AttachForm
**

 |
If AttachType is non-blank, this property determines where particles emit from the attached geometry. Set it to Vertices, Edges, Surface, or Volume.

 |

**
AttachType
**

 |
If this entity is attached to a parent entity, as described above, this field can be used to cause particles to emit from the entity's geometry.

Set it to one of these string values (heeding case):

-
**
blank:
**
 Emit from the effect origin, as normal.

-
**
BoundingBox:
**
 Emit from the parent effect's bounding box.

-
**
Physics:
**
 Emit from the parent effect's physics geometry.

-
**
Render:
**
 Emit from the parent effect's render geometry.
 |

**
CountPerUnit
**

 |
(flag) If AttachType is non-blank, this multiples the particle count by the "extent" of the attached geometry.

Depending on AttachForm, the extent is either total vertex count, edge length, surface area, or volume.

 |

**
CountScale
**

 |
Multiples the particle counts of the entire effect.

 |

**
Prime
**

 |
(flag) If true, and the assigned ParticleEffect is immortal, causes the emitter to start "primed" to its equilibrium state, rather than starting up from scratch.

Very useful for placed effects such as fires or waterfalls, which are supposed to be already running when the level starts. Applies only to immortal, not mortal effects. Defaults to true.

 |

**
Scale
**

 |
Multiplies the overall size and velocity of the entire effect.

 |

**
SizePerUnit
**

 |
(flag) Currently ignored

 |

**
SpawnPeriod
**

 |
(or PulsePeriod): If not 0, restarts the effect continually at this interval. This property should be used to create effects that pulse on and off at somewhat large intervals, a second or so.

Do not set a low value such as 0.1 to try to make an instant effect into a continuous one. That method is inefficient, framerate-dependent, and won't look as good as it should.

Instead, make sure the actual library effect is set Continuous and has an appropriate Count.

 |

**
vOffset
**

 |
Offset from light entity in local space.

 |

**
vRotation
**

 |
Rotation from light entity, as angles in local space.

 |

**
Direction
**

 |
Direction of the explosion.

 |

**
vOffset
**

 |
Offset of the explosion from the light entity in local space.

 |

Health

 |

 |

**
Invulnerable
**

 |
If true the light cannot be damaged.

 |

**
MaxHealth
**

 |
Maximum (and initial) health value.

 |

**
OnlyEnemyFire
**

 |
If true the light cannot be damaged by friendly fire.

 |

**
Model
**

 |
 |

**
Model
**

 |
The CGF model to use for the primary, non-destroyed model.

 |

**
ModelDestroyed
**

 |
The CGF model for the broken pieces.

 |

**
SubObject_Name
**

 |
If the model has sub-models, specifies the unbroken piece name.

 |

**
SubObject_NameDestroyed
**

 |
If the model has sub-models, specifies the broken piece name.

 |

**
Physics
**

 |
 |

**
ActivateOnDamage
**

 |
Activates a rigid body with RigidBodyActive=0, when it receives damage.

 |

**
CanBreakOthers
**

 |
True if the entity can break jointed objects by colliding with them (provided they overcome the strength limit). BasicEntities have this flag off unconditionally.

 |

**
Density
**

 |
(= Volume/Mass) Affects the way the objects interact with other objects and float in the water (they sink if their density is more than that of the water).

 |

**
Mass
**

 |
(= Density*Volume) The weight of the object (the density of the object multiplied by its volume).

 |

**
PushableByPlayers
**

 |
When set, the object can be moved by the player.

 |

**
RigidBody
**

 |
Determines whether the original "Main" object is physicalized; if not, it's static.

 |

**
RigidBodyActive
**

 |
Indicates that the object is a RigidBody, but initially it is immovable; instead, it can be later activated by an event.

 |

**
RigidBodyAfterDeath
**

 |
Determines whether the remaining "Remain" object is physicalized; if not, it's static.

 |

**
Simulation
**

 |
 |

**
damping
**

 |
(0..3) This sets the strength of damping on an object's movement. Most objects can work with 0 damping; if an object has trouble coming to rest, try values like 0.2-0.3.

Values of 0.5 and higher appear (visually) as over-damping. Note that when several objects are in contact, the highest damping is used for the entire group.

 |

**
max_time_step
**

 |
(0.005..0.1) This sets the maximum time step the entity is allowed to make (defaults to 0.01).

Smaller time steps increase stability (can be required for long and thin objects, for instance), but are more expensive.

Each time the physical world is requested to make a step, the objects that have their maxsteps smaller than the requested one, slice the big step into smaller chunks and perform several sub-steps.

If several objects are in contact, the smallest max_time_step is used.

 |

**
sleep_speed
**

 |
(0.01..0.3) If the object's kinetic energy falls below some limit over several frames, the object is considered to be sleeping. This limit is proportional to the square of the sleep speed value.

A sleep speed of 0.01 loosely corresponds to the object's center moving at a velocity of the order of 1 cm/s.

 |

**
Sounds
**

 |
 |

**
AISoundRadius
**

 |
Units to which distance the sounds can be heard.

 |

**
Alive
**

 |
Sound event to be played as long as the object is in the "Alive" state.

 |

**
Dead
**

 |
Sound event to be played as long as the object is in the "Dead" state.

 |

**
Dying
**

 |
Sound event to be played if the object is changed from the "Alive" state to the "Dead" state.

 |

**
StopSoundsOnDestroyed
**

 |
Stops playing sounds once the object has been broken/destroyed. Used, for instance, for a radio.

 |

**
Vulnerability
**

 |
 |

**
Bullet
**

 |
When set, the object will take damage from bullets.

 |

**
Collision
**

 |
When set, the object will take damage from impact with other objects.

 |

**
Explosion
**

 |
When set, the object will take damage from explosions.

 |

**
Melee
**

 |
When set, the object will take damage from melee hits.

 |

**
Other
**

 |
When set, the object will take damage from other damage sources.

 |

[#light-properties](
Light Properties
)
[#negative-lights-and-darkening-areas](
Negative Lights and Darkening Areas
)
[#attenuation-and-fall-off](
Attenuation and Fall Off
)
[#ambient-lights](
Ambient Lights
)
[#destroyablelight](
DestroyableLight
)
