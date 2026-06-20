# Elevator Entities

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/29796931
- Page ID: 29796931
- Breadcrumb: Editor Tools > Level Editor Tab > Create Object > Legacy Entities > Elevator Entities
- Parent: Legacy Entities

## Content

## Overview

The elevator entity simulates a moving platform. A switch is used to control the elevator object. By using the elevator entity you can define an object as an elevator to give the player access to different floors within a building.

The Elevator and ElevatorSwitch entities can be found in the **Create Object → Legacy Entities → Elevators** folder.![Image](https://www.cryengine.com/docs/static/attachments/56000537)

The Elevator can work together with the ElevatorSwitch, which acts as a call/go button:

- If the platform is not at the level of the switch, the elevator will come.
- If the platform is at the level of the switch, then when you press the switch, the elevator will go back to the destination floor.

### Elevator Properties

**Property** | **Description**
--- | ---
**Automatic** | When enabled, elevator will automatically return to initial floor, after reaching destination floor.
**Destination Floor** | Specifies the destination floor.
**FloorCount** | Specifies the number of floors.
**FloorHeight** | Specifies the distance between floors.
**InitialFloor** | Specifies the floor to start on.
**Model** | Specifies the model to use.
**SmartObjectClass** | Specifies the smart object class of the object.
**Acceleration** | Specifies how fast the elevator accelerates.
**Axis** | Specifies the axis of the elevator to move.
**Speed** | Specifies the speed to move.
**StopTIme** | Specifies how long the lift takes to stop.
**Sound Sound on Move** | Specifies which sound file would be played while the elevator is moving.
**Sound Sound on Start** | Specifies which sound file would be played when the elevator starts moving.
**Sound Sound on Stop** | Specifies which sound file would be played when the elevator stops moving.

### ElevatorSwitch Properties

**Property** | **Description**
--- | ---
**Delay** | Specifies how long before the lift starts.
**Enabled** | Enables the switch.
**Floor** | Specifies the floor.
**Model** | Specifies the model to use.
**SmartObjectClass** | Specifies the smart object class of the object.
**Use Distance** | Specifies the maximum distance from which the switch can be used.
**Use Message** | Specifies a message to be shown when the player gets close to the switch.
**SoundOnPress** | Specifies the sound to use when the object is pressed.

[Elevator Properties](#elevator-properties)[ElevatorSwitch Properties](#elevatorswitch-properties)
