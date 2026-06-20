# Rendering & Shader Programming

CRYENGINE's rendering pipeline is split across two major modules:
`CryRenderer` (GPU rendering, shaders, textures, meshes) and `Cry3DEngine`
(3D world, terrain, vegetation, sky, water, occlusion). This page covers
the C++ programming interfaces and concepts for both.

> **Shader authoring:** For writing `.cfx` shader files, extension files,
> shader flags, and common techniques, see
> [Shaders (API Reference)](../../API%20Reference/_Shaders.md). This page
> focuses on the C++ rendering APIs.

---

## Architecture

```
IRenderer (GPU rendering)
  ├── IShader / SShaderItem     — shader loading and management
  ├── ITexture                  — texture creation and streaming
  ├── IRenderMesh               — GPU mesh buffers
  ├── IRenderAuxGeom            — debug drawing
  ├── IRenderView               — render views (main, shadow, recursive)
  ├── IStereoRenderer           — VR stereo rendering
  └── IGpuParticles             — GPU particle system

I3DEngine (3D world)
  ├── IRenderNode               — base renderable object
  ├── IStatObj                  — static geometry
  ├── IMaterial                 — material system
  ├── ITerrain                  — terrain engine
  ├── IVisArea                  — visibility areas / portals
  ├── IWaterVolume              — water volumes
  ├── IClipVolume              — clip volumes
  ├── ITimeOfDay                — time-of-day system
  └── IGeomCache                — Alembic geometry cache
```

---

## IRenderer — GPU Rendering

**Header:** `Code/CryEngine/CryCommon/CryRenderer/IRenderer.h` · via `gEnv->pRenderer`

### Render Backends

`ERenderType` identifies the active backend: `Direct3D11`, `Direct3D12`,
`Vulkan`, or `GNM` (PS4). Query via `gEnv->pRenderer->GetRenderType()`.

### Shader Loading

```cpp
IShader*    pShader    = gEnv->pRenderer->EF_LoadShader("Illum");
SShaderItem shaderItem = gEnv->pRenderer->EF_LoadShaderItem("Illum");
gEnv->pRenderer->EF_ReloadShaderFiles(0);  // reload all shaders at runtime
gEnv->pRenderer->EF_SetShaderQuality(eST_General, eSQ_High);
```

For shader file format (`.cfx`), extension files (`.ext`), shader flags, and
techniques, see [Shaders (API Reference)](../../API%20Reference/_Shaders.md).

### Texture Management

```cpp
ITexture* pTex = gEnv->pRenderer->EF_LoadTexture("textures/defaults/white.dds");
ITexture* pTex = gEnv->pRenderer->EF_GetTextureByName("white");
ITexture* pTex = gEnv->pRenderer->CreateTexture("MyTex", 256, 256, 1,
                         pData, eTF_R8G8B8A8, FT_DONT_STREAM);
gEnv->pRenderer->EF_ReloadTextures();
```

### Render Mesh

```cpp
_smart_ptr<IRenderMesh> pMesh = gEnv->pRenderer->CreateRenderMesh(
    "MyMesh", "source.cgf", nullptr, eRMT_Static);

// With vertex/index data:
_smart_ptr<IRenderMesh> pMesh = gEnv->pRenderer->CreateRenderMeshInitialized(
    pVertices, nVertCount, vertexFormat,
    pIndices, nIndices, prtTriangleList,
    "MyMesh", "source.cgf", eRMT_Static);
```

### Debug Drawing (IRenderAuxGeom)

Per-frame debug drawing (must be called every frame):

```cpp
IRenderAuxGeom* pAux = gEnv->pRenderer->GetIRenderAuxGeom();
pAux->DrawSphere(Vec3(0,0,0), 1.0f, ColorB(255,0,0));
pAux->DrawLine(Vec3(0,0,0), Vec3(1,0,0), ColorB(0,255,0));
pAux->DrawAABB(AABB(Vec3(-1), Vec3(1)), ColorB(0,0,255));
pAux->Draw2dLabel(100, 100, 1.5f, ColorF(1,1,1), false, "Debug text");
```

### Post-Effects

```cpp
gEnv->pRenderer->EF_SetPostEffectParam("Global_User_Brightness", 1.5f);
gEnv->pRenderer->EF_SetPostEffectParamVec4("Global_User_ColorC", Vec4(1,1,1,1));
int32 id = gEnv->pRenderer->EF_GetPostEffectID("Global_User_Brightness");
gEnv->pRenderer->EF_ResetPostEffects();
```

For post-effect configuration in the editor, see
[Post-processing](../Post-processing.md).

