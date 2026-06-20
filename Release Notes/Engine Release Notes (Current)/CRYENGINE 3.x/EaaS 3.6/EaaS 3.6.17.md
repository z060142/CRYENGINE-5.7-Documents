# EaaS 3.6.17

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/47316993/pages/44963023
- Page ID: 44963023
- Breadcrumb: Engine Release Notes (Current) > CRYENGINE 3.x > EaaS 3.6 > EaaS 3.6.17
- Parent: EaaS 3.6

## Content

Released 20th February, 2015

##
Engine

-
**
Fixed
**
: (Common) Enums and TypeInfo: Reimplemented DEFINE_ENUM_VALS to work the same as DEFINE_ENUM, without needing 2 macros. Fixed SurfaceType enum to show surface names. Removed unused deep_ptr<> class. (CE-4924, CE-5201, CE-5283, CE-5324, CE-5325).

-
**
Fixed
**
: (CryDesigner) Fixed a bug about a top polygon of a created box on a terrain being warped (CE-5421).

-
**
Fixed
**
: (Particles) Fixed logic which deleted some used effects after level load, causing crashes.

-
**
Fixed
**
: (Particles) Fixed FPE in particle vortex rotation (CE-5103).

-
**
Fixed
**
: (Particles) Emitters now update when e_ParticlesThread = 0.

-
**
Fixed
**
: (Particles) Memory overwrite when out of particle vertex memory (CE-5514).

-
**
Fixed
**
: (Particles) Collision and timing issues, that prevented child decals from spawning or sticking; fixed infinite look-ahead on particle collisions (CE-5456).

-
**
Fixed
**
: (Particles) Errors in reading library versions <= 20: Facing conversion, Color splines.

-
**
Fixed
**
: (Particles) Restored Horizontal facing behavior (aligns particles regardless of forces or turbulence). Correctly align particles for all combinations of Facing / OrientToVelocity.

##
Renderer

-
**
Fixed
**
: (Renderer) NULL renderer crash (CE-5371).

-
**
Fixed
**
: (Renderer) Deferred decals now work with non-orthogonal transforms (e.g. stretched particles). Simplified and optimized transformations, fixed confusing axis labels.

##
Game

-
**
Fixed
**
: (AISystem) Collision Avoidance was not taking CAIPlayers into consideration (CE-5523).

-
**
Fixed
**
: (EntitySystem) CScriptBind_Entity::SetLinkTarget() was inspecting the wrong parameter (CE-5270).
