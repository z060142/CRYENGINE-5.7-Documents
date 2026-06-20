# Glossary

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/27591045
- Page ID: 27591045
- Breadcrumb: CRYENGINE - Getting Started > Glossary
- Parent: CRYENGINE - Getting Started

## Content

[Image: /docs/static/attachments/27561773]

[Image: /docs/static/attachments/26955149]

[Image: /docs/static/attachments/26955150]

[Image: /docs/static/attachments/26955151]

##
Overview

This page is dedicated to describing the commonly used terms when working with CRYENGINE V
. As a use case, you may find yourself asking questions like "What is a Brush
", "What is a
**
Component
**
", or "What is POM?
", this page will highlight and provide descriptions for those types of questions and more. Once you have an understanding of what each term means, links are provided for more documentation and guidance on working with them.

##
Sections

[#sections](
Sections
)
[#](
#
)
[#a](
A
)
[#b](
B
)
[#c](
C
)
[#d](
D
)
[#e](
E
)
[#f](
F
)
[#g](
G
)
[#h](
H
)
[#i](
I
)
[#j](
J
)
[#l](
L
)
[#m](
M
)
[#n](
N
)
[#o](
O
)
[#p](
P
)
[#q](
Q
)
[#r](
R
)
[#s](
S
)
[#t](
T
)
[#v](
V
)
[#y](
Y
)
[#z](
Z
)

##
#

Used to describe raycasting engines, such as Doom or Duke Nukem. The maps are generally drawn as 2D bitmaps with height properties but when rendered gives the appearance of being 3D.

##
2.5D

Refers to the ability to move in the X, Y and Z axis and also rotate around the X, Y, and Z axes.

##
3D

##
A

A form of a bounding box where the box is aligned to the axis therefore only two points in space are needed to define it. AABB’s are much faster to use, and take up less memory, but are very limited in the sense that they can only be aligned to the axis.

##
Axis-aligned Bounding Box (AABB)

An albedo is a physical measure of a material’s reflectivity, generally across the visible spectrum of light. An albedo texture simulates a surface albedo as opposed to explicitly defining a colour for it.

##
Albedo

Assigning varying levels of translucency to graphical objects, allowing the creation of

things such as glass, fog, and ghosts. This can be accomplished by using alpha channels.

##
Alpha Blending

The optional channel of image data in a texture file that can be used as a transparency map, height map, specular map, etc. The format of the alpha channel is usually 8 bits per pixel (256 colors), though certain file formats support different bit depths.

##
Alpha Channel

A method for creating transparency by checking the alpha value of a given pixel.

##
Alpha Testing

An animated storyboard which is used to refine timing, cameras, composition, when a complex shot is needed and static images have trouble making intention clear. When needed, low-resolution animated 3d scenes are used, intermixed with the remaining 2D storyboard panels.

##
Animatic

A texture filtering method, specifically for non-square filtering, usually of textures shown in radical perspective. Generally speaking, anisotropic improves clarity of images with severely unequal aspect ratios.

##
Anisotropic Filtering

Removes the stair-stepping or jaggies which occur at the edges of polygons or between the texels on the polygons. The way this works is by interpolating the pixels at the edges to make the difference between two color areas less dramatic.

##
Anti-aliasing (AA)

A set of computer instructions or algorithms designed to simulate the actions of an intelligent being to the extent necessary to meet the design requirements of a game.

##
Artificial Intelligence (AI)

An acronym for the American Standard Code for Information Interchange, which is an encoding method for text, based on the English alphabet.

##
ASCII

A number that describes the shape of a rectangle texture, whether it’s tall or wide. To calculate an aspect ratio, either divide the width by the height, or write it out as width:height.

##
Aspect Ratio

##
B

A secondary surface where the current frame’s graphics are stored before they are transferred to the primary display surface.

##
Back Buffer

The process of removing the unseen polygons that face away from the camera in the game. These surfaces are usually not needed (except sometimes for shadow casting). Doing so can dramatically speed up the rendering of a polygonal scene.

##
Backface Culling

This type of spline provides the ability to make a curved line using very few points. The two endpoints of the curve are called anchor points. The other points, which define the shape of the curve, are called handles, tangent points, or nodes.

##
Bezier Spline

