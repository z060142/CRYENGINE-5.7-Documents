# Creating A Bike

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/29793889
- Page ID: 29793889
- Breadcrumb: Physics > Vehicles Basics (GameSDK) > Creating A Bike
- Parent: Vehicles Basics (GameSDK)

## Content

![Image](https://www.cryengine.com/docs/static/attachments/29933325)

## Overview

## Sections

The [Vehicle Section](/docs/static/engines/cryengine-3/categories/1114113/pages/1310855) provides most of the information required for four wheel vehicle (4WD) setup. This section re-emphasizes the wheels, breakable windows, shootable tires, and the speedometer and tachometer setup options.

[Sections](#sections)[Sample Files](#sample-files)[Working Suspension Parts](#working-suspension-parts)[Breakable Windows](#breakable-windows)[Shootable Tires](#shootable-tires)[Tachometer and Speedometer](#tachometer-and-speedometer)[Lights and Exhaust smoke](#lights-and-exhaust-smoke)[In Sandbox](#in-sandbox)

### Sample Files

- [car.max](/docs/static/attachments/1443378)
- [suspension_example.rar](/docs/static/attachments/11406266)

### Working Suspension Parts

You now have the ability to create moving suspension parts simply by defining in the vehicle script which parts you want to utilize and whether or not they rotate or stretch.

It is important to note that this system is not actually changing the parameters of the vehicles suspension, this is a visual feature working off of the vehicles main parameters.

#### Swingarms

In the attached example file you will find the following code located in the parts of the main vehicles xml:

```
<Part name="wheel2_wishbone" class="SuspensionPart" component="" mass="10" disablePhysics="0" disableCollision="0" isHidden="0">
<IK target="wheel2" offset="0,0,0" targetHelper="wheel2_ik" mode="rotate" ignoreTargetRotation="1" />
</Part>
```

You have the main part being moved (wheel2_wishbone) and the two other nodes used to work the IK which moves it (wheel2 and wheel2_ik) and then finally the section which defines how the IK will interact with the part.

In this case its set to "rotate" so "wheel2_wishbone" will rotate when the IK handles receive information.

#### Springs

In the attached example below the code defining the swingarm, there is also the following which is defining spring parts:

```
<Part name="wheel2_damper" class="SuspensionPart" component="" mass="10" disablePhysics="0" disableCollision="0" isHidden="0">
<IK target="wheel2_wishbone" offset="0,0,0" targetHelper="wheel2_damper_term" mode="stretch" ignoreTargetRotation="0"/>
</Part>
```

You have the main part being moved (wheel2_damper) and the two other nodes used to create the IK which moves it (wheel2_wishbone and wheel2_damper_term) and then at last the section which defines how the IK will interact with the part.

In this case it is set to "stretch" so the spring "wheel2_damper" will expand or contract depending on how the IK handle is working.

#### Debugging Suspension Parts

Generally the output will tell you if there is an inconsistency defined in your vehicle script but something you can do to visualize how the suspension is working in-game (or when AI/Physics is enabled) is to enable the following CVar: **v_debugSuspensionIK**

### Breakable Windows

- To make a window breakable, it has to be a solid object, not a plane. The surface type has to be *mat_glass_vehicle* in the Editor's material settings. Also, it has to be physicalized in your 3D package.
- To have a spider web effect, you must have an additional material set up for this, and it has to be called *broken_windowpanes*. When you hit the glass, it will switch to this material.
- Glass objects have to be linked to the containing objects; windshield to chassis, side windows to doors.

### Shootable Tires

To have an *empty* rim to let the tires explode, you must have the models ready for this. This extra, empty rim object has to be called like the appropriate wheel + *_rim* suffix (wheel1 -> wheel1_rim). These objects have to be exported in the damaged version of the vehicle.

If you want to have a separate damaged version for the wheels also, those should be exported in this file as well, and they should be named with the regular damaged naming convention by adding the *_damaged* suffix (wheel_1 -> wheel_1_damaged).

LOD versions of these have to be exported in the regular way, as described above.

### Tachometer and Speedometer

It is also possible to have tachometer and speedometer pins on the dashboard. These have to be placed properly on the dashboard and the pivot point has to be set up properly.

All these are rotated around the local z-axis for Max, y-axis for Maya; therefore, set up the pivot accordingly. The default position should be at the lowest available value (speed = 0).

### Lights and Exhaust smoke

Lights are all setup in the vehicle editor and you do not need to setup helpers for them either.

It is still required to make a particle effect for the exhaust smoke and other effects, but they are joined to the vehicle via the editor.

### In Sandbox

Please refer to [this](../../Editor%20Tools/Deprecated%20Tab/Vehicle%20Editor.md) section for information on the vehicle editor.
