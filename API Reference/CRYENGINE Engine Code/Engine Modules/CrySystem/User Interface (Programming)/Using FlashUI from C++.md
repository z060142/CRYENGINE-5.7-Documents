# Using FlashUI from C++

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/23306534
- Page ID: 23306534
- Breadcrumb: CRYENGINE Engine Code > Engine Modules > CrySystem > User Interface (Programming) > Using FlashUI from C++
- Parent: User Interface (Programming)

## Content

##
Overview

This section discusses how to use the Flash UI System within C++.

##
Access IFlashUI Interface

To get access to the
**
IFlashUI
**
 Interface from anywhere you can simply include the
**
IFlashUI.h
**
 header file and use the global
**
gEnv->pFlashUI
**
.

```

`
#include <IFlashUI.h>

`

```

Since the FlashUI is implemented as an extension, which could be disabled for some reason, it is always good choice to check this pointer.

```

`
if ( gEnv->pFlashUI )
{
  // ...
}

`

```

##
UIArguments and UIData

For easy argument passing between Flash and C++ we are using the type
**
TUIData
**
 as variable data and the struct
**
SUIArguments
**
 as a set of
**
TUIData
**
. Each function and event uses these types for passing data between Flash and C++.

##
TUIData

The
**
TUIData
**
 type is a
**
CConfigurableVariant
**
 with strict conversation.

Examples:

```

`
bool bOk;
TUIData data( 7 );
int iVal;
float fVal;
string sVal;
bOk = data.GetValueWithConversion( iVal ); //bOk = true; iVal = 7;
bOk = data.GetValueWithConversion( fVal ); //bOk = true; fVal = 7.f;
bOk = data.GetValueWithConversion( sVal ); //bOk = true; sVal = "7";

`

```

```

`
bool bOk;
TUIData data( 11.f );
int iVal;
float fVal;
string sVal;
bOk = data.GetValueWithConversion( iVal ); //bOk = true; iVal = 11;
bOk = data.GetValueWithConversion( fVal ); //bOk = true; fVal = 11.f;
bOk = data.GetValueWithConversion( sVal ); //bOk = true; sVal = "11";

`

```

```

`
bool bOk;
TUIData data( 11.3f );
int iVal;
float fVal;
string sVal;
bOk = data.GetValueWithConversion( iVal ); //bOk = false; iVal = undefined;
bOk = data.GetValueWithConversion( fVal ); //bOk = true; fVal = 11.3f;
bOk = data.GetValueWithConversion( sVal ); //bOk = true; sVal = "11.3";

`

```

```

`
bool bOk;
TUIData data( string("11") );
int iVal;
float fVal;
string sVal;
bOk = data.GetValueWithConversion( iVal ); //bOk = true; iVal = 11;
bOk = data.GetValueWithConversion( fVal ); //bOk = true; fVal = 11.f;
bOk = data.GetValueWithConversion( sVal ); //bOk = true; sVal = "11";

`

```

```

`
bool bOk;
TUIData data( string("11.5") );
int iVal;
float fVal;
string sVal;
bOk = data.GetValueWithConversion( iVal ); //bOk = false; iVal = undefined;
bOk = data.GetValueWithConversion( fVal ); //bOk = true; fVal = 11.5f;
bOk = data.GetValueWithConversion( sVal ); //bOk = true; sVal = "11.5";

`

```

```

`
bool bOk;
TUIData data( string("11.5 foo") );
int iVal;
float fVal;
string sVal;
bOk = data.GetValueWithConversion( iVal ); //bOk = false; iVal = undefined;
bOk = data.GetValueWithConversion( fVal ); //bOk = false; fVal = undefined;
bOk = data.GetValueWithConversion( sVal ); //bOk = true; sVal = "11.5 foo";

`

```

##
SUIArgument

The
**
SUIArgument
**
 struct is a collection of
**
TUIData
**
. It provides some basic functions to set/add/get data to this argument list. It also converts between separated strings (default delimiter is "|") and list of
**
TUIData
**
 and provides a function to access the values as a pointer to a
**
SFlashVarValue
**
 vector (Scaleform data type, for more information look into
**
IFlashPlayer.h
**
).

##
Example

```

`
// fill some arguments
SUIArguments args;
args.AddArgument( 12 );
args.AddArgument( 7.3f );
args.AddArgument( string("foo") );
args.AddArgument( string("12") );

// get arguments as stringlist
const char* stringlist = args.GetAsString(); // stringlist="12|7.3|foo|12";

// copy arguments from string list
SUIArguments args2;
args2.SetArguments( stringlist );

// get arguments
bool bOk;
int arg1;
float arg2;
float arg3;
float arg4;
bOk = args2.GetArg(0, arg1); // bOk = true; arg1 = 12;
bOk = args2.GetArg(1, arg2); // bOk = true; arg2 = 7.3f;
bOk = args2.GetArg(2, arg3); // bOk = false; arg3 = undefined;
bOk = args2.GetArg(3, arg4); // bOk = true; arg4 = 12;

