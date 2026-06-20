# Weapon and ItemPackages

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/23306527
- Page ID: 23306527
- Breadcrumb: CRYENGINE Game Code > Miscellaneous Game Code > Weapon and ItemPackages
- Parent: Miscellaneous Game Code

## Child Pages

- [SCAR Example Script](Weapon and ItemPackages/SCAR Example Script.md)
- [ItemPackages Scripting](Weapon and ItemPackages/ItemPackages Scripting.md)

## Content

##
Overview

Below you'll find the majority of parameters available in CRYENGINE, which can be used by weapons, ammo and other item scripts.

The default location for these files is:
`
GameSDK\Scripts\Entities\Items\XML\
`

Please refer to the shipped
**
Rifle.xml
**
 file which outlines the structure and many useful parameters used in a real example weapon.

##
Items

Weapons, accessories, equipment, etc.

##
Root

`
Code\GameSDK\GameDll\WeaponSystem.cpp

Code\CryEngine\CryAction\ItemSystem.cpp
`

Param
 |
Type
 |
Description
 |

**
name
**
 |
<string>
 |
Name for the item. Needs to match the item filename. For example,
*
Rifle.xml
*
 uses
*
item name="Rifle"
*
.
 |

**
inherit
**
 |
<string>
 |
Inherit script values from another weapon. Useful for doing weapon skin modifications where the only thing defined in the custom weapon is the geometry.
 |

**
class
**
 |
<string>
 |
Class identifier for weapon C++ code which gives access to various parameters and functionality.
 |

**
category
**
 |
<string>
 |
Used for inventory management. Primary, Secondary, Special, Explosive, etc. These are used for controller mapping. See ItemSharedParams.cpp GetItemCategoryType.
 |

**
priority
**
 |
<int>
 |
Used for inventory management, a lower priority weapon will appear first when scrolling through inventory.
 |

**
weaponParams
**
 |
<bool>
 |
If true, loads basic shared weapon parameters to be used in the script. Should always be true for weapons.

Items (accessories/attachments/etc) don't require many of these params and therefore don't require the weaponParams to be true.
 |

##
Params

`
Code\GameSDK\GameDll\ItemSharedParams.cpp
`

Param
 |
Type
 |
Default
 |
Description
 |

**
selectable
**
 |
<bool>
 |
true
 |
Indicates whether the item can be selected in the player's inventory.
 |

**
droppable
**
 |
<bool>
 |
true
 |
Indicates whether the item can be dropped.
 |

**
pickable
**
 |
<bool>
 |
true
 |
Allows item to be "picked" up.
 |

**
mountable
**
 |
<bool>
 |
true
 |
Used for weapons which are fixed and cannot be picked up. Allows player to mount weapon to aim it.
 |

**
usable
**
 |
<bool>
 |
true
 |
Indicates whether the weapon can be used. Unlike selectable, this means a weapon can be used but without being selected.
 |

**
giveable
**
 |
<bool>
 |
true
 |
If false, item will not appear in the
[/docs/static/engines/cryengine-3/categories/1114113/pages/1048841](
Equipment Pack
)
 dialog and cannot be added to player inventory.
 |

**
unique
**
 |
<bool>
 |
true
 |

 |

**
mass
**
 |
<float>
 |
3.5
 |
The weight of the item, in kg, and how much it will slow the player down when held.
 |

**
drop_impulse
**
 |
<float>
 |
12.5
 |
Add a small physical impulse on -Z axis when weapon is dropped.
 |

**
select_override
**
 |
<float>
 |
0.0
 |
Time delay between selecting the weapon and being able to use the weapon can be overridden here.
 |

**
auto_droppable
**
 |
<bool>
 |
false
 |
Item will be automatically dropped when out of ammo.
 |

**
auto_pickable
**
 |
<bool>
 |
true
 |
Automatically pickup item when player collides with item.
 |

**
has_first_select
**
 |
<bool>
 |
false
 |
Plays an animation (
**
first
**
 fragment) when the weapon is selected for the first time.

If
**
SpecialSelect
**
 is activated on the entity properties then an alternative first select animation will play via the
**
special_first
**
 fragment.
 |

**
select_delayed_grab_3P
**
 |
<bool>
 |
false
 |

 |

**
attach_to_back
**
 |
<bool>
 |
false
 |
Visually attaches the weapon to the players back in 3rd person view when it's not in use.
 |

**
scopeAttachment
**
 |
<int>
 |
0
 |

 |

**
attachment_gives_ammo
**
 |
<bool>
 |
false
 |

 |

**
can_ledge_grab
**
 |
<bool>
 |
true
 |

 |

**
can_rip_off
**
 |
<bool>
 |
true
 |
Allows mounted weapons to be removed from their mounts and attach to player as standard weapon.
 |

**
check_clip_size_after_drop
**
 |
<bool>
 |
true
 |

 |

**
check_bonus_ammo_after_drop
**
 |
<bool>
 |
true
 |

 |

**
usable_under_water
**
 |
<bool>
 |
false
 |
Allow the weapon to fire while player is under water.
 |

**
can_overcharge
**
 |
<bool>
 |
false
 |

 |

**
fp_offset
**
 |
<vec3>
 |
0,0,0
 |

 |

**
fp_rot_offset
**
 |
<quat>
 |

 |

 |

**
hasAimAnims
**
 |
<bool>
 |
false
 |

 |

**
ironsightAimAnimFactor
**
 |
<float>
 |
1.0
 |

 |

**
fast_select
**
 |
<bool>
 |
false
 |
Plays
**
fast_select
**
 Mannequin fragment when selecting.
 |

**
tag
**
 |
<string>
 |
""
 |
Mannequin Tag state.
 |

**
itemClass
**
 |
<string>
 |
""
 |
Used by Mannequin as an additional tag "weaponType"
 |

**
attachment_left
**
 |
<string>
 |

 |

 |

**
attachment_right
**
 |
<string>
 |

 |

 |

**
aiAttachment_left
**
 |
