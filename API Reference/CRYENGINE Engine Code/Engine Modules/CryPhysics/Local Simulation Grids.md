# Local Simulation Grids

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/28182887
- Page ID: 28182887
- Breadcrumb: CRYENGINE Engine Code > Engine Modules > CryPhysics > Local Simulation Grids
- Parent: CryPhysics

## Content

Since version 5.2, CryPhysics supports multiple physical entity grids.
**
SetupEntityGrid
**
 can create a grid that's attached to a 'host' physical entity, and in that case it returns a pointer to the newly created grid object (which implements IPhysicalEntity interface). All interface structures that deal with world coordinates are augmented with a grid object pointer (is left unused in change requests, it assumes the current entity's grid). It's possible to have grid host entities reside in other grids, i.e. having grid hierarchies. It's not possible, however, for an entity to host more than one grid.

Simulation-wise, grids are considered 'inertial systems' (i.e. the entities are simulated as if they were in a static world), although the system can account for relative acceleration by manually applying impulses if acceleration of the grid host entity is above a certain adjustable threshold. This way it's possible to have local simulation perfectly still if the host's movement is smooth enough.

Grids can have portals to their parent grids (i.e. grids that their host entities belong to). Portals affect
**
GetEntitiesAround
**
 and
**
RayWorldIntersection
**
 functionality. For GEA, all queries that touch a portal's volume (specifically, oriented bounding box of its first geometry) return results from the other (portal's) grid as well. For RWI, rays that hit portal geometries use recursive RWI calls in the other grid. Since RWI still checks for flags, it's possible to have different portal geometries for GEA and RWI. Normally, portals are created in a twin fashion - there's a local portal that links to the outer grid, and in the outer grid there's a corresponding portal that links to the inner grid. To create a portal, one has to prepare two portal objects registered in different grids (which can be either or a placeholders, with trigger simulation class SC_TRIGGER), and attach them together with pe_action_add_constraint.

Internally, all entity collision checks and simulation loops are grid-aware and do cross-grid transformations when necessary.

Since multi-grid support incurs some minor performance and memory footprint cost, it's currently turned off by default with a
MULTI_GRID define (to enable it, CryPhysics has to be re-compiled).