// iterate thru arguments
for ( int i = 0; i < args2.GetArgCount(); ++i )
{
  TUIData arg = args2.GetArg( i );
  // ...
}

// change delimiter for string lists
args2.SetDelimiter(",");
const char* stringList2 = args2.GetAsString();//stringlist="12,7.3,foo,12";

`

```

##
UIElements

Each Flash asset that is defined in the xml can be accessed by the
**
IFlashUI
**
 interface. See also
[/docs/static/engines/cryengine-5/categories/23756813/pages/23306537](
UI Element
)
.

```

`
<UIElements name="HudElements">
  <UIElement name="HUD">
    <GFx file="HUD.gfx" layer="1">
      <Constraints>
        <Align mode="fullscreen" />
      </Constraints>
    </GFx>

    <functions>
      <function name="SetHealth" funcname="myHealthMc.mysubmc.setHealth">
        <param name="Health" desc="Players current health"/>
      </function>
    </functions>

    <events>
      <event name="OnButton1" fscommand="onMyButtonPressed">
        <param name="Arg1" desc="Some argument"/>
        <param name="Arg2" desc="Another argument"/>
      </event>
    </events>

    <variables>
      <variable name="SomeVariable" varname="someVariable"/>
      <variable name="TextField" varname="_root.myTextfield.text"/>
    </variables>

    <arrays>
      <array name="SomeArray" varname="_root.mc2.someArray"/>
    </arrays>

    <movieclips>
      <movieclip name="MovieClip1" instancename="_root.Mc1"/>
      <movieclip name="MovieClip2" instancename="_root.Mc1.subMc"/>
    </movieclips>

  </UIElement>
 </UIElements>

`

```

To have acces to the "HUD" UI element just use the
**
GetUIElement()
**
 function.

```

`
#include <IFlashUI.h>
// ...

if ( gEnv->pFlashUI )
{
  IUIElement* pHUD = gEnv->pFlashUI->GetUIElement( "HUD" );
  if ( pHUD )
  {
    // ...
  }
}

`

```

##
Variables and Arrays

To get or set a variable you can simply access them trough the
**
IUIElement
**
 interface.

Note that if you want to access a specific element, you will have to use the name, that is defined
 in the XML
 for this element and
**
not
**
 the real name in your flash asset.

```

`
pHUD->SetVar( "SomeVariable", 12 );
pHUD->SetVar( "TextField", string("Some text") );

// iVar can be undefined if "SomeVariable" has no valid integer (e.g. string)
int iVar = pHUD->GetVar<int>( "SomeVariable" );

// more safe you can check if TUIData is your expected type
TUIData text;
pHUD->GetVariable( "TextField", text );

// set array
SUIArguments myArray;
myArray.AddArgument( 12 );
myArray.AddArgument( 17 );
myArray.AddArgument( string("str") );
myArray.AddArgument( 23.f );
pHUD->SetArray( "SomeArray", myArray );

// get array
SUIArguments myArray;
pHUD->GetArray( "SomeArray", myArray );

`

```

##
MovieClips

To get access to your defined MovieClips you can use the
**
GetMovieClip()
**
 function:

```

`
IFlashVariableObject* pMC = pHUD->GetMovieClip( "MovieClip1" );
if ( pMC )
{
  // ...
}

`

```

The returned
**
IFlashVariableObject
**
 can be used to modify this MovieClip. Check
**
IFlashPlayer.h
**
 for more information.

##
Functions

To call a defined function you can simply use
**
CallFunction()
**
 method. You can pass
**
SUIArguments
**
 as arguments and optionally a
**
TUIData
**
 pointer as a return value.

```

`
SUIArguments args;
args.AddArgument( 80.f );

TUIData res;

pHUD->CallFunction( "SetHealth", args, &res ); // You can use the SUIArguments::Create<T>(...) if you only have just one argument you want to pass
`

```

##
Events

To receive events from flash you have to create an
**
IUIElementEventListener
**
, and register to your
**
IUIElement
**
.

**
Callbacks:
**

-
**
OnUIEvent
**
 - This is called, if an event (fscommand) is triggered from flash. This function is only called if the event is
**
found
**
 in the
[/docs/static/engines/cryengine-3/categories/1638401/pages/15011348](
UI Element
)
 XML file.

-
**
OnUIEventEx
**
- This is called, if an event is triggered from flash and it is not found in the
[/docs/static/engines/cryengine-3/categories/1638401/pages/15011348](
UI Element
)
 XML file.

-
**
OnInit -
**
This is called, when a new Flash
[/docs/static/engines/cryengine-3/categories/1638401/pages/15011348](
UI Element
)
 has been initialized.

-
**
OnSetVisible -
**
This is called, when an
[/docs/static/engines/cryengine-3/categories/1638401/pages/15011348](
UI Element
)
 changes visibility.

-
**
OnInstanceCreated -
**
 This is called, when a new
**
instance
**
 of an
[/docs/static/engines/cryengine-3/categories/1638401/pages/15011348](
UI Element
)
 has been created. A instance has an instance ID greater than zero ( the base instance of each element is 0).