<string>
 |

 |

 |

**
aiAttachment_right
**
 |
<string>
 |

 |

 |

**
bone_attachment_01
**
 |
<string>
 |

 |

 |

**
bone_attachment_02
**
 |
<string>
 |

 |

 |

**
deselectTime
**
 |
<float>
 |

 |
**
DEPRECATED (Define animation time for deselect Mannequin fragment)
**
 |

**
select
**
 |
<string>
 |
""
 |
**
DEPRECATED
**
 |

**
select_empty
**
 |
<string>
 |
""
 |
**
DEPRECATED
**
 |

**
display_name
**
 |
<string>
 |
""
 |
Used by the
[/docs/static/engines/cryengine-3/categories/1114113/pages/1310919](
localization system
)
 to display an item name in the UI.
 |

**
suffix
**
 |
<string>
 |
""
 |

 |

**
adb
**
 |
<string>
 |
""
 |
Defines which Mannequin Animation Database (ADB) file to load for this weapon's animations.
 |

**
animPrecache
**
 |
<string>
 |
""
 |
Pre-cache animation DBA files for this weapon.
 |

**
aimAnims
**
 |
<string>
 |
""
 |
**
DEPRECATED
**
 |

Delays
 |

 |

 |

 |

**
sprintToFireDelay
**
 |
<float>
 |
0.0
 |
Delay, in seconds, which prevents player from firing weapon after sprinting.
 |

**
sprintToZoomDelay
**
 |
<float>
 |
0.35
 |
Delay, in seconds, which prevents player from zooming weapon after sprinting.
 |

**
sprintToMeleeDelay
**
 |
<float>
 |
0.05
 |
Delay, in seconds, which prevents player from meleeing after sprinting.
 |

**
runToSprintBlendTime
**
 |
<float>
 |
0.2
 |
Delay, in seconds, to transition from running to sprinting state.
 |

**
sprintToRunBlendTime
**
 |
<float>
 |
0.2
 |
Delay, in seconds, to transition from sprinting to running state.
 |

**
autoReloadDelay
**
 |
<float>
 |
0.0
 |
Delay, in seconds, until the engine will automatically reload the weapon for the player, on empty of the current magazine.
 |

**
zoomTimeMultiplier
**
 |
<float>
 |
1.0
 |
Additional timing multiplier which can be used on accessories to slow down weapon zooming transitions.
 |

**
selectTimeMultiplier
**
 |
<float>
 |
1.0
 |
Additional timing multiplier which can be used on accessories to slow down weapon selection transitions.
 |

Stats
 |

 |

 |
DEPRECATED - See WeaponStats.cpp
 |

**
stat_accuracy
**
 |
<int>
 |

 |
Arbitrary number to portray designer interpretation of weapon performance, used to display on in-game HUD.
 |

**
stat_rate_of_fire
**
 |
<int>
 |

 |
Arbitrary number to portray designer interpretation of weapon performance, used to display on in-game HUD.
 |

**
stat_mobility
**
 |
<int>
 |

 |
Arbitrary number to portray designer interpretation of weapon performance, used to display on in-game HUD.
 |

**
stat_damage
**
 |
<int>
 |

 |
Arbitrary number to portray designer interpretation of weapon performance, used to display on in-game HUD.
 |

**
stat_range
**
 |
<int>
 |

 |
Arbitrary number to portray designer interpretation of weapon performance, used to display on in-game HUD.
 |

**
stat_recoil
**
 |
<int>
 |

 |
Arbitrary number to portray designer interpretation of weapon performance, used to display on in-game HUD.
 |

##
MovementModifiers

`
Code\GameSDK\GameDll\WeaponSharedParams.cpp
`

Param
 |
Type
 |
Default
 |
Description
 |

**
speedScale
**
 |
<float>
 |
1.0
 |
Player movement speed when using this zoom mode.
 |

**
rotationScale
**
 |
<float>
 |
1.0
 |
Player rotation speed when using this zoom mode.
 |

**
firingSpeedScale
**
 |
<float>
 |
1.0
 |
Player movement speed when firing, while using this zoom mode.
 |

**
firingRotationScale
**
 |
<float>
 |
1.0
 |
Player rotation speed when firing, while using this zoom mode.
 |

**
mouseRotationScale
**
 |
<float>
 |
1.0
 |
Same as
**
rotationScale
**
 but for Mouse input device only.
 |

##
Ammos

`
Code\GameSDK\GameDll\ItemSharedParams.cpp
`

`
Code\GameSDK\GameDll\WeaponSharedParams.cpp
`

Param

 |
Type

 |
Default
 |
Description

 |

**
name
**

 |
<string>

 |
""
 |
Specify the name of the ammo that will be used and obtained with the weapon.

 |

**
extra
**

 |
<int>

 |
0
 |
Amount of ammo that is given, extra ammo, aside from the current clip.

 |

**
amount
**

 |
<int>

 |
0
 |
Amount of ammo that is given, already loaded into the magazine.

 |

**
minAmmo
**

 |
<int>

 |
0
 |
Amount of ammo that is given from picked up weapons.

 |

**
accessoryAmmo
**

 |
<int>

 |
0
 |
Amount of weapon accessory ammo that is given. e.g; grenades for grenade launcher attachment.

 |

**
capacity
**

 |
<int>

 |
0
 |
Maximum ammo capacity for player's inventory.

 |

##
Fire

`
Code\GameSDK\GameDll\FireModeParams.cpp
`

Param
 |
Type
 |
Default
 |
Description
 |

**
suffix
**
 |
<string>
 |
""
 |

 |

**
suffixAG
**
 |
<string>
 |
""
 |

 |

**
tag
**
 |
<string>
 |
""
 |
Defines the fragment tag used by Mannequin for this firemode.
 |

**
rate
**
 |
<int>
 |
400
 |
The rate of fire (per minute) for the weapon.
 |

**
fake_fire_rate
**
 |
<int>
 |
0
 |

 |

