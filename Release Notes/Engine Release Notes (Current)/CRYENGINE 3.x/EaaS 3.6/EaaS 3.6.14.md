# EaaS 3.6.14

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/47316993/pages/44963020
- Page ID: 44963020
- Breadcrumb: Engine Release Notes (Current) > CRYENGINE 3.x > EaaS 3.6 > EaaS 3.6.14
- Parent: EaaS 3.6

## Content

Released 19th December, 2014

##
Editor

-
**
Fixed
**
: Clearing registry data also resets shortcuts during runtime (CE-4155)

-
**
Fixed
**
: Closing and re-opening the structure tab in VE crashes the editor (CE-5034)

##
Engine

-
**
Fixed
**
: (Input) Fixed small bug in ForceFeedbackEvent() (CE-5129)

-
**
Fixed
**
: (Animation) Fixed crash when enabling debug for physicalized bone and face attachment

-
**
Fixed
**
: (Server) No longer assume a HUD is always present (CE-5113)

-
**
Fixed
**
: (JobSystem) TextureCompiler invoker causing invalid JobState counter (CE-5079)

-
**
Fixed
**
: (Animation) Removed VEG sequencing code in CActionScope::CalculateFragmentTimeRemaining() for consistency (CE-5175)

-
**
Fixed
**
: (Audio) Fixed audio object ID invalidation on audio proxies during Save/Load

##
Renderer

-
**
Fixed
**
: Fixed gbuffer velocity generation when tesselation is enabled (CE-3335)

-
**
Fixed
**
: Fixed sun specular multiplier in standard shading path (CE-4871)

-
**
Fixed
**
: Use area lights for sub when just area light support is enabled

-
**
Fixed
**
: Fixed area lights with tiled shading

##
Tools

-
**
Fixed
**
: (RC) Slightly improved texture compression quality for certain paths

##
Assets

-
**
Fixed:
**
(UI) Clients can only join the server at the top of the server list
