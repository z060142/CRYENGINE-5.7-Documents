# ScriptBind_Particle

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/23306602
- Page ID: 23306602
- Breadcrumb: CRYENGINE API Reference > ScriptBind Reference > CRYENGINE Functions > ScriptBind_Particle
- Parent: CRYENGINE Functions

## Content

### CreateEffect

Creates a new particle effect.

```
Particle.CreateEffect( name, params )
```

Parameter | Description
--- | ---
name | Particle effect name.
params | Effect parameters.

### DeleteEffect

Deletes the specified particle effect.

```
Particle.DeleteEffect( name )
```

Parameter | Description
--- | ---
name | Particle effect name.

### IsEffectAvailable

Checks if the specified particle effect is available.

```
Particle.IsEffectAvailable( name )
```

Parameter | Description
--- | ---
name | Particle effect name.

### SpawnEffect

Spawns an effect.

```
Particle.SpawnEffect( effectName, pos, dir )
```

Parameter | Description
--- | ---
effectName | Effect name.
pos | Position vector.
dir | Direction vector.

### SpawnEffectLine

Spawns an effect line.

```
Particle.SpawnEffectLine( effectName, startPos, endPos, dir, scale, slices )
```

Parameter | Description
--- | ---
effectName | Effect name.
startPos | Start position.
endPos | End position.
dir | Direction of the effect.
scale | Scale value for the effect.
slices | Number of slices.

### SpawnParticles

Spawns a particle effect.

```
Particle.SpawnParticles( params, pos, dir )
```

Parameter | Description
--- | ---
params | Effect parameters.
pos | Effect position.
dir | Effect direction.

### CreateDecal

Creates a decal with the specified parameters.

```
Particle.CreateDecal( pos, normal, size, lifeTime, textureName )
```

Parameter | Description
--- | ---
pos | Decal position.
normal | Decal normal vector.
size | Decal size.
lifeTime | Decal life time.

### CreateMatDecal

Creates a material decal.

```
Particle.CreateMatDecal( pos, normal, size, lifeTime, materialName )
```

Parameter | Description
--- | ---
pos | Decal position.
normal | Decal normal vector.
size | Decal size.
lifeTime | Decal life time.
materialName | Name of the Material.

### Attach

Attaches an effect.

```
Particle.Attach()
```

### Detach

Detaches an effect.

```
Particle.Detach()
```
