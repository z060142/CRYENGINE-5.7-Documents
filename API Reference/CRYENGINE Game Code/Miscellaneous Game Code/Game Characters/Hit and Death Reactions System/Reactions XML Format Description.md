# Reactions XML Format Description

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/23306581
- Page ID: 23306581
- Breadcrumb: CRYENGINE Game Code > Miscellaneous Game Code > Game Characters > Hit and Death Reactions System > Reactions XML Format Description
- Parent: Hit and Death Reactions System

## Content

##
Overview

This section explains how the format of the Reactions XML files, the properties it can use, how to use them, etc. Think of it as a reference guide while editing the HitDeathReactions system XML files.

##
How To Read This Document

This document will explain XML properties frequently. The format used for those properties is as follows:

-
`
**
<property_name>
**
`
*
<property_type>
*
 (<property_format>) <description>

-
<property_name> -> Name of the property

-
<property_type> -> Type of the property:

-
*
Element
*
. XML elements, delimited by XML tags. e.g., <HitReactionParam></HitReactionParam> or <HitReactionParam/>

-
*
Attribute
*
. XML attributes, defined inside XML tags. e.g., <Whatever attribute="value"/>

-
<property_format> -> format used for the value of this property

-
<description> -> description of its functionality
If the color of a property is
red
, it means that property is of advanced or marginal use. I don't expect them to be used a lot, and usually only by programmers or technical staff for test purposes.

##
XML Files location

You can find the reactions XML files in this location:
`
GameData/Libs/HitDeathReactionsData/*.xml
`

An entity will use a given .xml if that file is specified on its
`
**
fileHitDeathReactionsParamsDataFile
**
`
 property (by default it will be
`
Libs/HitDeathReactionsData/HitDeathReactions_Default.xml
`
)

##
Sections of a reaction file

Each reaction file has five main sections:

-
[/docs/static/engines/cryengine-5/categories/23756813/pages/23306581#ReactionsXMLFormatDescription-DocumentTypeDefinition](
Document Type Definition (or DTD)
)

-
**
Root element.
**
 This is the main body of the XML file (delimited by the tags
`
<DeathHitReactionsParams>
`
 and
`
</DeathHitReactionsParams>
`
), it contains the other four important sections:

-
[/docs/static/engines/cryengine-5/categories/23756813/pages/23306581#ReactionsXMLFormatDescription-HitDeathReactionsConfig](
Hit Death Reactions Config
)

-
[/docs/static/engines/cryengine-5/categories/23756813/pages/23306581#ReactionsXMLFormatDescription-HitReactions](
Hit Reactions
)

-
[/docs/static/engines/cryengine-5/categories/23756813/pages/23306581#ReactionsXMLFormatDescription-DeathReactions](
Death Reactions
)

