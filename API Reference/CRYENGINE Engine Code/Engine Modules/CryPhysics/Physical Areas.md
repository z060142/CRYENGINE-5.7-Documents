# Physical Areas

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/24282225
- Page ID: 24282225
- Breadcrumb: CRYENGINE Engine Code > Engine Modules > CryPhysics > Physical Areas
- Parent: CryPhysics

## Content

In order to simulate various environmental effects one can use a special kind of physicalized objects - areas. They are created via several overloaded versions of AddArea function and implement IPhysicalEntity interface. They have simulation class SC_AREA (5) and can be used in world queries (such as box query and raycast query). There's also a global iterator over all registered areas.

There are several supported boundary representations for areas. It can either be a general physical geometry (either a primitive or a mesh), a polygonal boundary, or a 3d spline. Polygonal boundaries are checked whether they are close enough to lying in the same plane and if so, they are stored in a 2d form. Otherwise they are converted to general 3d triangle meshes.

Areas can be used to modify gravity and specify "medium" that has *buoyancy* and * resistance.*Water and air are the most common examples of mediums. Low-level buoyancy and resistance calculations are the same for all mediums, but there's an notable distinction in that only the smallest water area that touches an object is simulated, while air areas are applied en masse. In addition to the boundary geometry, medium areas have a boundary plane (that's mostly useful for water areas). There is a special case of heightfield boundary geometries, when the code adopts the medium plane to best fit the height data around a floating object. This is used to simulate the effects of externally animated water waves.

Areas' mediums support externally specified movement ("flow") vector. It can either be uniform or radial, with an optional falloff when approaching the boundary. For 3d spline areas radial direction is replaced with alignment to the closest spline segment. Areas with mesh geometry support per-triangle flow vectors.

Additionally the physics supports its own water simulation for water areas with polygonal boundaries. It has two separate components: volume redistribution and surface waves. If an area is requested to maintain a fixed volume, it dynamically samples physicalized geometry below it and updates water level to match that volume. Optional wave simulation uses 2d grids to locally modify the area's water level, similar to external heightfields. Unlike the latter though, it can both affect physicalized objects *and* be affected by them. Simulation-wise, both horizontal and vertical water movement is taken into account. For large water areas * tiling* is supported. 2d simulation surface is split into fixed-size square tiles, and only tiles around a specific point (typically the engine's view camera position) are simulated. Optionally, tiles that are farther away can have proportionally stronger damping.

By default, all physicalized objects are affected by all areas, but it can be disabled per object with pef_ignore_areas flag. Since usually a global air area is present, only objects that are affected "strongly enough" (based on their mass and dimensions) are considered. Note that buoyancy and resistance computations can be relatively expensive for complex meshes, so it's possible to have dedicated entity parts for that (marked with geom_floats flag).

Area sampling is exposed to other systems via CheckAreas function. Additionally, each area can be queried for its effect on a specific point.

Before any areas can be used, a global area must be added to the world. It should specify global gravity and ocean water level.
