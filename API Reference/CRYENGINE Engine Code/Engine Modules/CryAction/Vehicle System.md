# Vehicle System

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/23306516
- Page ID: 23306516
- Breadcrumb: CRYENGINE Engine Code > Engine Modules > CryAction > Vehicle System
- Parent: CryAction

## Content

##
Overview

The Vehicle System is implemented in CryAction (the interface between Engine and Game), Game, and Lua.

##
Scripts

The following Lua files are stored in the
`
Scripts/Entities/Vehicles
`
 directory.

**
Lua file
**

 |
**
Description
**

 |

**
VehicleBase.lua
**

 |
Implements several standard vehicle script functions which are mostly used to interact with other game systems.

 |

**
VehicleBaseAI.lua
**

 |
Integration with the AI System.

 |

**
VehiclePool.lua
**

 |
Merges all the standard vehicle script functions to the vehicle script table.

 |

**
VehicleSystem.lua
**

 |
Parses all the vehicle class implementation and store them inside of a script table.

 |

Every vehicle class is defined inside its corresponding XML file. Vehicle class XML files should be stored in the
`
Scripts/Entities/Vehicles/Implementations/Xml
`
 directory.

##
Vehicle interfaces

The following interfaces represent the major code components of a vehicle:

-
IVehicleAnimation

-
IVehicleClient

-
IVehicleComponent

-
IVehicleHelper

-
IVehicleSeat
With the exception of IVehicleClient, all these interfaces are implemented in CryAction. The IVehicleClient interface is implemented in the GameDLL as it defines the game-specific ways for the player on the client to handle the vehicles.

##
CVehicleSystem

The CVehicleSystem singleton class keeps registrations of all the available Vehicle Objects along with all the different vehicle classes.

##
Vehicle Object Factories

The following object factories can be used to extend the functionality of vehicles.

-
IVehicleAction

-
IVehicleDamageBehavior

-
IVehicleMovement

-
IVehiclePart

-
IVehicleSeatAction

-
IVehicleView
Except for IVehicleMovement, all these interface derive from IVehicleObject.

To register a new vehicle object factory, we can use the following macro:

```

`
IVehicleSystem* pVehicleSystem = pFramework->GetIVehicleSystem();

#define REGISTER_VEHICLEOBJECT(name, obj) \
REGISTER_FACTORY((IVehicleSystem*)pVehicleSystem, name, obj, false); \
obj::m_objectId = pVehicleSystem->AssignVehicleObjectId();

`

```

##
Vehicle classes

A vehicle class is defined in an XML file. The vehicle system will parse all the .xml files stored in this directory. The content of the XML file will instruct which vehicle objects will be required by this vehicle class.

More information are available on the structure of the vehicle class XML files.

During initialization of the Game Framework (CryAction), CVehicleSystem::RegisterVehicles() is called. This function will search for all the XML files at this path:
`
Game\Scripts\Entities\Vehicles\Implementations\Xml
`
.

A new CVehicle instance is create by the vehicle system each time a vehicle is spawned by the Entity System.

##
Vehicle Client

The Vehicle Client is a singleton class derived from the IVehicleClient interface and is usually implemented inside the GameDLL. It is required to handle game specific functionality like mapping action maps to vehicle features and also high-level handling of player entering/exiting seats. Gamepad actions are received with the IVehicleClient::OnAction() function. Adding support for new input controllers can be done within this class.

A default implementation is located at this path:
`
Code\Game\GameDll\VehicleClient.cpp
`

##
CVehicle Initialization

CVehicle::Init() will perform the following tasks:

-
Initializes all the vehicle components.

-
Initializes all the vehicle parts.

-
Initializes all the vehicle helpers.

-
Initialize all the request particle effects.

-
Initializes all the vehicle animations.

-
Initializes the vehicle movement.

-
Initializes all the vehicle seats.

-
Sets the vehicle paint.

-
Initializes all the vehicle actions.

-
Initializes the vehicle damages, including the damage behaviors.

##
Vehicle Seat

The vehicle seat class is handling all interaction involving the actors which are seated in a vehicle. Each seat can have multiple Seat Action that implements different gameplay feature applicable to the actor who used the seat.

