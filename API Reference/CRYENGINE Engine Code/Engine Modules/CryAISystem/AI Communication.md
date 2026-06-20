# AI Communication

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/23306491
- Page ID: 23306491
- Breadcrumb: CRYENGINE Engine Code > Engine Modules > CryAISystem > AI Communication
- Parent: CryAISystem

## Content

### Overview

AI Communication is about playing sound/voice and/or animations at the right times in the course of the game.

Note that Communication animations are not played if the AI is currently playing a smart object action.

### Example

To actually trigger a Communication (event), use goalop "".

For example:

```
<GoalPipe name="Cover2_Communicate">
<Communicate name="comm_welcome" channel="Search" expirity="0.5"/>
</GoalPipe>
```

- **name** is the name of the actual Communication (sound/voice and/or animation). Possible Communications are defined by the XML file that the property * CommConfig* of this AI refers to.
- **channel** is the name of the Communication Channel this AI is using. The Channel should be defined in some XML file which resides in `Game/Scripts/AI/Communication`.
- **expirity** (expiry) is the maximum allowable delay in triggering this Communication (when the Communication Channel is temporarily occupied). If the Communication couldn't be triggered within this time period, it is discarded.

### Communication Channels

Communication Channel determines whether an AI can play a Communication at the moment, depending on whether the Communication Channel is **occupied** or not.

A **hierarchy** of Communication Channels determine, which other Communication Channels (namely, ** parent** Communication Channels) are occupied as well, when a ** child** Communication Channel is occupied.

Let me emphasize that Communication Channel is a totally self-contained concept, independent of any other AI Communication concepts. Its sole purpose is to be in one of the two states: *occupied* or * free*.

#### Example

```
<Communications>
<ChannelConfig>
<Channel name="Global" minSilence="1.5" flushSilence="0.5" type="global">
<Channel name="Group" minSilence="1.5" flushSilence="0.5" type="group">
<Channel name="Search" minSilence="6.5" type="group"/>
<Channel name="Reaction" priority="2" minSilence="2" flushSilence="0.5" type="group"/>
<Channel name="Threat" priority="4" minSilence="0.5" flushSilence="0.5" type="group"/>
</Channel>
<Channel name="Personal" priority="1" minSilence="2" actorMinSilence="3" type="personal"/>
</Channel>
</ChannelConfig>
</Communications>
```

- **name**
- **priority**
- **minSilence**: Minimum time (in seconds) for which the Channel remains occupied after the Communication has completed.
- **flushSilence**: Time (in seconds) for which a Channel remains occupied after flushing the Channel. It is used to override the imposed silence time for the Channel which is no longer playing a Communication. If this attribute is not specified, the value of ** minSilence** is used.
- **actorMinSilence**: Minimum imposed time (in seconds) to restrict AI actors from playing voice libraries after starting a Communication.
- **ignoreActorSilence**: Ignore (AI) actor Communication restrictions from the script.
- **type**: * personal*, * group*, or * global*.

### Communication Configurations

Communication Configuration determines which Communications (and how) an AI can play. A concrete Communication Configuration is assigned to an AI using the its property *CommConfig*.

#### Example

```
<Communications>

<!--Animation + Sound Event example (needs state using the action/signal in the animation graph)-->
<Config name="Surprise">
<Communication name="comm_anim" finishMethod="animation" blocking="all" forceAnimation="1">
<Variation animationName="Surprise" soundName="sounds/interface:player:heartbeat" />
</Communication>
</Config>

<!--Sound Event example-->
<Config name="Welcome">
<Communication name="comm_welcome" finishMethod="sound" blocking="none">
<Variation soundName="sounds/dialog:dialog:welcome" />
</Communication>
</Config>

</Communications>
```

##### Config attributes

- **name**: Communication Configuration name, which can be assigned to an AI using its property * CommConfig*.

Every Communication Configuration should contain at least one Communication, using either tag <Communication>.

##### Communication attributes

- **name**
- **choiceMethod**: Method used to choose a variation: ** Random**, ** Sequence**, ** RandomSequence**, or ** Match** (just the first variation).
- **responseName**
- **responseChoiceMethod**: Similar to * choiceMethod*
- **forceAnimation**

Every Communication should contain at least one Variation.

##### Variation attributes

- **animationName**: Animation graph input value.
- **soundName**
- **voiceName**
- **lookAtTarget**: 1/0, true/false, or yes/no. Makes the AI look at the target.
- **finishMethod**: Any or all of: * animation*, * sound*, * voice*, * timeout*, * all*. It defines the way to determine when the communication is finished - after the animation is finished, or time interval has elapsed etc.
- **blocking**: Any or all of: * movement*, * fire*, * all*, * none*. It allows to disable the movement and/or firing of the AI.
- **animationType**: * signal* or * action*
- **timeout**

### Voice Libraries

To support localized dialogs, sub-titles, and lip sync, Voice Libraries are necessary. The right Voice Libraries can be assigned to the right AIs (or Entity Archetypes) using property *esVoice*.

