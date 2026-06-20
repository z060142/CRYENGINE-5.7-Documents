# Animation Precaching

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/26874182
- Page ID: 26874182
- Breadcrumb: Film and Cutscenes > Cinematics Overview > Animation & Characters > Animation Precaching
- Parent: Animation & Characters

## Content

##
Overview

Pre-Caching can be used to avoid animation streaming problems at the start of a sequence.

The "PrecacheTrigger" input on the Animations:PlaySequence node will precache all animation data that is needed to play the first two seconds of the sequence.

*
Simple pre-caching setup using two triggers.
*

Optimally pre-caching is triggered
**
about 4-5 seconds
**
 before the sequence starts playing. However, in some cases shorter pre-caching times work just as well.

The slowest platform will be decisive for determining the time that is needed. Ideally this is a console with disc emulation enabled, or even better a console with a proper game disc.

The pre-cached animations will remain in memory until the scene gets played.

-
Note that if the Start Time of a sequence has been changed to be larger than 0, pre-caching will take this into account and won't load any animation data that isn't needed.

-
Also note that once playing, a Track View sequence will automatically pre-cache the next two seconds of needed animation data.
