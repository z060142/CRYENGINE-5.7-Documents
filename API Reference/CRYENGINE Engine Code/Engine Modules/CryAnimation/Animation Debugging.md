# Animation Debugging

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/23306443
- Page ID: 23306443
- Breadcrumb: CRYENGINE Engine Code > Engine Modules > CryAnimation > Animation Debugging
- Parent: CryAnimation

## Content

## Layered Transition Queue Debugging

You can enable on-screen debug information to see which animations are queued and playing, as well as information about the applied pose modifiers and IK. See [Animation Layers](/docs/static/engines/cryengine-3/categories/1114113/pages/15012021) for more information about the system.

![Image](https://www.cryengine.com/docs/static/attachments/23461205) *Example output*.

### Show Per Entity

You can show the transition queue for all the characterinstances of a specified entity.

es_debuganim <entityname> [0 | 1]

Property | Description
--- | ---
**<entityname>** | the name of the entity to debug. In a single player game, the player is typically called "dude". Note that the GameSDK example player has both a first person and third person character instance.
**[0 | 1]** | Specify 1 or no second parameter to turn it on for this specific entity. Specify 0 to turn it off.

##### Examples...

es_debuganim dude 1

Turn on debugging for the player (assuming the player's entity is called "dude").

es_debuganim npc_flanker_01 0

Turn off debugging for the entity called npc_flanker_01

### Show Per CharacterInstance

You can show the transition queue for all characterinstances or the ones that have a specific model name.

ca_debugtext [<modelname-substring> | 1 | 0]

- If 1 is specified, all character instances are shown.
- If 0 is specified, the debug text is turned off.
- If <modelname-substring> is specified, shows information for all characterinstances whose modelname contains the specified string.

##### Examples...

ca_debugtext player

Show information on all character instances with "player" in their model name.

ca_debugtext 0

Turn off all transitionqueue information.

### Interpreting the Output

Each animation in the transition queue is displayed with a couple of lines like the following. The parts are explained below.

AnimInAFIFO 02: t:1043 _stand_tac_idle_scar_3p_01 ATime:0.84 (1.17s/1.40s) ASpd:1.00 Flag:00000042 (----------I-K----) TTime:0.20 TWght:1.00 seg:00 inmem:1

(Try)UseAimIK: 1 AimIKBlend: 1.00 AimIKInfluence: 1.00 (Try)UseLookIK: 0 LookIKBlend: 0.00 LookIKInfluence: 0.00

MoveSpeed: 4.49 locked: 1

PM class: AnimationPoseModifier_OperatorQueue, name: Unknown

...

LayerBlendWeight: 1.00

...

ADIK Bip01 RHand2RiflePos_IKTarget: 0.24 Bip01 RHand2Aim_IKTarget: 1.00 Bip01 LHand2Aim_IKTarget: 0.00

#### Text Color

- When an animation is not active yet, it will be black or green.
- When an animation is active, it's red or yellow.

Or in detail:

- Red Channel = Animation Weight.
- Green Channel = (layerIndex > 0)
- Alpha Channel = (Weight + 1)*0.5.

#### AnimInAFIFO Line (one per animation)

AnimInAFIFO 02: t:1043 _stand_tac_idle_scar_3p_01 ATime:0.84 (1.17s/1.40s) ASpd:1.00 Flag:00000042 (----------I-K----) TTime:0.20 TWght:1.00 seg:00 inmem:1

Part | Explanation |
--- | --- | ---
**AnimInAFIFO 02** | Layer index (decimal, zero-based). |
**t:1043** | User token (decimal). |
**_stand_tac_idle_scar_3p_01** | Animation name (alias) of the currently playing animation, aim/look-pose or bspace. |
**ATime:0.84 (1.17s/1.40s)** | ATime:XXXX (YYYYs/ZZZZs) - XXXX = current time in 'normalized time' (0.0...1.0) within the current segment. - YYYY = current time (seconds) within the current segment. - ZZZZ = expected duration (seconds) of the current segment. |
**ASpd:1.00** | Current animation speed (1.0 = normal speed). |
**Flag:00000042 (----------I-K----)** | Animation Flags Flag:XXXXXXXX (+ybVFx3nSIAKTRLM) The first number is the animation flags in hexadecimal. Between parentheses you see the individual flags: char | flag | value --- | --- | --- **+** | CA_FORCE_TRANSITION_TO_ANIM | 0x008000 ** y** | CA_FULL_ROOT_PRIORITY | 0x004000 ** b** | CA_REMOVE_FROM_FIFO | 0x002000 ** V** | CA_TRACK_VIEW_EXCLUSIVE | 0x001000 ** F** | CA_FORCE_SKELETON_UPDATE | 0x000800 ** x** | CA_DISABLE_MULTILAYER | 0x000400 ** 3** | CA_KEYFRAME_SAMPLE_30Hz | 0x000200 ** n** | CA_ALLOW_ANIM_RESTART | 0x000100 ** S** | CA_MOVE2IDLE | 0x000080 ** I** | CA_IDLE2MOVE | 0x000040 ** A** | CA_START_AFTER | 0x000020 ** K** | CA_START_AT_KEYTIME | 0x000010 ** T** | CA_TRANSITION_TIMEWARPING | 0x000008 ** R** | CA_REPEAT_LAST_KEY | 0x000004 ** L** | CA_LOOP_ANIMATION | 0x000002 ** M** | CA_MANUAL_UPDATE | 0x000001 |
char | flag | value
**+** | CA_FORCE_TRANSITION_TO_ANIM | 0x008000
**y** | CA_FULL_ROOT_PRIORITY | 0x004000
**b** | CA_REMOVE_FROM_FIFO | 0x002000
**V** | CA_TRACK_VIEW_EXCLUSIVE | 0x001000
**F** | CA_FORCE_SKELETON_UPDATE | 0x000800
**x** | CA_DISABLE_MULTILAYER | 0x000400
**3** | CA_KEYFRAME_SAMPLE_30Hz | 0x000200
**n** | CA_ALLOW_ANIM_RESTART | 0x000100
**S** | CA_MOVE2IDLE | 0x000080
**I** | CA_IDLE2MOVE | 0x000040
**A** | CA_START_AFTER | 0x000020
**K** | CA_START_AT_KEYTIME | 0x000010
**T** | CA_TRANSITION_TIMEWARPING | 0x000008
**R** | CA_REPEAT_LAST_KEY | 0x000004
**L** | CA_LOOP_ANIMATION | 0x000002
**M** | CA_MANUAL_UPDATE | 0x000001
**TTime:0.20** | Transition Time Total length of transition into this animation in seconds (this is static after pushing the animation). |
**TWght:1.00** | Transition Weight Current weight of this animation within the transition (0 = not faded in yet, 1 = fully faded in). |
**seg:00** | Current segment index (zero-based). |
**inmem:1** | Whether or not the animation is in memory (0 basically means it's not streamed in yet). |

#### Aim/Look-IK Line

(Try)UseAimIK: 1 AimIKBlend: 1.00 AimIKInfluence: 1.00 (Try)UseLookIK: 0 LookIKBlend: 0.00 LookIKInfluence: 0.00

Part | Description
--- | ---
**(Try)UseAimIK: 1** | Whether Aim IK is turned on or not. (set using PoseBlenderAim::SetState).
**AimIKBlend: 1.00** | Weight value requested for Aim IK. (could go up and down based on fade times etc).
**AimIKInfluence: 1.00** | Final influence weight value of AimIK. (== smoothed(clamped(AimIKBlend)) * weightOfAllAimPoses).
**(Try)UseLookIK: 0** | Whether Look IK is turned on or not.
**LookIKBlend: 0.00** | Weight value requested for Look IK. (could go up and down based on fade times etc)
**LookIKInfluence: 0.00** | Final influence weight value of LookIK. (== smoothed(clamped(LookIKBlend)) * weightOfAllLookPoses).

#### Parameter Line(s) (only for blend spaces)

MoveSpeed: 4.500000 locked: 1 TravelAngle: 0.000000 locked: 0

Part | Explanation
--- | ---
**MoveSpeed: 4.500000** | Value for the specified blendspace parameter (MoveSpeed in this case).
**locked: 1** | Whether or not the parameter is locked (= unable to change after it is set for the first time).

#### PoseModifier Lines (if running)

PM class: AnimationPoseModifier_OperatorQueue, name: Unknown

Displays which pose modifiers are running in this layer. The class as well as the name is shown (if available).

#### LayerBlendWeight Line (not on layer 0)

LayerBlendWeight: 1.00

The weight of this layer (0.00 - 1.00).

#### ADIK Line(s) (only if animation driven IK is applied)

ADIK Bip01 RHand2RiflePos_IKTarget: 0.24 Bip01 RHand2Aim_IKTarget: 1.00 Bip01 LHand2Aim_IKTarget: 0.00

Displays a list of the animation driven IK targets and their current weight. For more detailed position/rotation information you can use the separate cvar "ca_debugadiktargets 1".

## CommandBuffer Debugging

At the lowest level the animation system executes a list of simple commands to construct the final skeleton's pose.

These commands are for example "sample animation x at time t, and add the result with weight w to the pose". Or "clear the pose".

![Image](https://www.cryengine.com/docs/static/attachments/23461204) *Example output*.

You can enable on-screen debug information to see what is pushed on the command buffer (for all characters) using the following command:

ca_debugcommandbuffer [0 | 1]

## Warning Level

You can control when the animation system produces warnings using the ca_animWarningLevel cvar:

ca_animWarningLevel [0 | 1 | 2 | 3]

ca_animWarningLevel | Description
--- | ---
0 | Non-fatal warnings are off.
1 | Warn about illegal requests, for example requesting to start animations with an invalid index.
2 | Also warn about things like 'performance issues', for example animation-queue filling up. This might 'spam' your console with a dump of the animation queue at the time of the issue.
3 (default) | All warnings are on. This includes the least important warnings, e.g. a warning when playing uncompressed animation data.

## See Also

- [Mannequin Debugging](/docs/static/engines/cryengine-3/categories/1114113/pages/15011302) (includes the very useful *Frame by Frame debugging*!).
- [AimPoses and LookPoses](/docs/static/engines/cryengine-3/categories/1114113/pages/15011676) (last section in this page talks about debugging).

[Layered Transition Queue Debugging](#layered-transition-queue-debugging)[CommandBuffer Debugging](#commandbuffer-debugging)[Warning Level](#warning-level)[See Also](#see-also)
