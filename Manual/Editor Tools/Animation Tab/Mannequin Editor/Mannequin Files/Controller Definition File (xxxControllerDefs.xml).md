# Controller Definition File (xxxControllerDefs.xml)

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/23308471
- Page ID: 23308471
- Breadcrumb: Editor Tools > Animation Tab > Mannequin Editor > Mannequin Files > Controller Definition File (xxxControllerDefs.xml)
- Parent: Mannequin Files

## Content

##
Description

A Controller Definition contains the setup of a mannequin character.

It refers to the
[/docs/static/engines/cryengine-5/categories/23756816/pages/23308473](
Tag Definition File (xxxTags.xml)
)
 and
[/docs/static/engines/cryengine-5/categories/23756816/pages/23308474](
FragmentID Definition File (xxxActions.xml)
)
 used by this character.
It is typically referred to by the game entity, as the file is needed by the entity to create a
[/docs/static/engines/cryengine-5/categories/23756816/pages/23308466](
Mannequin ActionController
)
. See the overview picture in the
[/docs/static/engines/cryengine-5/categories/23756816/pages/23308470](
Mannequin Files
)
 document.

It defines which scopes are assigned to each of the FragmentIDs, aka the scopemasks. See
[/docs/static/engines/cryengine-5/categories/23756816/pages/23308432](
FragmentIDs
)
 and
[/docs/static/engines/cryengine-5/categories/23756816/pages/29450861](
Scopemasks
)
.

It defines which scopes and scope contexts the character has. See
[/docs/static/engines/cryengine-5/categories/23756816/pages/29450859](
Mannequin Scopes
)
 and
[/docs/static/engines/cryengine-5/categories/23756816/pages/29450870](
Scope Contexts
)
.

##
Creating a Controller Definition

You create a controller definition manually.
 See the
[/docs/static/engines/cryengine-5/categories/23756816/pages/23308471#ControllerDefinitionFile(xxxControllerDefs.xml)-FileFormat](
FileFormat
)
 section.

##
Editing a Controller Definition

The scopemasks and related flags can be edited in the
[/docs/static/engines/cryengine-5/categories/23756816/pages/23308446](
Mannequin FragmentID Editor
)
.

All the rest has to be edited manually in the xml file. See the
[/docs/static/engines/cryengine-5/categories/23756816/pages/23308471#ControllerDefinitionFile(xxxControllerDefs.xml)-FileFormat](
FileFormat
)
 section.

##
File Format

This is an example Controller Definition File:

```

`
<ControllerDef>
 <Tags filename="Animations/Mannequin/ADB/sampleTags.xml"/>
 <Fragments filename="Animations/Mannequin/ADB/sampleFragmentIds.xml"/>
 <SubContexts/>
 <FragmentDefs>
  <move scopes="FullBody+Torso" flags="Persistent"/>
  <burst_fire scopes="Torso+Weapon">
   <Override tags="heavyMortar" fragTags="boosted" scopes="Torso"/>
  </burst_fire>
 </FragmentDefs>
 <ScopeDefs>
  <FullBody layer="0" numLayers="3" context="MainContext"/>
  <Torso layer="3" numLayers="3" context="MainContext"/>
  <Face layer="6" numLayers="0" context="MainContext" Tags="scope_face"/>
  <Weapon layer="0" numLayers="2" context="WeaponContext"/>
 </ScopeDefs>
</ControllerDef>
`

```

The
*
Tags
*
 element contains a reference to the
[/docs/static/engines/cryengine-5/categories/23756816/pages/23308473](
Tag Definition File (xxxTags.xml)
)
 used by this setup.

The
*
Fragments
*
 element contains a reference to the
[/docs/static/engines/cryengine-5/categories/23756816/pages/23308474](
FragmentID Definition File (xxxActions.xml)
)
 used by this setup.

The
*
SubContexts
*
 element lists all the different
[/docs/static/engines/cryengine-5/categories/23756816/pages/23308478](
Mannequin SubContexts
)

available for this controller definition.

The
*
FragmentDefs
*
 element has to contain exactly one entry for each fragmentID specified in the FragmentID Definition. Typically editing of these elements is done automatically by the editor.

For each of the fragmentIDs:

-
*
scopes
*
 attribute: defines the
[/docs/static/engines/cryengine-5/categories/23756816/pages/29450861](
ScopeMasks
)
 for this fragmentID.

-
*
flags
*
 attribute: optionally provides flags in the Flags attribute. If more than one flag is set, separate them by a "+" character. Supported flags:
Flag

 |
Description

 |

**
Persistent
**

 |
Forces the action that requested this fragmentID to keep playing, even when the fragment that is playing is not looping and has ended.

 |

**
AutoReinstall
**

 |
Constantly checks whether there is a fragment available that matches the current
[/docs/static/engines/cryengine-5/categories/23756816/pages/23308435](
Mannequin TagState
)
.

If so, the system will push the new, better matching fragment for you. Useful for basic 'idling' actions. Typically used together with the "Persistent" flag.

 |

-
*
Override
*
 element: overrides the scopemask for this fragmentID when certain tags (and
[/docs/static/engines/cryengine-5/categories/23756816/pages/23308434](
fragtags
)
) are matched. In the example, when the fragmentID "burst_fire" is requested, normally the scopemask would be "Torso+Weapon". But if the global tag "heavyMortar" and fragtag "boosted" is set at that time, the scopemask "Torso" is used instead.
The
*
ScopeDefs
*
 elements defines the
[/docs/static/engines/cryengine-5/categories/23756816/pages/29450859](
scopes
)
 as well as the
[/docs/static/engines/cryengine-5/categories/23756816/pages/29450870](
scope contexts
)
 used by this setup. Each element inside the ScopeDefs element defines a scope. The element name is the scope name. Each scope has the following attributes:

Attribute

 |
Description

 |

**
layer
**

 |
The index of the first layer in the animation system this scope is bound to.

Careful: When picking a layer, make sure it doesn't clash with the layer being in use by the Pseudo Lip-Sync feature. Mannequin and Pseudo LipSync don't know about each other and therefore can't detect when one uses a layer that is already in use by the other!

 |

**
numLayers
**

 |
The number of animation layers this scope is bound to. A scope is bound to the animation layers with indices "layer" up to "layer+numLayers-1".

You have to make sure yourself that layers of scopes that use the same scope context do not overlap. It is allowed to specify '0' here, in which case the scope will only allow procedural layers.

 |

**
context
**

 |
The name of the scope context used by this scope.

 |

**
tags
**

 |
An optional tag, sometimes called the 'scope tag'. If set, it will be a tag that is
*
required
*
 for fragments playing on this scope.

This makes it possible to have multiple fragments playing on scopes that are using the same scope context.

In the above example, it is possible to have different fragments playing on the FullBody and Face scope. If you start an action on "FullBody+Face", the system will select two different fragments.

The fragment that is playing on the Face scope will need the "scope_face" tag. The fragment playing on the FullBody scope will not have this tag.

The editor will automatically add this tag to a fragment if you start editing this fragment on the Face scope.

The system will, however, only play
*
one
*
 fragment when you start an action on "FullBody+Torso", as they also both refer to the same context ("MainContext"), but neither of the two scopes has a scope tag.

In that example the fragment will end up on the FullBody scope.

 |
