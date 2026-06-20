# Legacy Feature Tutorials

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/56656701
- Page ID: 56656701
- Breadcrumb: Tutorials > Game and Level Design > Legacy Feature Tutorials
- Parent: Game and Level Design

## Child Pages

- [Legacy AI entity tutorials](Legacy Feature Tutorials/Legacy AI entity tutorials.md)
- [Legacy UI tutorials](Legacy Feature Tutorials/Legacy UI tutorials.md)
- [Legacy physics entities tutorials](Legacy Feature Tutorials/Legacy physics entities tutorials.md)
- [Tutorial - How to create a teleporter using Flow Graph](Legacy Feature Tutorials/Tutorial - How to create a teleporter using Flow Graph.md)
- [Tutorial - How to bind inputs to actions using Flow Graph](Legacy Feature Tutorials/Tutorial - How to bind inputs to actions using Flow Graph.md)
- [Tutorial - How to use alembic GeomCache for vertex cached animations in Flow Graph](Legacy Feature Tutorials/Tutorial - How to use alembic GeomCache for vertex cached animations in Flow Graph.md)
- [Tutorial - How to control equipment packs for single player games](Legacy Feature Tutorials/Tutorial - How to control equipment packs for single player games.md)
- [Tutorial - How to control interactive objects using Flow Graph game tokens](Legacy Feature Tutorials/Tutorial - How to control interactive objects using Flow Graph game tokens.md)

## Content

These tutorials rely on the legacy assets in the free
[https://www.cryengine.com/marketplace/product/CRYENGINE%20GameSDK%20Sample%20Project](
GameSDK sample project
)
. This project is essentially a first person shooter extracted from Crysis 2. It includes complex entities that were geared for the needs of that game, such as RigidBodyEx, and a full AI system with characters, comprehensive animations, and scriptable behaviors (movement,  responses to the player, attacks, driving, hiding behind cover surface, etc.). GameSDK also includes many free assets, including buildings, props, vegetation, textures, materials, particle effects, special effects (snow, rain, tornadoes), etc.

GameSDK allows new users to quickly develop working games, particularly in the FPS genre, and control its entities using the
[/docs/static/engines/cryengine-5/categories/23756816/pages/27594282](
Flow Graph
)
 visual scripting language (instead of C++), but it relies on legacy code and entities that have been replaced with the modern
[/docs/static/engines/cryengine-5/categories/23756816/pages/28180907](
entity component system
)
. Entity components cannot be controlled through Flow Graph, and Flow Graph is no longer maintained, although it may still be useful for some level scripting. Entity components are essentially always custom entities composed of whatever components the designer cares to assemble, and are thus unrecognizable to Flow Graph. Their parameters must be controlled through C++ (or the visual scripting system introduced after CRYENGINE 5.6), whereas the legacy entities are fully exposed to and are best controlled by Flow Graph.

If you want to use many of the GameSDK character animations, you may want to base your characters on the GameSDK skeleton for easy compatibility. Keep in mind that the majority of those animations presume that the character is carrying a weapon.

-
[/docs/static/engines/cryengine-5/categories/23756816/pages/56658164](
Legacy AI entity tutorials
)

-
[/docs/static/engines/cryengine-5/categories/23756816/pages/56658168](
Legacy UI tutorials
)

-
[/docs/static/engines/cryengine-5/categories/23756816/pages/26877256](
Legacy physics entities tutorials
)

-
[/docs/static/engines/cryengine-5/categories/23756816/pages/56658120](
Tutorial - How to create a teleporter using Flow Graph
)

-
[/docs/static/engines/cryengine-5/categories/23756816/pages/56658128](
Tutorial - How to bind inputs to actions using Flow Graph
)

-
[/docs/static/engines/cryengine-5/categories/23756816/pages/56658139](
Tutorial - How to use alembic GeomCache for vertex cached animations in Flow Graph
)

-
[/docs/static/engines/cryengine-5/categories/23756816/pages/56658142](
Tutorial - How to control equipment packs for single player games
)

-
[/docs/static/engines/cryengine-5/categories/23756816/pages/56658156](
Tutorial - How to control interactive objects using Flow Graph game tokens
)