##
Entering a vehicle

-
The vehicle physical entity is sent an awake action using the pe_action_awake structure.

-
In case that a dead actor currently occupy the seat, its body is being moved to the nearest area on the ground.

-
In case that an actor is already controlling this seat remotely, this remote passenger is unlinked.

-
The actor then holster his current item (if any are currently selected).

-
A target request to the starting point of the entering animation is sent to the AI object in order for the actor's body to stand at the exact position of the first frame of the entering animation (for an AI actor only).

-
The animation graph of the actor is being sent the input of the vehicle name and the seat number.

-
The network state of the vehicle is being set as having seated passengers.

-
The IVehicle::eVUS_PassengerIn update slot of the vehicle game object is being enabled.

##
Seat Actions

The seat actions provide ways to extend the functionality of the seats. The IVehicleSeatAction interface is used to implement new seat actions.

CryAction provides the following seat action implementations.

**
Name
**

 |
**
Class Name
**

 |
**
Description
**

 |

**
Lights
**

 |
CVehicleSeatActionLights

 |
Used to implements head-lights which can be turned on/off by the passenger.

 |

**
PassengerIK
**

 |
CVehicleSeatActionPassengerIK

 |
Allows IK movement from the actor to follow a pair of vehicle helpers.

 |

**
RotateTurret
**

 |
CVehicleSeatActionRotateTurret

 |
Used for turret rotation, for tanks or mounted machine gun.

 |

**
Sound
**

 |
CVehicleSeatActionSound

 |
Triggers a sound from an actions.

 |

**
SteeringWheel
**

 |
CVehicleSeatActionSteeringWheel

 |
Used to implement a steering wheel which rotates based on the movement controls.

 |

**
Weapons
**

 |
CVehicleSeatActionWeapons

 |
Used to add a vehicle weapon which are controlled by passenger.

 |

##
Damages to the passengers

The vehicle seat provides a way to shield the passenger from the damages passed from the game rules. The isPassengerShielded parameter can be used to disable any direct damages sent to the passenger until the moment when the vehicle itself is destroyed. The actor implementation needs to call IVehicleSeat::ProcessPassengerDamage() every time a hit is received in order to filter the damage in case the passenger is shielded.

##
Vehicle Damages

##
Hits

Any hit sent to a vehicle pass by the IVehicle::OnHit() function. Before the hit is processed by the vehicle, the classes registered as event listener with the IVehicle::RegisterVehicleEventListener() function will receive an event of type eVE_Hit.

The hit position and radius will be tested against all the Vehicle Component bounds. When this test is positive, the IVehicleComponent::OnHit() function is called to apply the hit to the component.

There is the v_goliathMode console variable which can be used in cheat mode to disable the effect of any hit, making the all vehicles invulnerable. Additionally, if the vehicle as a player driver who enabled his God Mode, the vehicle will be invulnerable as well.

##
Damage multipliers

The damage multipliers are used to balance different hit types to affect differently the multiple vehicle component. For example, a multiplier can be added to make a tank invulnerable to bullets by having a bullet multiplier set to 0.

##
Vehicle Components

Each Vehicle Components is responsible to determines if the hit will cause any damage to the vehicle. It the case that an appropriate damage multiplier has not been defined in the component, it will verify if the vehicle damages section as defined one instead.

##
Damage Behaviors

The Damage Behavior interface is used to implement new ways a vehicle react to damages. Explosions, flat tires or a sinking boat are all example of features which are implemented as damage behaviors.

**
Existing damage behaviors
**

The following Damage Behaviors are implemented inside CryAction:

DamageBehavior

 |
Description

 |
Parameters

 |

**
AISignal
**

 |
Sends a signal to the AI system.

 |
signalId: integer value used as the signal id.

 signalText: string used as parameter for the signal

 |

**
Destroy
**

 |
Will put the vehicle in the destroyed state, making it unusable.

 |
No parameter

 |

**
DetachPart
**

 |
Detach a vehicle part

 |
part: specify which vehicle part to detach

 |

**
Effect
**

 |
Spawns a particle effect.

 |