Voice Library is an XML Excel file which resides in `GameSDK/Libs/Communication/Voice`. Its format is as in the example (` GameSDK/Libs/Communication/Voice/npc_01_example.xml`).

Language | **American English** |
--- | --- | ---
File Path | ***languages/dialog/ai_npc_01/*** |
Signal | Sound File | SDK NPC 01 Example
**see** |  |
| see_player_00 | i see you
| see_player_01 | hey there you are
| see_player_02 | hey i have been looking for you
**pain** |  |
| pain_01 | ouch
| pain_02 | ouch
| pain_03 | ouch
| pain_04 | ouch
| pain_05 | ouch
**death** |  |
| death_01 | arrrhh
| death_02 | arrrhh
| death_03 | arrrhh
| death_04 | arrrhh
| death_05 | arrrhh
**alerted** |  |
| alerted_00 | watch_out
| alerted_01 | be careful
| alerted_02 | something there

**American English** defines the localization this Voice Library belongs to.

`Localization/<language>/dialog/ai_npc_01/` is the path where the files (2nd column) actually are.

For each Communication (1st column) - "see", "pain", "death", and "alerted" - a few variations are provided.

The 3rd column is just for comments.

### Flow Graph Node

To trigger Communications using Flow Graph logic the Flow Graph node "**AI:Communication**" can be used.

### Startup

At startup, folder `Game/Scripts/AI/Communication` and all subfolders are scanned for XML files which contain Channel Configurations and Communication Configurations.

The SDK includes two basic Configuration XML files:

- *BasicCommunications.xml*
- *ChannelConfig.xml*

### Turning off animation and/or voice

Communication animation and/or voice can be turned off using the AI's Lua script or the entity properties in Sandbox:

```
Readability =
{
bIgnoreAnimations = 0,
bIgnoreVoice = 0,
},
```

### Debugging

To get debug information about AI Communication, the following CVars are available (provided ai_DebugDraw is 1):

- **ai_DebugDrawCommunication**
- **ai_DebugDrawCommunicationHistoryDepth**
- **ai_RecordCommunicationStats**

Debug output to console:

Playing communication: comm_welcome[3007966447] as playID[84] CommunicationPlayer::PlayState: All finished! commID[-1287000849] CommunicationManager::OnCommunicationFinished: comm_welcome[3007966447] as playID[84] CommunicationPlayer removed finished: comm_welcome[3007966447] as playID[84] with listener[20788600]

### Implementation

The code of the Communication Manager resides in **CryAISystem** and ** CryAction**:

**CryAISystem** (`Code/CryEngine/CryAISystem/Communication/`):

- ***Communication.h***: Definitions for Channel, Communication, and Variation
- ***CommunicationChannel.h/.cpp***
- ***CommunicationChannelManager.h/.cpp***
- ***CommunicationManager.h/.cpp***: Loading Configurations, rendering debug information
- ***CommunicationPlayer.h/.cpp***: Triggering Communications
- ***CommunicationTestManager.h/.cpp***: A simple test system for the Communication Manager

**CryAction** (`Code/CryEngine/CryAction/AI/`):

- ***CommunicationHandler.h/.cpp***: Playing sound events, setting Animation Graph inputs
- ***CommunicationVoiceLibrary.h/.cpp***
- ***CommunicationVoiceTestManager.h/.cpp***: A simple test system for Voice Libraries

### Troubleshooting

[Warning] Communicate(77) [Friendly.Norm_Rifle1] Communication failed to start

You may find a message similar to the above if your AI's behavior tree calls a communication but the communication config is not set properly.

In this instance, "77" refers to the line in the `GameSDK/Scripts/AI/BehaviorTrees/SDK_Advanced_Grunt.xml` behavior tree script:

```
<Communicate name="TargetSpottedWhileSearching" channel="Reaction" expirity="1.0" waitUntilFinished="0" />
```

This TargetSpottedWhileSearching attribute is defined in the `GameSDK/Scripts/AI/Communication/HumanCommunication.xml` script:

```
<Communication name="TargetSpottedWhileSearching" finishMethod="voice" blocking="none">
<Variation voiceName="TargetSpottedWhileSearching"/>
</Communication>
```

So, if your AI character uses this Modular Behavior Tree but does not have the "Human" communication config set, the above error would occur.

![Image](https://www.cryengine.com/docs/static/attachments/23461258)

You should also select a "Voice" to use for the communication. In this case, AI_02. This content is discussed earlier in this article here: [VoiceLibraries](AI%20Communication.md#AICommunication-VoiceLibraries)

[Example](#example)[Communication Channels](#communication-channels)[Communication Configurations](#communication-configurations)[Voice Libraries](#voice-libraries)[Flow Graph Node](#flow-graph-node)[Startup](#startup)[Turning off animation and/or voice](#turning-off-animation-andor-voice)[Debugging](#debugging)[Implementation](#implementation)[Troubleshooting](#troubleshooting)
