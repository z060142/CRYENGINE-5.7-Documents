# Art Asset File Types

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/44959591
- Page ID: 44959591
- Breadcrumb: Asset Prep (External) > Asset Exporting Overview > Art Asset File Types
- Parent: Asset Exporting Overview

## Content

##
Overview

There are several file types that are relevant for CRYENGINE artists and animators in their daily work. This page lists the different file types along with a brief description of their functions and uses.

##
Geometry Assets

[Image: /docs/static/attachments/44959595]

**
.cgf (Crytek Geometry Format)
**

The .cgf file is created in the 3D application and contains geometry data (grouped triangles, vertex attributes like tangent space or vertex color and optional physics data).

**
.chr (Character)
**

The .chr file is created in the 3D application and contains the skeleton data and physics proxies used for hit detection and ragdoll simulation that are driven by animations.

**
.cga (Crytek Geometry Animation)
**

The .cga file is a pivot based animated hard body geometry data. That means we do not use a skinned geometry for this asset type and still get animated rigid parts of an Entity in the Engine. This is the asset type to use for Vehicles since it allows animations like opening the door or any animation which does not use parts bending like skinned geometries for characters. The .cga file is created in the 3D application. The parts will be linked to each other in a hierarchy and will have a main root base. It only supports directly linked objects and does not support skeleton based animation (bone animation) with weighted vertices. Crytek Geometry Animation (.cga) works together with .anm files.

**
.ma
**

The native ASCII file format used by Autodesk Maya.

**
.atom (Maya Anim file)
**

Autodesk Maya's
**
.atom
**
 file format lets you save animations from one object and import it onto another object.

**
.dae (Collada)
**

This is the intermediate file format exported from Autodesk Maya

**
.zip (contains dae)
**

The Maya exporter stores the .dae file inside a .zip file.

**
.fbx (intermediate file format)
**

In the future, .fbx will replace all other intermediate file formats (.dae, .zip, .ma, .anm,...)

**
.abc (Alembic Point Cache)
**

Alembic is a file format which stores the vertex information of a constant set of vertices for complex simulations or the illusion of skinned mesh geometry animating.

**
.cbc (Compression settings for Alembic Point cache)
**

This is a settings file which stores the parameters used to convert the Alembic (
**
.abc
**
) file.

**
.cax (CRYENGINE Geom Cache)
**

This file is the processed Alembic file which the Resource Compiler compresses into an Engine friendly format.

##
Textures and Materials

[Image: /docs/static/attachments/44959594]

**
.tif (Tagged Image File Format)
**

The .tif file should be created from within Photoshop with the CryTif plugin. It contains the pictures in TIF Format plus additional Metadata (i.e. compression), which is used by the Resource Compiler (RC). The RC transforms the .tif format into the target file format of the platform.

**
.dds (DirectDraw Surface)
**

The .dds files are texture files created by the resource compiler from Tif Source files, specifically optimized for the target platform. This is the optimal format for PC Graphic cards. It can contain compressed and uncompressed data.

**
.mtl (Material)
**

The .mtl file is created within the Material Editor in Sandbox and material description (internally an xml file). It contains settings for shaders, surface types, and references to textures. The.mtl file is a text file which holds all the information for the in-game material library. The material library is a collection of sub materials which can be assigned to each face of a geometry. You can have for example different surfaces like metal, plastic and humanskin within different IDs of the asset. Each of these sub materials can use different shaders and different textures.

The Sandbox material data is stored in an XML file with the extension,
*
.mtl
*
.

CRYENGINE will look for an .mtl file with the same name as the material name assigned to an object within your DCC Tool.

If this file is not existing, it will automatically scan the object's folder for a .mtl file with the same name as the object.

##
Animations

**
.cdf (Character Definition File)
**

The character definition file is created in the Character Editor in Sandbox. It contains the reference to a .chr file and its attachments (can be .chr or .cgf).

**
.skin (Skinned Render mesh)
**

The .skin file is created in the 3D application and contains skinned character data. It can be any asset that is animated with bone-weighted vertices like humans, aliens, ropes, lamps, heads, and parachutes. The .skin file includes the mesh, vertex weighting, vertex colors, and morph targets.

**
.anm (Animation)
**

The .anm file is created in the 3D application and contains animation data for .cga objects. Each CGA file with more then one animation uses .anm files to move the individual parts of the CGA object. If there is only one animation for the object, it will be stored within the CGA file as the default animation in the Character Editor. .anm files are used to group different rigid body animations. For example, you can group landing gear coming down, separately from the hatch, to the cockpit opening.

**
.chrparams (Character Parameters File)
**

For a (skeletal) character in the game, there are certain definitions that have to be made in a single unified XML file-structure called a .chrparams file. The .chrparams file has the same name as the character file to which it refers. Please see The
[/docs/static/engines/cryengine-5/categories/23756816/pages/25535608](
Animation Events
)
 document for more information.

**
.i_caf (Intermediate Character Animation File)
**

The intermediate character animation file contains the animated bone data for a specific character. The .i_caf files can be exchanged between characters with similar bone structures. The intermediate character animation file stores animation in an uncompressed format and is used in production. Such files are created with DCC plugins, see
[/docs/static/engines/cryengine-3/categories/1114113/pages/1310796](
Exporting Animations
)
 for details.

**
.animsettings (Animation Settings)
**

The animation settings file contains per-animation compression settings. This is a sidecar file that is stored next to an .i_caf file and describes how it should be compiled by the Resource Compiler. Animation Settings are created by the Animation Import tool in Sandbox, see
[/docs/static/engines/cryengine-3/categories/1114113/pages/1310796](
Exporting Animations
)
.

**
.caf (Character Animation File)
**

Compressed representation of the i_caf format. This format uses lossy compression and such files are created either by Sandbox or during the asset build build. Such files are loaded by the engine at run-time.

**
.bspace (Blend-Space)
**

Blend space defines how multiple animation assets are blended together. Blend spaces are parametrized at run-time with locomotion parameters such as movement speed, movement direction, turning angle or slope. See
[/docs/static/engines/cryengine-5/categories/23756816/pages/28186170](
Blend Spaces - Character Tool
)
.

**
.comb (Blend-Space combination)
**

This allows to combine multiple simpler blend-spaces into one, usually of a higher order.

**
.animevents (Animation Events Database)
**

This file stores a list of assets with timed event markups. It is used, for example, for footstep sounds. The event database can be created and modified in the Character Editor and gets mapped in the .chrparams file.

**
SkeletonList.xml (Skeleton Alias Table)
**

A table that maps skeleton aliases, that are used within .animsettings, to skeleton filenames. Skeleton structure information is needed during animation compression.

From engine version 5.6 onwards, the skeleton list is not used anymore.

**
DBATable.xml (DBA Table)
**

Contains a list of .dba files (Animation Databases). For each Animation Database there is a list of .caf files that gets included.

Compression Presets

**
.dba (Animation Database)
**

Such files are created by the Resource Compiler according to DbaTable.xml. They store multiple animation files and eliminate redundancy, providing additional lossless compression. Single .caf files are no longer needed unless they are on-demand assets. The database file must be set in the .chrparams file.

**
.phys (Cloth Editor File)
**

**
.adb (Mannequin Database)
**

Contains a Mannequin animation database. The .adb file is a container specifying the implementation of each fragment, i.e., which animations play on which fragment.

##
Facial Editor

[Image: /docs/static/attachments/44959593]

Please see
[/docs/static/engines/cryengine-3/categories/1114113/pages/1310899](
Facial Animation Asset Files
)
 for more information.

**
.fxl (Facial Editor Expression Library)
**

The facial expression library files contain information about how expressions and phonemes for a character are created with the character specific morph targets.

**
.fsq (Facial Editor Sequence)
**

The facial sequence files contain the key-frame animation data for a specific facial animation sequence.

**
.fpj (Facial Editor Project)
**

The facial editor project file sets up the Facial Editor for a specific character and contains information about .fxl and .cdf files. Use it to quickly set up the facial animation editor.

**
.joy (Facial Editor Joystick)
**

The joystick files contain the joystick control setup information for the Facial Editor.

**
.grp (Group File)
**

GRP files are exported sequence objects that appear in the level when a new Trackview sequence is created. Saving these objects as .grp files exports an XML format of everything contained in the sequence, from audio positions to skeletal animation and camera paths. This can then be imported into a facial sequence for use in the Facial Editor.

##
Audio Assets

**
.wav (Wave)
**

Wave files contain source sound data. Normally the build process filters .wav files out because they should not be used at run-time.

**
.fdp (FMOD Project)
**

The .fdp file is an XML-based project file for the FMOD Designer tool. This is shipped optionally, but needed for the SoundBrowser in Sandbox.

**
.fev (FMOD Runtime Project)
**

The .fev file is a binary file that is required for run-time loading of FMOD event data. It contains all of the necessary meta data for the sound events.

**
.fsb (FMOD SoundBank)
**

SoundBank files contain sound data in a specific format. For the Xbox360 they are typically encoded with the XMA format. On the PS3 the .mpeg format is used. FSB files are used for sound events, but also for music on consoles and in the future will be used for voice files as well.

**
.ogg (OGG-VORBIS)
**

OGG files contain sound data encoded in OGG-Vorbis. Currently they are only used on the PC for music and will eventually be replaced by specific FSB files.

**
.mp2 (MPEG encoded)
**

Voice files are currently encoded with the free lame-mp2 encoder on all platforms. Eventually they will be replaced by specific FSB files.

**
.cache/.seq/.fdt./.lst/.log/.h (misc FMOD files)
**

The FMOD build process creates several other files. All of these files are not crucial for Sandbox or the game and can be ignored and filtered. They are still useful, however, for the audio build process.

##
Flash Assets

[Image: /docs/static/attachments/44959592]

Please see
[/docs/static/engines/cryengine-3/categories/1638401/pages/1605718](
Flash UI System
)
 for more information.

**
.fla (Flash Movie Authoring File)
**

These are editable movies or animations created with Adobe Flash; they are often saved as a .SWF file for use on the Web. The FLA file is the editable project file saved by the Flash development program. The SWF file is a compressed format that is viewable in most Web browsers with the Flash plugin. Flash was originally developed by Macromedia, which merged with Adobe in 2005.

**
.swf (Flash Format File)
**

Animation created by Adobe Flash (formerly Macromedia Flash). The .swf file can include text as well as both vector and raster graphics. Plays in Web browsers that have the Flash plug-in installed. Most Web browsers come with a recent version of the Flash plug-in.

**
.gfx (Compressed Scaleform-converted Flash File)
**

Scaleform GFx is a lightweight, fast, image and vector graphics animation rendering engine, which is designed to take full advantage of modern 3D graphics hardware, yet be compatible with a wide range of systems. To complement the core rendering engine, Scaleform GFx contains a clean-room Flash player implementation, allowing game developers to create user interfaces with the award winning Adobe Flash Studio.

[#geometry-assets](
Geometry Assets
)
[#textures-and-materials](
Textures and Materials
)
[#animations](
Animations
)
[#facial-editor](
Facial Editor
)
[#audio-assets](
Audio Assets
)
[#flash-assets](
Flash Assets
)
