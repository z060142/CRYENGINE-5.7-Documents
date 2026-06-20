# Create Modify and Remove Feature Tests

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/23306423
- Page ID: 23306423
- Breadcrumb: CRYENGINE Game Code > Miscellaneous Game Code > Feature Tests > Create Modify and Remove Feature Tests
- Parent: Feature Tests

## Content

### Overview

Feature tests are stored in text files inside the `GameSDK/Scripts/FeatureTests` directory.

The names shouldn't contain spaces or other daft characters because the files get read into the game using console variables and commands, and a lot of characters have special meanings on the command line, in.cfg files, when typing into the in-game console and so on.

Stick to letters and numbers and you'll be fine. The files should have the extension.xml although you should leave that off when referring to the files when [loading and running the tests in the game](How%20to%20Run%20Feature%20Tests.md).

### Feature Test Instructions

#### Setup Instructions

**TrySpawnPlayer:** Tell the player to spawn in (if not spawned in already):

```
<TrySpawnPlayer localPlayer="true" />
<TrySpawnPlayer localPlayer="false" />
```

**SetItem:** Make the player select a particular item from his inventory:

```
<SetItem className="Mk60" />
<SetItem className="Revolver" />
<SetItem className="SCAR" />
```

**SetAmmo:** Changes the ammo count of the current selected item. "ammo" is the ammo count on the inventory and "clip" is the number of rounds on the clip:

```
<SetAmmo ammo="10" clip="4" />
```

**SetSuitMode:** Put the player into a particular suit mode:

```
<SetSuitMode modeName="Power" />
<SetSuitMode modeName="Armor" />
<SetSuitMode modeName="Stealth" />
<SetSuitMode modeName="Tactical" />
```

**MovePlayerToOtherEntity:** Move a player next to another entity in the level:

```
<MovePlayerToOtherEntity who="localPlayer" className="CrashSiteLocation" />
```

#### Input Instructions

**OverrideButtonInput_Press:** Send local player's input handler a button press message:

```
<OverrideButtonInput_Press inputName="jump" />
```

**OverrideButtonInput_Release:** Send local player's input handler a button release message:

```
<OverrideButtonInput_Release inputName="jump" />
```

**OverrideAnalogInput:** Send local player's input handler a change to an analogue input value:

```
<OverrideAnalogInput inputName="xi_rotatepitch" value="-1" />
```

**DoConsoleCommand:** Execute a console command:

```
<DoConsoleCommand command="kill" />
```

**DoMenuCommand:** Execute a menu command (actions normally activated by clicking buttons etc. in the front-end or in-game menu):

```
<DoMenuCommand command="SetLobbyService LAN" />
```

#### Code Coverage Checkpoint Instructions

**WatchCCCPoint:** Start counting the number of times a code coverage checkpoint is hit:

```
<WatchCCCPoint checkpointName="PlayerWeapon_IronSightOn" />
```

**ResetCCCPointHitCounters:** Reset how many times each code coverage checkpoint is hit to 0:

```
<ResetCCCPointHitCounters />
```

**CheckNumCCCPointHits:** Verify the number of times a code coverage checkpoint is hit is a specific number (fail feature test if not):

```
<CheckNumCCCPointHits checkpointName="PlayerWeapon_IronSightOn" expectedNumHits="1" />
```

**SetResponseToHittingCCCPoint:** Mark hitting a specific code coverage checkpoint as having a particular response (restartTest / restartSubroutine / failTest / passTest / expectedNext):

```
<SetResponseToHittingCCCPoint checkpointName="PlayerWeapon_IronSightOn" response="failTest" />
```

#### Wait Instructions

**Wait:** Wait for given period of time:

```
<Wait duration="10" />
```

**WaitSingleFrame:** Wait until a frame has gone by:

```
<WaitSingleFrame />
```

**WaitUntilPlayerIsAlive:** Wait until a player (or an entire set of players) is alive:

