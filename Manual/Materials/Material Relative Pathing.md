# Material Relative Pathing

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/29799264
- Page ID: 29799264
- Breadcrumb: Materials > Material Relative Pathing
- Parent: Materials

## Content

[Image: /docs/static/attachments/29933271]

##
Overview

##
Sections

A relative path refers to a location that is relative to a current directory. You can use a relative path when the textures are stored within the same directory. They prevent drive mapping issues when the entire directory is moved to a new location. For example, if the textures referenced in a material file (.mtl) are located in the same folder or in a sub-folder, the path to the texture can be set up relative to the .mtl file.

The main advantages for using relative path are:

-
Lets you move the objects together along with the
*
*.mtl
*
 and texture files anywhere within your project directory without breaking the texture paths.

-
Provides a better-intended view for the assets view irrespective of the project location. This enables you to prepare the assets for marketplaces.
The Material Editor checks the active material's texture paths once you make a change to a material and it automatically adjusts the path in the background. However, it will still show the actual absolute path of the project’s root folder. The relative path will not be visible to the user unless they examine the *.mtl files to see the relative path assigned to the assets.

Advanced users can also manually change the path using a text editor. This can be useful if you want to make large amount of changes outside the Sandbox editor.

[#sections](
Sections
)
[#how-does-it-work](
How does it work?
)
[#asset-optimization](
Asset Optimization
)

##
How does it work?

When you specify files with absolute paths and later move them, you must change these paths to reflect new locations. To prevent this, use relative paths that specify paths or files.

When you use a relative path, instead of referring to a file relative to the project's root folder, the path is stored relative to the .mtl file which provides reference to the texture file.

Actual Path:

```

File="<GameFolder>\objects\architecture\house\house.tif"

```

Relative Path:

`
File="./house.tif"
`

For example, if the texture is located in the same folder as the .mtl file, it will be referenced as
*
File="./house.tif"
*
. If the file is located in a subfolder called
*
textures
*
, it will be referenced as
*
File="./textures/house.tif"
*
.

Actual Path:

```

File="<GameFolder>\objects\architecture\house\
textures
*
\
*
house.tif"

```

Relative Path:

`
File="./textures/house.tif"
`

Please refer to the sample *.mtl file below:

```

```

```

`
<Material MtlFlags="524288" Shader="Illum" GenMask="20000001"
StringGenMask="%ALLOW_SILHOUETTE_POM%SUBSURFACE_SCATTERING" SurfaceType="" MatTemplate=""
Diffuse="0.58823532,0.58823532,0.58823532" Specular="0,0,0"
Opacity="1" Shininess="9.999999" vertModifType="0" LayerAct="1">
 <Textures>
 <Texture Map="Diffuse" File="./textures/house.tif"/>
 </Textures>
 <PublicParams EmittanceMapGamma="1" SSSIndex="0" IndirectColor="0.25,0.25,0.25"/>
</Material>
`

```

##
Asset Optimization

This feature enables the user to easily share assets through the Asset Database, and for prototyping.

During the optimization stage of your project, you might want to share textures between materials or objects to optimize the memory footprint of your project.

For more information about optimizing your assets, check
[/docs/static/engines/cryengine-3/categories/1114113/pages/1310836](
here
)
.
