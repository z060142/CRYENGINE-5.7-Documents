# Interpol Nodes

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/29450599
- Page ID: 29450599
- Breadcrumb: Editor Tools > Flow Graph > Flow Graph Node Reference > Interpol Nodes
- Parent: Flow Graph Node Reference

## Content

### Color

Interpol nodes can be used to linearly calculate from an initial value to an end value within a given time frame.

![Image](https://www.cryengine.com/docs/static/attachments/29687833)

**Inputs**

Port | Type | Description
--- | --- | ---
**Start** | Any | Starts interpolation
**Stop** | Any | Stops interpolation
**StartValue** | Vec3 | Starting value for color
**EndValue** | Vec3 | Ending value for color
**Time** | Float | Interpolation duration in seconds
**UpdateFrequency** | Float | Interpolation update frequency in seconds. 0 = every frame

**Outputs**

Port | Type | Description
--- | --- | ---
**Value** | Vec3 | Current value
**Done** | Any | Triggered when finished

### Easing

This node applies a transition-function to its input and returns its result.

![Image](https://www.cryengine.com/docs/static/attachments/29687832)

### Float

Interpol nodes can be used to linearly calculate from an initial value to an end value within a given time frame.

![Image](https://www.cryengine.com/docs/static/attachments/29687831)

**Inputs**

Port | Type | Description
--- | --- | ---
**Start** | Any | Starts interpolation
**Stop** | Any | Stops interpolation
**StartValue** | Float | Starting value for floating point
**EndValue** | Float | Ending value for floating point
**Time** | Float | Interpolation duration in seconds
**UpdateFrequency** | Float | Interpolation update frequency in seconds. 0 = every frame

**Outputs**

Port | Type | Description
--- | --- | ---
**Value** | Float | Current value
**Done** | Any | Triggered when finished

### Int

Interpol nodes can be used to linearly calculate from an initial value to an end value within a given time frame.

![Image](https://www.cryengine.com/docs/static/attachments/29687830)

**Input**

Port | Type | Description
--- | --- | ---
**Start** | Any | Starts interpolation
**Stop** | Any | Stops interpolation
**StartValue** | Integer | Starting value for integer
**EndValue** | Integer | Ending value for integer
**Time** | Float | Interpolation duration in seconds
**UpdateFrequency** | Float | Interpolation update frequency in seconds. 0 = every frame

**Outputs**

Port | Type | Description
--- | --- | ---
**Value** | Integer | Current value
**Done** | Any | Triggered when finished

### SmoothColor

Smooth nodes can be used to calculate an initial value to an end value within a given time frame. Calculation will slow as it reaches the end value.

See SmoothCD in Cry_Math.h for more in-depth description on how the calculation is dampened.

![Image](https://www.cryengine.com/docs/static/attachments/29687829)

**Inputs**

Port | Type | Description
--- | --- | ---
**InitialValue** | Vec3 | Initial interpolation value for color
**TargetValue** | Vec3 | Target interpolation value for color
**Time** | Float | Interpolation duration in seconds

**Outputs**

Port | Type | Description
--- | --- | ---
**Value** | Vec3 | Current value
**Done** | Any | Triggered when finished

### SmoothFloat

Smooth nodes can be used to calculate an initial value to an end value within a given time frame. The calculation will slow as it reaches the end value.

![Image](https://www.cryengine.com/docs/static/attachments/29687828)

**Inputs**

Port | Type | Description
--- | --- | ---
**InitialValue** | Float | Initial interpolation value for floating point
**TargetValue** | Float | Target interpolation value for floating point
**Time** | Float | Interpolation duration in seconds

**Outputs**

Port | Type | Description
--- | --- | ---
**Value** | Float | Current value
**Done** | Any | Triggered when finished

### SmoothInt

Smooth nodes can be used to calculate an initial value to an end value within a given time frame. Calculation will slow as it reaches the end value.

![Image](https://www.cryengine.com/docs/static/attachments/29687827)

**Inputs**

Port | Type | Description
--- | --- | ---
**InitialValue** | Integer | Initial interpolation value for integer
**TargetValue** | Integer | Target interpolation value for integer
**Time** | Float | Interpolation duration in seconds

**Outputs**

Port | Type | Description
--- | --- | ---
**Value** | Integer | Current value
**Done** | Any | Triggered when finished

### SmoothVec3

Smooth nodes can be used to calculate an initial value to an end value within a given time frame. Calculation will slow as it reaches the end value.

![Image](https://www.cryengine.com/docs/static/attachments/29687826)

**Inputs**

Port | Type | Description
--- | --- | ---
**InitialValue** | Vec3 | Initial interpolation value for Vec3
**TargetValue** | Vec3 | Target interpolation value for Vec3
**Time** | Float | Interpolation duration in seconds

**Outputs**

Port | Type | Description
--- | --- | ---
**Value** | Vec3 | Current value
**Done** | Any | Triggered when finished

### Vec3

Interpol nodes can be used to linearly calculate from an initial value to an end value within a given time frame.

![Image](https://www.cryengine.com/docs/static/attachments/29687825)

**Inputs**

Port | Type | Description
--- | --- | ---
**Start** | Any | Starts interpolation
**Stop** | Any | Stops interpolation
**StartValue** | Vec3 | Starting value for Vec3
**EndValue** | Vec3 | Ending value for Vec3
**Time** | Float | Interpolation duration in seconds
**UpdateFrequency** | Float | Interpolation update frequency in seconds. 0 = every frame

**Outputs**

Port | Type | Description
--- | --- | ---
**Value** | Vec3 | Current value
**Done** | Any | Triggered when finished

[Color](#color)[Easing](#easing)[Float](#float)[Int](#int)[SmoothColor](#smoothcolor)[SmoothFloat](#smoothfloat)[SmoothInt](#smoothint)[SmoothVec3](#smoothvec3)[Vec3](#vec3)
