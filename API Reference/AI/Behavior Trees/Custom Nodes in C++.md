# Custom Nodes in C++

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/36870709
- Page ID: 36870709
- Breadcrumb: AI > Behavior Trees* > Custom Nodes in C++
- Parent: Behavior Trees*

## Content

##
Overview

This page provides instructions for creating and implementing custom behavior tree nodes; as explained in the following section, these nodes can be of three types namely, Action, Composites or Decorators.

##
The Base Class

##
Action Nodes

Action nodes represent the leaf nodes in a Behavior Tree and are responsible for causing an AI agent to perform a specific action such as moving between locations, speaking dialog or playing animations.

```

`
// New Action node.
class MyNewActionNode : public BehaviorTree::Action
{
  typedef BehaviorTree::Action BaseClass;

  // ...
};
`

```

##
Composite Nodes

Composite nodes have multiple children that are executed as per a specific policy/strategy.

```

`
// New Composite node.
class MyNewCompositeNode : public BehaviorTree::CompositeWithChildLoader
{
  typedef BehaviorTree::CompositeWithChildLoader BaseClass;

  // ...
};
`

```

##
Decorator Nodes

A Decorator node has only a single child, to which it adds extra functionality regardless of  what the child node does.

```

`
// New Composite node.
class MyNewDecoratorNode : public BehaviorTree::Decorator
{
  typedef BehaviorTree::Decorator BaseClass;

  // ...
};
`

```

##
The Interface

All nodes, regardless of their type, must have a few basic functions defined in order to work properly; these are described below.

```

`
// MyNewActionNode.h

// Although we're creating an Action node, the syntax would be the same for a Decorator or a Composite node as well.
class MyNewActionNode : public BehaviorTree::Action
{
  typedef BehaviorTree::Action BaseClass;

public:
  // Action (or Decorator or Composite).
  //! Called before the first call to Update.
  virtual void OnInitialize(const BehaviorTree::UpdateContext& context) override;

  //! Called when a node is being terminated (Terminate was called).
  //! This can happen in the following cases:
  //! a) The node returns Success/Failure in Update.
  //! b) Another node causes this node to Terminate while this node was running.
  virtual void OnTerminate(const BehaviorTree::UpdateContext& context) override;

  //! Do your node's work here.
  //! - Note that OnInitialize will have been automatically called for you before you get your first update.
  //! - If you return Success or Failure the node will automatically get OnTerminate called on itself.
  //! - If you return Running the node will keep running and it will be executed again the next frame.
  virtual BehaviorTree::Status Update(const BehaviorTree::UpdateContext& context) override;

  //! Load up a behavior tree node with information from an XML node.
  virtual BehaviorTree::LoadResult LoadFromXml(const XmlNodeRef& xml, struct BehaviorTree::LoadContext& context) override;

#ifdef USING_BEHAVIOR_TREE_XML_DESCRIPTION_CREATION
  //! Save behavior tree node information in an XML node. Opposite of LoadFromXML.
  //! Saved information that is saved here should be read back when calling LoadFromXML and vice versa
  virtual XmlNodeRef CreateXmlDescription() override;
#endif // USING_BEHAVIOR_TREE_XML_DESCRIPTION_CREATION

#ifdef USING_BEHAVIOR_TREE_SERIALIZATION
  //! Serialize node data to be shown in the Interim Editor.
  //! All properties that are saved/loaded in the XML should be accessible (somehow) from the Editor.
  virtual void Serialize(Serialization::IArchive& archive) override;
#endif // USING_BEHAVIOR_TREE_SERIALIZATION

#ifdef DEBUG_MODULAR_BEHAVIOR_TREE
  // ! Information to be shown in the screen when Debug Tree (or cvar ai_ModularBehaviorTreeDebugTree) is enabled
  virtual void GetCustomDebugText(const UpdateContext& updateContext, stack_string& debugText) const override;
#endif // DEBUG_MODULAR_BEHAVIOR_TREE

  // ~Action (or Decorator or Composite).

private:
  // Only for Composite nodes.
  // This function determines how the Node will handle an Event.
  // A specific implementation for Composite nodes is required because we have to specify how the children will handle the event.
  virtual void HandleEvent(const EventContext& context, const Event& event) override;
  // Node data - member variables if required.
};
`

```

##
Node Data

As described on the
[previous page](../Behavior%20Trees.md)
, Behavior Trees maintain both Configuration and Runtime Data.

-
Configuration Data is stored as member data of the node's class.

-
Runtime Data is stored in the
*
RuntimeData
*
 struct. Every node must have a