```
<WaitUntilPlayerIsAlive who="localPlayer" />
<WaitUntilPlayerIsAlive who="localPlayer|firstRemotePlayer" />
```

**WaitUntilHitAllExpectedCCCPoints:** Wait until all code coverage checkpoints marked as "expected" have been hit:

```
<WaitUntilHitAllExpectedCCCPoints timeOut="5" />
```

**WaitUntilPlayerAimingAt:** Wait until a player (or an entire set of players) has a particular target type:

```
<WaitUntilPlayerAimingAt who="localPlayer" targetType="nobody" />
<WaitUntilPlayerAimingAt who="localPlayer|firstRemotePlayer" targetType="enemy" />
<WaitUntilPlayerAimingAt who="firstRemotePlayer" targetType="anybody" />
<WaitUntilPlayerAimingAt who="secondRemotePlayer" targetType="enemy" />
```

#### Miscellaneous Instructions

**RunFeatureTest:** Pause execution or this feature test, run another, then continue with this one if that one succeeds:

```
<RunFeatureTest testName="nameOfSomeOtherTest" />
```

**RunFlowGraphFeatureTests:** Run all flowgraph feature tests which exist in the loaded level:

```
<RunFlowGraphFeatureTests reloadLevel="true" quickload="false" timeout="120" />
```

**Fail:** Fail the current feature test:

```
<Fail />
```

### Elements of a Feature Tester XML file

#### FeatureTester

The top level XML tag. Can include a <**Settings**> section and multiple <** Tests**> sections.

```
<FeatureTester>
...
</FeatureTester>
```

#### Settings

Reserved for future use. For now, leave it empty.

```
<Settings>
...
</Settings>
```

#### Tests

Defines a set of feature tests with the specified set name. Should include zero or more <**FeatureTest**> sections.

```
<Tests setName="something">
...
</Tests>
```

#### FeatureTest

Defines a feature test. Should include zero or more [instructions](Create%20Modify%20and%20Remove%20Feature%20Tests.md#CreateModifyandRemoveFeatureTests-Featuretestinstructions).

```
<FeatureTest name="name" (description="description") (require="requirements") (enabled="true/false") (maxTime="numSeconds") (iterateOverParams="listOfParams")>
...
</FeatureTest>
```

#### For example

```
<FeatureTester>
<Settings>
</Settings>

<Tests setName="fooTests">

<FeatureTest name="firstFooTest" description="Some test or other" enabled="true" maxTime="10">
<!-- Instructions here -->
</FeatureTest>

<FeatureTest name="secondFooTest" description="Another test" enabled="true" maxTime="60">
<!-- Instructions here -->
</FeatureTest>

</Tests>

<Tests setName="barTests">

<FeatureTest name="justCheckLocalPlayerExists" description="An exciting test" require="localPlayerExists" enabled="true">
</FeatureTest>

<FeatureTest name="checkLocalPlayerExistsAndDoStuff" description="Another exciting test" require="localPlayerExists" enabled="true">
<!-- Instructions here -->
</FeatureTest>

<FeatureTest name="aTestWhichRepeatsMultipleTimes" description="Another exciting test" enabled="true" iterateOverParams="SCAR;Revolver;Feline;Marshall;SCARAB">
<!-- Instructions here -->
</FeatureTest>

</Tests>
</FeatureTester>
```

[Feature Test Instructions](#feature-test-instructions)[Setup Instructions](#setup-instructions)[Input Instructions](#input-instructions)[Code Coverage Checkpoint Instructions](#code-coverage-checkpoint-instructions)[Wait Instructions](#wait-instructions)[Miscellaneous Instructions](#miscellaneous-instructions)[Elements of a Feature Tester XML file](#elements-of-a-feature-tester-xml-file)[FeatureTester](#featuretester)[Settings](#settings)[Tests](#tests)[FeatureTest](#featuretest)[For example](#for-example)
