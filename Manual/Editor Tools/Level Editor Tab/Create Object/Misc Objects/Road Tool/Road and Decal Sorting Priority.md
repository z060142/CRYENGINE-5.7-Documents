# Road and Decal Sorting Priority

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/36869885
- Page ID: 36869885
- Breadcrumb: Editor Tools > Level Editor Tab > Create Object > Misc Objects > Road Tool > Road and Decal Sorting Priority
- Parent: Road Tool

## Content

##
Overview

Any road and decal can be set up using a sorting priority. This feature gives the user the control to decide in which order roads and decals are rendered in the engine.

[Image: /docs/static/attachments/44970941]

The priority can be changed from 0 to a maximum of 255.

[Image: /docs/static/attachments/44970943]

The engine uses these numbers like pages in a book. A lower number is a lower page and will be rendered to a page with a higher number. The highest number is always on top.

[Image: /docs/static/attachments/44970944]

In a setup where many roads and decals are intersecting each other, you have to make sure the objects have different sorting priorities.

[Image: /docs/static/attachments/44970945]

If you keep the value at the same numbers, the engine will miss the information on which object should be rendered on top and the assets will start to flicker in game.