A term commonly used in games to describe a camera-facing plane. This is a polygon with a texture using transparency, that rotates on various axes to always face the player. Billboards are commonly used for particles, trees, grass, clouds, and UI elements.

##
Billboard

This value defines the amount of color information an image holds. Typically 1-bit is two colors

(black and white), 2-bit is four colors, 4-bit is sixteen, 8-bit is 256 colors, and 16-bit is 65536 colors.

##
Bit depth

An image file, such as JPG, TIF, PSD, and BMP.

##
Bitmap

A BSP tree subdivides 3D space with 2D planes to help speed up sorting. In game development, BSP usually means using solid modeling techniques to carve the basic surfaces of a game level.

##
Binary Space Partition (BSP)

A post-processing effect which simulates bright light sources overwhelming a camera or the eye, creating a halo around the brightest parts of a scene.

##
Bloom

A Bitmap file type used in game development, for storing source files. This is an intermediary format for use outside of a game engine. Usually then imported and converted into a different in-game format.

##
BMP

A simplified approximation of the volume of a model, most commonly used for collision detection. It is common place to find referenced in code axis-aligned bounding box (AABB) and oriented

bounding box (OBB).

##
Bounding Box

A process of rendering polygons that gives them an illusion of depth.

##
Bump Map

##
C

typically the camera in a game is the player’s view into the game scene. Cameras can also be used

for other views in the game level, for example a virtual security camer can use “render to texture“ to show the player alternate views of a game level.

##
Camera

The standard coordinate system. With three dimensions, there are three scalars, x, y, and z used to represent a point at a given distance from a reference point, the origin.

##
Cartesian Coordinate

A technique which causes rendered objects to look as though they are hand-drawn, cartoon

images.

##
Cel Shading

Commonly used to describe a color component that makes up an image. A 24-bit image can have

red, green, and blue channels. 32-bit images have room for a fourth channel, commonly known as an alpha channel.

##
Channel

Any node in a hierarchy that is attached to another node.

##
Child

This plane throws away polygons on the other side of it. This can dramatically speed up the rendering of a polygonal scene, since unneeded polygons can take up valuable processing power.

##
Clipping Plane

The systematic check to see if any intersections are occurring between significant polygons. A common method to optimize collision detection is to use a bounding box to simplify collision

shapes.

##
Collision Detection

Programmers have to convert source code, written in a high-level language such as C++, into

object code (aka Assembly), so that a microprocessor can run the application.

##
Compile

Defined where any two points can be connected by a line that goes outside the shape. When

visualized the shape takes the formation of the letter C.

##
Concave

Defined where any two points can be connected by a line that goes outside the shape. This is a

shape without indentations and is the opposite of a concave surface.

##
Convex

Artifacts that appear around a bright light source. Often in circular or star like shapes.

##
Corona

Commonly utilized to compute something known as a surface normal. As by the cross product formula, a normal is simply a vector that is perpendicular to some plane. In graphics, this plane is

usually a polygon of some type.

##
Cross-Product

an alternative to sphere mapping used in environment mapping, cube mapping gets a ‘screenshot’ looking in 6 different directions and arranges them in a rolled out cube. When applied, the object appears to reflect the environment around it.

##
Cube Mapping

##
D

Scene effect to make objects that are farther away from the camera are rendered with a

lighter color so that they are given the illusion of distance.

##
Depth Cueing

Process of creating an illusion of more colors than are really available in the current color depth

by creatively arranging individual pixel patterns.

##
Dithering

These calls are based on how many objects are drawn to the screen. A good way to think about

this is 1 material = 1 draw call, and an object with 4 materials = 4 draw calls. This can grow exponentially when incorporating the lighting and shadows in a scene.

##
Draw Call

the way to define what polygons are drawn in a game engine. Back-to-front draw order means the furthest polygons are drawn first, and the rest are drawn on on top of another, with the last to draw being the one that appears to be in front. This can also be referred to as “sort priority” regarding transparent polygons as well.

##
Draw Order

The definition of dynamic lighting is a light source that is updated every frame, as you’d want for moving lights and for characters that move amongst various light sources. The opposite of dynamic lighting is “baked” lighting through lightmapping.

##
Dynamic Lighting

##
E

A game engine is what converts all the game assets into the display on your computer screen. Game engines often come with a level editor and other tools which help artists create content that work well in the engine.

