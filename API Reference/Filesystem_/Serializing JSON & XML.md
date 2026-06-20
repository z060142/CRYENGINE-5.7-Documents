# Serializing JSON & XML

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/29796853
- Page ID: 29796853
- Breadcrumb: Filesystem_ > Serializing JSON & XML
- Parent: Filesystem_

## Content

##
Overview

CRYENGINE uses the Yasli serialization library to support serializing from/to JSON and XML - in addition to simplifying Sandbox UI creation.

##
Table of Contents

[#api-types](
API Types
)
[#the-archive-host](
The Archive Host
)
[#control-characters](
Control Characters
)
[#decorators](
Decorators
)
[#serialization-contexts](
Serialization Contexts
)
[#conclusion](
Conclusion
)

##
API Types

-
[/docs/static/engines/cryengine-5/categories/28704770/pages/29797435](
Serialization::IArchiveHost
)

##
The Archive Host

Serialization is wrapped through the
[/docs/static/engines/cryengine-5/categories/28704770/pages/29797435](
Serialization::IArchiveHost
)
 interface, and wraps the ability to load/save from various formats with relative ease. This serialization approach always assumes that a native representation of the object we want to serialize is available. This is achieved by assuming that a Serialize (Serialization::IArchive&) function exists in each object we want to serialize, and will otherwise throw a compiler error.

For an example of how to load JSON from a buffer, see
[/docs/static/engines/cryengine-5/categories/28704770/pages/29797435](
Serialization::IArchiveHost::LoadJsonBuffer
)
. Similarly, we can also save to disk with almost identical code by calling
[/docs/static/engines/cryengine-5/categories/28704770/pages/29797435](
Serialization::IArchiveHost::SaveJsonFile
)
.

[/docs/static/engines/cryengine-5/categories/28704770/pages/29797143](
Example
)

##
Control Characters

Control sequences are put as a prefix to the label of the property, i.e. third argument for the archive. Multiple control characters can be put together to combine their effects.

For example:

```

`
ar(name, "name", "^!<Name"); // inline, read-only, expanded value field
`

```

Prefix
 |
Role
 |
Description

 |

!
 |
Read only field
 |
Prevents user from changing the value of the property. Non-recursive.
 |

^
 |
Inline
 |
Inline property on the same line as name of the structure root.

Can be used to put fields in one line in horizontal layout, rather than the default vertical list.

 |

^^
 |
Inline in front of a name
 |
Inline property in the way that is placed before the name of the parent structure. Useful to add checkboxes before name.
 |

<
 |
Expand value field
 |
Expand value part of the property to occupy all available space (usually taking free space)
 |

>
 |
Contract value field
 |
Reduces width of the value field to its minimal value. Useful to restrict width of inline fields.
 |

>
*
N
*
>
 |
Limit field width to
*
N
*
 pixels
 |
Useful for finer control over UI look. Not recommended for use outside of editor.
 |

+
 |
Expand row by default.
 |
Can be used to control which structures/containers are expanded by default or not.

Use this only when you need per-item control, otherwise QPropertyTree::setExpandLevels is a better option.
 |

[
*
S
*
]
 |
Apply
*
S
*
control characters to children.
 |
This allows to apply a control character to children properties. Especially useful with containers.
 |

##
Decorators

There are two kinds of decorators:

-
Wrappers that take the original value and implement a custom serialization function to do some two-way transformation over it

For example: Serialization/Math.h contains Serialization::RadiansAsDeg(float&) that allows to store and edit angles in radians

-
Wrappers that do no transformation but their type is used to select custom property implementation in the PropertyTree

An example of such a wrapper would be all Resource Selectors.
Decorator
 |
Purpose
 |
Defined for types
 |
Context needed
 |

Serialization/Resources.h
 |

**
AnimationPath
**
 |
Selection UI for full animation path.
 |
Any string-like type, like:

std::string,

string (CryStringT),

SCRCRef

CCryName

 |

 |

**
CharacterPath
**
 |
UI: browse for character path (cdf)
 |

 |

**
CharacterPhysicsPath
**
 |
UI: browse for character .phys-file.
 |

 |

**
CharacterRigPath
**
 |
UI: browse for .rig files.
 |

 |

**
SkeletonPath
**
 |
UI: browse for .chr/.skel files.
 |

 |

**
JointName
**
 |
UI: list of character joints
 |
ICharacterInstance*
 |

**
AttachmentName
**
 |
UI: list of character attachments
 |
ICharacterInstance*
 |

**
SoundName
**
 |
UI: list of sounds
 |

 |

**
ParticleName
**
 |
UI: particle effect selection
 |

 |

Serialization/Decorators/Math.h
 |

**
RadiansAsDeg
**
 |
Edit/store radians as degrees
 |
float, Vec3

 |

 |

Serialization/Decorators/Range.h
 |

**
Range
**
 |
Sets soft/hard limits for numeric value and provides slider UI
 |
Numeric types.
 |

 |

Serialization/Callback.h
 |

 |

**
Callback
**
 |
Provides per-property callback function

See
[/docs/static/engines/cryengine-5/categories/23756813/pages/29796853#SerializingJSON&XML-AddingCallbackstoPropertyTree](
Adding Callbacks to PropertyTree
)
 |
All types apart from compound ones (structs and containers)
 |

##
Example of usage

```

`
float scalar;
ar(Serialization::Range(scalar), 0.0f, 1.0f); // provides slider-UI
string filename;
ar(Serialization::CharacterPath(filename), "character", "Character"); // provides UI for file selection with character filter
`

```

##
Serialization Contexts

The signature of Serialize method is fixed and this may prevent you from passing additional arguments into nested Serialize methods. To resolve this issue, Serialization Contexts were introduced.

By providing Serialization Context you can pass a pointer of a specific type, to nested Serialize calls. For example:

```

`
void Scene::Serialize(Serialization::IArchive& ar)
{
  Serialization::SContext sceneContext(ar, this);
  ar(rootNode, "rootNode")
}

void Node::Serialize(Serialization::IArchive& ar)
{
  if (Scene* scene = ar.FindContext<Scene>())
  {
    // use scene
  }
}
`

```

Contexts are organized into linked lists and nodes are stored on stack (withing SContext instance).

You can have multiple contexts. If you provide multiple instances of the same type, the innermost context will be retrieved.

You may also use contexts with a PropertyTree without modyfing existing serialization code. The easiest way to do it is to use CContextList (QPropertyTree/ContextList.h):

```

`
// CContextList m_contextList;
tree = new QPropertyTree();
m_contextList.Update<Scene>(m_scenePointer);
tree->setArchiveContext(m_contextList.Tail());
tree->attach(Serialization::SStruct(node));
`

```

##
Conclusion

This concludes the article on Yasli-based Serialization to/from JSON and XML. You may be interested in:

-
[/docs/static/engines/cryengine-5/categories/23756813/pages/29793409](
Reading & Writing XML
)

-
[/docs/static/engines/cryengine-5/categories/23756813/pages/26874870](
Projects and Plugins
)