-
[/docs/static/engines/cryengine-5/categories/23756813/pages/23306581#ReactionsXMLFormatDescription-CollisionswithEnvironmentReactions](
Collisions with Environment Reactions
)
All sections are not mandatory (but of course, having an empty file won't do a lot, will it?). Below you will find more information about them.

##
Document Type Definition

This section is usually at the beginning of the file, outside the root element (which is
`
<DeathHitReactionsParams>
`
) and starts with the tag
`
<!DOCTYPE
`
. This section is not specific of the HitDeathReactions system, but a section part of the XML standard that can be on any XML file.

It's used on the HitDeathReactions XML files to define
*
XML Entities
*
, which are basically
*
macros
*
 that facilitates editing. e.g.:

```

`
<?xml version="1.0"?>

<!-- DTD (Document Type Definition) for defining XML Internal General Entities. Think of them as macros -->
<!DOCTYPE HitDeathReactions_Example [
  <!ENTITY Legs '
    <Part value="L Leg"/>
    <Part value="R Leg"/>
  '>

  <!-- Lower body part names -->
  <!ENTITY LowerBody '
    <Part value="Pelvis"/>
    &Legs;
  '>
]>

<DeathHitReactionsParams>
    <!-- HITS -->
    <HitReactionParams>

      <HitReactionParam animName="LowerBodyImpact">
        <AllowedParts>
          <!-- To use XML Entities put the name between the characters & and ; like &this;, it will be the same
          as if you had typed the same text you wrote on the Entity definition -->
          &LowerBody;
        </AllowedParts>
      </HitReactionParam>

    </HitReactionParams>

    <!-- DEATHS -->
    <DeathReactionParams>

      <DeathReactionParam animName="LowerBodyDeath">
        <AllowedParts>
          <!-- If we change the contents of the LowerBody entity, the changes will apply on every use of that
          entity, which is very useful while editing these files -->
          &LowerBody;
        </AllowedParts>
      </DeathReactionParam>

    </DeathReactionsParams>

</DeathHitReactionsParams>

`

```

##
Hit Death Reactions Config

This section allows to configure some aspects of the system for the character using the file by assigning some values to some attributes of the element <HitDeathReactionsConfig>.

These are the attributes you can use:

-
**
maximumReactionTime
**
 - Maximum time (in seconds) a reaction is allowed to last. The hit death reactions system automatically stops (and print a warning about it) any reaction that takes longer than this value as a failsafe behavior. If a valid reaction animation takes longer than this value just increase it. Default value: "4.0"

-
**
collisionBone
**
 - Name of the bone where the collision detection sphere will be centered on the horizontal (x-y) plane (see
[/docs](
Collisions with Environment Reactions
)
). Default value: "Bip01 Spine1".

-
**
collisionRadius
**
- Radius (in meters) of the collision detection sphere (see
[/docs](
Collisions with Environment Reactions
)
). Default value: "0.6".

-
**
collisionVerticalOffset
**
 - Height (in meters) where the collision detection sphere will be (see
[/docs](
Collisions with Environment Reactions
)
) from the character's location. Default value: "0.5".

-
**
collMaxHorzAngle
**
 - Sine of the maximum angle allowed for the collision normal respect the horizontal (x-y) plane (see
[/docs](
Collisions with Environment Reactions
)
). Default value: "0.342" -> sin 20º.

-
**
collMaxMovAngle
**
 - Cosine of the maximum angle of the collision normal respect the movement direction (see
[/docs](
Collisions with Environment Reactions
)
). Default value: "0.7071" -> cos 45º.

-
**
collReactionStartDist
**
 - Distance (in meters) from the collision point (and parallel to the normal) where the collision reaction starts (see
[/docs](
Collisions with Environment Reactions
)
). Default value: "0.4".
All properties are optional, if not specified they will take their default value.

##
Example

```

`
<?xml version="1.0"?>

<!-- Omitted DTD -->

<DeathHitReactionsParams>

  <HitDeathReactionsConfig collisionBone="Spine02" collisionRadius="1"
    collisionVerticalOffset="0.8"
    maximumReactionTime="4.5"/>

  <!-- Omitted Hit/Death/Collision reactions sections -->
</DeathHitReactionsParams>

`

```

##
Hit Reactions

This section is delimited by the tags
`
<HitReactionParams>
`
 and
`
</HitReactionParams>
`
. It can contain any number of reactions, which are delimited by the tags
`
<HitReactionParam>
`
 and
`
</HitReactionParam>
`
.

When a hit is detected the system starts evaluating reaction by reaction, in the order the are defined on the XML file. If one reaction is validated, it's executed and the process finalizes.

More details about their attributes and parameterization in the
[/docs/static/engines/cryengine-5/categories/23756813/pages/23306581#ReactionsXMLFormatDescription-ReactionProperties](
Reactions properties section
)

##
Death Reactions

This section is delimited by the tags
`
<DeathReactionParams>
`
 and
`
</DeathReactionParams>
`
. It can contain any number of reactions, which are delimited by the tags
`
<DeathReactionParam>
`
 and
`
</DeathReactionParam>
`
.

When a kill is detected the system starts evaluating reaction by reaction, in the order the are defined on the XML file. If one reaction is validated, it's executed and the process finalizes.

The main difference between Death Reactions and Hit Reactions is that the execution of a Death Reaction always ends enabling the ragdoll in the character.

More details about their attributes and parameterization in the
[/docs/static/engines/cryengine-5/categories/23756813/pages/23306581#ReactionsXMLFormatDescription-ReactionProperties](
Reactions properties section
)

##
Collisions with Environment Reactions

This section is delimited by the tags
`
<CollisionReactionParams>
`
 and
`
</CollisionReactionParams>
`
. It can contain any number of reactions, which are delimited by the tags
`
<CollisionReaction>
`
 and
`
</CollisionReaction>
`
.

Some Hit and Death reactions detect collisions with the environment while executing (specifically those with the
`
ragdollOnCollision
`
 or
`
reactionOnCollision
`
 property set, see the Reactions properties section).

If a collision is detected it can trigger one of these "Collision Reaction". These reactions are not validated, instead they are chosen based on the
`
reactionOnCollision
`
 property value or the parameter on some AnimationEvents (
*
ReactionOnCollision
*
) launched during the reaction.

If a Collision Reaction is triggered from a Death Reaction it will always end enabling the ragdoll in the character.

More details about their attributes and parameterization in the
[/docs/static/engines/cryengine-5/categories/23756813/pages/23306581#ReactionsXMLFormatDescription-ReactionProperties](
Reactions properties section
)
.

##
Reaction elements

Reactions do two important things:

##
Validation

A reaction can only be executed if it's valid. That is, if any of its validation blocks is valid, which means the requirements/constraints of that validation block fulfill the hit context.

Therefore a reaction can have several validation blocks or just one. You can specify several validation blocks by enclosing them inside the
`
<ValidationSection>
`
 element.

I'll illustrate that with examples so it's easier to understand:

```

`
  <HitReactionParam animName="smallCaliberReaction">
    <AllowedProjectiles>
      <Projectile value="SMGBullet"/>
      <Projectile value="PistolBullet"/>
    </AllowedProjectiles>
  </HitReactionParam>

`

```

... is equivalent to this version:

```

`
  <HitReactionParam animName="smallCaliberReaction">
    <ValidationSection>
      <Variation>
        <AllowedProjectiles>
          <Projectile value="SMGBullet"/>
          <Projectile value="PistolBullet"/>
        </AllowedProjectiles>
      </Variation>
    </ValidationSection>
  </HitReactionParam>

`

```

In both previous examples the
`
<AllowedProjectiles>
`
 element is the only constraint of the only validation that reaction is using.

Now imagine you want the animation "smallCaliberReaction" to be triggered also when the hit type is "collision" and the damage is less than 100. You could do something like this:

```

`
  <HitReactionParam animName="smallCaliberReaction">
    <ValidationSection>
      <Variation>
        <AllowedProjectiles>
          <Projectile value="SMGBullet"/>
          <Projectile value="PistolBullet"/>
        </AllowedProjectiles>
      </Variation>
    </ValidationSection>
  </HitReactionParam>

  <HitReactionParam animName="smallCaliberReaction" maximumDamage="100">
    <AllowedHitTypes>
      <HitType value="collision"/>
    </AllowedHitTypes>
  </HitReactionParam>

`

```

But generally is better if you limit the number of reaction blocks as much as possible. Instead, you could use the equivalent (and better) following version:

```

`
  <HitReactionParam animName="smallCaliberReaction">
    <ValidationSection>
      <Variation>
        <AllowedProjectiles>
          <Projectile value="SMGBullet"/>
          <Projectile value="PistolBullet"/>
        </AllowedProjectiles>
      </Variation>

      <Variation maximumDamage="100">
        <AllowedHitTypes>
          <HitType value="collision"/>
        </AllowedHitTypes>
      </Variation>
    </ValidationSection>
  </HitReactionParam>

`

```

Each validation process can be customized (using the
`
validationFunc
`
 property, see below) or just use the default C++ validation code (if the
`
validationFunc
`
 property isn't specified), which is the most used approach.

##
Execution

Once a reaction is validated, the next step is to execute it. The execution process can be customized (using the
`
reactionFunc
`
 property, see below) or just use the default C++ execution code (if the
`
reactionFunc
`
 property isn't specified), which usually translates into playing an animation.

##
Reaction Properties

##
Validation-related properties

-
**
validationFunc
**
 -
*
[Attribute]
*
 Specifies the name of the LUA or C++ function (registered on the CCustomReactionFunctions class) that will take care of the validation. Default value: it will use the default C++ validation code.
The default C++ validation code uses some properties that specify when a reaction is valid based on the context of the hit/kill. You can see them as constraints for the reaction to be selected.

If a constraint is not present, that means it won't have any effect (e.g., a reaction without any validation property/constraint will always be valid). These are the properties currently used for the Default Validation code:

-
**
minimumSpeed
**
 -
*
[Attribute]
*
 This reaction won't be valid unless the character is moving at this speed or greater.

-
**
maximumSpeed
**
 -
*
[Attribute]
*
 This reaction won't be valid unless the character is moving at this speed or lower.
You can easily see the speed a character has by typing g_hitDeathReactions_debug 1 on the console and looking to the
*
speedFlat
*
 value. You can find the speed values an AI uses if you look into its AI script file. Look for the AIMovementSpeeds table.

-
**
minimumDamage
**
 -
*
[Attribute]
*
 This reaction won't be valid unless the hit damage is equal or greater than this value. For most of the hits, the damage is not the health change actually caused, but the raw damage that type of hit causes. On kills it's the processed damage, though

-
**
maximumDamage
**
 -
*
[Attribute]
*
 This reaction won't be valid unless the hit damage is equal or lower than this value. For most of the hits, the damage is not the health change actually caused, but the raw damage that type of hit causes. On kills it's the processed damage, though

-
**
OnlyWhenPassingHealthThresholds
**
.
*
[Element]
*
 This HIT reaction won't be valid unless the hit caused the health of the character to go past one of the thresholds specified on it. For specifying health thresholds you can use absolute health values or a decimal percentage (floating values in the range [0, 1]) of the character's max health. e.g.,

```

`
<!-- This reaction will be executed when the hit causes the health of the character to go past 75% of health, 50% of health, 1500 health points and 25% of health. The order in which you define them is not relevant -->
  <HitReactionParam animName="alienHeavyReaction">
    <OnlyWhenPassingHealthThresholds>
      <HealthThreshold value="0.75"/>
      <HealthThreshold value="0.5"/>
      <HealthThreshold value="1500"/>
      <HealthThreshold value="0.25"/>
    </OnlyWhenPassingHealthThresholds>
  </HitReactionParam>
`

```

-
**
minimumDistanceToShooter
**
 -
*
[Attribute]
*
 (meters) This reaction won't be valid unless the distance between the shooter and the victim is equal or greater than this value.

-
**
maximumDistanceToShooter
**
 -
*
[Attribute]
*
 (meters) This reaction won't be valid unless the distance between the shooter and the victim is equal or lower than this value.

-
**
movementDirection
**
 -
*
[Attribute]
*
 (direction) This reaction won't be valid unless the character is moving on the specified direction range.

-
**
shotOrigin
**
 -
*
[Attribute]
*
 (direction) This reaction won't be valid unless the hit came from the specified direction range.

-
**
forward
**
. A 90 degrees range in front of the character

-
**
back
**
. A 90 degrees range behind the character

-
**
left
**
. A 90 degrees range to the left of the character

-
**
right
**
. A 90 degrees range to the right of the character

 —

-
**
ahead
**
. A 180 degrees range in front of the character

-
**
behind
**
. A 180 degrees range behind the character

-
**
leftSide
**
. A 180 degrees range to the left of the character

-
**
rightSide
**
. A 180 degrees range to the right of the character

-
**
probabilityPercent
**
.
*
[Attribute]
*
 (decimal percentage [0.0-1.0]) This reaction will only be valid its value percent of the time (e.g. below will only be valid 50% of the time)

```

`
<HitReactionParam animName="halfOfTheTime" probabilityPercent="0.5"/>
`

```

-
**
onlyIfUsingMountedItem
**
 -
*
[Attribute]
*
 (1/0) This reaction will only be valid if the character is using a mounted item (e.g., mounted machine gun)

-
**
destructibleEvent
**
 -
*
[Attribute]
*
 This reaction will only be valid if the hit has also triggered a body destruction event with this name (Body destruction events are managed by the BodyDestruction system, you can find them inside the files Libs/BodyDamage/BodyDestructibility_*.xml)

-
**
AllowedStances
**
 -
*
[Element]
*
 This reaction will only be valid if the character is in one of the stances specified on this property. e.g.,

```

`
<?xml version="1.0"?>

<!-- DTD (Document Type Definition) for defining XML Internal General Entities. Think of them as macros -->
<!DOCTYPE HitDeathReactions_Example [
  <!ENTITY StandingStances '
    <Stance value="STANCE_STAND"/>
    <Stance value="STANCE_RELAXED"/>
    <Stance value="STANCE_STEALTH"/>
    <Stance value="STANCE_ALERTED"/>
  '>
]>

<DeathHitReactionsParams>
  <!-- Omitted HitDeathReactions config section -->

  <HitReactionParams>

    <HitReactionParam animName="standingHitReaction">
      <AllowedStances>
        &StandingStances;
      </AllowedStances>
    </HitReactionParam>

    <HitReactionParam animName="crouchHitReaction">
      <AllowedStances>
        <Stance value="STANCE_CROUCH"/>
      </AllowedStances>
    </HitReactionParam>

  </HitReactionParams>

  <!-- Omitted Death/Collision reactions sections -->
</DeathHitReactionsParams>
`

```

Stance Identifiers
**
STANCE_PRONE, STANCE_CROUCH, STANCE_STAND, STANCE_RELAXED, STANCE_ALERTED, STANCE_STEALTH, STANCE_LOW_COVER, STANCE_HIGH_COVER, STANCE_SWIM, STANCE_LASTSTAND
**

-
**
AllowedHitTypes
**
 -
*
[Element]
*
 This reaction will only be valid if the hit type is part of the hit types specified on this property. e.g.,

```

`
<HitReactionParam animName="explosionReaction">
    <AllowedHitTypes>
      <HitType value="frag"/>
      <HitType value="explosion"/>
    </AllowedHitTypes>
  </HitReactionParam>
`

```

Hit Types
**
melee, collision, frag, normal, repair, bullet, gaussbullet, fire, stealthKill, silentMelee, tac, fall, event, punish, punishFall, avmine, moacbullet, scout_moac, aacannon, emp, pingerPing, kvolt, impulse_hit, heavyBullet, HMG, stamp, mike_burn, alienDropPodBounce, explosion, disableCollisions
**

-
**
AllowedProjectiles
**
 -
*
[Element]
*
 This reaction will only be valid if the projectile class that caused the hit/kill is one of the specified on this property. To know the projectile class of an ammunition edit the Ammo .xml files and search the value of the property name (e.g., <ammo name="GaussBullet" class="Bullet"> corresponds to a projectile of class "GaussBullet"). Classes names are case-sensitive, write it exactly as it appears on the ammo definition. e.g.,

```

`
  <HitReactionParam animName="smallCaliberReaction">
    <AllowedProjectiles>
      <Projectile value="SMGBullet"/>
      <Projectile value="PistolBullet"/>
    </AllowedProjectiles>
  </HitReactionParam>
`

```

-
**
AllowedWeapons
**
 -
*
[Element]
*
 This reaction will only be valid if the weapon class that caused the hit/kill is one of the specified on this property. To know the weapon class of a weapon edit the Weapon .xml files and search for the value of the property name (e.g., <item name="Gauss" class="Weapon" ...> corresponds to a weapon of class "Gauss"). Classes names are case-sensitive, write it exactly as it appears on the weapon definition. e.g.,

```

`
  <HitReactionParam animName="gaussHitReaction">
    <AllowedWeapons>
      <Weapon value="Gauss"/>
    </AllowedWeapons>
  </HitReactionParam>
`

```

-
**
AllowedParts
**
 -
*
[Element]
*
 This reaction will only be valid if the part (or attachment) impacted by the last hit is one of the specified on this property. e.g.,

```

`
  <DeathReactionParam animName="legsDeathReaction">
    <AllowedParts>
      <Part value="L Leg"/>
      <Part value="R Leg"/>
    </AllowedParts>
  </DeathReactionParam>
`

```

An easy way to obtain the name of the bones or attachments you are interested on (at least easier than ask a technical artist) would be to type i_giveItem debugGun on the console, and then aim to the character. The part or attachment you are aiming at will be displayed on a text like this: "partId: 77 (Bip01 Head)". Bip01 Head would be what you are looking for.

##
Execution-related properties

-
**
reactionFunc
**
 -
*
[Attribute]
*
 Specifies the name of the LUA or C++ function (registered on the CCustomReactionFunctions class) that will take care of the execution. Default value: it will use the default C++ execution code.

 Some existing custom execution functions are:

-
**
ReactionDoNothing
**
 - Does nothing (captain obvious), but the reaction is considered as succesful, so the game code won't try to run the fallback behavior.

-
**
MeleeDeath_Reaction -
**
 Special case for melee deaths. If the value of the pl_melee.impulses_enable CVar is 3 or 1, it will leave the Melee code to handle an impulse to the ragdoll, else will try to play the animation specified on the reaction, if present. If an animation is not specified it will ragdollize the character and run the ApplyDeathImpulse code of the ActorImpulseHandler.

-
**
FallAndPlay_Reaction
**
 - It will trigger fall and play on the character and run the ApplyDeathImpulse code of the ActorImpulseHandler.

-
**
BackHitInCover_Reaction -
**
 It will run the default execution code and will force the AI to leave cover.

-
**
DeathImpulse_Reaction
**
 - It will ragdollize the character and run the ApplyDeathImpulse code of the ActorImpulseHandler.
The default C++ execution code can cause a diverse range of effects, parameterized on its properties. If a property is not present, that means it won't cause any effect.

A reaction without any execution property won't do anything and will be considered as failed, so the game code will run the fallback code (a physic impulse on hits, ragdoll + impulses on deaths). That could be useful for some situations (there are already several reactions doing it).

These are the properties currently used for the Default Execution code:

-
**
ReactionAnim
**
 -
*
[Element]
*
 Specifies an animation (or a set of animations to choose one randomly) that will be played overriding the AnimationGraph, with a transition time of
**
0.1
**
 seconds. It uses some properties that affect how the anim is played:

-
**
additive
**
 -
*
[Attribute]
*
 (1/0) if enabled the animation will be played as an additive. Default value: "0"

-
**
layer
**
 -
*
[Attribute]
*
 ([0-15]) this is the animation layer where the animation will be played. The animation graph will be paused only if the layer used for the animation is the layer 0 (fullbody). Default value: "0"

-
**
overrideTransTimeToAG
**
 -
*
[Attribute]
*
 if this value if 0 or greater it will specify the transition time the current state of the animation graph will use when the animation graph is resumed at the end of the reaction. Default value: "-1.0"

-
**
AnimNames
**
 -
*
[Element]
*
 Contains a list of animations. The system shuffles the list randomly and plays one of the animations contained sequentially each time the reaction is executed, when the complete list is executed, it will be shuffled again. This is so the system ensures randomness without repetition. e.g.,

```

`
<!-- This reaction will play an additive animation in the layer 5 (I recommend using that layer or higher for partial/additive anims). In an hypothetical case, the system will behave like this:
(list is shuffled)
1st hit: Plays "stand_tac_hitShoulder_rifle_add_3p_01"
2nd hit: Plays "stand_tac_hitShoulderHMG_rifle_add_3p_02"
3rd hit: Plays "stand_tac_hitBelly_rifle_add_3p_01"
4th hit: Plays "stand_tac_hitShoulderHMG_rifle_add_3p_03"
5th hit: Plays "stand_tac_hitShoulderHMG_rifle_add_3p_01"
(list is shuffled)
6th hit: Plays "stand_tac_hitBelly_rifle_add_3p_01"
...
It won't matter which character has received the hit, the list is global to all the characters using the same reactions (so if you shot character A and then shot character B and both trigger the same reaction you can be sure they won't play the same animation in a row) -->
<HitReactionParam>
  <ReactionAnim additive="1" layer="5">
    <AnimNames>
      <AnimName name="stand_tac_hitBelly_rifle_add_3p_01"/>
      <AnimName name="stand_tac_hitShoulder_rifle_add_3p_01"/>
      <AnimName name="stand_tac_hitShoulderHMG_rifle_add_3p_0" variants="3"/>
      <!-- variants="3" above is equivalent to:
      <AnimName name="stand_tac_hitShoulderHMG_rifle_add_3p_01"/>
      <AnimName name="stand_tac_hitShoulderHMG_rifle_add_3p_02"/>
      <AnimName name="stand_tac_hitShoulderHMG_rifle_add_3p_03"/>
      -->
    </AnimNames>
  </ReactionAnim>
</HitReactionParam>
`

```

-
**
animName
**
 -
*
[Attribute]
*
 Simpler version of the ReactionAnim element above. So:

```

`
<DeathReactionParam animName="death_reaction_anim" />
`

```

... is equivalent to:

```

`
<DeathReactionParam>
  <ReactionAnim>
    <AnimNames>
      <AnimName name="death_reaction_anim"/>
    </AnimNames>
  </ReactionAnim>
</DeathReactionParam>
`

```

If both animName and ReactionAnim are used, animName will be ignored.

-
**
AnimGraphReaction
**
 -
*
[Element]
*
 Makes the animation graph play an animation by specifying a value for the
*
signal
*
 input and optionally some values for variation inputs. If this element is used together with ReactionAnim or animName it will override them. e.g.,

```

`
<!-- if shot from the left while running the reaction will set the "signal" input to "hitRunForward" and will set the variation input "stance" to "stand", the variation input "hitName" to "lft_torso_3p" and the variation input "variant" to "01" -->
<HitReactionParam shotOrigin="left" minimumSpeed="&RunningSpeed;">
  <AnimGraphReaction inputValue="hitRunForward">
    <Variations>
      <Variation name="stance" value="stand" />
      <Variation name="hitName" value="lft_torso_3p" />
      <Variation name="variant" value="01" />
    </Variations>
  </AnimGraphReaction>
</HitReactionParam>
`

```

-
**
pauseAI
**
 -
*
[Attribute]
*
 (1/0) Specifies if the AI should be paused during the reaction execution. Default value: "1"

-
**
AISignal
**
 -
*
[Attribute]
*
 If used, the AI will be sent the specified signal at the beginning of the reaction. If both this attribute and pauseAI="1" are used, the second will be ignored.

-
**
reactionOnCollision
**
 -
*
[Attribute]
*
 If used and greater than 0 it will make the system detect collisions with the environment during the reaction execution. The collision check works by using a sphere centered on the character with some parameterized attributes (see
[/docs](
Config Section
)
 for more details). If a collision is detected the system will interrupt the ongoing reaction and play the
[/docs](
collisionReaction
)
 which position matches the number used here (on death reactions, though, "1" will force the enabling of the ragdoll). Default value: "0". e.g.,

```

`
<HitDeathReactionParams>
  <!-- HIT REACTIONS -->
  <HitReactionParams>
    <!-- If the collision sphere detects a collision with the environment, the system will trigger the collision reaction number 2 (front collision, see below) -->
    <HitReactionParam minimumSpeed="&RunningSpeed;" movementDirection="forward" reactionOnCollision="2">
      <AnimGraphReaction inputValue="hitRunForward">
        <Variations>
          <Variation name="stance" value="stand" />
          <Variation name="hitName" value="torsoStumble" />
          <Variation name="variant" value="02" />
        </Variations>
      </AnimGraphReaction>
    </HitReactionParam>

    <!-- If the collision sphere detects a collision with the environment, the system will trigger the collision reaction number 3 (right side collision, see below) -->
    <HitReactionParam minimumSpeed="&RunningSpeed;" movementDirection="right" reactionOnCollision="3">
      <AnimGraphReaction inputValue="hitStrafe">
        <Variations>
          <Variation name="hitName" value="Rgt_all_torso" />
        </Variations>
      </AnimGraphReaction>
    </HitReactionParam>
  <HitReactionParams>

  <!-- COLLISION REACTIONS -->
  <CollisionReactionParams>
    <!-- THE FIRST REACTION COLLISION SHOULD ALWAYS BE A FALL AND PLAY ONE, OTHERWISE ragdollOnCollision
    PROPERTY WON'T TRIGGER ANY RAGDOLL IN HIT REACTIONS -->
    <!-- Fall and Play collision -->
    <CollisionReaction reactionFunc="FallAndPlay_Reaction" />

    <!-- front collision -->
    <CollisionReaction animName="stand_tac_hitColl_front_torso_3p_01" snapOrientationAngle="0">
    </CollisionReaction>

    <!-- right side collision -->
    <CollisionReaction animName="stand_tac_hitColl_rgt_torso_3p_01" snapOrientationAngle="90">
    </CollisionReaction>

    <!-- ... -->
  </CollisionReactionParams>

</HitDeathReactionParams>
`

```

ReactionOnCollision anim events
If the animation being played during the reaction execution uses ReactionOnCollision animation events it will be able to enable/disable/modify the collisions with the environment. The custom parameter of the animation event will change the value of the reactionOnCollision property on the reaction. So triggering a ReactionOnCollision animation event with "0" as custom parameter will disable collisions with environment, with "2" will enable it and make it trigger the second collision reaction defined, etc.

Some reaction don't even use the reactionOnCollision property, but rely on the animation to set the collision with the environment itself.

On Crysis 2, the typical indexes for the collision reactions are as follow:

-
Front collisions

-
Right side collisions

-
Left side collisions

-
Back collisions

-
Crouch right side collisions

-
Crouch left side collisions

-
Crouch back collisions

-
**
ragdollOnCollision
**
 -
*
[Attribute]
*
 (1/0) A simpler, more readable version of the reactionOnCollision property. So:

```

`
<HitReactionParam animName="StumbleForward" ragdollOnCollision="1"/>
`

```

... is equivalent to:

```

`
<HitReactionParam animName="StumbleForward" reactionOnCollision="1"/>
`

```

-
**
collisionCheckIntersectionWithGround
**
 -
*
[Attribute]
*
 (1/0) If enabled, on reactions that check collisions with the environment, will force the sphere to be at the character's feet height. Used for falling deaths. Default value: "0"

-
**
noRagdollOnEnd
**
 -
*
[Attribute]
*
 (1/0) If enabled won't enable the ragdoll when DeathReactions finish. Used only for 1st person camera deaths so it forces the character to stay on the last frame of the animation. Default value: "0"

-
**
noAnimCamera
**
 -
*
[Attribute]
*
 (1/0) Specifies if the camera will follow animation or not on 1st person reactions. "1": No animation-controlled camera, "0": animation-controlled camera. Default value: "0"

-
**
endVelocity
**
 -
*
[Attribute]
*
 (Vector) It forces this velocity on the character when the reaction ends. Used to improve transitions from stumble reactions to regular running locomotion groups. If not specified, no velocity is forced.

-
**
reactionFinishesAiming
**
 -
*
[Attribute]
*
 (1/0) It specifies if a reaction (other than a DeathReaction) forces aimIk to be enabled on the character when finished. This exist because many reaction animations assume the next pose after the reaction animation will have the character aiming. Default value: "1"

-
**
snapOrientationAngle
**
 -
*
[Attribute]
*
 (Degrees) If specified, the character's orientation will be snapped towards the shot origin and then rotated (counterclockwise) the number of degrees specified in the property right when the reaction starts. This is very useful to improve the look of reaction animations that show a heavy impulse on the character, so the impulse matches the shot direction wherever its origin is. e.g.,

```

`
<DeathReactionParam animName="stand_deathHeavy_front_torso_01" snapOrientationAngle="0" shotOrigin="ahead" ragdollOnCollision="1">
  <AllowedHitTypes>
    &HeavyHitTypes;
  </AllowedHitTypes>
</DeathReactionParam>

<DeathReactionParam animName="stand_deathHeavy_back_torso_01" snapOrientationAngle="180" shotOrigin="behind" ragdollOnCollision="1">
  <AllowedHitTypes>
    &HeavyHitTypes;
  </AllowedHitTypes>
</DeathReactionParam>
`

```

-
**
snapToMovementDir
**
 -
*
[Attribute]
*
 (Degrees) Similar to snapOrientationAngle, but instead of orientating the character towards the shot origin, it does it towards its movement direction. Used on some running reactions (the reaction animation assumes the character is moving forward so the inertia of the movement is animated forward. The character can be running on any direction, though, but by snapping it towards its movement direction it will look acceptably good no matter which direction is moving).

##
Hints for using the system

-
The system uses a reaction animation variations streaming logic that is very dependent on the reactions not being redundant.
Always try to minimize the number of reactions
 by using
`
[/docs/static/engines/cryengine-5/categories/23756813/pages/23306581#ReactionsXMLFormatDescription-Validation](
<validationsection>
)
`
 as much as possible.

-
When working on the data file, start by defining the most specific reactions and end with the most generic ones.

-
When adding a new reaction, test it by placing its definition at the beginning of the data file and removing any conditions for validation, that way that reaction will be selected 100% of the cases, so you can test its execution easier. Once the execution has been tested you can start adding its validation constraints until you are sure it's selected on the expected context. Then move it to the position on the reaction list that makes sense. Use
`
g_hitDeathReactions_reload
`
 command on each change and you'll be done in a few minutes.

-
Customized LUA functions are only for very isolated and specific cases or for quick tests. If you find yourself using a customized function a lot, then that code is better moved to C++ code.

-
Don't use Notepad for editing the HitDeathReaction data file
(unless you are into masochistic practices). It's the best way to make syntax errors while editing the file.
I recommend using Ultra-Edit 32
 (installed by default in most machines), Visual Studio, a XML editor or a text editor with syntax highlighting for XML format.

-
Use XML Entities to avoid duplication
 on the XML files. When supported, use external entities (explained on the
[/docs/static/engines/cryengine-5/categories/23756813/pages/23306581#ReactionsXMLFormatDescription-DocumentTypeDefinition](
Document Type Definition section
)
) as much as makes sense.
[#how-to-read-this-document](
How To Read This Document
)
[#document-type-definition](
Document Type Definition
)
[#hit-death-reactions-config](
Hit Death Reactions Config
)
[#hit-reactions](
Hit Reactions
)
[#death-reactions](
Death Reactions
)
[#collisions-with-environment-reactions](
Collisions with Environment Reactions
)
[#validation](
Validation
)
[#execution](
Execution
)
[#validation-related-properties](
Validation-related properties
)
[#execution-related-properties](
Execution-related properties
)
