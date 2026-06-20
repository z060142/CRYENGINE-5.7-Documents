# NoMaps

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/25534072
- Page ID: 25534072
- Breadcrumb: Asset Prep (External) > Asset Exporting Overview > Texture Creation Overview > NoMaps
- Parent: Texture Creation Overview

## Content

[Image: /docs/static/attachments/29934009]

##
Overview

##
Sections

NoMaps is a standalone tool created by Crytek to achieve high quality tangent-space normal maps for CRYENGINE. In the past when people tried to create tangent-space normal maps for our ENGINE they had to use software which assumed how our renderer accomplished tangent-space. The problem was that no software would know how exactly CRYENGINE rendered tangent-space, hence normal maps were never guaranteed to be completely accurate - or stay compatible between ENGINE revisions/versions. Now with NoMaps Crytek offers a standalone tool which produces tangent-space normal maps directly for CRYENGINE. This software takes the object and its matching object-space normal map and then converts it into a tangent-space normal map that fits its mesh perfectly. In this way NoMaps helps in achieving high quality assets for CRYENGINE, while simplifying previous workflows (only an object-space normal map is required).

[#sections](
Sections
)
[#common-misconceptions](
Common Misconceptions
)
[#preparation](
Preparation
)
[#nomaps-usage-guide](
NoMaps Usage Guide
)

##
Common Misconceptions

A short introduction to the common misconceptions about tangent-space normal maps:

-
Using only one smoothing group and no control loops/chamfers in the lowpoly creates gradients in the normal map and must be avoided at all cost!

-
No, as long as the tangent space is calculated in the same way during both baking and shading, then the gradients will appear flat in CRYENGINE and the result will be fine.

-
You can use one smoothing group and no control loops as long as you use a tangent space plugin for xNormal!

-
No, this will only get you 80-90% of the way and in extreme cases you will still get artifacts. Plugins can only go so far if you're baking directly to tangent space. For perfect results when baking into object-space, then converting the result to tangent space is a necessity.

-
I don't need tools like handplane, I can use control loops, selectively use hard/split normals, use one smoothing group for one UV shell.

-
That's fine, but all of these increase the polygon count. Using NoMaps will allow you to use less polygons, less UV seams and give more control over where the seams should go.

-
Lowpoly meshes with only one SG and no chamfers are impossible to shade unless you activate custom normals.

-
No, using custom normals is only necessary for the baking step. The in-game *.cgf can be shaded either with or without custom normals.

##
Preparation

-
Go to xNormal and setup the baking options for an object-space normal map (go into normal map options and uncheck "Tangent Space"). The orientation (X+, Y+) doesn't matter.

[Image: /docs/static/attachments/23445608]

-
Be sure to use a *.tif as the output filetype in xNormal and configure your .tif plugin to output 16bit depth:

[Image: /docs/static/attachments/23445624]

-
Bake the normal map. It is recommended to use *.sbm files and modified cages if your low-poly is really simplistic.

-
Export the lowpoly as a *.cgf using the "custom normals" option. Be sure to turn off any modifiers that change vertex normals (edit mesh, edit normals, etc).  This *.cgf is just for baking, the final in game mesh can have custom normals disabled. What custom normals do in this case is not only relevant to the vertex normals, rather the RC attempts to re-orient the vertex tangents to facilitate correct shading and allows for mirrored UV's as per Mikkelsen.
**
NOTE:
**
If you have imported your mesh from Maya to 3dsMax at one point in its creation process you should apply an "Edit Poly" modifier on your object to reset vertex normals, then collapse. This has to be done because Maya has different vertex normals than 3dsMax. Alternatively, you can export your mesh as an *.obj from 3dsMax, then re-import it and use this mesh thereafter.

[Image: /docs/static/attachments/23445625]

##
NoMaps Usage Guide

-
Drag & drop the normal map into the texture window of NoMaps, or alternatively add it to the layer stack by using the + icon:

[Image: /docs/static/attachments/23445626]

-
A dialog box will open prompting you to select the matching *.cgf mesh. Select it and hit OK. If you cancel you can also drag & drop the *.cgf into the model view or manually load it using the "browse" button (lower right).

[Image: /docs/static/attachments/23445683]

-
NoMaps will automatically re-orient the object-space normal map to fit your *.cgf. This is the default behaviour found in "settings". If you have this setting turned off, then you will need to manually select the "Reorient OSN to match CGF" option in the layer view:

[Image: /docs/static/attachments/23445628]

-
Select the "Convert OSN to TSN by using a CGF" option to convert your normal map:

[Image: /docs/static/attachments/23445630]

-
Check the shading of the map on the mesh by selecting the "3 point lit TS normals" viewmode in the model view:

[Image: /docs/static/attachments/23445631]

-
To save the map, select File -> Save as... and switch the filetype to *.tif

-
The texture will be saved as CryTIF, using the usual CryTIF settings specified in the leftmost window pane. These are the quality and size reduction settings you know from the Photoshop plugin:

[Image: /docs/static/attachments/23445643]

You will have to manually add the correct suffix or CRYENGINE will not interpret your files correctly. So, if you want to save a regular normal map add the _ddn suffix to the filename.

If you want to save normal maps with the smoothness map in the alpha channel, then add the _ddna suffix to the filename. You can also add the smoothness map in NoMaps by following the next step:

-
To add smoothness maps to your normal map, click on the “Browse” button for Gloss and specify a separate smoothness map:

[Image: /docs/static/attachments/23444687]

-
Then, change the texture preset in the upper left to this setting:

[Image: /docs/static/attachments/23445645]

Finally, save the texture by selecting File -> Save as, choose *.tif as the filetype and add the _ddna suffix to your filename.

-
Finally, look at the *.cgf, plus texture in CRYENGINE and marvel at the results!

[Image: /docs/static/attachments/23445647]

The lowpoly is one smoothing group only and has no chamfers (except on rounded edges - cylinder & sphere)

[Image: /docs/static/attachments/23445649]
[Image: /docs/static/attachments/23445652]
