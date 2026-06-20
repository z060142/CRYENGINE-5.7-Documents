# Environment Nodes

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/29450589
- Page ID: 29450589
- Breadcrumb: Editor Tools > Flow Graph > Flow Graph Node Reference > Environment Nodes
- Parent: Flow Graph Node Reference

## Content

### ComputeLighting

Compute the amount of light at a given point.

### MoonDirection

Set the 3DEngine's Moon Direction.

### OceanSwitch

Enable ocean rendering on demand.

### PreEntityShadows

Used to enable and specify per entity shadows.

![Image](https://www.cryengine.com/docs/static/attachments/28901285)

**Inputs**

Port | Type | Description
--- | --- | ---
**Enabled** | Boolean | Activates the node
**Trigger** | Any | Triggers the parameters
**ConstBias** | Float | Reduces any self-shadowing artifacts
**SlopeBias** | Float | Reduces any self-shadowing artifacts
**Jittering** | Float | Filters kernel size, which directly affects shadow softness
**BBoxScale** | Vec3 | Scale factor for the bounding box of the selected entity. Can be useful in case the bounding box is too small or too large
**ShadowMapSize** | Integer | Size of the custom shadow map, which is automatically rounded to the next power of two

### PresetSwitch

Used to Switch environment preset.

![Image](https://www.cryengine.com/docs/static/attachments/28901284)

### RecomputeStaticShadows

Cached shadow cascades are centered around the rendering camera by default, and automatically recenter and update once the camera gets close to the cascade border. Use this node to override this automated placement.

![Image](https://www.cryengine.com/docs/static/attachments/28901283)

**Input**

Port | Type | Description
--- | --- | ---
Trigger | Any | Activates the node
Min | Vec3 | Minimum bounding box position
Max | Vec3 | Maximum bounding box position
NextCascadesScale | Float | Input multiplier value

### RefreshStaticShadows

Used as a Static shadow helper.

![Image](https://www.cryengine.com/docs/static/attachments/28901282)

### SetOceanMaterial

Used to set the ocean material.

![Image](https://www.cryengine.com/docs/static/attachments/28901281)

**Inputs**

Port | Type | Description
--- | --- | ---
**Set** | Any | Set material on for the ocean
**Material** | String | Material to be set for the ocean

**Outputs**

Port | Type | Description
--- | --- | ---
**Success** | Any | Triggered when material set
**Failed** | Any | Triggered if an error occurred

### SkyMaterialSwitch

Used to enable sky material switching.

![Image](https://www.cryengine.com/docs/static/attachments/28901280)

**Inputs**

Port | Type | Description
--- | --- | ---
Material | String | Material to use for the sky
Start | Boolean | Start material switch
Angle | Float | Starting angle
Stretching | Float | If stretching is performed or not

### SkyboxSwitch

Node for asynchronous sky box switching.

### Sun

Set the 3DEngine's Sun Data.

### VolumetricCloudSwtich

Used to set the volumetric cloud texture.

![Image](https://www.cryengine.com/docs/static/attachments/28901278)

### Wind

Used to get and output the wind direction vector.

![Image](https://www.cryengine.com/docs/static/attachments/28901279)

**Inputs**

Port | Type | Description
--- | --- | ---
Get | Any | Get the current environment wind vector

**Outputs**

Port | Type | Description
--- | --- | ---
WindVector | Vec3 | Outputs current environment wind vector

### Deprecated Nodes

- MaterialParam
- MaterialParamSerialize

[ComputeLighting](#computelighting)[MoonDirection](#moondirection)[OceanSwitch](#oceanswitch)[PreEntityShadows](#preentityshadows)[PresetSwitch](#presetswitch)[RecomputeStaticShadows](#recomputestaticshadows)[RefreshStaticShadows](#refreshstaticshadows)[SetOceanMaterial](#setoceanmaterial)[SkyMaterialSwitch](#skymaterialswitch)[SkyboxSwitch](#skyboxswitch)[Sun](#sun)[VolumetricCloudSwtich](#volumetriccloudswtich)[Wind](#wind)[Deprecated Nodes](#deprecated-nodes)
