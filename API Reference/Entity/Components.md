# Components

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/26871489
- Page ID: 26871489
- Breadcrumb: Entity > Components
- Parent: Entity

## Content

##
Overview

**
Components
**
represent user-authored code that attach to
[/docs/static/engines/cryengine-5/categories/23756813/pages/26216196](
Entities
)
, known in code by the name
[/docs/static/engines/cryengine-5/categories/28704770/pages/29797021](
IEntityComponent
)
.

[/docs/static/engines/cryengine-5/categories/28704770/pages/29797021](
Minimal Component Implementation Example
)

##
Table of Contents

[#api-types](
API Types
)
[#type-and-instance-guids](
Type and Instance GUIDs
)
[#events](
Events
)
[#transform](
Transform
)
[#creating-and-querying-components](
Creating and Querying Components
)
[#editor-properties](
Editor Properties
)
[#adding-components-to-entities](
Adding Components to Entities
)
[#adding-components-programmatically](
Adding Components Programmatically
)
[#conclusion](
Conclusion
)

##
API Types

-
[/docs/static/engines/cryengine-5/categories/28704770/pages/29797021](
IEntityComponent
)

##
Type and Instance GUIDs

As seen in the
[/docs/static/engines/cryengine-5/categories/28704770/pages/29797021](
minimal entity component implementation
)
, each component type has to specify a GUID - used to uniquely identify this component implementation across the engine. This is stored as a
[/docs/static/engines/cryengine-5/categories/28704770/pages/29797020](
CryGUID
)
. Each component's type GUID is defined in its ReflectType function, for reference see the
[/docs/static/engines/cryengine-5/categories/28704770/pages/29797021](
minimal component example
)
.

In addition to the type GUID, each component instance is assigned a GUID. This is mostly used for internal purposes, but can also be used to query components using
[/docs/static/engines/cryengine-5/categories/28704770/pages/29797019](
IEntity::GetComponentByGUID
)
. The instance GUID of a component can be retrieved by calling
[/docs/static/engines/cryengine-5/categories/28704770/pages/29797021](
IEntityComponent::GetGUID
)
.

##
Generating GUIDs

GUIDs can be generated from Visual Studio by going to
**
Tools -> Create GUID
**
, bringing up the dialog below:

[Image: /docs/static/attachments/29926602]

Once open, select
**
4. Registry Format
**
 and click
**
Copy
**
. This will place the generated GUID into your clipboard, ready for usage in the CRYENGINE codebase.

##
Events

Entities routinely send events of type
[/docs/static/engines/cryengine-5/categories/28704770/pages/29797082](
EEntityEvent
)
, for example
ENTITY_EVENT_UPDATE
 - sent each frame to give components a chance to do per-frame logic.

Components can handle events by overriding the
[/docs/static/engines/cryengine-5/categories/28704770/pages/29797021](
IEntityComponent::ProcessEvent
)
 function, and providing a bit-mask of the desired event in
[/docs/static/engines/cryengine-5/categories/28704770/pages/29797021](
IEntityComponent::GetEventMask
)
.

[/docs/static/engines/cryengine-5/categories/28704770/pages/29797021](
Example
)

##
Transform

Each component can contain a transformation, supporting a relative offset of contained render or physical geometry from the parent entity. This is automatically exposed to the Sandbox Editor if
EEntityComponentFlags::Transform
 is applied to the component type in its
ReflectType
 call.

Once exposed, we can manipulate the world transformation of components using the following functions:

Function name
 |
Description
 |

[/docs/static/engines/cryengine-5/categories/28704770/pages/29797021](
IEntityComponent::SetTransformMatrix
)
 |
Sets the local transformation, in relation to the parent entities world transformation
 |

[/docs/static/engines/cryengine-5/categories/28704770/pages/29797021](
IEntityComponent::GetTransformMatrix
)
 |
Gets the local transformation, in relation to the parent entities world transformation
 |

[/docs/static/engines/cryengine-5/categories/28704770/pages/29797021](
IEntityComponent::GetWorldTransformMatrix
)
 |
Gets the world space transformation of the component, automatically applying the parent entities world transformation to the result
 |

In addition, each component can assign itself one
[/docs/static/engines/cryengine-5/categories/23756813/pages/26216196](
entity slot
)
that will be automatically moved with the component's transformation. This is made possible by loading geometry into the slot returned by
[/docs/static/engines/cryengine-5/categories/28704770/pages/29797021](
IEntityComponent::GetOrMakeEntitySlotId
)
.

##
Creating and Querying Components

Components can be created and queried using two kinds of functions; the Template helpers and low-level functions. The template helpers exist to simplify querying of a component type known at compile-time, while the low-level functions can be used to operate on components not known as the code is written.

We can also get components from an interface type, assuming that the interface implements
ReflectType
 and is added to the implementation via the
Schematyc::CTypeDesc<T>::AddBase
 function.

##
Template function helpers

The template helpers take one template parameter
T
 that is assumed to be derived from
