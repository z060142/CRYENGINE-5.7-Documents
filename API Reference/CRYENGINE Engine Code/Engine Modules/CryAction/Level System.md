# Level System

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/24283716
- Page ID: 24283716
- Breadcrumb: CRYENGINE Engine Code > Engine Modules > CryAction > Level System
- Parent: CryAction

## Content

### Overview

The Level System takes care of all the available levels in your game. This come in handy when you want to define a certain level rotation as well as just feeding available level suggestions to the "map" console command.

### Initialization

The Level System is created during the initialization of CryAction. It will scan your current game directory for all available levels and store them depending on their type. Since the scan process actually accesses your game folder and tries to gather the level information, this can be quite expensive during game runtime and should only be done during initialization.

### Level Rotation

You can add levels and game modes to your level rotation, the Level System then will take care of loading the corresponding game rules.

Level Rotation offers 3 standard modes for level selection:

mode | purpose
--- | ---
None | the levels will get loaded in the same order they got added
Shuffle | levels and game modes will be shuffled
ShallowShuffle | only levels with same game mode will be shuffled
