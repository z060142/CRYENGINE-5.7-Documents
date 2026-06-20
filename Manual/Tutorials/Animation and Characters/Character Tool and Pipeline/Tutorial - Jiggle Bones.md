# Tutorial - Jiggle Bones

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/44959301
- Page ID: 44959301
- Breadcrumb: Tutorials > Animation and Characters > Character Tool and Pipeline > Tutorial - Jiggle Bones
- Parent: Character Tool and Pipeline

## Child Pages

- [Jiggle Bones - Skeleton Hierarchy Setup - 3dsMax](Tutorial%20-%20Jiggle%20Bones/Jiggle%20Bones%20-%20Skeleton%20Hierarchy%20Setup%20-%203dsMax.md)
- [Jiggle Bones - Skeleton Hierarchy Setup - Maya](Tutorial%20-%20Jiggle%20Bones/Jiggle%20Bones%20-%20Skeleton%20Hierarchy%20Setup%20-%20Maya.md)
- [Jiggle Bones - CRYENGINE](Tutorial%20-%20Jiggle%20Bones/Jiggle%20Bones%20-%20CRYENGINE.md)

## Content

## Overview

In this tutorial you will learn the workflow of

- **how to create a simplified base primary skeleton (the character CHR file)**
- **how to create a secondary skeleton and its bound geometry (the SKIN file) to extend the primary skeleton (CHR file)**
- **how to set up the physics parameters in CRYENGINE Character Tool Attachment System to get nice secondary procedural animations**

We'll take you through the process of creating a "jiggle bone" attachment to a basic skeleton. You should be familiar with how to use your favorite 3D program, like Maya or 3ds Max, to create a joint hierarchy and bind a mesh to the skeleton. Some experience with how to export characters to CRYENGINE would also help.

The expression "jiggle bones" often means in CGI a joint hierarchy which looks like an antenna that sticks out of an underlying (character) mesh. When the underlying mesh is animated, the motion of this primary object makes the jiggle bones shake and, thus, move the skinned/attached jiggle bone geometry. Ideally, this motion is called secondary motion and could be generated procedurally, in this case applied by CRYENGINE's Attachment System from the Character Tool.

Depending on the physics setup parameters in Character Tool you could apply this jiggle bone technique for pony tails, antennas, ropes, tails, strips of cloth hanging down a character, collars and other appendices.

To be clear, what this tutorial is NOT for:

If you want the jiggle bone/physics joint chain to interact with other environment objects and other characters you have to look at the other physics system in CRYENGINE.

This tutorial is meant to show you how to add secondary/procedural animation to your characters, reducing the workload for the animators and enhance the visual quality of a character.

### Tutorial Files

This tutorial may rely on the GameSDK Sample Project. We recommend that you download this from the **[Asset Database](https://www.cryengine.com/marketplace/product/crytek/cryengine-gamesdk-sample-project)**, import it into your Launcher, start it from there and then create a new level.

See **[this page](/docs/static/engines/cryengine-5/categories/23756816/pages/36870288)** to find out how to import a project to your Launcher. (The default folder for the GameSDK Sample Project when downloaded is `C:\Program Files (x86)\Crytek\CRYENGINE Launcher\Crytek\gamesdk_<XXX>\GameSDK`)

Source 3ds Max / Maya scenes with exported CRYENGINE files:

**[GameSDK.zip](/docs/static/attachments/44959302)**(this zip file should be extracted under`GameSDK\Assets`.)

**[skeletonlist.zip](/docs/static/attachments/44959304)**(This should be extracted to **`GameSDK\Assets\animations.pak\Animations\`**. Note that you'll have to extract the animations.pak file first.

Since the skeleton list is not used in Engine release 5.6 onwards, the Tutorial SkeletonList.xml file doesn't need to be downloaded. Any other references to this file within this tutorial can also be ignored.

**Please backup your "SkeletonList.xml" before overwriting!**

If you want to open the provided tutorial CDF in Character Tool immediately, you'll have to add the pony tail CHR file to your custom "SkeletonList.xml" first.

For the rest of the tutorial, please continue on the following pages:

**[Jiggle Bones - Skeleton Hierarchy Setup - 3dsMax](Tutorial%20-%20Jiggle%20Bones/Jiggle%20Bones%20-%20Skeleton%20Hierarchy%20Setup%20-%203dsMax.md)**

or

**[Jiggle Bones - Skeleton Hierarchy Setup - Maya](Tutorial%20-%20Jiggle%20Bones/Jiggle%20Bones%20-%20Skeleton%20Hierarchy%20Setup%20-%20Maya.md)**

[Tutorial Files](#tutorial-files)