### Screenshots & Frame Capture

```cpp
gEnv->pRenderer->ScreenShot("screenshot.jpg");
gEnv->pRenderer->ReadFrameBuffer(pPixels, width, height);
```

### GPU Info

```cpp
IRenderer::SGpuInfo info;
gEnv->pRenderer->QueryActiveGpuInfo(info);
// info.name, info.dedicatedVideoMemory, etc.
```

### Render Views

Render views represent the rendering target context (main, shadow, etc.):

```cpp
CRenderView* pView = gEnv->pRenderer->GetOrCreateRenderView();
gEnv->pRenderer->ReturnRenderView(pView);  // return to pool when done
```

---

## I3DEngine — 3D World

**Header:** `Code/CryEngine/CryCommon/Cry3DEngine/I3DEngine.h` · via `gEnv->p3DEngine`

### Static Geometry (IStatObj)

```cpp
IStatObj* pStatObj = gEnv->p3DEngine->LoadStatObj("objects/default/primitive_box.cgf");
IStatObj* pFound   = gEnv->p3DEngine->FindStatObjectByFilename(".../primitive_box.cgf");
IStatObj* pNew     = gEnv->p3DEngine->CreateStatObj();
```

### Render Nodes

`IRenderNode` is the base type for all renderable objects in the 3D world
(brushes, lights, particles, vegetation, etc.):

```cpp
IRenderNode* pNode = gEnv->p3DEngine->CreateRenderNode(eERType_Brush);
gEnv->p3DEngine->RegisterEntity(pNode);
gEnv->p3DEngine->UnRegisterEntityDirect(pNode);
gEnv->p3DEngine->DeleteRenderNode(pNode);
```

### Terrain

```cpp
float z        = gEnv->p3DEngine->GetTerrainElevation(x, y);
Vec3  normal   = gEnv->p3DEngine->GetTerrainSurfaceNormal(pos);
int   size     = gEnv->p3DEngine->GetTerrainSize();
ITerrain* pTer = gEnv->p3DEngine->GetITerrain();
```

### Water / Ocean

```cpp
bool  bUnderwater = gEnv->p3DEngine->IsUnderWater(pos);
float waterLevel  = gEnv->p3DEngine->GetWaterLevel();
gEnv->p3DEngine->AddWaterRipple(pos, 1.0f, 1.0f);
```

### Sky & Lighting

```cpp
gEnv->p3DEngine->SetSkyColor(Vec3(0.3f, 0.5f, 0.8f));
gEnv->p3DEngine->SetSunColor(Vec3(1.0f, 0.9f, 0.7f));
Vec3 sunDir = gEnv->p3DEngine->GetSunDir();
gEnv->p3DEngine->SetSkyLightParameters(sunDir, intensity, Km, Kr, g, wavelengths);
```

### Global 3D Engine Parameters

Set via `SetGlobalParameter(E3DEngineParameter, Vec3)`. Key parameters include
sun/sky/fog colors (`E3DPARAM_SUN_COLOR`, `E3DPARAM_FOG_COLOR`), HDR filmic
tonemapping, eye adaptation, bloom, color grading, volumetric fog, volumetric
clouds, and ocean fog. The `E3DEngineParameter` enum defines 60+ entries.

### Decals

```cpp
CryEngineDecalInfo decal;
decal.vPos      = hitPosition;
decal.vNormal   = hitNormal;
decal.fSize     = 1.0f;
decal.pMaterial = pDecalMaterial;
gEnv->p3DEngine->CreateDecal(decal);
```

### VisAreas & ClipVolumes

VisAreas (portals) control visibility between indoor areas:

```cpp
IVisArea* pArea = gEnv->p3DEngine->GetVisAreaFromPos(pos);
bool connected = gEnv->p3DEngine->IsVisAreasConnected(pArea1, pArea2);
IClipVolume* pVol = gEnv->p3DEngine->CreateClipVolume();
```

### Vegetation

```cpp
IStatInstGroup group;
group.pStatObj    = pTreeModel;
group.fDensity    = 0.5f;
gEnv->p3DEngine->SetStatInstGroup(groupId, group);

IRenderNode* pVeg = gEnv->p3DEngine->GetITerrain()->AddVegetationInstance(
    groupId, pos, scale, brightness, angle);
```

### Level Loading

```cpp
// Blocking
gEnv->p3DEngine->LoadLevel("levels/example", missionXml);

// Time-sliced (for loading screens)
gEnv->p3DEngine->StartLoadLevel("levels/example", missionXml);
while (gEnv->p3DEngine->UpdateLoadLevelStatus() == I3DEngine::ELevelLoadStatus::InProgress) {
    // update loading screen
}
gEnv->p3DEngine->UnloadLevel();
```

