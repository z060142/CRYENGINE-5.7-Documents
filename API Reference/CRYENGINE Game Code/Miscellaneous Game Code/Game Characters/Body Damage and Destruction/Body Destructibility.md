# Body Destructibility

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/23306585
- Page ID: 23306585
- Breadcrumb: CRYENGINE Game Code > Miscellaneous Game Code > Game Characters > Body Damage and Destruction > Body Destructibility
- Parent: Body Damage and Destruction

## Content

### Overview

Body Destructibility xml files can be found in this folder: `GameSDK/Libs/BodyDamage/`

Any number of files can be created, usually one per actor type is enough. The naming convention is the following: *BodyDestructibility_NameOfCharacter.xml*

For example:

- BodyDestructibility_AlienGrunt.xml
- BodyDestructibility_CryNetOps.xml

These files will be usually edited by tech artist together with game designers.

They define a mapping of character bones and attachments to destructible 'body parts', destruction events, actor health thresholds and special death events.

### File Contents and Structure

Let's explain it with an example. The following is a collapsed version of the body parts setup for the alien grunt.

```
<BodyDestructibility>
<DestructibleParts>
<!-- Attachments -->
<Attachment name="armor_chest_l" >
<Health ratio="0.05" ratioToDestroyOnDeath="0.01" eventOnDestruction="armor_chest_l_explode" eventOnActorDeath="armor_chest_l_explode" />
<HitTypes>
<HitType name="gaussbullet" damageMultiplier="1.0" eventOnDestruction="armor_chest_l_explode" eventOnActorDeath="jelly_explode" />
<HitType name="mike_burn" damageMultiplier="0" />
<HitType name="frag" damageMultiplier="0.5" />
</HitTypes>
</Attachment>
...

<!-- Bones -->
<Bone name="Head" >
<Health ratio="1" ratioToDestroyOnDeath="0" eventOnDestruction="head_explode" eventOnActorDeath="head_explode" />
<HitTypes>
<HitType name="mike_burn" damageMultiplier="0.0" />
</HitTypes>
</Bone>
...
</DestructibleParts>

<Events>
<Event name="head_explode" >
<AttachmentsToHide>
<Attachment name="armor_head" />
<Attachment name="jelly_alive" />
<Attachment name="armor_head_tentacles" />
<Attachment name="eye_left" />
<Attachment name="eye_right" />
</AttachmentsToHide>
<AttachmentToUnhide>
<Attachment name="jelly_destroyed_head" />
</AttachmentToUnhide>
<Effect name="Crysis2_alien_effects.grunt.jelly_head_explode" />
<DisableEvents>
<Event name="head_damaged" />
<Event name="jelly_explode" />
</DisableEvents>
</Event>
...
</Events>
<HealthRatioEvents>
<HealthRatio ratio="0" bone="" event=""  material="Objects/characters/alien/grunt/grunt_dead" />
</HealthRatioEvents>
<ExplosionDeaths>
<GibEvent minExplosionDamage="200" probability="0.5" event="aliengrunt_gib" bone="jellyBone" /> <!-- Trigger event, and hide actor -->
<NonGibEvent event="jelly_boiling_explode" bone="jellyBone" material="Objects/characters/alien/grunt/grunt_dead" />
</ExplosionDeaths>
<MikeDeath>
<Destruction event="jelly_boiling_explode" bone="jellyBone" />
<Attachment name="jelly_destroyed_mike_attach" object="Objects/characters/alien/grunt/jelly_destroyed_mike.cdf" animation="jelly_destroyed_mike" alphaTestFadeOutDelay="0.85" alphaTestFadeOutTimeOut="0.25" />
</MikeDeath>
</BodyDestructibility>
```

### DestructibleParts

Contains a list of **Bones and Bone Attachments** that can be destroyed. Each part has a certain amount of health points - when they are depleted a ** Destruction Event** is triggered.

The following parameters are available:

- Health - ratio: Health points relative to the actor's maximum health points.
- Health - eventOnDestruction: Event to trigger when the part's health points are depleted.
- Health - ratioToDestroyOnDeath: Health points for the *eventOnActorDeath* relative to the actor's maximum health points.
- Defaults to *ratio* if undefined.
- Health - eventOnActorDeath: Event to trigger if the actor dies and the *ratioToDestroyOnDeath* health points are depleted.
- This can be used to destroy parts on actor death even if they were not hit by the fatal impact - adds more dismemberment on actor death.
- Defaults to *eventOnDestruction* if undefined.
- HitTypes: Can defined damage multipliers and events per hit type.
- HitType - damageMultiplier: The damage multiplier for the specified hit type.
- HitType - eventOnDestruction: Event to trigger when the part is destroyed with this hit type.
- HitType - eventOnActorDeath: Event to trigger when the actor is killed with this hit type.

### Events

Contains a list of **Destruction Events** that can be triggered by destroyed body parts or actor health thresholds being crossed.

Each event has a enabled/disabled state and can only be triggered if enabled. Once triggered an event will be disabled.

The following parameters are available:

- AttachmentsToHide: These character attachments will be hidden when the event is triggered.
- This also be used to disable particle effects that are attached to certain attachments - e.g. the glowing eye trails of our aliens.
- AttachmentToUnhide: These character attachments will be unhidden when the event is triggered.
- DisableEvents: These events will be disabled when this event is triggered - e.g. the head on an alien can no longer be destroyed when the whole body already exploded.
- Effect: This particle effect will be spawned when the event is triggered.
- The particle effect will be attached to the bone or the parent bone of the attachment that was destroyed.
- Explosion: This will spawn an explosion at the destroyed part's center - caution: this will also damage the actor that the explosion spawned from!
- Explosion - damage: Damage at the center of the explosion.
- Explosion - minRadius: Size of the center of the explosion, where maximum damage is dealt.
- Explosion - maxRadius: Size of end of the explosion where 0 damage is dealt.
- Explosion - pressure: Physical pressure of the explosion that pushes physicalized objects away.
- Explosion - effect: Particle effect for the explosion.
- ScriptCallback: Specifies a lua script function that will be executed when the event is triggered.
- The function must be defined inside the actor's lua script.
- e.g. the alien heavy's rocket launcher gets disabled by its destruction event.
- ScriptCondition: Specifies a lua script function that will be evaluated before the event happens - the event will only continue if this function returns true.
- The function must be defined inside the actor's lua script.
- e.g. the alien tick's biomass sack can only explode if it is filled.
- StopEvents: these events will be stopped if they are currently running.
- e.g. can be used to stop bleeding after actor death.

### HealthRatioEvents

Contains a list of **Destruction Events** which will happen as the health of the character reaches certain levels.

The following parameters are available:

- ratio: Health ratio at which the destruction event will be triggered. Value must be in the range (0, 1), 1 representing full health.
- bone: Defines which character bone location will be used to spawn effects tied to the destruction event.
- event: Destruction event to be triggered.
- material: This can be used to change the appareance of the character when a health ratio is reached.

### ExplosionDeaths

When a character dies by an explosion, two different events can be triggered.

- GibEvent: If certain conditions are met, the character will be hidden and this event triggered. The user can define the following parameters:
- minExplosionDamage: Minimum amount of damage that the explosion should have caused to be able to gib the character.
- probability: A value inside the range (0, 1), which is randomly evaluated at run time to dedice if it should trigger the gib event.
- event: Destruction event to be triggered.
- bone: Defines which character bone location will be used to spawn effects tied to the destruction event.

- NonGibEvent: If the conditions for the gib event are not met, this event will be executed. It triggers a destruction event at a bone location, and optionally a replacement material can be specified.
- event
- bone
- material

### MikeDeath

The mike death block is a special destruction event for Crysis2. This events triggers a destruction event at a bone location, and additionally it spawns and attaches an extra animated chr to the base character.

Additionally some alpha blend operations are done in the attached chr material.

- Destruction:
- event
- bone

- Attachment:
- name: Name of the attachment to attach the chr object.
- object: chr/cdf object to attach.
- animation: Animation to play on the attached object.
- alphaTestFadeOutDelay, alphaTestFadeOutTimeOut, alphaTestFadeOutMaxAlpha: Controls fade out of material on the attached object over time.
