# Mannequin SubContexts

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/23308478
- Page ID: 23308478
- Breadcrumb: Editor Tools > Animation Tab > Mannequin Editor > Mannequin Technical Topics > Mannequin SubContexts
- Parent: Mannequin Technical Topics

## Content

##
Overview

SubContexts are a convenience offered to programmers when dealing with
[/docs/static/engines/cryengine-5/categories/23756816/pages/23308432](
FragmentIDs
)
 whose
[/docs/static/engines/cryengine-5/categories/23756816/pages/29450861](
Scopemask
)
 can ultimately encompass multiple scope contexts, each one referring to a different
*
role
*
. For example, a vehicle could provide multiple seats, each one having its own scope and unique associated tag.
Another simple example would be two characters playing a synchronized animation, such as a synchronized execution move.
SubContexts provide a way for programmers of explicitly referring to one of the different logical roles one could have (i.e. seat name, or initiator/target of the execution move) when requesting an action.

SubContexts are completely transparent for animators and designers. They do not impact the way fragments are set up in the editor. Their goal is only to provide gameplay programmers a safe and convenient way to provide some additional context information when dealing with actions which can involve multiple independent scope contexts.

##
Usage

SubContexts are defined in the
[/docs/static/engines/cryengine-5/categories/23756816/pages/23308471](
Controller Definition File
)
. Each SubContext is uniquely identified with a name, and exposes a
[/docs/static/engines/cryengine-5/categories/23756816/pages/29450861](
Scopemask
)
 and
[/docs/static/engines/cryengine-5/categories/23756816/pages/23308435](
Global TagState
)
. Following up on the vehicle example, this snippet shows how the vehicle's controller definition file could define different SubContexts for different seats, each seat having its own set of scopes.

```

`
<SubContexts>
 <Driver scopeMasks="Driver+DoorDriver" tags="Driver"/>
 <Passenger scopeMasks="Passenger+DoorPassenger" tags="Passenger"/>
</SubContexts>
`

```

Upon entering the vehicle, a character would typically get enslaved to either the Driver or Passenger
[/docs/static/engines/cryengine-5/categories/23756816/pages/29450870](
Scope Context
)
. When requesting a FragmentID that we want to be local to either one of those seats (for instance entering or leaving the vehicle), the game code would need to state which SubContexts it refers to. This is done by requesting the SubContext in a mannequin action:

```

`
// Driver just entered the vehicle, already enslaved to it
IActionController* pVehicleActionController;
IAction* pEnterVehicleAction;

// ...

// Queue the "EnterVehicle" FragmentID with the suitable SubContext
pEnterVehicleAction->SetFragment(EnterVehicle);
pEnterVehicleAction->SetTagContext(isDriver ? Driver : Passenger); // Change SubContext based on which role the enslaved character is supposed to have
pVehicleActionController->Queue(pEnterVehicleDriverAction);
`

```

This will internally result in the matching scopeMask and global tags being automatically added to the default state during the
[/docs/static/engines/cryengine-5/categories/23756816/pages/23308439](
Fragment Selection Process
)
 for this action. In this example, with a proper setup, the system would then know which character and which door to animate when processing this action. This way, we can simply query the same FragmentID and resolve it to different scopeMasks and ultimately fragments based on the given SubContext.