*
RuntimeData
*
 struct defined regardless of whether it is used or not; the struct can hence even be left empty. If not empty, the struct:

-

-
Must be initialized in the
*
OnInitialize
*
 function of the node.

-
Should be cleared in the
*
OnTerminate
*
 function of the node.

-
Should be updated in the
*
Update
*
 function of the node.

-
Can be accessed by calling the
*
GetRuntimeData(context)
*
 function.

```

`
// Simplified version of the Timeout node to be used as an example.
class Timeout: public BehaviorTree::Action
{
  typedef BehaviorTree::Action BaseClass;
public:
  // It's mandatory to have one although it may be empty.
  // Runtime node data.
  struct RuntimeData
  {
    Timer timer;
  };

  Timeout()
    : m_duration(0.0f)
  {
  }

  virtual void OnInitialize(const UpdateContext& context) override
  {
    RuntimeData& runtimeData = GetRuntimeData<RuntimeData>(context);
    runtimeData.timer.Reset(m_duration);
  }

  virtual Status Update(const UpdateContext& context) override
  {
    RuntimeData& runtimeData = GetRuntimeData<RuntimeData>(context);
    return runtimeData.timer.Elapsed() ? Failure : Running;
  }

  // ...
private:
  // Configuration data.
  // While editing, we set how much the timer should last.
  float m_duration;
};
`

```

##
Implementation

##
Node Execution

The following functions are executed in different circumstances while a Behavior Tree node is active.

```

`
// MyNewActionNode.cpp
void MyNewActionNode::OnInitialize(const BehaviorTree::UpdateContext& context)
{
  BaseClass::OnInitialize(context);
  // Specific OnInitializenode code.
}

void MyNewActionNode::OnTerminate(const BehaviorTree::UpdateContext& context)
{
  // Specific OnTerminate node code.
  BaseClass::OnTerminate(context);
}

BehaviorTree::Status MyNewActionNode::Update(const BehaviorTree::UpdateContext& context)
{
  // Do your work.
  // Return
  //   Success if you finished your work successfully.
  //  Failure if you finished your work unsuccessfully.
  //   Running if you didn't finish your work yet and execution will last more than one frame.
}

`

```

All nodes also require a
*
HandleEvent
*
 function.

Actions and Decorators have a default implementation for this function; this is because Action nodes don't have children, while Decorators only have one, making implementations trivial in this case.

Composite nodes, however, may have multiple children that can be active in different situations, and hence require a specific implementation for the
*
HandleEvent
*
 function. These Composite nodes need to know how to handle a event and how to propagate it to the children.

```

`
// (Simplified) Handle event implementation for a Sequence.
void Sequence::HandleEvent(const EventContext& context, const Event& event)
{
  // Only propagate the event to the currently active child.
  RuntimeData& runtimeData = GetRuntimeData<RuntimeData>(context);
  m_children[runtimeData.currentChildIndex]->SendEvent(context, event);
}
`

```

##
Utility Functions

##
LoadFromXml

Since Behavior Trees on CRYENGINE are described in XML, specific functions need to be implemented in order to load and store them from disk.

For example, this is what a simplified form of the
*
LoadFromXml
*
 function of the
*
SendEvent
*
 action node looks like. Since
*
LoadFromXml
*
 is executed when the Behavior Tree is loaded from a file, this function is mandatory.

```

`
// Simplified LoadFromXml of the SendEvent action node.
BehaviorTree::LoadResult MyNewActionNode::LoadFromXml(const XmlNodeRef& xml, struct BehaviorTree::LoadContext& context)
{
  // Always.
   IF_UNLIKELY (BaseClass::LoadFromXml(node, context) == LoadFailure)
  {
    return LoadFailure;
  }

  // Specific LoadFromXml node code.
//Get the name attribute from XML and initialize the m_eventToSend data member.
  const stack_string eventName = xml->getAttr("name");
  m_eventToSend = Event(eventName);
  return LoadSuccess;
}
`

```

