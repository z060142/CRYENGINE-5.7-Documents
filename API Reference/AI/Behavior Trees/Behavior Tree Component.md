# Behavior Tree Component

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/44958306
- Page ID: 44958306
- Breadcrumb: AI > Behavior Trees* > Behavior Tree Component
- Parent: Behavior Trees*

## Content

##
Component Interface

In Sandbox, adding an AI
[Behavior Tree Component](../../../Manual/Entities%20and%20Tools/Entity%20Components/Entity%20Components%20(From%20Engine%20Version%205.6)/AI%20Components.md)
 to an Entity gives it the ability to run AI behaviors by specifying which Behavior Tree must be used. In addition, extra functionality is provided to the Entity in C++ through the Behavior Tree Component Interface, called
*
IEntityBehaviorTreeComponent,
*
 which exposes the following functions.

```

`
//! Check if the behavior tree is running.
//! \return True if the behavior tree is running.
bool IsRunning() const;

//! Sends an event to the behavior tree, which will handle it.
//! \param szEventName Name of the event to be sent.
//! \note The event may trigger a change in the behavior tree execution logic, such as a variable change, transition to a different state, etc.
void SendEvent(const char* szEventName);
`

```

*
IEntityBehaviorTreeComponent
*
also allows values to be read from and written to the
[Blackboard](Behavior%20Tree%20Blackboard.md)
.

```

`
//! Sets the value of the given variable name. If the variable exists, it updates the value. If it does not it creates a new entry in the Blackboard.
//! \param szKeyName Name of the variable.
//! \param value Value of the variable.
//! \return True if successfully set.
//! \note It may fail to set the variable value if the id of the provided variable exists but its value has a different type.
template <class TValue>
bool SetBBKeyValue(const char* szKeyName, const TValue& value);

//! Gets the value of a Blackboard entry by name if it exists.
//! \param szKeyName Name of the variable.
//! \param value Value of the variable.
//! \return True if successfully retrieved the value.
//! \note It may fail to get the variable value if the id of the provided variable does not exist, or if it exists but its value has a different type.
template <class TValue>
bool GetBBKeyValue(const char* szKeyName, TValue& value) const;
`

```

##
Example

Retrieving and setting the value of a variable in the Blackboard via the
*
IEntityBehaviorTreeComponent
*
 is as simple as doing it in the Blackboard directly. To do this, you first need to retrieve the AI Behavior Tree Component of the desired Entity and then call the above mentioned functions as shown below.

```

`
void SetBlackboardVariableHealth(IEntity& entity, float healthValue)
{
  if (IEntityBehaviorTreeComponent* pBehaviorTreeComponent = static_cast<IEntityBehaviorTreeComponent*>(entity.GetComponent<IEntityBehaviorTreeComponent>()))
  {
    const bool variableSetSuccessfully = pBehaviorTreeComponent->SetBBKeyValue("Health", healthValue);
   }
}
`

```
