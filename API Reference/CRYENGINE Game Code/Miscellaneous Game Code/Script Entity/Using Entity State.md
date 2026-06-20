# Using Entity State

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/23306591
- Page ID: 23306591
- Breadcrumb: CRYENGINE Game Code > Miscellaneous Game Code > Script Entity > Using Entity State
- Parent: Script Entity

## Content

##
Overview

The Entity System provides a simple state switching mechanism for Script Entity.

Each state consists of:

-
A name (string).

-
A Lua table within the entity table identified with the state name.

-
An OnEndState function (optional).

-
An OnBeginState function (optional).

-
A bunch of further callback functions (all optional). For a list of available functions c. f.
[Entity System Script Callbacks](../../../CRYENGINE%20Engine%20Code/Engine%20Modules/CryEntitySystem/Entity%20System%20Script%20Callbacks.md)
All entity states must be
**
declared
**
 in the entity's main table first, otherwise the Entity Script System won't know about them. Here's how the 3 example states "Opened", "Closed", "Destroyed" would be declared:

```

`
AdvancedDoor =
{
    Client = {},
    Server = {},
    PropertiesInstance = ...
    Properties = ...
    States = {"Opened","Closed","Destroyed"},
}
`

```

Entity states can be either on the server or client (or both). Defining the server-sided "Opened"-state with the 2 functions "OnBeginState()" and "OnUpdate()" would look like this:

```

`
AdvancedDoor.Server.Opened =
{
  OnBeginState = function( self )
    if(self.Properties.bUsePortal==1)then
      System.ActivatePortal(self:GetWorldPos(),1,self.id);
    end;
    self.bUpdate=1;
    self.lasttime=0;
    AI.ModifySmartObjectStates( self.id, "Open-Closed" );
    self:Play(1);
   end,

  OnUpdate = function(self, dt)
    self:OnUpdate();
  end,
}

`

```

Initially, the entity is in
**
no state
**
 state at all. To put the entity in a state, you would use one of the
**
entity's callback functions
**
 (don't confuse with entity
**
state
**
's callback functions here) and call its
**
GotoState()
**
 method:

```

`
function AdvancedDoor:OnReset()
    self:GotoState("Opened");
end

`

```

From now on, the entity resides in the "Opened" state and events will also be directed to that state.

Transitioning from the current state to any other state can also be done via the
**
GotoState()
**
 method:

```

`
function AdvancedDoor.Server:OnHit(hit)
    ...
    if(self:IsDead())then
        self:GotoState("Destroyed");
    end
end
`

```

Querying the state the entity is currently in can be done via the
**
GetState()
**
 method:

```

`
if (self:GetState()=="Opened") then ...

if (self:GetState()~="Opened") then ...

`

```
