# Force Feedback

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/26873013
- Page ID: 26873013
- Breadcrumb: Gameplay > Game Rules Overview > Force Feedback
- Parent: Game Rules Overview

## Content

![Image](https://www.cryengine.com/docs/static/attachments/29933291)

##
Overview

##
Topics

CRYENGINE can make use of the ForceFeedback (FFB) system. A simple series of numbers are looped to implement the generated effects. An effect is a combination of pattern to play and envelope to control the patterns effect over a period of time on the controller's motor. For more information on Forcefeedback nodes, please refer to
[Game Nodes](../../Editor%20Tools/Flow%20Graph/Flow%20Graph%20Node%20Reference/Game%20Nodes.md)
.

The file that contains the configuration information of the effects is located at:

-
*
`
GameSDK\Libs\GameForceFeedback\ForceFeedbackEffects.xml
`
*
The key configuration areas in the file are:

-
Patterns

-
Envelopes

-
Effects

[Topics](#topics)
[Patterns](#patterns)
[Envelopes](#envelopes)
[Effects](#effects)
[Bad combinations of Patterns and Envelopes](#bad-combinations-of-patterns-and-envelopes)
[Debugging ForceFeedback](#debugging-forcefeedback)
[Flow Graph](#flow-graph)

##
Patterns

A pattern defines the power of the rumble effect that needs to be applied to the specified motor within the controller. To begin with, open the file specified above (
*
ForceFeedbackEffects.xml
*
) and let's look at the pattern definitions. The sample's field basically sends a power value to the motor ranging from 0 -> 1 (unspecified- maximum rumble).

```

`
  <Patterns>
    <!-- Pattern definition accepts from 1 to 16 samples -->
      <Pattern name="100" samples="1" />
      <Pattern name="75" samples="0.75" />
      <Pattern name="50" samples="0.5" />
      <Pattern name="30" samples="0.3" />
      <Pattern name="20" samples="0.2" />
      <Pattern name="12" samples="0.12" />
    <Pattern name="square" samples="1,1,1,1,1,1,1,1,0,0,0,0,0,0,0,0" />
    <Pattern name="triangle" samples="0,0.15,0.3,0.45,0.6,0.75,0.9,1,1,0.9,0.75,0.6,0.45,0.3,0.15,0" />
  </Patterns>
`

```

A Pattern can have between 1 - 16 samples.

##
Example 1

-
*
<Pattern name="100" samples="1" />
*
This pattern is called
**
"100"
**
 and it uses one constant value
**
 "1"
**
 over the entire length of the pattern.

*
Pic1: Full power (samples = 1)
*

![Image](https://www.cryengine.com/docs/static/attachments/35401845)

##
Example 2

-
*
<Pattern name="square" samples="1,1,1,1,1,1,1,1,0,0,0,0,0,0,0,0" />
*
This pattern is called "
**
square
**
" and it applies full power to the motors for the first 8 samples, and then applies no values to the following 8 samples.

*
Pic2: Approx Full power, then none (samples = 1,0)
*

![Image](https://www.cryengine.com/docs/static/attachments/35401846)

This pattern could also be represented by a sample series of
**
samples="1,0"
**
.)

##
Example 3

-
*
<Pattern name="50" samples="0.5" />
*
This pattern is called
**
"50"
**
 with a constant 1/2 power.

*
Pic3: 50% power (samples = 0.5)
*

![Image](https://www.cryengine.com/docs/static/attachments/35401847)

##
Example 4

-
*
<Pattern name="triangle" samples="0,0.15,0.3,0.45,0.6,0.75,0.9,1,1,0.9,0.75,0.6,0.45,0.3,0.15,0" />
*
This pattern is called
**
"triangle"
**
 and it uses the full 16 values to create an effect.

If you note the name of this effect
**
"triangle",
**
the first 8 samples grows from 0 -> 1 and the last 8 decreases from 1 -> 0. This simulates a triangle pattern by slowly building up the strength of the effect and then goes back down again to zero to create a loop.

*
Pic4: Approx representation of the triangle wave
*

![Image](https://www.cryengine.com/docs/static/attachments/35401848)

This describes the concept of patterns for the power that will be delivered to the controller's motors. The range of the power runs from 0 -> 1 and the maximum variation that you can add to the samples is 16.

Note that by wildly swapping between 0,1,0,1,0,1,0,1,0,1,0,1,0,1,0,1, you will produce jagged wave pattern, but you have to remember that the motors within the controller
**
need time to spin-up/spin-down
**
, so in reality you're more than likely to end up with a constant vibration, rather than feeling the full-on/full-off effect.

This will happen if the time specified for the effect to play is too short to allow the motors to adjust to the speed that you are asking them to do!

Creating your own patterns is as simple as defining a new name for the pattern and then specifying the values that will be played at the motor (
**
with a maximum of 16 individual values
**
)
**
.
**
 If you decide to use less than the full 16 samples, make sure they are divisible by 2, so the system can distribute the effect evenly over the timeline. For example: 1, 2, 4, 8, 16 samples within the effect.

##
Envelopes

Envelopes are used as overrides to the patterns. They complement the pattern by either blending in or out the actual effect, depending on how you set the envelope up.

```

`
  <Envelopes>
    <!-- Envelope definition accepts from 1 to 8 samples -->
    <Envelope name="linearDecrease" samples="1,0" />
    <Envelope name="Gate" samples="1,1,1,1,1,1,1,0" />
      <Envelope name="CosineDecrease" samples="1,0.98,0.92,0.83,0.69,0.54,0.25,0" />
    <Envelope name="constant" samples="1" />
    <Envelope name="50constant" samples="0.5" />
      <Envelope name="Gausscharge" samples="0,0,0,0,1,1,1,1" />
  </Envelopes>
`

```

An envelope can only use up to a maximum of 8 samples.

##
Example 1

-
*
<Envelope name="linearDecrease" samples="1,0" />
*
This envelope when used in conjunction with an effect will allow the underlying effect to play at the maximum to begin with, then over time, it reduces the impact that the effect can send to the motor, all the way down to zero.

Let us consider the pattern above called "
**
0.5
**
" as an example.

*
Pic5: Envelope with a pattern 0.5
*

![Image](https://www.cryengine.com/docs/static/attachments/35401849)

Now the representation of the envelope for "
**
linearDecrease
**
" is described below.

*
Pic6: Linear decrease envelope (note the 1 - 8 max samples)
*

![Image](https://www.cryengine.com/docs/static/attachments/35401850)

##
Result

Now this will be the result when you combine the pattern 0.5 with the envelope linear decrease. The pattern starts off at the maximum value (0.5) since the envelope plays at the maximum possible value specified within the pattern.

Then over the course of the effect, the envelope reduces the ability of the pattern to play at its set value until it reaches zero.

Pic7: Result of
*
pattern 0.5 + l
*
inear decrease envelope

![Image](https://www.cryengine.com/docs/static/attachments/35401851)

*
*

##
Example 2

The previous example was quite simple and this time we will show a more complex effect in action which is being adjusted by the envelope. The pattern will be a saw-tooth effect, a series of 0,1,0,1.0,1,0,1.0,1,0,1,0,1,0,1's.

*
Pic8: A saw-tooth pattern
*

![Image](https://www.cryengine.com/docs/static/attachments/35401852)

*
Pic9: Linear decrease envelope
*
(note the 1 - 8 max samples)
*

![Image](https://www.cryengine.com/docs/static/attachments/35401853)

*

##
Result

Now when we apply the linear decrease envelope on top of the saw-tooth pattern, the resulting effect will be:

*
Pic10: Saw-tooth with Linear decrease applied
*

![Image](https://www.cryengine.com/docs/static/attachments/35401854)

This shows you how to combine an effect to create
**
pattern
**
, and then when applied with the
**
envelope
**
, the effect tries its best to play the full pattern but it gets restricted by the envelope.

The combination of a pattern and envelope saves you time in having to calculate the actual true values of the decrease in power. Which would resemble values such as 0, 0.95, 0, 8.2, 0, etc., when represented as a comma separated string within the *.xml file.

##
Effects

The effects section will be the actual part that will be called using code, Flowgraph or any other means to trigger the effect to play. The effect encapsulates the pattern and envelope together, and then also assigns it to the specific motor that you want to play it on. We will again run through a few examples of different variations of the effects, and how to set them up below.

##
Effect breakdown

```

`
    <Effect name="explosion" time="1.0" >
      <MotorAB frequency="1" pattern="100" envelope="linearDecrease" />
    </Effect>
`

```

To begin with, let's breakdown this block to understand the basic flow.

-
*
<Effect name="explosion" time="1.0" >
*

-
**
Effect name
**
 = Name of the effect that will be referenced in the FlowGraph or code. So the name the effect based on its function in a logical manner.

-
**
Time
**
 = Specifies the time length for which the rumble effect will be played.

-
*
<MotorAB frequency="1" pattern="100" envelope="linearDecrease" />
*

-
**
MotorA
**
**
B
**
= The motor you want to target this effect on. You can either target MotorA or MotorB individually, or both together at once with MotorAB (as in this example). We give you the option to split them up as you may want to play the same effect on both motors, but with a different envelope!

-
**
Frequency
**
 = Leave this at one (There is no real need to change this). Increasing this number will start to blend all the values together, remember that the motor has to power-up to the level that you set, and we have found that the frequency of 1 is optimal to "feel" all the data that you are sending to the motors. When increasing this value (to use the phrase = “
*
can’t see the wood for the trees
*
”), there will be too many values that are being sent to the motors which you won’t be able to distinguish the difference between them. Try increasing/decreasing the time instead of frequency to modify the played effect.

-
**
Pattern
**
 = Specifies the pattern that you want to play inside this effect.

-
**
Envelope
**
 = Specifies the second value that will be added to your effect (for example,
*
linearDecrease
*
).

##
Example 1

```

`
<Effect name="100_50Constant" time="5.0" >
  <MotorAB frequency="1" pattern="100" envelope="50constant " />
</Effect>
`

```

This effect will send same pattern to both the motors, with the same envelope.

##
Example 2

```

`
<Effect name="100_50Constant" time="5.0" >
  <MotorA frequency="1" pattern="100" envelope="50constant " />
  <MotorB frequency="1" pattern="100" envelope="50constant " />
</Effect>
`

```

This effect is similar to the above effect, but we are splitting the Motors (A,B) into their own line for individual control (Even though they are same).

##
Example 3

```

`
<Effect name="100_50Constant" time="5.0" >
  <MotorA frequency="1" pattern="100" envelope="50constant " />
  <MotorB frequency="1" pattern="12" envelope=" linearDecrease " />
</Effect>
`

```

MotorA is running at max power (but clamped to 50% output due to the envelope)

MotorB is running at 0.12 power, and moves towards to zero at the end due to the LinearDecrease envelope.

In Xbox One gamepads, the force feedback system now reads MotorLT for the left trigger, MotorRT for the right trigger and MotorLTRT for both triggers from ForceFeedbackEffects.xml.

##
Bad combinations of Patterns and Envelopes

In certain circumstances, if you're not paying close attention, you can end up cancelling out the FFB effect that you want to play. This can happen when the envelope is working in the opposite direction to the pattern. Let's look at the below example:

```

`
<Effect name="Not_so_good_effect" time="5.0" >
  <MotorA frequency="1" pattern="square" envelope="Gausscharge" />
</Effect>
`

```

Based on the above example, the
**
Square
**
 pattern (1,1,1,1,1,1,1,1,0,0,0,0,0,0,0,0) plays at the start of the effect (1) and does not play anything towards the end of the effect (0). The
**
Gausscharge
**
 envelope (0,0,0,0,0,0,0,0,1,1,1,1,1,1,1,1) is the exact opposite and just cancels out the pattern.

**
Note:
**
 Be careful, do not set this setting when you create your own effects. Otherwise you could end up with an effect which completely cancels itself out or with partially missing data.

##
Debugging ForceFeedback

We have made some console variables to allow you to investigate the ForceFeedback system. This tool allows you to visualize the inputs that are being sent to the motors.

CVar
 |
Description
 |

*
ffs_debug
*

 |
Turns on/off ForceFeedback system debug.
 |

*
ffs_PlayEffect
*

 |
Play a ForceFeedback effect, passed by name as first parameter. For example,
**
ffs_PlayEffect explosion.
**
 |

*
ffs_Reload
*

 |
Reload ForceFeedback system data.
 |

*
ffs_StopAllEffects
*

 |
Stop all the active ForceFeedback effects.
 |

*
Pic11: Debug visual output from the ffs_debug CVar
*

![Image](https://www.cryengine.com/docs/static/attachments/35401855)

##
Flow Graph

The ForceFeedback system is provided with dedicated Flow Graph nodes. These allow access to designers and artists to configure test, and control the effects easier.

*
Pic12: FlowGraph nodes for the ForceFeedback system.
*

![Image](https://www.cryengine.com/docs/static/attachments/35401856)
