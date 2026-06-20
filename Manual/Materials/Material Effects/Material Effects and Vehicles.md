# Material Effects and Vehicles

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/27593782
- Page ID: 27593782
- Breadcrumb: Materials > Material Effects > Material Effects and Vehicles
- Parent: Material Effects

## Content

##
Overview

This tutorial will guide you through the creation and implementation of a mud 'splatter' Material Effect, which can be used with vehicles.

To do this we're going to create a new Particle Effect (or "PFX") and Surface Type as well as modify a vehicle script.

##
Particle Effect

First let's start with the Particle Effect as this will make up the bulk of our change. Start the Sandbox Editor with a new level open where we can create and test the effect.

Because this is a vehicle effect (although it doesn't have to be limited to that), the PFX will be created inside the existing "vehicles" PFX library.

To get started lets copy and modify the existing
vehicles.Common.Ground.Light.Mud
 PFX and save it under
vehicles.Common.Ground.New.NewMud
. It now looks something like this:

[Image: /docs/static/attachments/35402303]

*
It's a good idea to create your PFX against an easy-to-distinguish background, like a Designer object.
*

##
Material Effects

Okay, so we now have our new Particle but how exactly does the vehicle use it? Like most effects in-game, it runs through the Material Effects system.

Using Excel, open the file located in:
`
<GameFolder>\Libs\MaterialEffects\MaterialEffects.xml
`

If you scroll down a bit you will find the following block of information:

[Image: /docs/static/attachments/35402304]

*
Disregard the inclusion of the "SCAR" row for this tutorial.
*

Those of you familiar with the SDK will probably recognize some familiar sounding vehicles listed here. In this case we're going to be working closely with the HMMWV content.

Shortly we'll explain how exactly these setups all communicate, but for now, create a new row underneath (doesn't technically matter where) the vfx_HMMWV and call it "
vfx_CarNew
".

Also add a new column called
mat_mud
 (typically you would arrange these better, in groups).

[Image: /docs/static/attachments/35402305]

So, three new main pieces of content we've added here are:

-
A new surface type reference called "mat_mud".

-
A new mfx row called "vfx_CarNew".

-
A new reference to the vehicles FXLib with "new_mud".

##
Surface Types

As mentioned just above, we've created a new
*
reference
*
 to a new surface type, but that surface type does not yet exist, you cannot assign it to any materials yet.

To create a new surface type simply open the file:
`
<GameFolder>\Libs\MaterialEffects\SurfaceTypes.xml
`

Add in a new entry as follows (copied mat_soil but lowered the friction value to better simulate mud):

```

`
 <SurfaceType name="mat_mud">
  <Physics friction="0.15" elasticity="0" pierceability="7" can_shatter="1" sound_obstruction="0.5" />
 </SurfaceType>
`

```

[Image: /docs/static/attachments/35402306]

Now you can assign the "Mud" surface type in your material that you're going to be driving on.

##
FXLibs

Segue
At this point, this may seem a little overkill just to add some new mud effects, but by the end of this you'll hopefully understand and appreciate the immense amount of flexibility this system offers.

Don't forget that you can of course always copy/paste existing content to give you a head-start and existing setups can always be expanded on, rather than needing to create brand new setups!

Now we have our SurfaceType setup and our terrain material is using it. We also have our MaterialEffect setup but what was that "vehicles:new_mud" entry we made all about anyway? That was our FXLibs entry!

Open the following file:
`
<GameFolder>\Libs\MaterialEffects\FXLibs\vehicles.xml
`

In here you'll find some familiar sounding entries that you may have noticed in the MaterialEffects spreadsheet. It's currently split into 3 sections: Heavy, Light and Helicopter.

We're going to make a new section, based off the last entry in the "Light" section:

```

`
    <Effect name="new_mud">
        <Particle>
            <Name>vehicles.Common.Ground.New.NewMud</Name>
        </Particle>
        <Sound>
            <Name>soil</Name>
        </Sound>
    </Effect>
`

```

[Image: /docs/static/attachments/35402307]

Here we reference the Particle Effect we want to use as well as the Sound it should use (we'll use the existing "Soil" entry as it's close enough).

Note that we can, if we wanted, reference multiple Particles, as well as Decals. Including the ability to scale and randomize the effects used.

##
Vehicle Script

At this point we've got one final thing to do, and that's figure out what to do with the "vfx_CarNew" entry we created earlier.

Open up the HMMWV vehicle script here:
`
<GameFolder>\Scripts\Entities\Vehicles\Implementations\Xml\HMMWV.xml
`

Scroll down towards the bottom and you'll see a "Particles" block which looks something like this:

[Image: /docs/static/attachments/35402308]

Now it all starts to come together! To recap the chain of events that will happen:

-
Depending on the surface type, the HMMWV will execute the FXLibs defined on the "vfx_HMMWV" row inside the MaterialEffects.xml file. Inside the FXLibs file are entries covering the existing surface types and the effects wished to be played.

-
Or, HMMWV.xml -> SurfaceTypes.xml -> MaterialEffects.xml -> FXLibs/vehicles.xml -> Particles/vehicles.xml -> PFX.
Now lets modify the HMMWV script to see if our setup works. Change the
mfxRow
 parameter to use our new "vfx_CarNew" row.

If you haven't already, now would be a good time to restart the Editor to bring in all of our changes.

If your Surface Type doesn't seem to be working, try creating a copy of the material, set the surface type to Mud and then apply that material to the terrain.

##
Testing

[Image: /docs/static/attachments/35402309]
 |
[Image: /docs/static/attachments/35402310]
 |

New Mud Effect
 |
No Grass Setup for the vfx_NewCar row!
 |

[Image: /docs/static/attachments/35402311]
 |
[Image: /docs/static/attachments/35402312]
 |

Testing New Surface Types
 |
Particle System only bound by your creativity!
 |