-
**
OnInstanceDestroyed -
**
This is called, when an
**
instance
**
 of an
[/docs/static/engines/cryengine-3/categories/1638401/pages/15011348](
UI Element
)
 has been destroyed.

```

`
class CHUDEventListener : public IUIElementEventListener
{
public:
  virtual void OnUIEvent( const SUIEventDesc& event, const SUIArguments& args )
  {
    if ( event.sDisplayName == "OnButton1" )
    {
      int arg1;
      int arg2;
      if ( args.GetArg( 0, arg1) && args.GetArg( 1, arg2 ) )
      {
        // do somthing
      }
      else
      {
        // args don't are interger or doesn't exist
      }
    }
    else
    {
      // event is not "OnButton1" event
    }
  }
};

// ...

// Registering the listener
CHUDEventListener eventListener;

if ( gEnv->pFlashUI )
{
  IUIElement* pHUD = gEnv->pFlashUI->GetUIElement( "HUD" );
  if ( pHUD )
  {
    pHUD->AddEventListener( &eventListener );

  }
}

`

```

The OnUIEvent callback function will
**
only
**
 handle events, which are defined in the UI Element XML file. There is also a OnUIEventEx callback function, which will trigger for other fscommands coming from your UI element.

##
Instances

If you want to have more than one instance per Flash Element, you can just call
**
GetInstance()
**
 to you
**
UIElement
**
. You have to pass an instance ID. If no instance of the element exists with this id, it will be automatically created.

```

`
if ( gEnv->pFlashUI )
{
  IUIElement* pHUDInstance0 = gEnv->pFlashUI->GetUIElement( "HUD" );
  if ( pHUDInstance0 )
  {
    IUIElement* pHUDInstance1 = pHUDInstance0->GetInstance( 1 );
    IUIElement* pHUDInstance2 = pHUDInstance0->GetInstance( 2 );
    // ...
  }
}

`

```

To iterate through all created instances you can use the
**
IUIElementIteratorPtr
**
.

```

`
IUIElement* pHUD = gEnv->pFlashUI->GetUIElement( "HUD" );
if ( pHUD )
{
  IUIElementIteratorPtr instances = pHUD->GetInstances();
  while ( IUIElement* pInstance = instances->Next() )
  {
    int instanceID = pInstance->GetInstanceID();
    // ...
  }
}

`

```

##
Raw IFlashPlayer Interface

You can always access the
**
IFlashPlayer
**
 of any
**
IUIElement
**
 by using the
**
GetFlashPlayer()
**
 function. For more information look into
**
IFlashPlayer.h
**
.

```

`
IFlashPlayer* pFlashPlayer = pHUD->GetFlashPlayer();

`

```

Once you access the
**
IFlashPlayer
**
 Interface, you will have direct access to IFlashVariableObjects in Flash. Since you can create IFlashVariableObjects through the
**
IFlashPlayer
**
 Interface, you
**
must
**
 make sure that you call
**
Release
**
 on them, once you don't need them anymore. This is also very important, if you unload any
**
IUIElement
**
. Since unloading can be done through code or
[/docs/static/engines/cryengine-5/categories/23756813/pages/23306550](
Flowgraph (MANUAL)
)
, you should implement the
**
IUIElementEventListener
**
 interface on your custom HUD code and Release all created and not yet released IFlashVariableObjects within the
**
OnUnload()
**
 callback.

##
UIActions

Each
[/docs/static/engines/cryengine-3/categories/1638401/pages/15011350](
UIAction
)
 (
[/docs/static/engines/cryengine-3/categories/1638401/pages/1605670](
Flowgraph
)
) can be accessed and executed via code. To start an action you have to use the
**
IUIActionManager.
**

##
UIActionManager

The
**
IUIActionManager
**
 provides simple functions to start/stop or disable
**
IUIActions
**
.

```

`
if ( gEnv->pFlashUI )
{
  // The Name "MyAction" is the name of the UIAction FlowGraph
  IUIAction* pAction = gEnv->pFlashUI->GetUIAction( "MyAction" );
  IUIActionManager* pActionManager = gEnv->pFlashUI->GetUIActionManager();
  pActionManager->StartAction( pAction );
}

`

```

##
UIActionListener

You can create an
**
IUIActionListener to listen to actions events
**
.

```

`
class CUIActionListener: public IUIActionListener
{
public:
  virtual void OnStart( IUIAction* pAction )
  {
    CryLogAlways( "Action %s was started", pAction->GetName() );
  }

  virtual void OnEnd( IUIAction* pAction )
  {
    CryLogAlways( "Action %s is done", pAction->GetName() );
  }

};

// ...
if ( gEnv->pFlashUI )
{
  IUIActionManager* pActionManager = gEnv->pFlashUI->GetUIActionManager();

  CUIActionListener* pActionListener = new CUIActionListener();
  pActionManager->AddListener( pActionListener );
}

`

```

[#access-iflashui-interface](
Access IFlashUI Interface
)
[#uiarguments-and-uidata](
UIArguments and UIData
)
[#uielements](
UIElements
)
[#uiactions](
UIActions
)