**
minimum_ammo_count
**
 |
<int>
 |
0
 |

 |

**
clip_size
**
 |
<int>
 |
30
 |
The maximum amount of bullets a magazine for this weapon can carry.
 |

**
max_clips
**
 |
<int>
 |
20
 |
Maximum amount of clips player inventory can store for this weapon.
 |

**
hit_type
**
 |
<string>
 |
bullet
 |
The name of the hit type. This is used to set damage done to vehicles in vehicle XMLs.
 |

**
ammo_type
**
 |
<string>
 |
 ""
 |
The name of the bullet script that the weapon will fire. For the SDK Rifle, this is "RifleBullet" and the script is defined in:
`
Items/XML/Ammos/RifleBullet.xml
`
 |

**
ammo_type_spawn
**
 |
<string>
 |
""
 |

 |

**
hitTypeId
**
 |
<int>
 |
0
 |

 |

**
changeFMFireDelayFraction
**
 |
<float>
 |
0.0
 |
What percentage through the change firemode anim you can start firing in the new firemode, typically this is set to 1 (or 100%) of the anim.
 |

**
endReloadFraction
**
 |
<float>
 |
1.0
 |
What percentage of the way through the reload anim you can start firing again.
 |

**
fillAmmoReloadFraction
**
 |
<float>
 |
1.0
 |
What percentage of the way through the reload anim you can interrupt the reload and it will still count as having reloaded the weapon.
 |

**
autoReload

**
 |
<bool>
 |
true
 |
If more ammo is available then automatically reload weapon (without user input) after the last bullet is fired.
 |

**
autoSwitch
**
 |
<bool>
 |
true
 |

 |

**
stabilization
**
 |
<float>
 |
0.2
 |

 |

**
speed_override
**
 |
<float>
 |
0.0
 |

 |

**
bullet_chamber
**
 |
<int>
 |
0
 |
How many additional bullets can be loaded into the bullet chamber when weapon is reloaded.
 |

**
damage
**
 |
<int>
 |
32
 |
The damage this weapon will do by default.
 |

**
damage_drop_per_meter
**
 |
<float>
 |
0.0
 |
Amount of damage decrease per meter of projectile travel.
 |

**
damage_drop_min_distance
**
 |
<float>
 |
0.0
 |
Minimum distance the projectile has to travel before initiating damage drop calculations.
 |

**
damage_drop_min_damage
**
 |
<float>
 |
0.0
 |
Minimum damage value at which point the damage_drop_per_meter no longer applies
 |

**
point_blank_amount
**
 |
<float>
 |
1.0
 |

 |

**
point_blank_distance
**
 |
<float>
 |
0.0
 |

 |

**
point_blank_falloff_distance
**
 |
<float>
 |
0.0
 |

 |

**
ai_infiniteAmmo
**
 |
<bool>
 |
false
 |

 |

**
ai_vs_player_damage
**
 |
<int>
 |
0
 |
**
DEPRECATED (was replaced with npc_additional_damage)

**
Additional damage player receives when shot by AI with this weapon. Needs to be activated with
**
secondary_damage
**
.
 |

**
secondary_damage
**
 |
<bool>
 |
0
 |
**
DEPRECATED (was replaced with npc_additional_damage)
**

Allow additional damage from AI to player. Define damage amount with ai_vs_player_damage.
 |

**
npc_additional_damage
**
 |
<int>
 |
0
 |
Set a
**
damage
**
 value override for AI. If base
**
damage
**
 is 40 and
**
npc_additional_damage
**
 is set to 5 then the final damage will be 45. Negative values are also supported.
 |

**
crosshair
**
 |
<int>
 |
1
 |
**
DEPRECATED

**
Maps to specific flash frames to override the weapon crosshair.
 |

**
no_cock
**
 |
<bool>
 |
true
 |
If set to false, will attempt to play "fire_cock" Mannequin fragment. Useful for bolt-action rifles for example.
 |

**
helper_fp
**
 |
<string>
 |
""
 |

 |

**
helper_tp
**
 |
<string>
 |
""
 |

 |

**
barrel_count
**
 |
<int>
 |
1
 |

 |

**
spin_up_time
**
 |
<float>
 |
0.0
 |

 |

**
fire_anim_damp
**
 |
<float>
 |
1.0
 |

 |

**
ironsight_fire_anim_damp
**
 |
<float>
 |
1.0
 |

 |

**
holdbreath_ffeedback_damp
**
 |
<float>
 |
0.5
 |

 |

**
holdbreath_fire_anim_damp
**
 |
<float>
 |
0.5
 |

 |

**
knocks_target
**
 |
<bool>
 |
false
 |

 |

**
min_damage_for_knockDown
**
 |
<int>
 |
0
 |

 |

**
knockdown_chance_leg
**
 |
<int>
 |
0
 |

 |

**
min_damage_for_knockDown_leg
**
 |
<int>
 |
0
 |

 |

**
bullet_pierceability_modifier
**
 |
<int>
 |
0
 |

 |

**
is_silenced
**
 |
<bool>
 |
false
 |

 |

**
ignore_damage_falloff
**
 |
<bool>
 |
false
 |

 |

**
muzzleFromFiringLocator
**
 |
<bool>
 |
false
 |

 |

##
Recoil

`
Code\GameSDK\GameDll\Recoil.cpp
`

Param
 |
Type
 |
Default
 |
Description
 |

**
max_recoil
**
 |
<float>
 |
0.0
 |
Max_recoil is an arbitrary value which is mapped onto the
**
maxx
**
 and
**
maxy
**
 and is referenced by the
**
attack
**
.
 |

**
attack
**
 |
<float>
 |
0.0
 |
Attack is the fraction of the
**
max_recoil
**
 added on with each bullet fired, so effectively
**
attack
**
 is the fraction of the
**
maxx
**
 and
**
maxy
**
 added on with each shot. As an example if
**
max_recoil
**
 is 1 (as it usually is for clarity) and