---

## IMaterial — Material System

**Header:** `Code/CryEngine/CryCommon/Cry3DEngine/IMaterial.h`

```cpp
IMaterial* pMat = gEnv->p3DEngine->GetMaterialManager()->LoadMaterial("materials/presets/wood.mtl");
IMaterial* pCurrent = pStatObj->GetMaterial();
pStatObj->SetMaterial(pMat);
IMaterial* pClone = pMat->GetMaterialManager()->CloneMaterial(pMat);  // per-instance
```

For material editor usage, see [Materials](../Materials.md).

---

## ITimeOfDay — Time-of-Day System

**Header:** `Code/CryEngine/CryCommon/Cry3DEngine/ITimeOfDay.h`

```cpp
ITimeOfDay* pTOD = gEnv->p3DEngine->GetTimeOfDay();
pTOD->SetTime(12.0f);  // 12:00 noon
float time = pTOD->GetTime();
pTOD->SetVariableValue(Vec3(1,0,0), ITimeOfDay::PARAM_SUN_COLOR);
pTOD->SetVariableValue(Vec3(0.5,0.6,0.7), ITimeOfDay::PARAM_FOG_COLOR);
```

---

## IGeomCache — Alembic Geometry Cache

**Header:** `Code/CryEngine/CryCommon/Cry3DEngine/IGeomCache.h`

```cpp
IGeomCache* pCache = gEnv->p3DEngine->LoadGeomCache("animations/explosion.abc");
pCache->SetPlaybackTime(2.5f);
pCache->SetLooping(true);
bool bPlaying = pCache->IsPlaying();
```

---

## GPU Particles

**Header:** `Code/CryEngine/CryCommon/CryRenderer/IGpuParticles.h`

```cpp
gpu_pfx2::IManager* pGpuParticles = gEnv->pRenderer->GetGpuParticleManager();
```

For particle editor usage, see [Particles](Particles.md).

---

## Stereo / VR Rendering

**Header:** `Code/CryEngine/CryCommon/CryRenderer/IStereoRenderer.h`

```cpp
IStereoRenderer* pStereo = gEnv->pRenderer->GetIStereoRenderer();
bool bStereo = gEnv->pRenderer->IsStereoEnabled();
```

For VR setup, see [Virtual Reality](../Virtual%20Reality.md) and
[Stereoscopic Rendering](Stereoscopic%20Rendering.md).

---

## Quick Reference

```cpp
IRenderer*       pRend = gEnv->pRenderer;
I3DEngine*       p3D   = gEnv->p3DEngine;
IRenderAuxGeom*  pAux  = pRend->GetIRenderAuxGeom();

IShader*     pShader = pRend->EF_LoadShader("Illum");
SShaderItem  item    = pRend->EF_LoadShaderItem("Illum");
ITexture*    pTex    = pRend->EF_LoadTexture("textures/defaults/white.dds");
IStatObj*    pObj    = p3D->LoadStatObj("objects/default/primitive_box.cgf");

float     z          = p3D->GetTerrainElevation(x, y);
bool      bUnderwater = p3D->IsUnderWater(pos);
Vec3      sunDir     = p3D->GetSunDir();

pAux->DrawSphere(pos, 1.0f, ColorB(255,0,0));
pAux->Draw2dLabel(100, 100, 1.5f, ColorF(1,1,1), false, "Debug");

pRend->EF_SetPostEffectParam("Global_User_Brightness", 1.5f);
pRend->ScreenShot("capture.jpg");
```

---

## Related Documentation

- [Shaders (API Reference)](../../API%20Reference/_Shaders.md) — .cfx shader format, techniques, flags
- [Entity Slots & Geometry](../../API%20Reference/Entity/Slots,%20Geometry%20and%20Effects.md) — entity slot types
- [Engine Architecture Overview](../CRYENGINE%20-%20Getting%20Started/Engine%20Architecture%20Overview.md) — module structure, main loop
- [Materials](../Materials.md) — material editor
- [Post-processing](../Post-processing.md) — post-effect configuration
- [Particles](Particles.md) — particle system
- [Lighting](Lighting.md) — lighting overview
- [Stereoscopic Rendering](Stereoscopic%20Rendering.md) — stereo rendering
- [Virtual Reality](../Virtual%20Reality.md) — VR setup
- [Profiling & Optimization](../Profiling%20&%20Optimization.md) — render debug CVars