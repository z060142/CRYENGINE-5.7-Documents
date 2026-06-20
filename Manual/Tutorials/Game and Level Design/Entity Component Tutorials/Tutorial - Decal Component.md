# Tutorial - Decal Component

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/28181771
- Page ID: 28181771
- Breadcrumb: Tutorials > Game and Level Design > Entity Component Tutorials > Tutorial - Decal Component
- Parent: Entity Component Tutorials

## Content

##
Using the Decal Component

This tutorial is going to explain the decal components and how to use it. With the decal component, you can add decals to your scene, this technique is mostly used to add blood splatter, dirt or bullet holes dynamically to already existing geometry. I would also recommend seeing the
[/docs/static/engines/cryengine-5/categories/23756816/pages/28180907](
Entity Components
)
 documentation to understand or look up what the specific attributes do.

First, we need to prepare some assets before we can use the decal component. We need a texture and a material in order to work with the decal component. Use can use any texture you want for the decal component, if you have your texture make sure that you exported the texture as .tif and that the texture is power of two. To import the texture open up the asset browser under Tools -> Asset Browser and drag and drop the texture into the folder you want to have it.

*
Opening the asset browser

*
[Image: /docs/static/attachments/28254495]

Drag and drop the .tif file into the asset browser

*
Importing the decal texture
*

[Image: /docs/static/attachments/28254502]

Now we have to add a new material, open the
[/docs/static/engines/cryengine-5/categories/23756816/pages/44967563](
Material Editor Legacy
)
 under
**
Tools → Material Editor
**
. Right-click on any folder and select "Add New Material" in the context menu.

*
Adding a new material

*
[Image: /docs/static/attachments/28254497]

The newly created material should now be selected and editable. The only attribute we have to change is the diffuse texture of the material. To do so click on the three dots right next to the "Diffuse" attribute in the "Texture Maps" category and select the texture. Save the material and close the window again.

*
Adding the texture to the material

*
[Image: /docs/static/attachments/28254503]

Now we have a material for the decal component and we can finally create an entity and the component. Click on the "Empty Entity" button in the "Create Object" panel and place the entity in the level. After that select the entity and click on the "Add Component" button in the "Properties" panel and select the environment probe component.

*
Creating the entity and adding the decal component

*
[Image: /docs/static/attachments/28254500]

After adding the decal component we can see the attributes of the decal component in the "Properties" inspector. The first thing necessary in order to see anything is to assign the previously created material to the component. Click on the folder icon right next to the "Material" attribute and select the material.

*
Selecting the decal material

*
[Image: /docs/static/attachments/28254504]

Now you can see the decal projection on the ground and it already looks like the would be dirt in that spot. Move the entity around and see how the decal behaves. The decal will be projected on every surface around it as long it stays in the projection depth.

*
Moving the entity around

*
[Image: /docs/static/attachments/28254505]

As you can see the decal is going to blend if the slope is going to be too hard. To change this behavior adjust the "Projection Depth" value and set it to 10, now it tries to always project the texture.

*
Changing the projection depth

*
[Image: /docs/static/attachments/28254506]

The decal component can also be rotated if the decal should, for example, be on a wall instead of the ground. To rotate the entity adjust the "Transformation" attribute of the component.

*
Changing the transformation of the component

*
[Image: /docs/static/attachments/28254507]

##
Using the Decal Component

This tutorial is going to explain the decal components and how to use it. With the decal component, you can add decals to your scene, this technique is mostly used to add blood splatter, dirt or bullet holes dynamically to already existing geometry. I would also recommend seeing the
[/docs/static/engines/cryengine-5/categories/23756816/pages/28180907](
Entity Components
)
 documentation to understand or look up what the specific attributes do.

First, we need to prepare some assets before we can use the decal component. We need a texture and a material in order to work with the decal component. Use can use any texture you want for the decal component, if you have your texture make sure that you exported the texture as .tif and that the texture is power of two. To import the texture open up the asset browser under Tools -> Asset Browser and drag and drop the texture into the folder you want to have it.

*
Opening the asset browser

*
[Image: /docs/static/attachments/28254495]

Drag and drop the .tif file into the asset browser

*
Importing the decal texture
*

[Image: /docs/static/attachments/28254502]

Now we have to add a new material, open the
[/docs/static/engines/cryengine-5/categories/23756816/pages/44967563](
Material Editor Legacy
)
 under
**
Tools → Material Editor Legacy
**
 or the new Material Editor under
**
Tools → Material Editor
**
. Right-click on any folder and select "Add New Material" in the context menu.

*
Adding a new material

*
[Image: /docs/static/attachments/28254497]

The newly created material should now be selected and editable. The only attribute we have to change is the diffuse texture of the material. To do so click on the three dots right next to the "Diffuse" attribute in the "Texture Maps" category and select the texture. Save the material and close the window again.

*
Adding the texture to the material

*
[Image: /docs/static/attachments/28254503]

Now we have a material for the decal component and we can finally create an entity and the component. Click on the "Empty Entity" button in the "Create Object" panel and place the entity in the level. After that select the entity and click on the "Add Component" button in the "Properties" panel and select the environment probe component.

*
Creating the entity and adding the decal component

*
[Image: /docs/static/attachments/28254500]

After adding the decal component we can see the attributes of the decal component in the "Properties" inspector. The first thing necessary in order to see anything is to assign the previously created material to the component. Click on the folder icon right next to the "Material" attribute and select the material.

*
Selecting the decal material

*
[Image: /docs/static/attachments/28254504]

Now you can see the decal projection on the ground and it already looks like the would be dirt in that spot. Move the entity around and see how the decal behaves. The decal will be projected on every surface around it as long it stays in the projection depth.

*
Moving the entity around

*
[Image: /docs/static/attachments/28254505]

As you can see the decal is going to blend if the slope is going to be too hard. To change this behavior adjust the "Projection Depth" value and set it to 10, now it tries to always project the texture.

*
Changing the projection depth

*
[Image: /docs/static/attachments/28254506]

The decal component can also be rotated if the decal should, for example, be on a wall instead of the ground. To rotate the entity adjust the "Transformation" attribute of the component.

*
Changing the transformation of the component

*
[Image: /docs/static/attachments/28254507]
