# Streaming Animations

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/29450891
- Page ID: 29450891
- Breadcrumb: Animation > Character Assembly > Streaming Animations
- Parent: Character Assembly

## Content

![Image](https://www.cryengine.com/docs/static/attachments/29933227)

## Overview

## Sections

DBA files are bundles of animations which can be streamed in and out as one. They are typically smaller and take up less memory than individual animations.

If an animation is in a DBA file, it will *not* be available anymore as an individual CAF file. If the game tries to play one of these animations, the DBA containing that animation will be loaded. As this can take a while, programmers typically make sure the DBA is preloaded.

Typically you put all of your game animations (player, AI, weapons,...) inside one or more DBAs.

What should *not* be in DBAs:

- Aimposes, BSPACE and COMB files, as they cannot be stored in DBAs.
- Animations that only need to be accessed once, on demand, like trackview (cinematic) animations. (in case of trackview, these animations are preloaded a couple of seconds before they start, and the trackview flownodes allow for preloading of sequences)
- Animations that need to be individually loaded and unloaded. A real world example was the hit death reaction system in Crysis 2. Because of memory constraints we kept only a very limited amount of these in memory and we used a 'round robin' technique to keep replacing the variations.

For more technical information on what is stored in DBA files, how to use them from code, and how to keep them in memory, see [Animation Streaming](/docs/static/engines/cryengine-3/categories/1638401/pages/15012010).

When two animations in the same DBA have exactly the same animation for a joint, the data for that animation will only be stored once. This can give huge memory savings if used well.

[Sections](#sections)[DBATable.json](#dbatablejson)[CHRPARAMS Changes](#chrparams-changes)

### DBATable.json

DBA files are created by the Resource Compiler after compressing the individual animations (CAFs). See [Resource Compiler](../../System%20Utilities/System%20Utilities%20Overview/Resource%20Compiler.md) for more details on the process that creates DBA files.

The resource compiler uses the rules in `Animations\DBATable.json` to find out which animations to put in which DBAs. You can edit the rules in the Character Tool, see [Animation Compression - Character Tool](../../Editor%20Tools/Animation%20Tab/Character%20Tool/Animation%20Compression%20-%20Character%20Tool.md).

In CRYENGINE 3.5 and 3.6 the resource compiler used `Animations\DBATable.xml` for this purpose. This still works in CRYENGINE 3.7, but is deprecated and so will be removed in a later release.

CRYENGINE 3.5 and 3.6: DBATable.xml
Before CRYENGINE 3.5: The CBA File

#### CHRPARAMS Changes

All DBA files that you create for a model (CHR) *must* be listed in its CHRPARAMS file.

For example:

```
<?xml version="1.0" ?>
<Params>
<AnimationList>
...
<Animation name="$TracksDatabase" path="animations\dba\level1.dba"/>
...
<Animation name="#filepath" path="animations\zombie"/>
<Animation name="*" path="*\*.caf"/>
...
</AnimationList>
</Params>
```

In this case the game will look for all caf files in the `animations\zombie` folder on disk as well as in ` animations\dba\level1.dba`.

If you fail to include the line that adds the DBA, the animations that are inside the DBA will not be found.

If the animations inside the DBA are not in the `animations\zombie` folder, they will not be found either. It's as if the DBA just 'extends' the file system.

You can use wildcards to add dba files.

If you want to include all DBAs inside the `animations\dba` folder:

```
<Animation name="$TracksDatabase" path="animations\dba\*.dba"/>
```

If you want to include DBAs inside the `animations\dba` folder and subfolders:

```
<Animation name="$TracksDatabase" path="animations\dba\*\*.dba"/>
```

If you want a DBA to be loaded automatically when a character gets loaded, and if you want the DBA to be kept in memory forever, you can use the persistent flag:

```
<Animation name="$TracksDatabase" path="animations\dba\level1.dba" flags="persistent"/>
```

See [Character Parameters File (chrparams)](../../Asset%20Prep%20(External)/Asset%20Exporting%20Overview/Geometry%20Creation%20Overview/Animated%20Geometry/Character%20(animated)/Engine%20Setup%20(animated)/Character%20Parameters%20File%20(chrparams).md) for more details.