##
Engine

An effect where an object reflects its surroundings, much like chrome.

##
Environment Probe

An expression is a formula used to create procedural animation, often using mathematical elements like sine and cosine. Expressions can automate and greatly speed up repetitive animation tasks.

##
Expression

##
F

Face is another name for a Polygon. This term can be used specifically for a single triangle or more generally for a multi-triangle polygon.

##
Face

A system to taxonomize human facial movements by their appearance on the face. Movements of individual facial muscles are encoded by FACS from slight different instant changes in facial appearance. It is a common standard to systematically categorize the physical expression of emotions, and it has proven useful to psychologists and to animators alike.

##
Facial Action Coding System (FACS)

The FOV is usually defined by its width in degrees. A typical FOV in games is around 60 degrees, although players enjoy being able to change the FOV themselves.

##
Field of View (FOV)

Assigning only one color shade per face.

##
Flat Shading

Fog makes objects become more and more the same color as they recede into the distance. This is similar to real fog, except that game fog is a perfect gradient, whereas real fog usually has some wispy qualities to it. Heavy fogging in a game is used to disguise the far clipping plane.

##
Fog

A method of manipulating objects in a hierarchy where the animator positions objects and the program calculates the positions and orientations of the objects below it in the hierarchy.

##
Forward Kinematics (FK)

A measure of animation display rate. Not to be confused with the genre First Person Shooter.

##
Frames Per Second (FPS)

What a video card uses to store the images it renders, while it is rendering them. When it is

done rendering, it sends the completed frame to your monitor and starts building the next frame.

##
Frame Buffer

Measures how fast the game is being rendered. Generally if the frame rate is lower than 30

frames per second, then the game will seem “choppy” and unresponsive.

##
Frame Rate

A term from traditional photography, the shape that the camera creates when projected into the

scene. This pyramidal shape defines the limits of what the viewer can see, so it is used to calculate clipping, collisions, Fog, etc.

##
Frustum

##
G

Geometry is commonly used to define all polygonal objects in a game. Also called a mesh.

##
Geometry

Graphics Interchange Format. A format for saving graphics that usually uses a 8-bit (256 color)

indexed bitmap.

##
GIF

A problem encountered when one tries to rotate using the 3 axes where one ends up rotating in the wrong direction after several rotations.

##
Gimbal Lock

Also known as intensity interpolation. A shading model where the light intensity is calculated at each of the vertices, and is interpolated across the polygon.

##
Gouraud Shading

Graphical User Interface.

##
GUI

##
H

Real world lighting contains a high range of luminance values. HDR, or High Dynamic Range lighting, is essentially a technique that exceeds the normal computer graphics color range of 0 to 255, allowing for more realistic lighting models.

##
HDR

A method often used to create 3D landscapes, height maps contain a grid of points that are

given height values and the landscape is rendered by building polygons out of them.

##
Height Map

Existing where each node can trace its lineage up through this upside-down tree, back though

parents to the root. If you choose any parent, then you can call its collection of children a branch of the tree.

##
Hierarchy

Heads-Up-Display. This means status information which isalways visible like health or ammo information.

##
HUD

##
I

When color information is stored in a look up table that contains the colors red, green and

blue information.

##
Indexed Color

The process of determining from two or more values what the “in-between” values should be. Interpolation is used with animation and with textures, particularly texture filtering.

##
Interpolation

The process of creating realistic positioning of a complex object, such as an arm, based on the positioning of a lower-level node in the skeletal hierarchy, such as the twisting of a hand. This process works in the reverse of forward kinematics.

##
Inverse Kinematics (IK)

##
J

A bitmap file type used in game development. This format is often used for web games, because it

can be highly compressed for faster download. After the download it is usually converted into a different in-game format to use in the game.

##
JPEG

##
L

An abbreviation for Linear Interpolation.

##
Lerp

Traditionally, light maps store the color and brightness of pre-baked lighting. The Diffuse map is applied to the mesh with no lighting, and the light map is then multiplied against it, darkening the diffuse where the light map has shadows.

##
Light Mapping

##
M

This can either mean texturing or it can mean creating texture coordinates.

##
Mapping

A set of parameters that determine the textures, color, shininess, smoothness, etc. for a surface. A