[/docs/static/engines/cryengine-5/categories/28704770/pages/29797021](
IEntityComponent
)
. This allows for easily querying and creating components of a known type of interface.

Function name
 |
Description
 |

[/docs/static/engines/cryengine-5/categories/28704770/pages/29797019](
IEntity::CreateComponent
)
 |
Searches the component registry for the type description and creates a new instance of it in the entity
 |

[/docs/static/engines/cryengine-5/categories/28704770/pages/29797019](
IEntity::GetOrCreateComponent
)
 |
Searches the component registry for the type description, searches the entity for other instances of the same type and if found, returns that instance. If none are found, a new instance of the type is created.
 |

[http://docs.cryengine.com/docs.cryengine.com/display/CPP/IEntity#a2ade8aa2c906405edf195b2fabefa801](
IEntity::CreateComponentClass
)
 |
Creates a new instance of the component using the 'new' operator, skipping the need to search the component registry.
 |

[/docs/static/engines/cryengine-5/categories/28704770/pages/29797019](
IEntity::GetOrCreateComponentClass
)
 |
Searches the entity for other instances of the same type and if found, returns that instance. If none are found, a new instance of the type is created using the 'new' operator, skipping the need to search the component registry.
 |

[/docs/static/engines/cryengine-5/categories/28704770/pages/29797019](
IEntity::GetComponent
)
 |
Searches the component for existing instances of the type - and returns the first result, or nullptr if none are found.
 |

[/docs/static/engines/cryengine-5/categories/28704770/pages/29797019](
IEntity::GetAllComponents
)
 |
Searches the component for existing instances of the type - and returns all results in a dynamic array.
 |

[/docs/static/engines/cryengine-5/categories/28704770/pages/29797019](
IEntity::RemoveComponent
)
 |
Searches the component for existing instances of the type and removes the first occurrence.
 |

[/docs/static/engines/cryengine-5/categories/28704770/pages/29797019](
IEntity::RemoveAllComponents
)
 |
Searches the component for existing instances of the type and removes every occurrence.
 |

##
Low-level functions

The low-level functions operate on unique component type and instance GUIDs, and will always return an
[/docs/static/engines/cryengine-5/categories/28704770/pages/29797021](
IEntityComponent
)
* that can then be statically cast to the requested type.

Function name
 |
Description
 |

[/docs/static/engines/cryengine-5/categories/28704770/pages/29797019](
IEntity::CreateComponentByInterfaceID
)
 |
Queries the component registry for any component type that implements the specified interface ID, and creates a new instance of the first result, if any.
 |

[/docs/static/engines/cryengine-5/categories/28704770/pages/29797019](
IEntity::AddComponent
)
 |
Adds an already created component instance to the entity. Note that a component can
**
not
**
be added to multiple entities!
 |

[/docs/static/engines/cryengine-5/categories/28704770/pages/29797019](
IEntity::Remove Component
)
 |
Removes the specified component instance from the entity.
 |

[http://docs.cryengine.com/docs.cryengine.com/display/CPP/IEntity#aadfb3f8561409670123de7ab6e0c527a](
IEntity::RemoveAllComponents
)
 |
Removes all components from the entity.
 |

[/docs/static/engines/cryengine-5/categories/28704770/pages/29797019](
IEntity::GetComponentByTypeId
)
 |
Queries the entity for any components with the specified type ID, and returns the first occurrence.
 |

[/docs/static/engines/cryengine-5/categories/28704770/pages/29797019](
IEntity::GetComponentsByTypeId
)
 |
Queries the entity for any components with the  specified type ID, and returns all occurrences.
 |

[/docs/static/engines/cryengine-5/categories/28704770/pages/29797019](
IEntity::GetComponentByGUID
)
 |
Queries the entity for a component with the specific
**
instance
**
ID, and returns it if found.
 |

[http://docs.cryengine.com/docs.cryengine.com/display/CPP/IEntity#a9f63d88d4766c2c240de99fa8161e8df](
IEntity::QueryComponentsByInterfaceID
)
 |
Queries the entity for any components that implement the specified interface ID, and returns the first occurrence. Note that this function is significantly slower than
[/docs/static/engines/cryengine-5/categories/28704770/pages/29797019](
IEntity::GetComponentByTypeId
)
!
 |

[http://docs.cryengine.com/docs.cryengine.com/display/CPP/IEntity#ae4d452243ec37971e311b2d89d727f9a](
IEntity::QueryComponentByInterfaceID
)
 |
Queries the entity for any components that implement the specified interface ID, and returns all occurrences. Note that this function is significantly slower than
[/docs/static/engines/cryengine-5/categories/28704770/pages/29797019](
IEntity::GetComponentsByTypeId
)
!
 |

##
Editor Properties

It is often useful to expose component properties too the Editor in order to simplify designer workflow. This can be done by reflecting members in the component implementation's
ReflectType
 implementation, resulting in the properties being shown in the
**
Properties
**
 window when an entity with the component is selected:

[Image: /docs/static/attachments/28893578]

See the example below:

