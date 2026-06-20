# EaaS 3.6.16

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/47316993/pages/44963022
- Page ID: 44963022
- Breadcrumb: Engine Release Notes (Current) > CRYENGINE 3.x > EaaS 3.6 > EaaS 3.6.16
- Parent: EaaS 3.6

## Content

Released 30th January, 2015

##
Editor

-
**
Fixed
**
: No longer export all vegetation-object's static-object-groups to all surface-types that have at least one vegetation-object using the same static-object applied to it (CE-5348).

##
Engine

-
**
Fixed
**
: (Particles) Division overflow in targeting code, when radius is very near target radius (CE-5353).

-
**
Fixed
**
: (Occlusion) Sign fix to speed up occlusion culling (CE-5210).

##
Audio

-
**
Fixed
**
: Ref counting of AFCM entries, blocking load requests now cause a blocking stream as well (CE-4570).

##
Game

-
**
Fixed
**
: (AISystem) CollisionAvoidanceSystem: Removed a heuristic to minimize the case where an agent would get stuck at a side of a corridor when avoiding a standing agent (the constraint line no longer changes suddenly) (CE-5300).
