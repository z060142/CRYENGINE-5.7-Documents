# Chapter 2 - Flash and Gfx

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/89456800
- Page ID: 89456800
- Breadcrumb: Tutorials > Game and Level Design > UI > UI Design Tutorials > Tutorial - Introduction to Scaleform UI > Chapter 2 - Flash and Gfx
- Parent: Tutorial - Introduction to Scaleform UI

## Content

### GFx Compiling

By default we will be using a GFx exporter to compile our SWF file; the GFx exporter is located in the *Tools* folder of the CRYENGINE build you have installed.

Large packages can be bundled into a single SWF file to house almost all of your game functionality through one GFx, but it is also good to break them up into individual elements to make them even more manageable.

It should be noted that, by default, the GFx exporter will generate TGA files for the bitmap images used in your Flash project. This will have the undesired effect of consuming more resources than what would otherwise be used by a more appropriate image format such as DDS.

Thankfully, there is a flag switch that can be used with the GFx export tool that allows the generation process to output DDS files for us. Below, the workflow for this procedure is explained.

### Steps for Saving and Compiling the GFx

#### Scaleform 3

- Start by first saving your Flash file in the UI folder of your project, for example, *<root>/Assets/libs/UI*.![Image](https://www.cryengine.com/docs/static/attachments/89456846) * libs/UI*
- Be sure that you have an SWF file from your FLA source by using the Publish procedure in the Adobe Flash Editor.
![Image](https://www.cryengine.com/docs/static/attachments/90833523)
*Publishing an SWF file from your FLA source*
- Next, create a custom shortcut to the *gfxexport.exe* file, so that it will generate any necessary images used in your Flash project. Add `-i DDS` to the end of the new shortcut's **Target Path** (after the last quotation mark).
![Image](https://www.cryengine.com/docs/static/attachments/89456848)
*Add -i DDS to end of the shortcut target path*
- You then need to drag and drop your SWF file over the new shortcut to generate the GFx file and any necessary images.![Image](https://www.cryengine.com/docs/static/attachments/89456849) *Drag and drop your SWF file over the new shortcut*

The GFx Export tool for Scaleform 3 can be found at *<root>/Tools/GFxExport/Scaleform3/gfxexport.exe.*

#### Scaleform 4

- Start by saving your Flash file in the UI folder of your project, for example, *<root>/Assets/Libs/UI.![Image](https://www.cryengine.com/docs/static/attachments/89456846) libs/UI*
- Be sure that you have an SWF file from your FLA source by using the Publish procedure in the Adobe Animate editor.
![Image](https://www.cryengine.com/docs/static/attachments/90833135)
*Publish in Adobe Animate*
- Then, create a custom shortcut to the *GFxExport1.exe* file so that it will generate any necessary images used in your Animate project. Add `-i DDS` to the end of the new shortcut's Target Path (after the last quotation mark).
![Image](https://www.cryengine.com/docs/static/attachments/90833136)
*Target Path*
- You then need to drag and drop your SWF file over the new shortcut to generate the GFx file and any images necessary.![Image](https://www.cryengine.com/docs/static/attachments/90833137) *Drag-drop your SWF file over the new shortcut*

The GFx Export tool for Scaleform 4 can be found at *<root>\Tools\GFxExport\Scaleform4\GFxExport1.exe.*

[GFx Compiling](#gfx-compiling)[Steps for Saving and Compiling the GFx](#steps-for-saving-and-compiling-the-gfx)[Scaleform 3](#scaleform-3)[Scaleform 4](#scaleform-4)