material is the user interface for a shader; the shader controls how the surface is rendered, while the material merely stores the user-adjusted settings for the shader.

##
Material

Used to split a model’s surface into multiple Materials. Normally a model can only use a single material. However a number can be assigned to sets of polygons which each correspond to a particular material.

##
Material IDs

The amount of quickly-retrievable space for storing the assets currently being used by the game.

Games use a number of different types of memory, but game artists are mostly concerned with RAM. The biggest question for the artist is how much RAM is available for textures.

##
Memory

Another word for geometry, or polygon.

##
Mesh

To render a texture more smoothly in a game, it is resized multiple times to make “mips,” which are smaller versions of the texture. These smaller versions are swapped or blended with the original texture as the texture recedes in the scene.

##
Mip Mapping

An animated 2D or 3D effect that makes one texture or geometry smoothly transform into another.

When used with models, all the shapes must have exactly the same vertex count, and vertex order. The individual mesh shapes are called blend shapes, or morph targets.

##
Morph

##
N

This means a polygon with “n” number of sides. It can be used interchangeably with polygon. The

letter N stands for any whole number. A 3-sided n-gon is a triangle, a 4 sided n-gon is called a quad.

##
N-gon

Each single object in a hierarchy is called a node. Without nodes there can be no hierarchy-- there’s nothing to link together. Also sometimes called a bead.

##
Node

Short for Non-Uniform Rational B-Spline, a mathematical representation of a 3-dimensional object. Most applications support NURBS, which can be used to represent analytic shapes, such as cones, as well as free-form shapes, such as car bodies.

##
NURBS

##
O

Defined as a screen pixel being drawn more than once. Overdraw is usually caused by multiple

triangles being drawn over each other, for example with particle effects or tree foliage.

##
Overdraw

##
P

A parent is any Node in a Hierarchy that has another node linked to it. Usually when a parent is

adjusted, all its children nodes get the same transform.

##
Parent

An approach for materials and rendering that creates more accurate and predictable results than previous game rendering techniques, and works very well with dynamic lighting conditions (like time-of-day).

##
Physically-based Rendering (PBR)

Any of the perceptually distinct units of sound in a specified language that distinguish one word

from another, for example p, b, d, and t in the English words pad, pat, bad, and bat.

##
Phoneme

A method of lighting a 3D world, the Phong lighting model applies three different types of lighting

to the vertex of every polygon. Phong lighting works by performing operations based on the normal of the polygon, the “normal” being an imaginary line drawn orthogonal (straight up from) the face of the polygon.

##
Phong

This term comes from aviation. Most game engines count from +90 to -90 degrees, starting out

pointed straight up, turning downwards and ending pointed straight down. Straight forward is 0 degrees.

##
Pitch

Short for picture element. There are two common meanings: the pixels that Textures or Bitmaps are made of, and the pixels that are rendered onto your computer screen by the game engine.

##
Pixel

A bitmap file type used in game development. It is the main image format for Photoshop.

##
Photoshop Document (PSD)

Developed as a patent-free alternative to GIF, Portable Network Graphics (PNG) format is used for

lossless compression and for display of images on the web. Unlike GIF, PNG supports 24‑bit images and produces background transparency without jagged edges.

##
PNG

Most game engines use polygons to make the surfaces of their objects. A polygon can be made

up of 1 or more triangles, like a quad is made of two triangles, a pentagon is made of three triangles, etc. Some engines support multiple polygon types, but triangles are the most common.

##
Polygon

This means the numbers 2, 4, 8, 16, 32, 64, 128, 256, 512, etc. Usually this is used to describe the Texture sizes that a game engine requires in order to make good use of video Memory. An example pow2 texture size would be 32x64.

##
Power of Two

To project something means to blanket the object with a detail that is either permanent or temporary. Projecting light textures in the engine provide enhanced floor detail while projecting a texture onto an object is considered to be baking the projected information to the new topology/geometry.

##
Project

##
Q

In systems that support multi-sided faces, polygons and faces are equivalent. However, most rendering hardware supports only 3- or 4-sided faces, so polygons are represented as multiple faces. When referenced as a quad it means this is a 4-sided face.

##
Quad

##
R

A form of computer storage
 which stores frequently used program instructions to increase the general speed of a system. A random-access
