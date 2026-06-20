# Compressing Animations

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/25534879
- Page ID: 25534879
- Breadcrumb: Animation > Character Assembly > Compressing Animations
- Parent: Character Assembly

## Content

![Image](https://www.cryengine.com/docs/static/attachments/29933224)

##
Overview

We want to have assets that take the lowest amount of memory, but that animate at the highest possible quality.

Uncompressed, an animation contains a key
**
for every frame
**
 in the animation and
**
for each joint
**
 that has been exported. We usually want to reduce the amount of joints and keys to minimize the size. We have separate channels for rotation keys and position keys per joint.

To compress animations for characters we use the
**
[Resource Compiler](../../System%20Utilities/System%20Utilities%20Overview/Resource%20Compiler.md)
**
 tool (RC).

![Image](https://www.cryengine.com/docs/static/attachments/26952870)

##
Sections

[Sections](#sections)
[Compression of Existing Animations](#compression-of-existing-animations)
[Setting the Compression Settings](#setting-the-compression-settings)
[Per-Joint Setup](#per-joint-setup)
[Define Animation Tags](#define-animation-tags)
[Batch-compression](#batch-compression)

##
Compression of Existing Animations

To adjust compression settings of the animation, load your character by double-clicking on it in the Asset Explorer.

Choose your animation in the Animations tree in the Asset Explorer. Note that both *.i_caf and *.animsettings should present and writable. (
**
Not inside a *.pak file
**
)

Note for Perforce users: *.i_caf and *.animsettings files should be synced and checked out locally. If they are not, use a perforce client to do so first.

##
Compression settings

![Image](https://www.cryengine.com/docs/static/attachments/51347671)

-
You can adjust compression settings and instantly see the resulting animation and its size...

-
In the display options, set
**
Compression
**
 to
**
Side by Side
**
 to compare the original animation with the compressed version.

##
Compression Side by Side

*
![Image](https://www.cryengine.com/docs/static/attachments/51347672)
*
You can remove specific
**
per-joint
**
 compression settings via the context menu

##
Per Joint Compression Settings

![Image](https://www.cryengine.com/docs/static/attachments/51347673)

Click the
**
Save
**
 button in the properties panel toolbar, or
**
Save All
**
 in the
**
File
**
 menu when you're done

##
Setting the Compression Settings

##
Removing channels (position/rotation keys) automatically

-
You can get huge savings by automatically removing joints that don't contribute to the animation.

-
Roughly, for the RC to know if a joint contributes to an animation, it finds out how much it moves during the animation and compares it to the provided values. If it finds that it moves less than what the specifies, it will remove the keys for the joint. Higher values will remove more joints.

-
The values to tweak for this are
**
Position
**
 for the position channel and
**
Rotation
**
for rotation channel. This means rotation and position keys are considered separately.

-
**
Position
**
and
**
Rotation
**
are global values for the whole animation.

-
Additive animations have smaller movement so you'll need to use smaller values.

-
This is an all or nothing process: Either the keys are all kept for a channel(position/orientation), or deleted.

##
Reducing the amount of keys within a channel

-
The previous step has removed joints completely. We now want to reduce the number of keys each channel has, since at this point we have one key per frame.

-
For this the RC uses the
**
Compression
**
 value. Higher values will remove more keys within a channel.

-
The
**
Compression
**
 value is a global value so it will affect all joints the same by default (although we can still tweak it later on a per joint detail level).
The goal should be at this point to have an animation that takes as little as possible but looks good. Sometimes though, playing around with global values for a whole animation is not enough, and we will need to fix up individual joints that show choppy motion.

##
Per-Joint Setup

##
Per joint control over the removal process

-
For each joint, by default, the values are used to decide if they are removed or not.

-
We can force a joint to be removed by clicking the checkbox next to it. Position and Rotation channels will both be removed for the selected joints.

##
Per joint control over the compression value

-
For each joint we can specify a multiplier that is applied to the
**
Compression
**
 value. By default this value is 1, so a joint uses the global Compression value.

##
Define Animation Tags

Each animation can have a list of tags associated with it. Tags can be used to:

-
Select animations that have to go into a specific DBA by means of an
**
Animation Filter
**
 (see below)

-
Apply compression to a group of animation files by means of
**
Compression Presets
**
 (see below)
You can find
**
Tags
**
 in the
**
Properties
**
 window when you select animation in the
**
Asset Explorer
**
.

To add a new tag use the context button with tag count and select
**
Add
**
 in the popup menu:

Pic4: Adding a tag

![Image](https://www.cryengine.com/docs/static/attachments/51347674)

Then click on an empty string to enter its name.

To remove a tag you can use the context menu (
**
RMB
**
 on the tag name):

*
Pic5: Removing a tag
*

![Image](https://www.cryengine.com/docs/static/attachments/51347675)

For curious readers: tags are case insensitive. I.e. the tag "CINEMATIC" will be treated the same way as "cinematic".

##
Batch-compression

Compression Presets can be used to apply the same set of compression rules to multiple animations at once. You can locate them in the Compression section of the Asset Explorer.

Each compression preset entry defines a filter that can match animations according to a certain filter, i.e. a set of criteria such as folder, filename or tags. Such criteria can be combined using logical operations into a complex condition, like "in folder and doesn't contain specific tag but has sub-string in name". When multiple presets match the same animation only the first one is used. You can always preview which compression setting entry was applied to an animation in the animation properties (by selecting a specific animation in the asset explorer).

Compression presets are saved in:
`
<GameFolder>\Assets\Animations.pak\CompressionPresets.json.
`