**
maxy
**
 is 3.0 and
**
attack
**
 is 0.33 then the first shot causes the sights to recoil upwards 1 degree, the second shot causes the sights to continue to climb now up 2 degrees and the third and all subsequent shots hold the sights at 3 degrees above the initial aim point.  However, its not quite that simple because we also have
**
decay
**
.
 |

**
first_attack
**
 |
<float>
 |
0.0
 |
**
First_attack
**
 is only applied to the first bullet, it can be used to give an extra large initial attack and then use a lower attack for the subsequent shots, typically to prevent people tapping fire to be really accurate.
 |

**
decay
**
 |
<float>
 |
0.65
 |
**
Decay
**
 is the time in seconds it takes for the
**
max_recoil
**
 to be reduced to zero. If
**
max_recoil
**
 is 1 and
**
decay
**
 is 1.0 second then every 10
th
 of a second the
**
max_recoil
**
 would be reduced by 0.1. The
**
rate
**
 must be taken into account of course. At
**
rate
**
 600 the gun fires 10 bullets per second. If
**
attack
**
 is set to 0.1 and
**
decay
**
 is set to 1.0 then every tenth of a second the
**
max_recoil
**
 is reduced by 10% or 0.1 attack. So in this case each shot causes 10% of the total recoil to be applied but the sights then return to 0 recoil just as the next bullet is fired, so the sights do not climb steadily in the Y whilst the trigger is held down. If
**
decay
**
 is increased slightly then
**
attack
**
 has not returned to 0 before the next bullet is fired so the sights slowly climb as the trigger is held down until the
**
attack
**
 reaches the
**
max_recoil
**
.
 |

**
end_decay
**
 |
<float>
 |
0.0
 |
**
End_decay
**
 is the time it takes for the
**
max_decay
**
 value to return to zero once firing ceases.
 |

**
recoil_time
**
 |
<float>
 |
0.0
 |
The length of time decay will apply after a shot.
 |

**
maxx
**
 |
<float>
 |
8.0
 |
**
Maxx
**
 is the maximum recoil deviation in degrees along the x-axis (upwards).  This is influenced by the <hints>.
 |

**
maxy
**
 |
<float>
 |
4.0
 |
**
Maxy
**
 is the maximum recoil deviation in degrees upwards in the y-axis (sideways). This is influenced by the <hints>.
 |

**
tilt
**
 |
<float>
 |
0.0
 |
Applies a rotation to the recoil to tilt the camera/HUD. The higher the number, the more rotation that is applied.
 |

**
randomness
**
 |
<float>
 |
1.0
 |
**
Randomness
**
 is added to each
**
hint
**
 when they are applied to the x and added or subtracted from the y recoil (should be added or subtracted to x as well).
 |

**
impulse
**
 |
<float>
 |
0.0
 |
Value defines the amount of physical impulse when firing. Firing direction is calculated and then impulse is applied to the weapon owner. If a character is holding this weapon, the character also receives the impulse.
 |

**
recoil_crouch_m
**
 |
<float>
 |
0.85
 |
**
Recoil_crouch_m
**
 is the modifier to recoil when player is in crouched stance. If this is
**
greater
**
 than 1.0, the recoil in Crouch will be less than the recoil in Stand stance.

This value is applied to the amount of
**
decay
**
 reduction per frame and increasing the decay per frame reduces the recoil.
 |

**
recoil_jump_m
**
 |
<float>
 |
1.5
 |
**
Recoil_jump_m
**
 is the modifier to recoil when jumping (or falling, essentially if the player is in the air). If this is
**
less
**
 than 1.0, the recoil will be greater in the air than the recoil while on the ground.

This value is applied to the amount of
**
decay
**
 reduction per frame and increasing the decay per frame reduces the recoil.
 |

**
recoil_holdBreathActive_m
**
 |
<float>
 |
0.5
 |
**
Recoil_holdBreathActive_m
**
 is the modifier to recoil when player is holding their breath. If this is less than 1.0, the recoil while holding breath will be less than the standard recoil.
 |

##
RecoilShake

`
Code\GameSDK\GameDll\FireModePluginParams.cpp
`

Param
 |
Type
 |
Default
 |
Description
 |

**
rotateShake
**
 |
<vec3>
 |
0,0,0
 |
Amount to rotate the camera on the X,Y,Z axis.
 |

**
shiftShake
**
 |
<vec3>
 |
0,0,0
 |
Amount to shift the camera on the X, Y, Z axis.
 |

**
frequency

**
 |
<float>
 |
1.0
 |
How frequently to apply the shift/rotation. '2' will mean it's applied every 2 seconds.
 |

**
time
**
 |
<float>
 |
0.1
 |
Time taken to achieve the full amount of shift/rotation. '3' will mean it takes 3 seconds to reach maximum XYZ values and return to normal.
 |

**
randomness
**
 |
<float>
 |
0.0
 |
Add randomness to all values.
 |

##
Spread

`
Code\GameSDK\GameDll\Recoil.cpp
`

Param
 |
Type
 |
Default
 |
Description
 |

**
min
**
 |
<float>
 |
0.015
 |
Minimum spread (cone size) in all directions.
 |

**
max
**
 |
<float>
 |
0.0
 |
Maximum spread (cone size) in all directions, excluding modifiers.
 |

**
attack
**
 |
<float>
 |
0.95
 |
**
Attack
**
 is the amount the cone size increases with each bullet until the
**
max
**
 is reached.
 |

**
decay
**
 |
<float>
 |
0.65
 |
Time taken for the
**
attack
**
 to reduce to zero. Is active whenever your spread is above minimum, but is more noticeable when not firing.
 |

**
end_decay
**
 |
<float>
 |
0.65
 |
**
End_decay
**
 is the time to reduce the
**
attack
**
 to 0 once firing stops.
 |

**
speed_m
**
 |
<float>
 |
0.25
 |
Amount of spread added while moving. Multiplies the current velocity by the amount stated and then adds it to the
**
attack
**
.

