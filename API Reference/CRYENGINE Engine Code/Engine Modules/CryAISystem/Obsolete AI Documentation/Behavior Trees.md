# Behavior Trees

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/23306469
- Page ID: 23306469
- Breadcrumb: CRYENGINE Engine Code > Engine Modules > CryAISystem > Obsolete AI Documentation > Behavior Trees
- Parent: Obsolete AI Documentation

## Content

This article is for CRYENGINE 3.4 or earlier. The Behavior Selection Tree and old-style behavior scripts was deprecated in favor of the Modular Behavior Tree in CRYENGINE 3.5 and beyond.

Since CryENGINE 3.3.0 Behavior Trees are obsolete and have been replaced by
[Behavior Selection Trees](Obsolete%20AI%20Scripting%20Documentation/Behavior%20Selection%20Trees.md)
.

Any class can utilize a behavior/decision tree. The benefits of using a behavior tree are:

-
Single storage place for knowledge - anything that needs to be considered when making a decision is located in a single place where it can be easily modified and maintained.

-
Single location for decision making - the tree is easily accessible and easy to follow.

-
Tactics offer up a way to organize cooperate interactions between multiple (same or different) trees. This includes the AI!

-
Global knowledge can be shared between all tree users. This includes the AI!

##
Table of Contents

