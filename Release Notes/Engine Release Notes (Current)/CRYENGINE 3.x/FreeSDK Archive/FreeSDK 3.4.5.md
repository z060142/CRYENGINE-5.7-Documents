# FreeSDK 3.4.5

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/47316993/pages/44963030
- Page ID: 44963030
- Breadcrumb: Engine Release Notes (Current) > CRYENGINE 3.x > FreeSDK Archive > FreeSDK 3.4.5
- Parent: FreeSDK Archive

## Content

##
CryENGINE 3 Free SDK – Build 6666 Changelog

Released February 27th, 2013

**
Fixed
**

-
Out of memory crash and random snow appearance in levels.

-
Remove deprecated "merge static geometry" option.

-
Scrolling was sending wrong mouse coordinates which makes the rotate screen flip out.

-
Potential crash when a server session shuts down and a client tries to connect at the same time.

-
Player profile (no save implementation) uses incorrect SaveProfile signature.

-
Animations don't update after player revives.

-
Client side collision handling.

-
Fixed Mounted Gun pointing to incorrect particle effect.

-
ALT-Tabbing from Editor game mode doesn't confine cursor anymore.

-
Fixed possible/rare crash with null shader pointer in EF_AddParticle.

-
Fire particle needs to be reloaded to turn on/off debug draw.

-
Fixed muzzle-flash delay, connect-to-origin particles, and other issues: CParticle.Update() is again called in all cases from CParticle.Init(), handles negative ages.

-
FG: The 'Door' Entity Locked/Unlocked function cannot be triggered using flowgraph.

-
Vehicle Editor component bound size.

-
Making a change to a level, creating a new level and Cancelling when asked if you want to save your current level crashes the editor.

-
Wrong set of sound velocity when updating particle sounds (velocity is calculated internally).

**
Tweak
**

-
Changed SphereRandomPos function algorithm to be single-pass, using parametric phi/theta/z coords.

-
Set AreaBezierVolume entity to invisible as it's obsolete.

-
Removed destroy vehicle on submerge in DM gamerules.

-
Increased flash memory space to 64MB on PC, set to 32MB for console.

-
Select Objects tool: realigned elements, fixed elements artifacting from resize, limited minimum window size to ensure all content is displayed.

-
Set Gravity entities to use same Editor gravity icon.

-
Updated flag entity model and Editor icon.

-
Set gravitysphere entity to place icon at pivot, not at top of sphere.

-
Increased vegetation sprite texture resolution.

-
Tweaked SCAR muzzleflash light to be more orange, added muzzleflash light to single firemode.

-
Pressurized object, set to canister model, changed leak particle effect.

**
New Feature
**

-
Added OffsetInnerScale param, to define inner emission volume.

-
Change ca_UseIMG_AIM = 1, ca_UseIMG_CAF = 1.

-
Added scroll wheel support for Flash in Launcher.
