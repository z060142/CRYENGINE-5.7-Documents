# EntityID Explained

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/23306401
- Page ID: 23306401
- Breadcrumb: CRYENGINE Engine Code > Engine Modules > CryEntitySystem > EntityID Explained
- Parent: CryEntitySystem

## Content

##
Problem

Referring to some dynamic C++ object can be done in many ways. Pointers can be used but removing objects requires iterating through all objects and manually finding the dangling pointers. Reference counting is another solution but can result in hidden memory leaks. What we want is a weak reference which means we want to able to remove the object and references should become invalid. In Far Cry we just used a simple 16 bit
**
index
**
 for our entities. As a consequence we had to iterate over all objects to invalidate the objects that we wanted to remove. Especially when traversing the complex AI data structures, a lot of memory was touched and because of the cache misses this cost performance.

##
Idea

The idea is to store with each reference some number that we call
**
salt
**
 (called "magic number" in the Game Programming Gems). This number together with the
**
index
**
 gives the object a unique name over the game lifetime. Whenever we destroy an object and reuse the same index, we increase the salt and all references with the same index become invalid. To get an entity position/pointer, the entity manager needs to resolve the EntityId and as the
**
salt
**
 is different the method fails.

##
Implementation

The class
*
CSaltBufferArray
*
 handles adding and removing of objects and does the required adjustments to the
**
salt
**
. We try to keep the object array compact for more cache friendly memory access. Storing EntityId references to disc is possible and used for save games and by the editor game export. However, when loading a save game of a level that was patched and has now more entities, this can result in some severe conflict. To solve this problem, we create dynamic entities starting with a high index counting down and create static EntityId starting with a small index counting up.

##
Limitations

A
**
16 bit index
**
 only allows up to approximately 65 thousand living objects but that should be enough for any non massive multiplayer game. In a massive multiplayer game, the described method should not be used by the server. However it can be used between specific clients and the server.

A
**
16 bit salt
**
 value only allows to reuse the same index up to approximately 65 thousand times. If that happens, the index cannot be used any more but all other indices are still available. Again this should not be a problem for a non massive multiplayer game, when used with some care (don't create and destroy objects too rapidly, e.g. bullets). Massive multiplayer games, or in general games that support very long game sessions (many days), can run into this limit.

It would be easy to extend the bitcount to some higher number but so far there was no need for that.

##
Links

-
**
"1.6 A Generic Handle-Based Resource Manager"
**

 in "Game Programming Gems 1" by Scott Bilas.

-
**
Halo 2 Solution
**

[http://www.game-tech.com/Talks/Butcher.doc](http://www.game-tech.com/Talks/Butcher.doc)
