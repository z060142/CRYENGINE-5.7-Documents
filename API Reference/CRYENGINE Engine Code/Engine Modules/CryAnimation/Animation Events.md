# Animation Events

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/23306438
- Page ID: 23306438
- Breadcrumb: CRYENGINE Engine Code > Engine Modules > CryAnimation > Animation Events
- Parent: CryAnimation

## Content

### Overview

Animations in CryENGINE can be marked up to send custom events at a specific time in the animations. This markup is used for time-aligned blending to match footplants in animations for example. Another application of the events is to spawn particle effects at the right moment.

These events can also be used for a variety of systems that need to receive information about when an animation has reached a certain point, for example in combination with a melee system etc.

### Marking up Animations with Events

The events for animations are stored in an xml-based file which is loaded upon character loading. For this to be done automatically the database needs to be included in the chrparams file. See this documentation on how to create such a database and on how to create events:

- Specific Information about the AnimEvents Database: [Animation Events (animevents)](/docs/static/engines/cryengine-3/categories/1114113/pages/1310772).
- General ChrParams File Information: [ChrParams File Reference](/docs/static/engines/cryengine-3/categories/1114113/pages/1310814).
- Markup specifically for blending with matching events: [Footstep Markup](/docs/static/engines/cryengine-3/categories/1114113/pages/1310780).

### Receiving Animation Events in the Game Code

The Animation Events are passed on to the GameObject once they have been triggered. The Actor and the Player implementation both handle these animation events.

See either Actor.cpp or Player.cpp for the function:

```
void AnimationEvent(ICharacterInstance *pCharacter, const AnimEventInstance &event)
```
