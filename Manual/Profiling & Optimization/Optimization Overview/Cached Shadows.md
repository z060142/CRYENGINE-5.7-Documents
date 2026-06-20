# Cached Shadows

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/26215322
- Page ID: 26215322
- Breadcrumb: Profiling & Optimization > Optimization Overview > Cached Shadows
- Parent: Optimization Overview

## Content

### Overview

Cached shadows are a very effective optimization method that is used to reduce the number of shadow draw calls, and at the same time increase the shadow casting and receiving range. Starting from a defined cascade number, subsequent shadow cascades can be rendered once, and then kept in memory. CRYENGINE still samples shadows from the cached cascades, but once the cached cascade is initialized no more draw calls are spent on updating it. This strategy enables long range distant shadows at almost no cost.

*Shadow cascade visualization: starting from the blue cascade all subsequent cascades are cached enabling a shadow covered range of more than 16 km*

### Placement and Update

Cached shadow cascades are centered around the camera by default, and automatically recenter (and update) once the camera gets too close to the cascade border.

This can potentially cause a slight stall as a large number of shadow casting items need to be rendered for one frame. In practice however, this hasn't caused any issues so far. For convenience, a warning message is displayed in the console each time a cached shadow cascade is updated.

The automated placement can, however, be overridden via flowgraph. The **Environment:RecomputeStaticShadows** node takes the world space min/max positions of the bounding area for the first cached cascade. Bounding boxes for subsequent cached cascades are scaled versions of the preceding cascades and are based on the * NextCascadeScale* multiplier. The * Trigger* input causes an update of all cached shadow cascades.

### Dynamic Distance Shadows

Cached shadows work very well with static objects, however, dynamic objects won't get their shadows updated when moving. This can be more or less noticeable depending on the case - for a large wind mill for example the error can be quite obvious at medium distance. To overcome this, dynamic objects can selectively be excluded from the cache and rendered to the standard cascades. The performance overhead of enabling the feature for a limited number of entities is generally quite low.

To enable dynamic distance shadows for an object, enable the option **DynamicDistanceShadows** on the entity.

### Notes

- Cached shadows are rather memory intensive: the default configuration requires approximately **130 MB** of video memory.
- Resolutions for individual cached cascades can be set via CVar (see below):
- With automated placement, the selected resolution combined with the desired world space pixel density (derived from the approximate logarithmic split scheme) determines the world space area covered by each cascade. Lowering the resolution will thus lower the shadowed range for each cascade, but still maintains shadow quality.
- With manual placement the available resolution is uniformly stretched across the cascade. Thus, lower resolution will result in lower shadow quality at the same world space coverage.
- Make sure all your shaders have been compiled before triggering an update or some objects may not be rendered into the cached shadow maps.

### Related CVars

- **r_ShadowsCache**: Cache all sun shadow cascades above CVar 0=no cached cascades, 1=cache first cascade and up, 2=cache second cascade and up.
- **r_ShadowsCacheResolutions**: The resolution of the cached cascades.
- **r_ShadowsCacheFormat**: Storage format for cached shadow maps: 0=D32: 32 bit float, 1=D16: 16 bit integer.
- **e_ShadowsCacheUpdate**: Trigger updates of cached shadow maps: 0=no update, 1=one update, 2=continuous updates.
- **e_ShadowsCacheObjectLod**: The LOD used for rendering objects into the cached shadow maps.
- **e_ShadowsCascadesDebug:** Enables the Debug View Mode: 0 or 1 where 1=enable (as shown above).
- **e_DynamicDistanceShadows**: Toggles support for having selected objects cast dynamic shadows.

[Placement and Update](#placement-and-update)[Dynamic Distance Shadows](#dynamic-distance-shadows)[Notes](#notes)[Related CVars](#related-cvars)