effect: name of the vehicle effect

 disableAfterExplosion: will stop the effect once the vehicle is destroyed

 |

**
Group
**

 |
Triggers a damage group

 |
name: name of the damage group

 |

**
Impulse
**

 |
Will request an impulse to be given on the vehicle.

 |
forceMin, forceMax: specify the range in which the impulse force will be determined from a random value

 direction: vector to specify the direction of the impulse

 momentum: vector to specify the direction of the impulse

 helper: vehicle helper used as the impulse location

 |

**
Indicator
**

 |
Used to have interaction with a damage indicator, most often on the dashboard.

 |
No Parameter

 |

**
MovementNotification
**

 |
Used to send a damage notification to the Vehicle Movement

 |
isSteering: used to limit to the steering any movement limitation coming from the damage

 isDamageAlwaysFull: used to force the notification to always report a complete damage (1.0) regardless of the damage ratio from the vehicle component

 |

**
Sink
**

 |
Will make a boat sink in the water by modifying the buoyancy parameters of the vehicle

 |
No parameters

 |

**
SpawnDebris
**

 |
Will automatically find in the damaged vehicle assets any part which are identified as potentially detachable

 |
No parameters

 |

##
Implementing a new damage behavior

**
C++ implementation
**

The IVehicleDamageBehavior interfaces needs to be used to implements a new damage behavior. As example, the following code sample can be used for the definition of a new damage behavior.

```

`
class CVehicleDamageBehavior
: public IVehicleDamageBehavior
{
IMPLEMENT_VEHICLEOBJECT
public:

CVehicleDamageBehavior () {}
virtual ~CVehicleDamageBehavior() {}

virtual bool Init(IVehicle* pVehicle, const SmartScriptTable &table);
virtual void Reset() {}
virtual void Release() { delete this; }
virtual void Serialize(TSerialize ser, unsigned aspects) {}
virtual void Update(const float deltaTime) {}

virtual void OnDamageEvent(EVehicleDamageBehaviorEvent event, const SVehicleDamageBehaviorEventParams& behaviorParams);
virtual void OnVehicleEvent(EVehicleEvent event, const SVehicleEventParams& params){}

virtual void GetMemoryStatistics(ICrySizer * s);
};

`

```

It is important to add the following line inside the C++ definition file:

```

`
DEFINE_VEHICLEOBJECT(CVehicleDamageBehavior);

`

```

To have the new behavior recognized by the vehicle system, it's recommended to use the REGISTER_VEHICLEOBJECT macro. This macro is defined inside
`
CryAction/VehicleSystem_FactoryRegistration.cpp
`
 and also
`
GameFactory.cpp
`
 in the GameDLL. The name string passed to this macro will then be used to identify the behavior when requesting new instances from the vehicle system.

**
Registering the new damage behavior
**

If the damage behavior needs to be requested from a XML based vehicle class, it's required to edit the vehicle definition file (
`
Game/Scripts/Entities/def_vehicle.xml
`
). Locate the section similar to the following extract:

```

`
<Array name="DamageBehaviors" elementName="DamageBehavior" extendable="1" id="idDamageBehaviors">
<Property name="class" type="string">
<Enum>
<Value>AISignal</Value>
...
</Enum>
</Property>

`

```

A new enum value needs to be added using the same name string previously passed to the REGISTER_VEHICLEOBJECT.

In order to be able to pass properties from the XML vehicle class, a new table should be added inside the
*
DamageBehaviors
*
 array definition. It's important that this table be specified as optional.

[Scripts](#scripts)
[Vehicle interfaces](#vehicle-interfaces)
[Vehicle Object Factories](#vehicle-object-factories)
[Vehicle classes](#vehicle-classes)
[Vehicle Client](#vehicle-client)
[Entering a vehicle](#entering-a-vehicle)
[Seat Actions](#seat-actions)
[Damages to the passengers](#damages-to-the-passengers)
[Hits](#hits)
[Damage multipliers](#damage-multipliers)
[Vehicle Components](#vehicle-components)
[Damage Behaviors](#damage-behaviors)
[Implementing a new damage behavior](#implementing-a-new-damage-behavior)
