# Legacy Feature Tutorials

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/56656701
- Page ID: 56656701
- Breadcrumb: Tutorials > Game and Level Design > Legacy Feature Tutorials
- Parent: Game and Level Design

## Child Pages

- [Legacy AI entity tutorials](Legacy%20Feature%20Tutorials/Legacy%20AI%20entity%20tutorials.md)
- [Legacy UI tutorials](Legacy%20Feature%20Tutorials/Legacy%20UI%20tutorials.md)
- [Legacy physics entities tutorials](Legacy%20Feature%20Tutorials/Legacy%20physics%20entities%20tutorials.md)
- [Tutorial - How to create a teleporter using Flow Graph](Legacy%20Feature%20Tutorials/Tutorial%20-%20How%20to%20create%20a%20teleporter%20using%20Flow%20Graph.md)
- [Tutorial - How to bind inputs to actions using Flow Graph](Legacy%20Feature%20Tutorials/Tutorial%20-%20How%20to%20bind%20inputs%20to%20actions%20using%20Flow%20Graph.md)
- [Tutorial - How to use alembic GeomCache for vertex cached animations in Flow Graph](Legacy%20Feature%20Tutorials/Tutorial%20-%20How%20to%20use%20alembic%20GeomCache%20for%20vertex%20cached%20animations%20in%20Flow%20Graph.md)
- [Tutorial - How to control equipment packs for single player games](Legacy%20Feature%20Tutorials/Tutorial%20-%20How%20to%20control%20equipment%20packs%20for%20single%20player%20games.md)
- [Tutorial - How to control interactive objects using Flow Graph game tokens](Legacy%20Feature%20Tutorials/Tutorial%20-%20How%20to%20control%20interactive%20objects%20using%20Flow%20Graph%20game%20tokens.md)

## Content

These tutorials rely on the legacy assets in the free
[GameSDK sample project](https://www.cryengine.com/marketplace/product/CRYENGINE%20GameSDK%20Sample%20Project)
. This project is essentially a first person shooter extracted from Crysis 2. It includes complex entities that were geared for the needs of that game, such as RigidBodyEx, and a full AI system with characters, comprehensive animations, and scriptable behaviors (movement,  responses to the player, attacks, driving, hiding behind cover surface, etc.). GameSDK also includes many free assets, including buildings, props, vegetation, textures, materials, particle effects, special effects (snow, rain, tornadoes), etc.

GameSDK allows new users to quickly develop working games, particularly in the FPS genre, and control its entities using the
[Flow Graph](../../Editor%20Tools/Flow%20Graph.md)
 visual scripting language (instead of C++), but it relies on legacy code and entities that have been replaced with the modern
[entity component system](../../Entities%20and%20Tools/Entity%20Components.md)
. Entity components cannot be controlled through Flow Graph, and Flow Graph is no longer maintained, although it may still be useful for some level scripting. Entity components are essentially always custom entities composed of whatever components the designer cares to assemble, and are thus unrecognizable to Flow Graph. Their parameters must be controlled through C++ (or the visual scripting system introduced after CRYENGINE 5.6), whereas the legacy entities are fully exposed to and are best controlled by Flow Graph.

If you want to use many of the GameSDK character animations, you may want to base your characters on the GameSDK skeleton for easy compatibility. Keep in mind that the majority of those animations presume that the character is carrying a weapon.

-
[Legacy AI entity tutorials](Legacy%20Feature%20Tutorials/Legacy%20AI%20entity%20tutorials.md)

-
[Legacy UI tutorials](Legacy%20Feature%20Tutorials/Legacy%20UI%20tutorials.md)

-
[Legacy physics entities tutorials](Legacy%20Feature%20Tutorials/Legacy%20physics%20entities%20tutorials.md)

-
[Tutorial - How to create a teleporter using Flow Graph](Legacy%20Feature%20Tutorials/Tutorial%20-%20How%20to%20create%20a%20teleporter%20using%20Flow%20Graph.md)

-
[Tutorial - How to bind inputs to actions using Flow Graph](Legacy%20Feature%20Tutorials/Tutorial%20-%20How%20to%20bind%20inputs%20to%20actions%20using%20Flow%20Graph.md)

-
[Tutorial - How to use alembic GeomCache for vertex cached animations in Flow Graph](Legacy%20Feature%20Tutorials/Tutorial%20-%20How%20to%20use%20alembic%20GeomCache%20for%20vertex%20cached%20animations%20in%20Flow%20Graph.md)

-
[Tutorial - How to control equipment packs for single player games](Legacy%20Feature%20Tutorials/Tutorial%20-%20How%20to%20control%20equipment%20packs%20for%20single%20player%20games.md)

-
[Tutorial - How to control interactive objects using Flow Graph game tokens](Legacy%20Feature%20Tutorials/Tutorial%20-%20How%20to%20control%20interactive%20objects%20using%20Flow%20Graph%20game%20tokens.md)
