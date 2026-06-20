# Areas and Triggers

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/26871540
- Page ID: 26871540
- Breadcrumb: Entity > Areas and Triggers
- Parent: Entity

## Content

##
Overview

The entity system is capable of creating tracking area shapes, as well as entities that may enter them. This exposes the ability to receive callbacks when an entity enters an area in the world, usually used to trigger gameplay logic in specific sections of a level.

Access to the internal proximity grid is made possible by adding an instance of the
[IEntityTriggerComponent](/docs/static/engines/cryengine-5/categories/28704770/pages/29797287)
 component to an entity, see the example below.

[Example](/docs/static/engines/cryengine-5/categories/28704770/pages/29797287)
Once the trigger has been created on an entity, the
ENTITY_EVENT_ENTERAREA
 and
ENTITY_EVENT_LEAVEAREA
 events will be automatically fired on any entity that has not set the
ENTITY_FLAG_NO_PROXIMITY
 flag.

##
Table of Contents

[API Types](#api-types)
[Conclusion](#conclusion)

##
API Types

-
[IEntityTriggerComponent](/docs/static/engines/cryengine-5/categories/28704770/pages/29797287)

##
Conclusion

This concludes the article on areas and triggers, you may be interested in:

-
[Audio](Audio.md)

-
[Execution Order and Lifecycle](Execution%20Order%20and%20Lifecycle.md)
