# CRYENGINE 5.6.5

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/47316993/pages/56656270
- Page ID: 56656270
- Breadcrumb: Engine Release Notes (Current) > CRYENGINE 5 > CRYENGINE 5.6 > CRYENGINE 5.6.5
- Parent: CRYENGINE 5.6

## Content

## Animation

### Animation General

- **Fixed:**(Cloth): Added output of skin-filename - for a warning in the case of missing metadata.
- **Fixed:** Issue with view distance ratios not being refreshed correctly when propagating through attachment hierarchies.
- **Tweaked:** Shipping pose modifiers that have been missing since the 5.6.3 release.

## Audio

### Audio General

- **Tweaked:** Updated to FMOD 2.00.06.
- **Tweaked:** Updated to Wwise 2019.1.5.

## Core System

### Entity System

- **Fixed:** (DefaultComponents): Physicalized entities using CBaseMeshComponent are re-physicalized on any slot change resulting in physical properties being reset.

## Graphics and Rendering

### Renderer General

- **Fixed:** (Volumetric Fog): Fog on light probes - by bringing its GenerateLightList more in line with its counterpart in TiledLightVolumes.

## Sandbox

### Editor General

- **Fixed:** (Prefab LE): Snapping a hidden prefab to a place will un-hide the brush object inside of it, but keep the UI and helper in the invisible state.
- **Fixed:** (MayaExporter): The "Create CryExportNode" window is smaller than the content displayed.

## Tools

### Resource Compiler

**Fixed:** Converted a number of RCLogError to RCLogWarning. Will prevent the RC quitting early in the case of the Assets Folder containing an invalid skeleton. NOTE: Will still output a single error for the failing to load the skeleton after warnings (if LoadSkeletonInfo is called with bWarningsAsErrors disabled).
