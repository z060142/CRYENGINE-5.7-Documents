# Mannequin CTagDefinition

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/23308477
- Page ID: 23308477
- Breadcrumb: Editor Tools > Animation Tab > Mannequin Editor > Mannequin Technical Topics > Mannequin CTagDefinition
- Parent: Mannequin Technical Topics

## Content

##
Description

The CTagDefinition class represents a set of of keywords (tags). The class is used to represent a couple of different sets-of-keywords in the mannequin system. This includes the
[Mannequin Tags & Tag Definitions](../Mannequin%20Concepts/Mannequin%20Tags%20%26%20Tag%20Definitions.md)
 and
[FragmentID Definition File](../Mannequin%20Files/FragmentID%20Definition%20File%20(xxxActions.xml).md)
.

##
Features

Tags can have priorities associated to them. Tag priorities are used mainly for ranking
[Mannequin Tagstates](../Mannequin%20Concepts/Mannequin%20TagState.md)
.

Tags can be assigned to a group. Tags that are grouped together will be mutually exclusive, so we will not be able to have a TagState indicating that both of them are active at the same time.

Tags in a CTagDefinition are assigned a sequential and unique TagId (starting from 0 and unique within its TagDefinition) that can be used to more efficiently perform operations instead of always using the name of the Tag.

Tags can be referred to by lowercase-crc32 for efficiency if using the order-dependent TagId is too restrictive.

Tags can be assigned bit sequences so they can become part of a tagstates (combination of tags) for looking up fragments or transitions.

Each tag can optionally have a Sub TagDefinition. This is mainly used by
[FragmentID Definition Files](../Mannequin%20Files/FragmentID%20Definition%20File%20(xxxActions.xml).md)
 to specify what the Tag Definition is for their fragmentID-specific tags (aka Fragment Tags).

##
Loading

It is possible to store TagDefinitions in xml files and load them through the Animation Database Manager:

```

`
// Example of how to load a tag definition stored in an xml file.
IMannequin& mannequinInterface = pGameFramework->GetMannequinInterface();
IAnimationDatabaseManager& animationDatabaseManager = pMannequinInterface->GetAnimationDatabaseManager();
const CTagDefinition* pTagDefinition = animationDatabaseManager.LoadTagDefs( "Animations/Mannequin/ADB/ExampleTagDefinition.xml" );
`

```

##
Creation

TagDefinitions can also be created directly through code, although this is a lot less common.

```

`
// Example of how to create a tag definition from code
CTagDefinition example;
example.AddTag("Aiming");
example.AddTag("Crouch", "StanceGroup");
example.AddTag("Stand", "StanceGroup");
example.AssignBits();
`

```
