# Creating a Particle Effect

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/36869022
- Page ID: 36869022
- Breadcrumb: Editor Tools > Particle Editor > Creating a Particle Effect
- Parent: Particle Editor

## Content

##
Creating a Particle Effect

A particle effect can be easily created and used in a level by simply following these steps:

-
To create a new particle effect, click
**
File→
**
**
New
**
on the Particle Editor panel and define a name for the particle.

Users can also create particle effects by simply right-clicking on a blank space and choosing
**
New→
**

**
Particles
**
 on the Create Particle panel the Asset Browser.
*
![Image](https://www.cryengine.com/docs/static/attachments/53543073)
*

In this example, the new particle is named as
*
p
*
*
article_fire.
*
*

*

-
After creating a new particle effect, follow the
**
File→Open
**
path and select the effect (p
*
article_fire
*
), then click
**
OK
**
to access its components and features:

![Image](https://www.cryengine.com/docs/static/attachments/44961632)

-
New particle effects appear with a basic component which can we displayed on Graph Editor. Users can work on this default component or they can choose a pre-made component to start modifying the effect. Preset components can be accessed by right clicking on an empty space in Effect Graph to bring up the preset libraries. For more information about the Preset Library, please refer to
[Particle Presets Library](Particle%20Presets%20Library.md)
.

In this example,
*
explosion_fire
*
 under
**
Advanced
**
 section is used and the default component is removed from the Effect Graph panel:

![Image](https://www.cryengine.com/docs/static/attachments/53543075)

![Image](https://www.cryengine.com/docs/static/attachments/44961635)

-
After the
*
explosion_fire
*
component is added to the particle effect, click the
**
Save
**
 button and drag the particle entity from the
**
Asset Browser
**
 into your level. The visual result of the effect depends entirely on the type of the components and the changes that have been made on the feature properties list.

In this example,
*
explosion_fire
*
 particle effect emits a basic white cloud:

![Image](https://www.cryengine.com/docs/static/attachments/44106060)

-
Once the particle effect is introduced to the level, its properties can be modified on the
**
Particle Editor
**
to create a more sophisticated effect such as fireworks, explosions, and omnipresent effects like rain or snow.

For more information about the particle effect components and features, please refer to
[Particle Effect Features](Particle%20Effect%20Features.md)
.
