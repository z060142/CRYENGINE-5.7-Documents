# Shadow Proxies

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/26215318
- Page ID: 26215318
- Breadcrumb: Asset Prep (External) > Asset Exporting Overview > Geometry Creation Overview > Static Geometry > Shadow Proxies
- Parent: Static Geometry

## Content

[Image: /docs/static/attachments/29934003]

##
Overview

##
Sections

Shadow Proxies are a method of reducing shadow performance costs by creating a dedicated piece of (low-poly) geometry which is solely responsible for the shadow casting of that object. Shadow Proxies can also be used to alleviate shadow artifacts by giving the artist more control over which geometry casts shadows.

[#sections](
Sections
)
[#shadow-proxy-creation](
Shadow Proxy Creation
)
[#shadow-proxy-material-setup](
Shadow Proxy Material Setup
)
[#results](
Results
)

##
Shadow Proxy Creation

The amount of detail you use for your shadow proxy is up to you, though with the entire purpose of this exercise being to optimize and gain performance, the less detail the better. Keep in mind that if the Shadow Proxy mesh doesn't line up close enough with the RenderMesh then you may start noticing self-shadow artifacts.

The mesh itself can be created however you like, though treating it like you are creating a low-poly LOD is probably the best approach. There is no special setup required in the DCC tool apart from the shadow proxy being linked as a child node of the RenderMesh, and it being on its own material ID.

Below you can see an example of a shadow proxy setup being used on a vegetation object which ships with the CRYENGINE SDK (Objects/natural/trees/tree_roots/na_tree_roots_c.cgf):

For the RenderMesh, the triangle count is 3,969. For the Shadow Proxy mesh, it's 640 triangles. This will lead to a significant saving and the visual difference should be minimal, which you can see in the
[/docs/static/engines/cryengine-5/categories/23756816/pages/26215318#ShadowProxies-Results](
)
 section below.

##
Shadow Proxy Material Setup

As there is no special setup required in the DCC tool, the setup actually takes place in the material with just a couple of tweaks. As mentioned above, the Shadow Proxy should be on its own sub-material. The only change you need to make for the Shadow Proxy sub-material is to set the
**
Opacity
**
 to 0 and ensure that
**
No Shadow
**
 is
*
not
*
 checked (default setting).

Now, for the RenderMesh material, you want to have everything set as per normal, except under the Advanced properties, check the
**
No Shadow
**
 option.

This tells the engine that you don't want the shadow to be rendered from the RenderMesh, instead, use the Shadow Proxy to render the shadows.

##
Results

Below shows using a standard approach of having the RenderMesh create shadows. This results in a scene (the tree object is the only thing casting shadows) shadow triangle count of 10,218.

Note that the reason the shadow triangle count is higher than the RenderMesh triangle count is because the shadow is being generated across multiple cascades.

Using the Shadow Proxy approach, we bring the shadow triangle count down from 10,218 to just 1,890.

If we set the RenderMesh Opacity to 0 and set the Shadow Proxy opacity to 100, you can see how the Shadow Proxy is represented in-engine.

Keep in mind, however, that this is just one object and it scales with every object. If we multiply this brush several times then the savings become enormous, from 11,970 triangles to 64,714 triangles:
