# Vis Area and Portals

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/26215443
- Page ID: 26215443
- Breadcrumb: Profiling & Optimization > Optimization Overview > Vis Area and Portals
- Parent: Optimization Overview

## Content

##
Overview

The Vis Area is a shape object which is used to define indoor areas for culling and optimization purposes, as well as lighting.
Objects inside a Vis Area won't be rendered from outside and vice versa, this can help with performance immensely.

Vis Areas also can be setup to occlude certain lighting elements such as the sun, which gives flexibility in setting up lighting for your indoor areas. Note that since CRYENGINE 3.6, Ambient Color is no longer supported and
[/docs/static/engines/cryengine-5/categories/23756816/pages/26215363](
Environment Probes
)
 should be used.

With Portals you can cut holes inside the Vis Areas to create an 'entrance' to the Vis Area. Portals have to be smaller than the Vis Area Shape but thick enough to protrude both the inside and outside of the Vis Area, like a door.
You can enable and disable Portals via Flow Graph and you can have multiple Portals in one Vis Area.

Click
[/docs/static/engines/cryengine-5/categories/23756816/pages/36869910](
here
)
for more information about Vis Areas and
[/docs/static/engines/cryengine-5/categories/23756816/pages/36869900](
here
)
 for the Portal documentation.
