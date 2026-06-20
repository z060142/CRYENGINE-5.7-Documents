# Terrain Minimaps

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/25534556
- Page ID: 25534556
- Breadcrumb: Editor Tools > Terrain Editor > Terrain Minimaps
- Parent: Terrain Editor

## Content

[Image: /docs/static/attachments/29933308]

##
Overview

The Sandbox Editor has a built in tool for creating mini-maps. Note that Scale form needs to be installed in order to use mini-maps.

[#preparing-to-create-a-mini-map](
Preparing to Create a Mini Map
)
[#creating-a-minimap](
Creating a Minimap
)

##
Preparing to Create a Mini Map

When creating a mini-map, there are certain console variables that are better left turned off.
Specific adjustment of CVars for mini-maps are controlled in the
MapScreenshotSettings.xml
 file.

You can edit this file, located in the
`
<root>\Editor\
`
 folder, with a text editor. You can create a Mini Map by selecting the desired area, and then click
Generate Mini Map
, under
Terrain Editor -> Mini Map
.

Most settings in the MapScreenShotSettings can be modified to create the most desirable results, but make sure to create a backup copy of the original MapscreenshotSettings.xml.
The standing settings are shown here:

```

`
<settings>
            <r_HDRRendering value="1"/>
            <r_PostProcessEffects value="0"/>
            <r_MotionBlur value="0"/>
            <e_ScreenShotQuality value="0"/>
            <e_ViewDistRatio value="100000000"/>
            <r_DisplayInfo value="0"/>
            <e_StreamCgfPoolSize value="128" />
            <e_VegetationSpritesDistanceRatio value="20"/>
            <e_ViewDistRatioVegetation value="100"/>
            <e_Lods value="0"/>
            <e_Vegetation value="0"/>
            <e_TerrainOcclusionCulling value="0"/>
            <e_OcclusionVolumes value="0"/>
            <e_shadows value="0"/>
            <e_portals value="3"/>
            <e_fog value="0"/>
            <r_hdrdebug value="1"/>
</settings>

`

```

For a better quality, you can adjust the
Size
and
Resolution
 settings from the Mini Map tab. In addition, you can also change some of the lines in the *.xml file, or add new CVar commands.

These settings will raise the quality and the amount of objects visible.

Here is an example of some higher quality settings:

```

`
<e_TerrainDetailMaterials value="100000">
<e_TerrainDetailMaterialsViewDistZ value="1000000">
<e_LodRatio value="0">
<e_ViewDistRatio value="100000">

`

```

##
Creating a Minimap

Open the desired level in the Sandbox Editor, and then open the Mini Map tab located in the
Terrain

Editor
 window.

*
Pic1: Mini Map tab
*

[Image: /docs/static/attachments/32178863]

After pressing the Mini Map button, a green bounding box, and a smaller blue selection box appears on the terrain. It is helpful to zoom far away from the terrain in order to see the entire area.

If you cannot see the terrain after zooming out, try increasing the
ViewDistance
 setting under the
Environment Editor
.

*
Pic2: Selected area for creating a Mini Map
*

*
[Image: /docs/static/attachments/32178864]
*

To move the mini-map bounding box, click on a different section of the terrain where you want to create your mini-map.

The green bounding box shows the area that will be converted into a mini-map image, you can adjust the preferred height by editing the input in the
Size
 option under the
Mini Map
 tab.

Make sure that the mini-map bounding box is actually larger than the actual play area of your map. Or else it may lead to anomalies if the player stands on the edge of your map.

Adjusting the
Resolution
 in the mini-map increases the size of the mini-map image that the Editor generates. For example, choosing a resolution of 2048 provides you a mini-map image of 2048x2048 pixels.

You should only choose to use very large resolutions (8192 or 16384) if you are running the editor on a very high spec system with a minimum of 8 GB of RAM.

After you have moved the box and set the
Resolution
 and
Size
, and you can choose the file formats (*.dds and *.tif), and then click
Generate MiniMap.
 The output are directly saved in the same folder as the currently opened .cry file along with an .xml file
*
.
*

*
Pic3: Generating a Mini Map using the Terrain Editor
*

[Image: /docs/static/attachments/32178865]

All the associated files (*.tif, *.dds and *.xml) will be saved in the level file name.

The
*
*.xml
*
 file provides the CryENGINE with the map coordinates so that the player position is correctly displayed on the mini-map.

Example from Woodland level:

```

`
<MetaData>
 <MiniMap Filename="woodland.dds" startX="1122.5697" startY="327.42395" endX="1922.5697" endY="1127.424" width="2048" height="2048"/>
</MetaData>
`

```

The generated levelname.tif should be rotated 90° Clock-Wise in an image editing program, to match the the terrain texture orientation.

Save and reload the editor to see the mini-map active in the HUD.