-
[#Setting up the Behavior Tree](Behavior%20Trees.md#BehaviorTrees-SettinguptheBehaviorTree)

-
[#Advance Topics](Behavior%20Trees.md#BehaviorTrees-AdvanceTopics)

-
[#Implementing a Behavior Tree User Class](Behavior%20Trees.md#BehaviorTrees-ImplementingaBehaviorTreeUserClass)

-
[#Other Discussion Points](Behavior%20Trees.md#BehaviorTrees-OtherDiscussionPoints)

##
Setting up the Behavior Tree

You will need to accomplish these steps to set up a new Behavior Tree:

-
Create a new Profile.

-
Create a new Activation Condition chart.

-
Create a new Tree chart.

##
Create a new Profile

*
(Location: Game\Scripts\BehaviorTree\Profiles)
*

A Profile is an Xml file that connects the Tree chart to an arbitrary list of Activation Condition charts. You refer to this profile by name in code when you want to start using the tree in your class.

A typical profile looks as followed:

```

`
<BTProfile tree="TestClass">
  <ActivationConditions>
    <ActivationCondition name="TestClass" table="TestClass" doReset="0" />
  </ActivationConditions>
</BTProfile>
`

```

**
BTProfile:
**

**
tree
**
 - This attribute defines which Tree chart should be loaded and used.

-
**
ActivationConditions
**
 - Child elements with the name
*
ActivationCondition
*
 are used to define a new Activation Condition chart to use. You can define as many of these as you wish.

-
**
ActivationCondition : name
**
 - This attribute defines the name of the Activation Condition chart which should be loaded and used.

-
**
ActivationCondition : table
**
 - This attribute defines the name to use for the Lua sub-table to access this chart's knowledge.

-
**
ActivationCondition : doReset
**
 - Optional; if specified with a TRUE value, it means if the user already has this knowledge chart loaded when this profile is switched over to, the information contained will be reset back to its initial state. A FALSE value (or if you don't define this attribute) means that information will be retained when the profile is switched over.
Note that the order of the Activation Condition definitions in the Profile Xml sheet is important! Input is parsed from top-down, so tables along the bottom get the input signals sent to them last.

##
Create a new Activation Condition chart

*
(Location: Game\Scripts\BehaviorTree\ActivationConditions)
*

Activation Condition charts are Excel spreadsheets. The name of the file should match the name referred to by the Profile Xml. There are two important sheets to define in your Activation Conditions chart:

-
**
Values
**
 - This chart defines the default values for the knowledge table. It's a place where you can define values with which to fill the knowledge table.

-
The
*
Name
*
 column defines the name of the variable for the knowledge table.

-
The
*
Starting Value
*
 column defines the initial value of the variable.

-
The
*
Notes
*
 column is an optional place where you can write a note about the variable, like how it is used.
[TestClassAC.xls](/docs/static/attachments/23461222)
*
**
Signals
**
 - This chart defines the signals (input code) to alter the knowledge table. When a signal is sent to the tree, it is looked up in this sheet. You are able to modify the knowledge table as needed per signal, utilizing optional data that may have been passed along with the signal call.

-

-
The
*
Signal
*
 column defines the name of the signal that is sent from code to trigger this action. See the
[#Tree Input](Behavior%20Trees.md#BehaviorTrees-TreeInput)
 section below for more details.

-
The
*
Parent
*
 column is an optional control. You can specify the name of a signal which should also be executed along with this one.

-
The
*
Values Change
*
 column defines the Lua chunk of code to execute when this signal is called. See
[#Lua Language Rules](Behavior%20Trees.md#BehaviorTrees-LuaLanguageRules)
 section below for more details.
[TestClassAC.xls](/docs/static/attachments/23461222)

##
Create a new Table chart

*
(Location: Game\Scripts\BehaviorTree\Trees)
*

Tree charts are Excel spreadsheets. The name of the file should match the name referred to by the Profile Xml. There are two important sheets to define in your Tree chart:

-
**
DAG
**
 - This is where you define the directed acyclic graph for the tree. This tree is represented as a top-down flow, with child elements expanding to the right. Parent nodes are represented as merged cells.
[TestClassTree.xls](/docs/static/attachments/23461224)

**
Node properties
**
 - This is the tree implementation, where you define the outputs of the nodes and the conditional statements for traversing the tree. Each line represents a node in the tree, parent or child.

-

-
The
*
Path
*
 column represents the parent path of this node. Each traversal step is represented with a dot (.). So if the path is Root -> Parent -> Child, the parent path is "Root.Parent".

-
The
*
Name
*
 column represents the child name of this node. So if the path is Root -> Parent -> Child, the child name is "Child".

-
The
*
Impulse
*
 column is an optional way to jump through the tree. If this node passes its condition, the tree traversal will jump to the location defined by the path in this column.

-
The
*
Child selection
*
 column represents how the children of this node are traversed. For now, the only valid option is "Prioritized".

-
The
*
SubTactic
*
 column represents which SubTactic must be ran (and passed) for traversal of the tree to continue in this branch.

-
The
*
Signal
*
 column represents the output signal sent from the tree when the node traverses pass this. See the
[#Tree Output](Behavior%20Trees.md#BehaviorTrees-TreeOutput)
 section below for more details.

-
The
*
Activation Conditions
*
 column defines the Lua chunk of code to execute when this node is traversed to. If the statement returns true, traversal is allowed to continue. If this node is a child node, the tree selects it as the new leaf node and stops traversing. See
[#Lua Language Rules](Behavior%20Trees.md#BehaviorTrees-LuaLanguageRules)
 section below for more details.
[TestClassTree.xls](/docs/static/attachments/23461224)

##
Advance Topics

##
Tactics

*
(Location: Game\Scripts\BehaviorTree\Tactics.xml)
*

Tactics are a way to coordinate two or more trees by restricting certain parts of the tree from being traversed until enough candidates are ready to satisfy the tactic. The Tactics.xml defines all valid tactics. The sub-tactics of these definitions are then referenced throughout the trees where they are valid. There are two important sheets to define in your Tree chart:

-
**
Tactics
**
 - This is where you define all valid tactics that exist in the system and connect them to their sub-tactics.

-
The
*
Name
*
 column contains the name of the tactic.

-
The
*
Max tactic instances
*
 column defines the maximum number of instances that can be created for this tactic. A value of "max" means infinite. If a sub-tactic for this tactic is in use and another one wants to be started, it will not be permitted if this count exceeds the number of maximum instances.

-
The
*
Uses Group
*
 column states if the tactic can only be used within a Tactics Group or not. See
[#Tactics Group](Behavior%20Trees.md#BehaviorTrees-TacticsGroup)
 section below for more details.

-
The
*
Max group instances
*
 column defines the maximum number of instances that can be created for this tactic PER GROUP. This is ignored if the tactic does not use groups. A value of "max" means infinite. If a sub-tactic for this tactic is in use by a group and another one wants to be started by that same group, it will not be permitted if this count exceeds the number of maximum instances.

-
The
*
Behavior when less than Min actors
*
 column defines how the tactic should be handled when there are no longer enough uses to participate in the tactic. The only valid option for this now is
*
"DESTROY_TACTIC"
*
.

-
The
*
SubTactic
*
 column defines the sub-tactic associated with this tactic. For multiple sub-tactics, create a new blank row below and fill in only this column with the name of the next sub-tactic.
[Tactics.xls](/docs/static/attachments/23461226)

**
Requirements
**
 - This is where you define all valid sub-tactics and their requirements.

-

-
The
*
Name
*
 column contains the name of the sub-tactic.

-
The
*
Tree
*
 column defines which tree can be considered a user of this sub-tactic. The properties described in the next columns reflect on this tree. For multiple tree users, create a new blank row below and fill in the Tree name and the data for the next set of columns that reflect on that tree.

-
The
*
Min actors to start
*
 column defines how many actors must be candidates for this tactic before it can start.

-
The
*
Min actors to run
*
 column defines how many actors are needed to keep the tactic running. If too many drop out, the tactic will be stopped.

-
The
*
Max actors
*
 column defines how many actors at most can join in on the tactic. If more want to, they will be forced to try to create a new instance of the tactic.

-
The
*
Ordering Function
*
 is a Lua chunk of code executed to sort potential candidates. Two users (A and B) are passed in. A return value of TRUE means to rank A higher than B as a candidate for this tactic. The highest-ranking candidates will be selected, up to the Max count. See
[#Lua Language Rules](Behavior%20Trees.md#BehaviorTrees-LuaLanguageRules)
 section below for more details.
[Tactics.xls](/docs/static/attachments/23461226)

##
Tactics Group

Users can be placed inside a group by being given a unique Tactics Group Id. This can be any integer value you specify. When a user starts a sub-tactic, if that user is part of a Tactics Group, only other members of his group can join him in that sub-tactic. This is an optional method to isolate a common pool of potential candidates.

##
Global Activation Conditions

*
(Location: Game\Scripts\BehaviorTree\Globals.xml)
*

Global Activation Conditions are stored in a unique Activation Conditions Chart. This is a special knowledge table that is accessible and modifiable by any and all active Profile users. Code can also send signals straight to the Global table for quick changing of values. See
[#Lua Language Rules](Behavior%20Trees.md#BehaviorTrees-LuaLanguageRules)
 section for more details on how to access this knowledge table.

**
Values
**

[Globals.xls](/docs/static/attachments/23461225)
**
Signals
**

[Globals.xls](/docs/static/attachments/23461225)

##
Implementing a Behavior Tree User Class

Any class can load up and use a Behavior Tree by inheriting from the
*
IBSSProfileUser
*
 abstract base class. When you inherit from this, you can then load a behavior tree and connect it to the class via a unique Id returned.

##
IBSSProfileUser Interface

This ABC should be inherited by the class which will be responsible for handling input and output to the tree. The virtual functions are as followed:

-
**
GetBTUserName
**
 - Return a unique user name for this tree user. Used for debugging purposes.

-
**
GetBTUserTable
**
 - Return an IScriptTable* that can be easily accessed inside the Activation Conditions and Tree charts. See
[#Lua Language Rules](Behavior%20Trees.md#BehaviorTrees-LuaLanguageRules)
 section for more details.

-
**
GetBTUserBlackBoard
**
 - Return an IBlackBoard* that should be used to store information relating to the tree and its traversal. Useful for AI purposes.

-
**
CanBTUserTreeRun
**
 - Return TRUE if the tree is allowed to be ran. This is called when the knowledge table has changed and the tree needs to update. Returning FALSE here can stall the tree update.

-
**
OnBTUserEvent
**
 - Called when the tree has outputted a value. See the
[#Tree Output](Behavior%20Trees.md#BehaviorTrees-TreeOutput)
 section below for more details.

##
Linking to a Tree

To link the class to a tree, you should use the
**
InitNewUser
**
 function in the
*
IBSSProfileManager
*
 object returned from AISystem. Pass in the name of the Profile to load. A
**
TBSSProfileUserId
**
 value is returned which you should store. Use this in future calls to send input to the tree or perform other operations on it.

As part of your cleanup process, be sure to use the
**
RemoveUser
**
 function to delete the tree.

Other functions of interest:

-
**
SwitchUserProfile
**
 - Call to change which Profile the class should be using. This is a useful way to easily change to a new tree at run-time. A new UserId is returned.

-
**
ResetUser
**
 - Reset the tree and the knowledge tables to their initial state.

-
**
EnableUser
**
 - Turn the tree on/off completely on the user.

##
Tree Input

To send input to the Activation Condition charts, you should use the
**
SendUserInput
**
 function in the
*
IBSSProfileManager
*
 object returned from AISystem. You should pass along your unique
**
TBSSProfileUserId
**
 returned when you linked to the tree, described above. The name of the signal and optional data are passed along to all Activation Condition charts, from top to bottom as defined in the Profile Xml sheet.

##
Tree Output

When the tree has output to send back, it is sent through the
**
OnBTUserEvent
**
 function inherited from
*
IBSSProfileUser
*
. The arguments sent are as followed:

-
**
event
**
 - The event that was triggered. Valid values are:

-
**
eBTUE_OnNodeSignal
**
 - Sent when tree has come across a node signal (node was traversed through)

-
**
eBTUE_OnNewLeafNode
**
 - Sent when tree has traversed to a new leaf node (sent each frame until you allow the node change!)

-
**
eBTUE_OnDecisionMade
**
 - Sent when tree has made a decision (node change was approved)

-
**
pTree
**
 - The personal behavior tree object. Use it to accept node changes on new leaf nodes or interact with the tree as needed.

-
**
sSignal
**
 - The output signal from the tree.

-
**
pArgValue
**
 - Argument value that was sent along with the last input which caused the tree to update, resulting in this event being sent out.
When
**
eBTUE_OnNewLeafNode
**
 is received, the tree is informing you that a new leaf node has been hit. However, it is up to you to permit the tree to switch over to that leaf node i.e., make a decision. You can do this by calling the
**
AllowNodeChange
**
 function on the tree object sent in as a function argument. If you do not do this, the tree will continue to send out this event each frame. There are reasons you may want to stall a decision, for example to introduce a delay or to prevent constant state changes from happening due to an influx of new data. In any case, you will not receive
**
eBTUE_OnDecisionMade
**
 until you have allowed the node change to go through.

##
Example Class

Here is an example class that is loading our TestTree defined above and using it.

```

`
// Test behavior tree using class
class CBehaviorTreeTest : public IBSSProfileUser
{
public:
  CBehaviorTreeTest();
  virtual ~CBehaviorTreeTest();

  // Sent when action is processed
  void OnButtonState(bool bDown);
  void SetGlobalValue(bool bValue);

  // IBSSProfileUser
  bool GetBTUserName(string &sOut) const;
  bool CanBTUserTreeRun() const;
  void OnBTUserEvent(EBTUserEvents event, IPersonalBehaviorTree *pTree, const string& sData, const ScriptAnyValue* pArgValue = NULL);
  //~IBSSProfileUser

private:
  TBSSProfileUserId m_userId;
};
`

```

```

`
//////////////////////////////////////////////////////////////////////////
CBehaviorTreeTest::CBehaviorTreeTest()
: m_userId(g_uBTUserId_Invalid)
{
  // Link to tree and get the unique Id back
  IBSSProfileManager *pManager = gEnv->pAISystem->GetBSSProfileManager();
  if (pManager)
  {
    pManager->InitNewUser(this, "TestClass", m_userId);
  }

  CRY_ASSERT_MESSAGE(m_userId != g_uBTUserId_Invalid, "CBehaviorTreeTest failed to init with the \"TestClass\" BT profile");
}

//////////////////////////////////////////////////////////////////////////
CBehaviorTreeTest::~CBehaviorTreeTest()
{
  // Release the tree
  IBSSProfileManager *pManager = gEnv->pAISystem->GetBSSProfileManager();
  if (pManager && m_userId != g_uBTUserId_Invalid)
  {
    pManager->RemoveUser(m_userId);
    m_userId = g_uBTUserId_Invalid;
  }
}

//////////////////////////////////////////////////////////////////////////
void CBehaviorTreeTest::OnButtonState(bool bDown)
{
  IBSSProfileManager *pManager = gEnv->pAISystem->GetBSSProfileManager();
  if (pManager && m_userId != g_uBTUserId_Invalid)
  {
    // Send the input signal into our Activation Conditions chart.
    // The 'data' property will be set to the value of 'bDown'.
    pManager->SendUserInput(m_userId, "SetButtonState", bDown);
  }
}

//////////////////////////////////////////////////////////////////////////
void CBehaviorTreeTest::SetGlobalValue(bool bValue)
{
  IBSSProfileManager *pManager = gEnv->pAISystem->GetBSSProfileManager();
  if (pManager)
  {
    // Send a signal to the Global Activation Conditions chart.
    // The 'data' property will be set to the value of 'bValue'.
    pManager->SendGlobalSignal("SetTestValue", bValue);
  }
}

//////////////////////////////////////////////////////////////////////////
bool CBehaviorTreeTest::GetBTUserName(string &sOut) const
{
  // A good unique name for our tree.
  sOut = "CBehaviorTreeTest";
  return true;
}

//////////////////////////////////////////////////////////////////////////
bool CBehaviorTreeTest::CanBTUserTreeRun() const
{
  // Tree can always be ran!
  return true;
}

//////////////////////////////////////////////////////////////////////////
void CBehaviorTreeTest::OnBTUserEvent(EBTUserEvents event, IPersonalBehaviorTree *pTree, const string& sData, const ScriptAnyValue* pArgValue)
{
  switch (event)
  {
    // Sent when a parent node has been traversed which defined some signal data.
    case eBTUE_OnNodeSignal:
    {
      CryLogAlways("[CBehaviorTreeTest] Event=eBTUE_OnNodeSignal Data=%s", sData.c_str());
    }
    break;

    // Sent when a new leaf node has been hit.
    case eBTUE_OnNewLeafNode:
    {
      CryLogAlways("[CBehaviorTreeTest] Event=eBTUE_OnNewLeafNode Data=%s", sData.c_str());

      // Call to allow the tree to switch to this leaf node (make a decision).
      // NOTE: Decision won't be made until we call this! We could stall here for a moment!
      pTree->AllowNodeChange();
    }
    break;

    // Sent when the tree has made a new decision (new leaf node and change was allowed to be made).
    case eBTUE_OnDecisionMade:
    {
      CryLogAlways("[CBehaviorTreeTest] Decision Made! %s", sData.c_str());
    }
    break;

    default:
      CRY_ASSERT_MESSAGE(false, "CBehaviorTreeTest received unhandled user event");
      break;
  }
}
`

```

##
Other Discussion Points

##
Lua Language Rules

When dealing with the Lua code chunks present in the Activation Conditions or Tree charts, there are a few specific things you can reference in the Lua code.

-
**
g
**
 - This table can be used to access all global values defined in the Global Activation Conditions chart.

 (
*
g["SomeVariable"]
*
)

-
**
a
**
 - This table can be used to access the local values defined in the profile's Activation Conditions charts. Each condition table is stored as a child table in this with the name specified in the Profile Xml sheet.

(
*
a.TestValue["SomeVariable"]
*
)

-
**
userTbl
**
 - This table can be used to access the script table returned from code via the user's
**
GetBTUserTable
**
 function.

 (
*
userTbl:CallSomeFunc()
*
)
Within the Tactics Ordering Function code, there are a different set of a few specific things you can reference in the Lua code.

-
**
a
**
 - This table can be used to access the script table returned from code via the user's
**
GetBTUserTable
**
 function for User A of the tactic.

 (
*
a:CallSomeFunc()
*
)

-
**
b
**
 - This table can be used to access the script table returned from code via the user's
**
GetBTUserTable
**
 function for User B of the tactic.

 (
*
b:CallSomeFunc()
*
)
