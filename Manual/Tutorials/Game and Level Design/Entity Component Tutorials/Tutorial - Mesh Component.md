# Tutorial - Mesh Component

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/28181713
- Page ID: 28181713
- Breadcrumb: Tutorials > Game and Level Design > Entity Component Tutorials > Tutorial - Mesh Component
- Parent: Entity Component Tutorials

## Content

### Using the Mesh Component

This tutorial concentrates on the Mesh Component and serves as an introduction to its use and to some of its features. The Mesh Component is primarily used for giving an Entity geometry and a visual representation.

Before attempting this tutorial we recommend that you read the [Entity Components](../../../Entities%20and%20Tools/Entity%20Components.md) documentation. Doing so will give you a much better understanding of the concepts behind CRYENGINE's Entity Components, furthermore the documentation can be used as a reference guide in regard to the various attributes/parameters that relate to each of the available Components.

Different methods can be used to create a new Entity, for more information see the [Entity Components](../../../Entities%20and%20Tools/Entity%20Components.md) documentation.

You will need to open a new or an existing level in the Sandbox Editor in order to undertake this tutorial.

- **Components Method**. From the Create Object tool, left mouse click on the Components icon - this opens the Components menu. Expand the relevant menu (in this case the Geometry menu) and then select Mesh. Drag and anchor the Mesh Component into your level (all with the left mouse button). The Mesh Component will now be highlighted in the level and the Component parameters along with Properties Panel will be visible allowing the various parameters to be set by the user.
![Image](https://www.cryengine.com/docs/static/attachments/28254543)
- **Empty Entity Method**. From the Create Object tool, left mouse click on the Empty Entity Components icon, then drag and anchor the Empty Entity into your level (all with the left mouse button). The Empty Entity will be highlighted, the next step is to add the Mesh Component using the + Add Component button (under the Properties Panel). Note: The Mesh Component has already been added in the image below.
![Image](https://www.cryengine.com/docs/static/attachments/28254544)
- Regardless of the Entity creation method used a default Mesh will have been created, we now need to replace that default Mesh. To do that, go to the property parameters of your Mesh Component and click on the folder symbol. The "Open File" dialog will open, next navigate to the Objects\Default\ folder. Click on the Default folder and select one of the default meshes from those available. For this tutorial, we have selected the primitive_cylinder.cgf. Finally, double click on the open button to accept the new mesh. If you want to import your own geometry have a look at the [FBX Import](../../../Editor%20Tools/FBX%20Import%20Tools.md).
![Image](https://www.cryengine.com/docs/static/attachments/28254869)
- To create a new material open up the [Material Editor Legacy](../../../Editor%20Tools/Material%20Editor%20Legacy.md) **Tools → Material Editor.![Image](https://www.cryengine.com/docs/static/attachments/28254874)**
- In the material editor right click on the folder where the materials should be saved and select "Add New Material". In the "Save File" pop up you can change the path and give the material a name if you are done with that hit the save button.
![Image](https://www.cryengine.com/docs/static/attachments/28254875)
- Now you can see your new material. It changes the color of the material you have to add a texture to the "Diffuse" attribute first. Click on the three dots next to the attribute and you can start to choose a texture you want to have, for this example use the texture "Engine/EngineAssets/Textures/white.dds" and click on the "OK" button
![Image](https://www.cryengine.com/docs/static/attachments/28254889)
- To change the color of your material click on the color field next to the "Diffuse Color" attribute and select any color you want.
![Image](https://www.cryengine.com/docs/static/attachments/28255115)
- Save the material with the save icon (middle top) and close the Material Editor.
- In the next step, we are going to change the material of our Mesh component - the Material attribute can be found underneath the File attribute that we used in step 3. Now either double click the option with the pen where you can directly adjust the already applied material or you double click on the folder icon to assign a new material to your mesh. Select the previously created material.
- You will now have a different material assigned to your Mesh. You can also manipulate the transformation of your Mesh. For example, if you wanted to rotate or move your mesh, but not your Entity, then you can change the values in the "Transform" attribute.
The transformation is relative to your Entity's original position in the world.
- The last thing we will do is to change the physical properties of our Mesh.
The Mesh component will not have any collision or a physical simulation until you add a Rigid Body Component to the Entity.
This topic will be covered in another tutorial when we discuss Physics in more in detail. You can also change the mass or the density of your object (where one calculates the other). To change the mass or the density value go to the Physics Settings option and enter a value.
The mouse wheel can be used to quickly adjust the value.