This can take
**
attack
**
 above the
**
max
**
 spread. As an example if the player is moving at 5m/s and the
**
Speed_m
**
 is set to 0.2 then the attack will be increased by 1.
 |

**
speed_holdBreathActive_m
**
 |
<float>
 |
0.25
 |
Additional modifier placed on top of
**
speed_m
**
, used when the 'hold breath' function is active.
 |

**
rotation_m
**
 |
<float>
 |
0.35
 |
Amount of spread added while rotating (turning, pitching, etc).
 |

**
spread_crouch_m
**
 |
<float>
 |
0.85
 |
**
Spread_crouch_m
**
 is a modifier that alters the spread whilst in Crouch stance. The lower this is below 1 the greater the reduction.
 |

**
spread_jump_m
**
 |
<float>
 |
1.5
 |
**
Spread_jump_m
**
 is a modifier that alters the spread whilst jumping (or falling, essentially if the player is in the air). The higher this is above 1 the greater the increase.
 |

**
spread_slide_m
**
 |
<float>
 |
1.0
 |
**
Spread_slide_m
**
 is a modifier that alters the spread whilst in sliding state. The lower this is below 1 the greater the reduction.
 |

**
spread_holdBreathActive_m
**
 |
<float>
 |
1.0
 |
Additional modifier which affects final spread result, used when the 'hold breath' function is active. The lower this is below 1 the greater the reduction.
 |

##
Tracer

`
Code\GameSDK\GameDll\FireModeParams.cpp

Code\GameSDK\GameDll\TracerManager.cpp

`

Param
 |
Type
 |
Default
 |
Description
 |

**
geometryFP
**
 |
<string>
 |
""
 |
Path to the object file of the first person tracer.
 |

**
geometry
**
 |
<string>
 |
""
 |
Path to the object file of the third person tracer.
 |

**
effectFP
**
 |
<string>
 |
""
 |
Path to the particle effect for the first person tracer.
 |

**
effect
**
 |
<string>
 |
""
 |
Path to the third person particle effect for the tracer.
 |

**
speed
**
 |
<float>
 |
200.0
 |
