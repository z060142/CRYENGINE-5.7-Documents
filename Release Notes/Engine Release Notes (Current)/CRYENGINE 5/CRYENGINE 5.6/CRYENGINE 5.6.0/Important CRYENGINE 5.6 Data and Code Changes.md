# Important CRYENGINE 5.6 Data and Code Changes

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/47316993/pages/44962803
- Page ID: 44962803
- Breadcrumb: Engine Release Notes (Current) > CRYENGINE 5 > CRYENGINE 5.6 > CRYENGINE 5.6.0 > Important CRYENGINE 5.6 Data and Code Changes
- Parent: CRYENGINE 5.6.0

## Content

The following is not intended to be a complete list of CRYENGINE 5.6 C++ API changes, rather it is an indication of the most important changes that Programmers need to be aware of.

##
Table of Contents

##
Components

-
RigidBodyComponent

-
The
*
RigidBodyComponent
*
 properties for
*
Density
*
 and
*
Resistance
*
now have a higher default value of
**
1000
**
.

-
PointConstraintComponent

-
The
*
PointContraintComponent
*
is now
**
active
**
 by default.

-
AudioSwitchComponent

-
This component has been moved to the SwitchStateComponent.

##
Core System

-
CRY_ASSERT_MESSAGE

has been deprecated.
CRY_ASSERT
 now has the functionality to provide a message if necessary and should be used instead. In user code a simple find and replace will suffice.

##
Entity System

-
IEntityComponent::GetEventMask
's signature has changed from
uint64 GetEventMask() const
 to
Cry::Entity::EventFlags GetEventMask() const
. User code needs updating to change the return value, code inside should continue building and functioning as before.

-
The
ENTITY_EVENT_BIT
 and
BIT64
 macros no longer need to be used for
IEntityComponent::GetEventMask
. Instead, the event can be applied directly. For example:
Cry::Entity::EventFlags GetEventMask() const
 { return EEntityEvent::Update | EEntityEvent::NameChanged; }
.

-
The move from
ENTITY_EVENT_BIT
 can be automated using Visual Studio's Find and Replace tool. Find: "
ENTITY_EVENT_BIT
\((?<event>.+?)\)
", and replace with "
${event}
", without the citation marks. Make sure to enable 'Use Regular Expressions'.

-
Entity timers have been moved from the entity level (
IEntity
) to the component level (
IEntityComponent
). This change was made to remove the need to find unique identifier on the entity instance level to avoid a clash with other components, something that could become very expensive.

-
The majority of use cases in a component can change
m_pEntity->SetTimer
 to
this->SetTimer
 and maintain behavior as before. The same applies for
KillTimer
.

[#components](
Components
)
[#core-system](
Core System
)
[#entity-system](
Entity System
)