Find more information on reading and writing XML with CRYNENGINE
[here](http://docs.cryengine.com/x/gZzGAQ)
.

##
Errors

Errors in the Saving/Loading of XML files can be reported by using the Error reporter, and by calling
*
BehaviorTree: ErrorReporter
*
 for pre-defined error messages.

```

`
string BehaviorTree::ErrorReporter::ErrorMessageMissingOrEmptyAttribute(const string& tag, const string& fieldMissing)

string BehaviorTree::ErrorReporter::ErrorMessageInvalidAttribute(const string& tag, const string& invalidField, const string& providedInvalidValue, const string& reason)

string BehaviorTree::ErrorReporter::ErrorMessageTooManyChildren(const string& tag, const int currentChildCount, const int maxSupportedChildren)
`

```

These messages can be used as follows:

```

`
// Simplified LoadFromXml of the SendEvent action node with error reporting.
BehaviorTree::LoadResult MyNewActionNode::LoadFromXml(const XmlNodeRef& xml, struct BehaviorTree::LoadContext& context)
{
  // Always
   IF_UNLIKELY (BaseClass::LoadFromXml(node, context) == LoadFailure)
  {
    return LoadFailure;
  }
  // Specific LoadFromXml node code.
// Check if XML contains an attribute 'name'.
  if (!xml->haveAttr("name"))
  {
    // Use error reported.
    ErrorReporter(*this, context).LogError(ErrorReporter::ErrorMessageMissingOrEmptyAttribute("SendEvent","name"));
    return LoadFailure;
  }

  const stack_string eventName = xml->getAttr("name");
  m_eventToSend = Event(eventName);
  return LoadSuccess;
}
`

```

##
CreateXmlDescription

Here is a simplified form of the
*
CreateXmlDescription
*
 function for the same node. As opposed to the
*
LoadFromXml
*
 function,
*
CreateXmlDescriptionis
*
 optional;  it is required only when we want to use a node in the Behavior Tree Editor.

*
CreateXmlDescription
*
is executed when the Tree is saved and written to a file.

```

`
// Simplified CreateXmlDescription of the SendEvent action node.
#ifdef USING_BEHAVIOR_TREE_XML_DESCRIPTION_CREATION
virtual XmlNodeRef CreateXmlDescription() override
{
 XmlNodeRef xml = BaseClass::CreateXmlDescription();
 xml->setTag("SendEvent");
 xml->setAttr("name", m_eventToSend.GetName());
 return xml;
}
#endif // USING_BEHAVIOR_TREE_XML_DESCRIPTION_CREATION
`

```

##
Serialize

Behavior Tree nodes use the Yasli library for serialization, so they require a Serialize function to be implemented. Serializing of nodes works in the same way as it does in other modules.

More information on CRYENGINE's
[Serialization Library](../../Filesystem_/Serializing%20JSON%20%26%20XML.md)
 can be found here.

```

`
#ifdef USING_BEHAVIOR_TREE_SERIALIZATION
virtual void MyNewActionNode::Serialize(Serialization::IArchive& archive)
{
  // Specific Serialize node code.
  archive(m_float, "float", "^Float");
  //...
  BaseClass::Serialize(archive);
}
#endif // USING_BEHAVIOR_TREE_SERIALIZATION
`

```

##
Data Through Context

It is sometimes necessary to have access to Behavior Tree data when serializing a node. This can be achieved through
 the
*
archive.context
*
property of the Archive.

```

`
#ifdef USING_BEHAVIOR_TREE_SERIALIZATION
virtual void MyNewActionNode::Serialize(Serialization::IArchive& archive)
{
  // Get some data through archive context.
  const BehaviorTree::Timestamps* timestamps = archive.context<BehaviorTree::Timestamps>();
  const Variables::Declarations* variablesDeclaration = archive.context<Variables::Declarations>();
  const Variables::EventsDeclaration* eventsDeclaration = archive.context<Variables::EventsDeclaration>();
  //...
  BaseClass::Serialize(archive);
}
#endif // USING_BEHAVIOR_TREE_SERIALIZATION
`

```

##
Errors

Errors in the Serialization process can be reported by calling
*
archive.error
*
 and using pre-defined errors messages in
*
SerializationUtils:Messages
*
.

```

`
// When the node child is empty.
string SerializationUtils::MessagesErrorEmptyHierachy(const string& childType)

// When the field is empty.
string SerializationUtils::MessagesErrorEmptyValue(const string& fieldName)

// When the field with the same value is duplicated.
string SerializationUtils::MessagesErrorDuplicatedValue(const string& fieldName, const string& duplicatedValue)

// When the field has an invalid value. A reason must be specified.
string SerializationUtils::MessagesErrorInvalidValueWithReason(const string& fieldName, const string& providedInvalidValue, const string& reason)
`

```

These messages can be used as follows:

```

`
#ifdef USING_BEHAVIOR_TREE_SERIALIZATION
virtual void MyNewActionNode::Serialize(Serialization::IArchive& archive)
{
  // Specific Serialize node code
  archive(m_positiveFloat, "positiveFloat", "^Positive Float");
  archive.doc("The money the Agent has");
  if (m_positiveFloat < 0)
  {
    archive.error(m_positiveFloat , SerializationUtils::Messages::ErrorInvalidValueWithReason("Positive Float", ToString(m_positiveFloat ), "Value must be greater or equals 0"));
  }
  //...
  BaseClass::Serialize(archive);
}
#endif // USING_BEHAVIOR_TREE_SERIALIZATION
`

```

##
GetCustomDebugText

The
*
GetCustomDebugText
*
 function has an output string that stores what is to be displayed on screen while debugging a Behavior Tree. For example, the following piece of code belongs to the
*
SendTransitionSignal
*
 Action node.

Real-time debugging is enabled via the Behavior Tree Editor's
[Debug Menu](../../../Manual/Editor%20Tools/Behavior%20Tree%20Editor/Behavior%20Tree%20Editor%20Window.md)
.

```

`
// SendTransitionSignal DebugCustomText
#ifdef DEBUG_MODULAR_BEHAVIOR_TREE
// ! Information to be shown in the screen when Debug Tree (or cvar ai_ModularBehaviorTreeDebugTree) is enabled.
virtual void GetCustomDebugText(const UpdateContext& updateContext, stack_string& debugText) const override
{
  debugText = m_signalName;
  // The following is a custom line added to illustrate usage of the GetCustomDebugText function.
  // debugText = "Smile! I am taking a picture";
}
#endif // DEBUG_MODULAR_BEHAVIOR_TREE
`

```

In-game, the above code will create the following debug text where the
*
SendTransitionSignal
*
 node displays the value of
*
m_signalName,
*
 which is
*
GoTo_Combat.
*

![Image](https://www.cryengine.com/docs/static/attachments/44965773)

*
debugText=m_signalName
*

When the
*
debugText ="Smile! I am taking a picture"
*
line is used in the above code, the
*
SendTransitionSignal
*
 node displays the custom debug text as shown.

![Image](https://www.cryengine.com/docs/static/attachments/44965774)

*
debugText=Smile! I am taking a picture
*

##
Use Debug Log

Messages can be written to the Behavior Tree log by accessing the
*
UpdateContext
*
 parameter, from any of the core execution functions (
*
OnInitialize, Update
*
 and
*
OnTerminate
*
) described in the
[Custom Nodes](Custom%20Nodes%20in%20C%2B%2B.md)
 documentation. This will appear as folows:

```

`
Status Update(const UpdateContext& context)
{
  context.behaviorLog.AddMessage("Hello World");

  // Some other logic.
}
`

```

The above code writes the
*
Hello World
*
 message to the Debug Log every time the node executes the

*
Update
*

function. During the execution of your game, this message will be displayed on screen as shown below if the
**
Debug → Show Log
**
option has been enabled from the Behavior Tree Editor main menu.

![Image](https://www.cryengine.com/docs/static/attachments/44958422)

*
Hello World
*

##
Registering Nodes

Created nodes need to be registered before they can be used in a Behavior Tree.

This is done via the
**
REGISTER_BEHAVIOR_TREE_NODE_WITH_SERIALIZATION(1, 2, 3, 4)
**
macro where:

-
**
1
**
 corresponds to the Behavior Tree manager (accessed through
*
gEnv
*
 or
*
gAIEnv);
*

-
**
2
**
 corresponds to the class of the new node that needs to be added;

-
**
3
**
 refers to the path of the node in the menu;

-
**
4
**
 corresponds to the color of the node.
It is recommended to create a function to register all custom nodes as follows:

```

`
// From your Game code, you need to call this function
void RegisterBehaviorTreeNodes_Custom()
{
  BehaviorTree::IBehaviorTreeManager& manager = gEnv->pAISystem->GetIBehaviorTreeManager();

  CRY_ASSERT(manager);

  const char* COLOR_GAME = "ff00ff";
  REGISTER_BEHAVIOR_TREE_NODE_WITH_SERIALIZATION(manager, MyNewActionNode, "Game\\Custom\\Actions", COLOR_GAME );
  REGISTER_BEHAVIOR_TREE_NODE_WITH_SERIALIZATION(manager, MyNewDecoratorNode, "Game\\Custom\\Decorators", COLOR_GAME );
  REGISTER_BEHAVIOR_TREE_NODE_WITH_SERIALIZATION(manager, MyNewSpecialNode, "Game\\Other", COLOR_GAME );
  //...
}
`

```

##
Table of Contents

[The Base Class](#the-base-class)
[The Interface](#the-interface)
[Node Data](#node-data)
[Implementation](#implementation)
[Use Debug Log](#use-debug-log)
[Registering Nodes](#registering-nodes)