memory device allows data
items to be read
or written in almost the same amount of time irrespective of the physical location of data inside the memory.

##
Random Access Memory (RAM)

The task of taking an image described in a vector
 format (shapes) and converting it into a raster image
 (pixels
or dots)
for storage in a bitmap
 file format. It refers to both rasterisation of models
 and 2D rendering primitives.

##
Rasterize

The use of ray–surface intersection tests
 to solve a variety of problems in computer graphics
and computational geometry. Typically a mouse cursor or crosshair will ray cast from a camera and provide the Entity ID needed to transform the object in 3D space.

##
Ray Cast

A technique for generating an image
 by tracing the path of light
 through pixels
 in an image plane
 and simulating the effects of its encounters with virtual objects. The technique is capable of producing a very high degree of visual realism, usually higher than that of typical scanline rendering
 methods, but at a greater cost.

##
Ray Tracing

A sub-field of computer graphics
 focused on producing and analyzing images in real-time
. The term is most often used in reference to interactive 3D computer graphics
, typically using a GPU
, with video games
the most noticeable users
. The term can also refer to anything from rendering an application
's GUI
 to real-time image processing
 and image analysis.

##
Real-time

##
Render to Texture

Sometimes over the course of modelling you will want to wrap a new topology around an object to either sculpt finer detail or bake a very precise normal map for photoreal results. This is simply tracing the pattern over the new object and transferring the details through baking.

##
Re-topology

Refers to the act of weighting a polygon mesh to a skeleton for the purposes of animation. The

“mesh” is the skin, and it is stuck to the “bones” of the animation rig, which form a skeleton that can then be manipulated by an animator to pose and animate the model.

##
Rigging

An additive color model
 in which red, green, and blue
 light are added together in various ways to reproduce a broad array of colors.
 The name of the model comes from the initials of the three additive primary colors,
red, green and blue.

##
RGB

The
roll axis
 (or
longitudinal axis
) has its origin at the center of gravity and is directed forward, parallel to the fuselage reference line.

##
Roll

The rotational axis of an object still adheres to Cartesian Coordinates (X,Y,Z) and has the terms of Yaw, Pitch, and Roll to define the look and feel of say an plane in a scene.

##
Rotational Axis

##
S

The use of software that offers tools to push, pull, smooth, grab, pinch or otherwise manipulate a digital object as if it were made of a real-life substance such as clay.

##
Sculpting

At the base of all materials are source files called Shaders that drive specific qualities at runtime while stripping out extra features that could cost performance. Various shaders that ship with CRYENGINE include Illum, Glass, Eye, and Skin.

##
Shading

The term skinning usually refers to assigning bone weights to the vertices of the model.

##
Skinning

A group of polygons
 in a mesh
 which should appear to form a smooth surface
. P
olygons in a mesh that should appear to be smoothly connected, smoothing groups allow 3D modeling software
 to estimate the surface normal
at any point on the mesh, by averaging the surface normals
 or vertex normals
in the mesh data that describes the mesh.

##
Smoothing Groups

Sorting is the term used to prioritize objects on a screen. This can be found in say glass that needs to have a priority to stack correctly when viewing it. To the sorting of layers on your UI Element when creating Scaleform assets that need to exist in the same place at the same time.

##
Sorting

Splat maps are a term for a projected texture over the terrain generation to provide even greater variation for the end result.

##
Splat Maps

Frequently refers to a piecewise polynomial (parametric curve).
 Splines are popular curves in these subfields because of the simplicity of their construction, their ease and accuracy of evaluation, and their capacity to approximate complex shapes through curve fitting
 and interactive curve design.

##
Spline

A two-dimensional bitmap
 that is integrated into a larger scene. Usually constrained to be oriented to always look at the camera and is a favorite of showing large forests and trees through a single plane.

##
Sprite

A graphic organizer in the form of illustrations and images
displayed in sequence for the purpose of pre-visualizing
 a motion picture
, animation
, motion graphics
 or an interactive media

sequence.

##
Storyboard

An XML
-based vector image format
 for two-dimensional
 graphics with support for interactivity and animation.

##
Scalable Vector Graphics (SVG)

##
T

A texel is each pixel of a texture during the time the texture is being processed by the game engine After the engine performs calculations to project the texture onto polygons, the texture pixels are transformed into texels. Then the engine renders the scene, and at that point it transforms those texels into screen pixels.

