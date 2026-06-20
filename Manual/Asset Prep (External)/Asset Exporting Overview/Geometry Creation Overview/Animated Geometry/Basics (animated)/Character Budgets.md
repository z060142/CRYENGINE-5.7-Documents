# Character Budgets

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/23307976
- Page ID: 23307976
- Breadcrumb: Asset Prep (External) > Asset Exporting Overview > Geometry Creation Overview > Animated Geometry > Basics (animated) > Character Budgets
- Parent: Basics (animated)

## Content

![Image](https://www.cryengine.com/docs/static/attachments/29934057)

## Overview

## Sections

In order to assist users with determining the optimal polygon counts and texture resolutions of characters when working on CRYENGINE projects, listed below are the typical budgets used by the video game HUNT: Showdown.

[Sections](#sections)[Triangle Counts](#triangle-counts)[Texture Resolutions](#texture-resolutions)[Drawcalls/Lods](#drawcallslods)

### Triangle Counts

##### Hunters (Main Characters)

The Hunters on HUNT: Showdown represent the primary characters of a level or project. The typical triangle count used by these are as follows:

- LOD0: 35,000 - 70,000 triangles.
- LOD3: 5,000 - 8,000 triangles.

Additionally the poly-counts of Hunters on HUNT: Showdown vary depending on their tier; a Hunter with from a higher tier will have significantly higher poly-counts, due to the amount of extra attachments and gear carried by them.

##### Grunts (Non-primary Characters)

Grunts are monsters on HUNT: Showdown, and are representative of the non-primary characters of a project. The typical triangle count used by them are as follows:

- - LOD0: 25,000 - 35,000 triangles.
- LOD3: 4,000 - 5,000 triangles.

**Bosses (Special Characters)**

- LOD0: 25,000 - 45,000 triangles.
- LOD3: 4,000 - 7,000 triangles.

### Texture Resolutions

##### Hunters (Main Characters)

Since Hunters on HUNT: Showdown are highly customizable, each of their body parts are assigned separate materials. The resolutions of these materials are as follows:

Body Part | Material Resolution
--- | ---
Face | 1024 x1024
Head | 256 x 256
Eyeballs | 2048 x 2048 (512 x 512, in some cases)
Eyelashes | 512 x 512
Hair | 512 x 512
Beard | 512 x 512
Brows | 512 x 512
Hands | 4096 x 2048
Legs | 1024 x 1024

The gear carried by Hunters are also assigned materials with the following resolutions:

Gear | Material Resolution
--- | ---
Gear harness | 2048 x 1024
Head gear | 512 x 512
Chest gear | 1024 x 1024
Backpack | 2048 x 2048
Bracelets | 1024 x 1024
Ropes | 512 x 512
Trinket | 256 x 256

##### Grunts and Armored Monsters (Non-primary characters)

Similar to Hunters, Grunts too have separate materials assigned to different body parts. This is not only because Grunts can be dismembered, but to also allow for easy variations in their designs.

For example, the material assigned to the head of one grunt might be used as the upper body material of another.

Body Part | Material Resolution
--- | ---
Head | 1024 x 1024
Hair | 1024 x 1024
Upper body | 1024 x 1024
Shirts | 1024 x 1024
Pants/Legs | 1024 x 1024

In contrast, Armored Monsters on HUNT: Showdown utilize a single material with 7 material IDs corresponding to the following parts:

Body Part/Gear | Material Resolution
--- | ---
Body | 1024 x 1024
Head | 1024 x 1024
Head Armor | 1024 x 1024
Armor | 2048 x 2048
Organs | 1024 x 1024
Legs | 1024 x 1024
Tentacles | 1024 x 1024

**Bosses (Special Characters)**

Spiders, boss monsters on HUNT: Showdown, also utilize a single material with 4 material IDs.

Body Part | Material Resolution
--- | ---
Body | 1024 x 1024
Head | 1024 x 1024
Organs | 1024 x 1024
Hair | 64 x 256

### Drawcalls/Lods

- To keep drawcalls to a minimum for the sake of performance efficiency, it's best to combine several smaller, individual textures into a single one.
- It would also be helpful to check out [Asset Performance Guidelines](/docs/static/engines/cryengine-3/categories/1114113/pages/1310836) as it features more information on what causes drawcalls.
