# EaaS 3.6.13

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/47316993/pages/44963019
- Page ID: 44963019
- Breadcrumb: Engine Release Notes (Current) > CRYENGINE 3.x > EaaS 3.6 > EaaS 3.6.13
- Parent: EaaS 3.6

## Content

Released 8th December, 2014

##
Editor

-
**
Fixed
**
: Re-saving a level breaks the pivot positions of prefabs (CE-5083).

-
**
Fixed
**
: Changing game rules to MP in the editor causes a crash (CE-5094).

##
Engine

-
**
Fixed
**
: (3DEngine) Compile time assert in GetStatObjAndMatTables moved to GenerateStatObjAndMatTables (CE-5066).

-
**
Fixed
**
: (RC) Fixed bug in removal of duplicate morph vertices.

-
**
Fixed
**
: (Particles) Crash during phys area update callback (CE-4890).

-
**
Fixed
**
: (Dedicated Server) Recording system now disabled to prevent crash on level load.

-
**
Fixed
**
: (Dedicated Server) Now handle "quit" command without crash.

-
**
Fixed
**
: (RC ColladaCompiler) Now using temporary .$tmp$ file when saving .cgf to prevent Editor's file monitor from reading half-written file (CE-5064).

-
**
Fixed
**
: Change SRenderLight::EntityId back to 32 bit, reduce SRenderLight::m_Id to 16 bits instead (this should work until we support more than 32767 lights per frame!) (CE-5035).

-
**
Fixed
**
: Physicalization issue with multi-part brushes.

##
Renderer

-
**
Fixed
**
: HUD UI flickering when coming out of menu (CE-4594).

-
**
Fixed
**
: Wrong assert in ConvertToDepthStencilFmt (CE-5015).

##
Audio

-
**
Fixed
**
: Pushing audio request with invalid data in CAnimSceneNode::ApplyAudioKey.

##
Assets

-
**
New
**
: Include *.wem files in Sounds.pak.

-
**
New
**
: Added new campfire PFX that responds to wind effects: campfire.small_wind.

-
**
Fixed
**
: normal-map with gloss-map preset on Moss texture.

-
**
Fixed
**
: FPE due to UI errors.

-
**
Fixed
**
: Delayed the stretch on pfx : waterfall_refract.

-
**
Fixed
**
: Increased texture resolution on some rock assets.

-
**
Fixed
**
: Tweaked grass_4 material, added new grass_4_ddna.

-
**
Fixed
**
: Tweaked snow material/textures.

-
**
Optimized
**
: Characters Archetypes: Made Easy versions less perceptive but increased health. Set all to be affectedByLight.

-
**
Optimized
**
: Copied and repathed game character head textures at lower resolution more suited to game rather than showcase.