##
Texel

An atlas describes the method of packing many separate textures together into a single texture. Other common names for this are “decal sheet”, “packed texture.”

##
Texture Atlas

Baking is the process of transferring details from one model to another. The baking starts a certain distance out from the model (usually a low-resolution model for game use), and casts rays inwards towards another model (usually a high-resolution sculpt).

##
Texture Baking

Compression is a technique to use larger or more textures in the same amount of memory and graphics bus bandwidth.

##
Texture Compression

Coordinates, also called UVs, are pairs of numbers stored in the vertices of a mesh. These numbers are often used to stretch a 2D texture onto a 3D mesh, but they can be used for other things like coloring the mesh, controlling the flow across the surface, etc.

##
Texture Coordinates

Filtering is used whenever a texture is altered by the game engine to eliminate jagged edges and shimmering pixels.

##
Texture Filtering

There are various types of textures that are associated with any given material. Some of the most common are listed here and are all combined to create a believable material in the end through a technique known as compositing:

-
Albedo - the base color information of your object which has the light and shadow information stripped from the captured image.

-
Specular - This map controls the reflectivity of a surface and can be driven by a texture map or specific scientific values (example: 60,60,60 Skin)

-
Normal/Gloss - A specific map that modifies vertex normals in a finer detail and the gloss map defines how wide or narrow the specular highlights appear.

##
Texture Types

A format that is known as TARGA or the Truevision format which allows for you to save out color channel and alpha information. This is a standard texture format in most game engines.

##
TGA

TIF is a file format that is used through the CryTIF image exporter inside of Photoshop. The term stands for Tagged Image File Format and due to this ability to tag or store metadata you can define the resolution and Mipmapping or presets when saving out the file.

##
TIF

The process of repeating the UVs or material of an object in order to get the highest repetition possible without giving away that the material is indeed repeating.

##
Tiling

These values are the Position, Rotation, and Scale of an object and should be known not only when using objects in an Editor but also when exporting objects from other 3D Editors. Holding on to these offsets over the course of your development will break your end product.

##
Transforms

The transparency of an object can be seen in multiple types of surfaces ranging from the typical glass to the transparency/translucency of a vegetation object within the scene. Sorting is key to this feature and further results can be refined using Depth Peeling or Order Independent Transparency.

##
Transparency

In relation to the point and the line with 2 points you have the most primitive form of a face in the triangle or "tri" for short. This type of face is universally the face that all game engines run on since it provides the proper deformation and material surface resolution to produce realistic results.

##
Triangle

##
V

The most simple form of all geometry is the vertex and it is the foundation for all types of geometry (line, tri, quad, and ngon). These vertices correlate to the model shape, the UVs for materials, and even skinning influence when conducting advanced rigging.

##
Vertex

A generic facial image that can be used to describe a particular sound. A viseme is the visual

equivalent of a phoneme or unit of sound in spoken language. Visemes and phonemes do not share a oneto-one correspondence. Often several phonemes correspond to a single viseme, as several phonemes look the same on the face when produced.

##
Viseme

A value on a regular grid
 in 3D
 space. As with pixels
 in a bitmap
, voxels themselves do not typically have their position
 explicitly encoded along with their values. Instead, rendering systems infer the position of a voxel based upon its position relative to other voxels.

##
Voxel

##
Y

Has its origin at the center of gravity and is directed towards the bottom of the aircraft, perpendicular
 to the wings and to the fuselage reference line. Motion about this axis is called
**
yaw
**
. A positive yawing motion moves the nose of the aircraft to the right.

The rudder
 is the primary control of yaw.

##
Yaw

##
Z

Known as
depth buffering
, is the management of image depth coordinates
 in 3D graphics
, usually done in hardware, sometimes in software
 It is one solution to the visibility problem
, which is the problem of deciding which elements of a rendered scene are visible, and which are hidden. The painter's algorithm
 is another common solution which, though less efficient, can also handle non-opaque scene elements.

##
Z-buffer

A phenomenon in 3D rendering
 that occurs when two or more primitives
 have similar or identical values in the z-buffer
. It is particularly prevalent with coplanar
 polygons, where two faces occupy essentially the same space, with neither in front.

##
Z-fighting