Speed at which you see the tracer fly in third person (should be equal to the bullet's speed).
 |

**
speedFP
**
 |
<float>
 |
400.0
 |
Speed at which you see the tracer fly in first person (should be equal to the bullet's speed).
 |

**
thickness
**
 |
<float>
 |
1.0
 |

 |

**
thicknessFP
**
 |
<float>
 |
1.0
 |

 |

**
lifetime
**
 |
<float>
 |
1.5
 |

 |

**
frequency
**
 |
<int>
 |
1
 |
How often a new tracer appears per bullet. If 1, every bullet will have a tracer. If 2, every second bullet will have a tracer, etc.
 |

**
delayBeforeDestroy
**
 |
<float>
 |
0.0
 |

 |

**
slideFraction
**
 |
<float>
 |
0.5
 |

 |

**
helper_fp
**
 |
<string>
 |
""
 |

 |

**
helper_tp
**
 |
<string>
 |
""
 |

 |

##
Rapid

`
Code\GameSDK\GameDll\FireModeParams.cpp
`

Param
 |
Type
 |
Default
 |
Description
 |

**
min_speed
**
 |
<float>
 |
1.5
 |

 |

**
max_speed
**
 |
<float>
 |
3.0
 |

 |

**
acceleration
**
 |
<float>
 |
3.0
 |

 |

**
deceleration
**
 |
<float>
 |
3.0
 |

 |

**
barrel_attachment
**
 |
<string>
 |
""
 |

 |

**
min_firingTimeToStop
**
 |
<float>
 |
0.1
 |

 |

##
Melee

`
Code\GameSDK\GameDll\FireModeParams.cpp
`

Param
 |
Type
 |
Default
 |
Description
 |

**
helper
**
 |
<string>
 |
""
 |
Object used for collision detection when performing melee attack?
 |

**
range
**
 |
<float>
 |
1.75
 |

 |

**
target_range_mult
**
 |
<float>
 |
1.5
 |

 |

**
damage
**
 |
<int>
 |
32
 |
Default damage done by a melee hit.
 |

**
damage_ai
**
 |
<int>
 |
32
 |

 |

**
impulse
**
 |
<float>
 |
50.0
 |
How much the player will be pushed back when performing a melee attack.
 |

**
impulse_actor
**
 |
<float>
 |
200.0
 |

 |

**
impulse_ai_to_player
**
 |
<float>
 |
-1.0
 |

 |

**
impulse_vehicle
**
 |
<float>
 |
50.0
 |

 |

**
ai_delay
**
 |
<float>
 |
0.5
 |

 |

**
delay
**
 |
<float>
 |
0.5
 |
Time between pressing the Melee button and the damage happens.
 |

**
duration
**
 |
<float>
 |

 |
Duration of the animation?/Duration of time the helper can collide with objects during animation?
 |

**
knockdown_chance
**
 |
<float>
 |
0.0
 |

 |

**
impulse_up_percentage
**
 |
<float>
 |
0.0
 |

 |

**
use_melee_weapon_delay
**
 |
<float>
 |
-1.0
 |

 |

**
is_melee_weapon
**
 |
<bool>
 |
false
 |

 |

**
weapon_restore_delay
**
 |
<float>
 |
0.0
 |

 |

**
FPSignal
**
 |
<string>
 |
""
 |

 |

**
3PSignal
**
 |
<string>
 |
""
 |

 |

closeAttack
 |

 |

 |

 |

**
range
**
 |
<float>
 |
1.75
 |

 |

**
delay
**
 |
<float>
 |
0.5
 |

 |

**
duration
**
 |
<float>
 |
0.5
 |

 |

**
impulse_ai_to_player
**
 |
<float>
 |
-1.0
 |

 |

##
Zoom

`
Code\GameSDK\GameDll\WeaponSharedParams.cpp
`

Param
 |
Type
 |
Default
 |
Description
 |

**
suffix
**
 |
<string>
 |
ironsight
 |

 |

**
suffixAG
**
 |
<string>
 |
""
 |

 |

**
dof
**
 |
<bool>
 |
false
 |

 |

**
dof_focusMin
**
 |
<float>
 |
1.0
 |

 |

**
dof_focusMax
**
 |
<float>
 |
150.0
 |

 |

**
dof_focusLimit
**
 |
<float>
 |
150.0
 |

 |

**
dof_shoulderMinZ
**
 |
<float>
 |
0.0
 |

 |

**
dof
**
_
**
shoulderMinZScale
**
 |
<float>
 |
0.0
 |

 |

**
dof_minZ
**
 |
<float>
 |
0.0
 |

 |

**
dof_minZScale
**
 |
<float>
 |
0.0
 |

 |

**
blur_amount
**
 |
<float>
 |
0.0
 |

 |

**
blur_mask
**
 |
<string>
 |
""
 |

 |

**
dof_mask
**
 |
<string>
 |
""
 |
Path to the blur mask used for the depth of field (DoF) effect.
 |

**
zoom_overlay
**
 |
<string>
 |
""
 |

 |

**
zoom_in_time
**
 |
<float>
 |
0.35
 |
Amount of time it takes to zoom in.
 |

**
zoom_out_time
**
 |
<float>
 |
0.35
 |
Amount of time it takes to zoom out.
 |

**
zoom_out_delay
**
 |
<float>
 |
0.0
 |

 |

**
stage_time
**
 |
<float>
 |
0.055
 |

 |

**
scope_mode
**
 |
<bool>
 |
 false
 |
Indicates whether this is a scope or an ironsight zoommode.
 |

**
scope_nearFov
**
 |
<float>
 |
 55.0
 |
Field of view (FoV) when zoomed in (the lower the more zoomed).
 |

**
shoulderRotationAnimFactor
**
 |
<float>
 |
1.0
 |

 |

**
shoulderStrafeAnimFactor
**
 |
<float>
 |
1.0
 |

 |

**
shoulderMovementAnimFactor
**
 |
<float>
 |
1.0
 |

 |

**
ironsightRotationAnimFactor
**
 |
<float>
 |
1.0
 |

 |

**
ironsightStrafeAnimFactor
**
 |
<float>
 |
1.0
 |

 |

**
ironsightMovementAnimFactor
**
 |
<float>
 |
1.0
 |

 |

**
cameraShakeMultiplier
**
 |
<float>
 |
1.0
 |

 |

**
muzzle_flash_scale
**
 |
<float>
 |
1.0
 |

 |

**
fp_offset
**
 |
<quat>
 |

 |

 |

**
fp_rot_offset
**
 |
<quat>
 |

 |

 |

**
hide_weapon
**
 |
<bool>
 |
false
 |
Hide the weapon when using this zoom mode.
 |

**
target_snap_enabled
**
 |
<bool>
 |
true
 |

 |

**
hide_crosshair
**
 |
<bool>
 |
true
 |

 |

**
near_fov_sync
**
 |
<bool>
 |
false
 |

 |

**
armor_bonus_zoom
**
 |
<bool>
 |
false
 |
**
DEPRECATED
**
 |

Stages
 |

 |

 |

 |

**
value
**
 |
<float>
 |
1.5
 |

 |

**
rotationSpeedScale
**
 |
<float>
 |
1.0
 |

 |

**
movementSpeedScale
**
 |
<float>
 |
1.0
 |

 |

**
useDof
**
 |
<bool>
 |
true
 |

 |

##
zoomSway

`
Code\GameSDK\GameDll\WeaponSharedParams.cpp
`

Param
 |
Type
 |
Default
 |
Description
 |

**
maxX
**
 |
<float>
 |
0.0
 |
Maximum sway on the X (up/down) axis when zoomed in.
 |

**
maxY
**
 |
<float>
 |
0.0
 |
Maximum sway on the Y (left/right) axis when zoomed in.
 |

**
stabilizeTime
**
 |
<float>
 |
3.0
 |
Time taken (in seconds) for sway to stabilize down to minScale value, when activating scope/ironsight.
 |

**
holdBreathScale
**
 |
<float>
 |
0.1
 |

 |

**
holdBreathTime
**
 |
<float>
 |
1.0
 |

 |

**
minScale
**
 |
<float>
 |
0.15
 |
Scale of maxX/Y once fully stabilized (see stabilizeTime).
 |

**
scaleAfterFiring
**
 |
<float>
 |
0.5
 |

 |

**
crouchScale
**
 |
<float>
 |
0.8
 |
Amount the zoom sway is scaled when the player is crouching.
 |

##
Scope

`
Code\GameSDK\GameDll\WeaponSharedParams.cpp
`

Param
 |
Type
 |
Default
 |
Description
 |

**
helper_name
**
 |
<string>
 |
""
 |

 |

**
crosshair_sub_material
**
 |
<string>
 |
""
 |

 |

**
dark_out_time
**
 |
<float>
 |
0.025
 |

 |

**
dark_in_time
**
 |
<float>
 |
0.15
 |

 |

**
techvisor
**
 |
<bool>
 |
false
 |
**
DEPRECATED
**
 |

##
spreadMod

While the zoom mode is being used the values in
 |
<spread> are multiplied by the matching values here.
 |
Eg: "attack_mod" matches with "attack".
 |

##
recoilMod

While the zoom mode is being used the values in
 |
<recoil> are multiplied by the matching values here.
 |
Eg: "attack_mod" matches with "attack".
 |

##
Ammo

Bullets, rockets, grenades, etc.

##
Flags

Param
 |
Type
 |
Default
 |
Description
 |

**
ClientOnly
**
 |
<int>
 |

 |
Indicates whether the ammo type is only hosted on the client or also on the server.
 |

**
ServerOnly
**
 |
<int>
 |

 |

 |

**
ServerSpawn
**
 |
<bool>
 |
false
 |

 |

**
PredictSpawn
**
 |
<bool>
 |
false
 |
Indicates whether the game will predict where the bullet will go. Used with
**
ServerSpawn
**
.
 |

**
Reusable
**
 |
<bool>
 |
false
 |
Not used with
**
ServerSpawn
**
.
 |

##
Physics

Setting the Physics "Type" will unlock certain parameters based on which you choose. See
**
AmmoParams.cpp
**
 for more detailed code information.

"Rigid" is designed to be used for projectiles such as cannonballs, for example. "Particle" is designed to be used for projectiles which have added effects like smoke trails or flame effects.

Param
 |
Type
 |
Description
 |
Used With
 |

**
type
**
 |
<string>
 |
"particle", "rigid", or "static".
 |

 |

**
material
**
 |
<string>
 |
Surface material applied to the bullet.
 |
All
 |

**
mass
**
 |
<float>
 |
Weight of the bullet, in kg.
 |
Static/Rigid
 |

**
speed
**
 |
<float>
 |
Speed at which the bullet will fly (m/s).
 |
Static/Rigid
 |

**
max_logged_collisions
**
 |
<int>
 |
Maximum amount of collisions before the projectile disappears/explodes. single_contact must be set to 0.
 |
Static/Rigid
 |

**
traceable
**
 |
<bool>
 |
TBA
 |
Static/Rigid
 |

**
spin
**
 |
<vec3>
 |
Applies a vector rotation on the ammo CGF, useful for things like grenade launchers.
 |
Static/Rigid
 |

**
spin_random
**
 |
<vec3>
 |
Applies a random vector rotation on the ammo CGF, useful for things like grenade launchers.
 |
Static/Rigid
 |

**
bounceableBullet
**
 |
<int>
 |
TBA
 |
Static/Rigid
 |

**
single_contact
**
 |
<int>
 |
Indicates whether the bullet/rocket will explode on first contact.
 |
Particle
 |

**
constant_orientation
**
 |
<int>
 |
TBA
 |
Particle
 |

**
no_roll
**
 |
<int>
 |
Disable roll on the particle effect.
 |
Particle
 |

**
no_spin
**
 |
<int>
 |
Disable spin on the particle effect.
 |
Particle
 |

**
no_path_alignment
**
 |
<int>
 |
Disable path alignment on the particle effect.
 |
Particle
 |

**
radius
**
 |
<float>
 |
Radius of the projectile, for collision purposes.
 |
Particle
 |

**
air_resistance
**
 |
<float>
 |
How much the bullet will be slowed down by air friction, when in the air (m/s
2
).
 |
Particle
 |

**
water_resistance
**
 |
<float>
 |
How much the bullet will be slowed down by water friction, when underwater (m/s
2
).
 |
Particle
 |

**
gravity
**
 |
<vec3>
 |
Amount of gravity applied to the bullet when in flight (m/s
2
).
 |
Particle
 |

**
water_gravity
**
 |
<vec3>
 |
Amount of gravity applied to the bullet when underwater (m/s
2
).
 |
Particle
 |

**
thrust
**
 |
<float>
 |
Speed at which the bullet leaves the barrel (m/s).
 |
Particle
 |

**
lift
**
 |
<float>
 |
Amount of upward acceleration the projectile receives (m/s
2
).
 |
Particle
 |

**
min_bounce_speed
**
 |
<float>
 |
Minimum speed the projectile must be traveling for the it to bounce off objects and terrain (must have single_contact to 0, in m/s).
 |
Particle
 |

**
pierceability
**
 |
<int>
 |
Indicates what surface materials the bullet can penetrate. Surface pierceability is defined through
[/docs/static/engines/cryengine-3/categories/1114113/pages/1310761](
SurfaceTypes
)
.
 |
Particle
 |

**
rollAxis
**
 |
<vec3>
 |
TBA
 |
Particle
 |

##
Explosion

Param
 |
Type
 |
Description
 |

**
pressure
**
 |
<float>
 |
Force of the explosion. Size is defined by min/max_phys_radius.
 |

**
min_radius
**
 |
<float>
 |
Minimum damage radius of the explosion (meters).
 |

**
max_radius
**
 |
<float>
 |
Maximum damage radius of the explosion (meters).
 |

**
hole_size
**
 |
<float>
 |
**
DEPRECATED -
**
 Related to the hole created when terrain deformation is activated.
 |

**
terrain_hole_size
**
 |
<float>
 |
**
DEPRECATED -
**
 Related to the hole created when terrain deformation is activated.
 |

**
decal
**
 |
<string>
 |
Path to the decal the projectile will spawn on explosion.
 |

**
effect
**
 |
<string>
 |
Default explosion effect (particle).
 |

**
effect_scale
**
 |
<string>
 |
Amount the explosion effect will be scaled (multiplier).
 |

**
type
**
 |
<string>
 |
Hit type definition for the projectile. (TBA)
 |

**
min_phys_radius
**
 |
<float>
 |
Minimum radius for things to be effected by the explosion force (meters).
 |

**
max_phys_radius
**
 |
<float>
 |
Maximum radius for things to be effected by the explosion force (meters).
 |

**
radialblurdist
**
 |
<float>
 |
Radius in which players vision is blurred by the explosion (meters).
 |

**
sound_radius
**
 |
<float>
 |
TBA
 |

##
Collision

Param
 |
Type
 |
Description
 |

**
sound
**
 |
<string>
 |
Sound to be played on collision.
 |

**
effect
**
 |
<string>
 |
Particle effect to be played on collision.
 |

**
scale
**
 |
<float>
 |
Amount the above is scaled.
 |

##
Params

`
Code\GameSDK\GameDll\AmmoParams.cpp
`

Param
 |
Type
 |
Default
 |
Description
 |

**
lifetime
**
 |
<float>
 |

 |
Length of time ammo (particle/geometry) should be rendered for, after being fired (seconds).
 |

**
showtime
**
 |
<float>
 |

 |
Time delay before engine starts rendering the ammo (particle/geometry), after being fired (seconds).
 |

**
armTime
**
 |
<float>
 |

 |

 |

**
sleepTime
**
 |
<float>
 |

 |

 |

**
safeExplosion
**
 |
<float>
 |

 |

 |

**
mpProjectileDestructDelay
**
 |
<float>
 |

 |

 |

**
bulletType
**
 |
<int>
 |

 |

 |

**
hitPoints
**
 |
<int>
 |

 |

 |

**
noBulletHits
**
 |
<bool>
 |

 |
Shooting the ammo does not remove hit points.
 |

**
quietRemoval
**
 |
<bool>
 |

 |
Will not cause the ammo to explode when they time out.
 |

**
aitype
**
 |
<string>
 |

 |
What the AI will treat the projectile as, "grenade" or "rpg".
 |

**
display_name
**
 |
<string>
 |

 |

 |

**
ammo_category
**
 |
<int>
 |

 |
The
[/docs/static/engines/cryengine-3/categories/1114113/pages/1048755#ItemsEntities-AmmoCrate](
AmmoCrate
)
 entity recharges ammo of a particular "Ammo Category". With this you can define which ammo types should be added or not.
 |

**
trackOnHud
**
 |
<bool>
 |

 |

 |

**
hitRecoil
**
 |
<int>
 |

 |

 |

**
hitRecoilArmorMode
**
 |
<int>
 |

 |

 |

##
Homing Missile

`
Code\GameSDK\GameDll\AmmoParams.cpp

Code\GameSDK\GameDll\HomingMissile.cpp

`

Params
 |
 Type
 |
Default
 |
Description
 |

**
cruise
**
 |
<bool>
 |
true
 |
If set, the projectile will attempt to cruise at an altitude before striking the target.
 |

**
cruise_altitude
**
 |
<float>
 |
100.0
 |
Altitude the projectile will attempt to cruise at if "cruise" is enabled (meters).
 |

**
cruiseActivationTime
**
 |
<float>
 |
0.0
 |

 |

**
controlled
**
 |
<bool>
 |
false
 |
Indicated whether the projectile will seek the target or not.
 |

**
autoControlled
**
 |
<bool>
 |
false
 |

 |

**
accel
**
 |
<float>
 |
10.0
 |

 |

**
initial_delay
**
 |
<float>
 |
0.2
 |

 |

**
align_altitude
**
 |
<float>
 |
50.0
 |
Altitude the projectile must reach before it points toward the target, should be less than "cruise_altitude" (meters).
 |

**
descend_distance
**
 |
<float>
 |
50.0
 |
Distance to the target when cruise will end and the projectile will head directly to the target. Should be less than both "cruise_altitude" and "align_altitude" (meters).
 |

**
turn_speed
**
 |
<float>
 |
2.0
 |
Maximum centripetal acceleration the projectile can achieve (m/s
2
).
 |

**
max_speed
**
 |
<float>
 |
20.0
 |

 |

**
max_target_distance
**
 |
<float>
 |
200.0
 |
Maximum distance for the homing target (meters).
 |

**
lazyness
**
 |
<float>
 |
0.35
 |

 |

**
tracks_chaff
**
 |
<bool>
 |
false
 |

 |

**
detonation_radius
**
 |
<float>
 |
0.0
 |

 |

##
Flashbang

Param
 |
Type
 |
Default
 |
Description
 |

**
max_radius
**
 |
<float>
 |
25.0
 |
TBA
 |

**
blindAmount
**
 |
<float>
 |
0.7
 |
TBA
 |

**
flashbangBaseTime
**
 |
<float>
 |
2.5
 |
TBA
 |

##
Trail

Param
 |
Type
 |
Default
 |
Description
 |

**
effect
**
 |
<string>
 |
""
 |
Path to the effect of the trail of the projectile.
 |

**
effect_fp
**
 |
<string>
 |
""
 |
Path to the effect of the trail of the projectile, as shown in First Person view.
 |

**
scale
**
 |
<float>
 |
1.0
 |
Define the size of the effect used in the trail.
 |

**
sound
**
 |
<string>
 |
""
 |
**
DEPRECATED -
**
 The sound the projectile's trail makes. Like a missile's thruster or a bullet's whiz.
 |

**
prime
**
 |
<bool>
 |
false
 |
Starts in equilibrium state, as if activated in past.
 |

##
trailUnderWater

Param
 |
Type
 |
Description
 |

**
effect
**
 |
<string>
 |
Path to the effect of the bullet trail when the bullet is underwater.
 |

**
scale
**
 |
<float>
 |
Amount the above is scaled.
 |

##
BulletTimeParams

Param
 |
Type
 |
Default
 |
Description
 |

**
geometry
**
 |
<string>
 |
""
 |

 |

**
**
effect
**
**
 |
<string>
 |
""
 |

 |

**
disableRifling
**
 |
<bool>
 |
false
 |

 |

**
always
**
 |
<bool>
 |
false
 |

 |

[#items](
Items
)
[#root](
Root
)
[#params](
Params
)
[#movementmodifiers](
MovementModifiers
)
[#ammos](
Ammos
)
[#fire](
Fire
)
[#recoil](
Recoil
)
[#recoilshake](
RecoilShake
)
[#spread](
Spread
)
[#tracer](
Tracer
)
[#rapid](
Rapid
)
[#melee](
Melee
)
[#zoom](
Zoom
)
[#zoomsway](
zoomSway
)
[#scope](
Scope
)
[#spreadmod](
spreadMod
)
[#recoilmod](
recoilMod
)
[#ammo](
Ammo
)
[#flags](
Flags
)
[#physics](
Physics
)
[#explosion](
Explosion
)
[#collision](
Collision
)
[#params](
Params
)
[#homing-missile](
Homing Missile
)
[#flashbang](
Flashbang
)
[#trail](
Trail
)
[#trailunderwater](
trailUnderWater
)
[#bullettimeparams](
BulletTimeParams
)