```

`
static void ReflectType(Schematyc::CTypeDesc<CMyComponent>& desc)
{
    /* ...Reflect GUID, set category etc... */
    // Use of multi-character literal to create a unique identifier for this member, in the scope of the component
    const uint32 id = 'floa';
    // Internal name of the property, will be visible in XML files
    const char* szInternalName = "MyParameter";
    // Human readable name, shown in the user interface
    const char* szDisplayName = "My Parameter";
    // Help text / description shown to users when they hover over the property in Editor
    const char* szDescription = "My Parameter Description";
    // Default value of the property
    const float defaultValue = 0.25f;
    desc.AddMember(&CMyComponent::m_floatValue, id, szInternalName, szDisplayName, szDescription, defaultValue);
}
`

```

It is also possible to create groups, this is accomplished by creating a struct with a
ReflectType
 function and adding an instance of it as a member to the component's
ReflectType
 function.

##
Adding Components to Entities

There are three methods of adding a component to an entity:

-
Through the Sandbox
**
Properties
**
 panel (see below)
[Image: /docs/static/attachments/28893356]

-
By creating a new Schematyc Entity, and adding the component (any instances of this entity in the scene will automatically instantiate the predefined components)

-
Programmatically, using the
[/docs/static/engines/cryengine-5/categories/28704770/pages/29797019](
IEntity
)
 interface (see below).

##
Adding Components Programmatically

Components can be attached to entities through code using the
[/docs/static/engines/cryengine-5/categories/28704770/pages/29797019](
IEntity
)
 interface through a set of simple functions:

Name
 |
Description
 |

[/docs/static/engines/cryengine-5/categories/28704770/pages/29797019](
IEntity::CreateComponent
<T>
)

 |
Creates an instance of the specified component, assuming that the component implementation was registered (see the section below).
 |

[/docs/static/engines/cryengine-5/categories/28704770/pages/29797019](
IEntity::GetOrCreateComponent
<T>
)

 |
Queries the entity for an existing instance of the specified component, and returns it if present. Otherwise, fallback to creating the entity component like
[/docs/static/engines/cryengine-5/categories/28704770/pages/29797019](
IEntity::CreateComponent<T>
)
.
 |

[/docs/static/engines/cryengine-5/categories/28704770/pages/29797019](
IEntity::CreateComponentClass
<T>
)

 |
Creates an instance of the specified component by using the 'new' operator directly, this does
**
not
**
 require the component implementation to be registered.
 |

[/docs/static/engines/cryengine-5/categories/28704770/pages/29797019](
IEntity::GetOrCreateComponentClass
<T>
)

 |
Queries the entity for an existing instance of the specified component, and returns it if present.
Otherwise, fallback to creating the entity component like
[/docs/static/engines/cryengine-5/categories/28704770/pages/29797019](
IEntity::CreateComponentClass<T>
)
.
 |

##
Registering a Component implementation

In order for
[/docs/static/engines/cryengine-5/categories/28704770/pages/29797019](
IEntity::CreateComponent<T>
)
 and
[/docs/static/engines/cryengine-5/categories/28704770/pages/29797019](
IEntity::GetOrCreateComponent<T>
)
 to work, component implementations need to be registered into the entity component registry. Additionally, this exposes your component to the Sandbox user interface - allowing direct usage of your component by designers without needing to modify code.

This is achieved by creating a Schematyc package, and registering your components inside it:

```

`
static void RegisterComponents(Schematyc::IEnvRegistrar& registrar)
{
  Schematyc::CEnvRegistrationScope scope = registrar.Scope(IEntity::GetEntityScopeGUID());
  {
    Schematyc::CEnvRegistrationScope componentScope = scope.Register(SCHEMATYC_MAKE_ENV_COMPONENT(CMyComponent));
  }
}

gEnv->pSchematyc->GetEnvRegistry().RegisterPackage(
  stl::make_unique<Schematyc::CEnvPackage>(
    "{E44AA983-48EF-4567-A545-324AC547A354}"_cry_guid,
    "My Entity Components Package",
    "My Company Name",
    "My Description",
    [this](Schematyc::IEnvRegistrar& registrar){ RegisterComponents(registrar); });
`

```

Once done, your component will show up in the 'Add Component' dialog for both selected entities and the Schematyc Editor.

##
Conclusion

This concludes the article on entity components. You may be interested in:

-
[/docs/static/engines/cryengine-5/categories/23756813/pages/26216232](
Networking
)

-
[/docs/static/engines/cryengine-5/categories/23756813/pages/28184910](
Execution Order and Lifecycle
)

-
[/docs/static/engines/cryengine-5/categories/23756813/pages/26216226](
Characters and Animations
)

-
[/docs/static/engines/cryengine-5/categories/23756813/pages/26216230](
Slots, Geometry and Effects
)

-
[/docs/static/engines/cryengine-5/categories/23756813/pages/29428286](
Input and Action Mapping
)

-
[/docs/static/engines/cryengine-5/categories/23756813/pages/26216224](
Physics and Movement
)

-
[/docs/static/engines/cryengine-5/categories/23756813/pages/26871538](
Audio
)
