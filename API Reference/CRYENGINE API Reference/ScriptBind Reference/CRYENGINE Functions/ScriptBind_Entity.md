# ScriptBind_Entity

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/23306601
- Page ID: 23306601
- Breadcrumb: CRYENGINE API Reference > ScriptBind Reference > CRYENGINE Functions > ScriptBind_Entity
- Parent: CRYENGINE Functions

## Content

### DeleteThis

Deletes this entity.

```
Entity.DeleteThis()
```

### CreateRenderProxy

Create a proxy render object for the entity, allows entity to be rendered without loading any assets in immediately.

```
Entity.CreateRenderProxy()
```

### CheckShaderParamCallbacks

Check all the currently set shader param callbacks on the renderproxy with the current state of the entity.

```
Entity.UpdateShaderParamCallback()
```

### LoadObject

Load CGF geometry into the entity slot.

```
Entity.LoadObject( nSlot, sFilename )
```

Parameter | Description
--- | ---
nSlot | Slot identifier.
sFilename | CGF geometry file name.

### LoadObjectWithFlags

Load CGF geometry into the entity slot.

```
Entity.LoadObject( nSlot, sFilename, nFlags )
```

Parameter | Description
--- | ---
nSlot | Slot identifier.
sFilename | CGF geometry file name.
nFlags | entity load flags

### LoadObjectLattice

Load lattice into the entity slot.

```
Entity.LoadObjectLattice( nSlot )
```

### LoadSubObject

Load geometry of one CGF node into the entity slot.

```
Entity.LoadSubObject( nSlot, sFilename, sGeomName )
```

Parameter | Description
--- | ---
nSlot | Slot identifier.
sFilename | CGF geometry file name.
sGeomName | Name of the node inside CGF geometry.

### LoadCharacter

Load CGF geometry into the entity slot.

```
Entity.LoadCharacter( nSlot, sFilename )
```

Parameter | Description
--- | ---
nSlot | Slot identifier.
sFilename | CGF geometry file name.

### LoadGeomCache

Load geom cache into the entity slot.

```
Entity.LoadGeomCache( int nSlot,const char *sFilename )
```

Parameter | Description
--- | ---
nSlot | Slot identifier.
sFilename | CAX file name.

### LoadLight

Load CGF geometry into the entity slot.

```
Entity.LoadLight( nSlot, lightTable )
```

Parameter | Description
--- | ---
nSlot | Slot identifier.
lightTable | Table with all the light information.

### SetLightColorParams

changes the color related params of an existing light.

```
Entity.SetLightColorParams( nSlot, color, specular_multiplier)
```

### UpdateLightClipBounds

Update the clip bounds of the light from the linked entities.

```
Entity.UpdateLightClipBounds( nSlot )
```

Parameter | Description
--- | ---
nSlot | Slot identifier.

### SetSelfAsLightCasterException

Entity render node will be a caster exception for light loaded in nLightSlot.

```
Entity.SetLightCasterException( nLightSlot, nGeometrySlot )
```

Parameter | Description
--- | ---
nLightSlot | Slot where our light is loaded.

### LoadCloud

Loads the cloud XML file into the entity slot.

```
Entity.LoadCloud( nSlot, sFilename )
```

Parameter | Description
--- | ---
nSlot | Slot identifier.
sFilename | Filename.

### SetCloudMovementProperties

Sets the cloud movement properties.

```
Entity.SetCloudMovementProperties( nSlot, table )
```

Parameter | Description
--- | ---
nSlot | Slot identifier.
table | Table property for the cloud movement.

### LoadFogVolume

Loads the fog volume XML file into the entity slot.

```
Entity.LoadFogVolume( nSlot, table )
```

Parameter | Description
--- | ---
nSlot | Slot identifier.
table | Table with fog volume properties.

### FadeGlobalDensity

Sets the fade global density.

```
Entity.FadeGlobalDensity( nSlot, fadeTime, newGlobalDensity )
```

Parameter | Description
--- | ---
nSlot | nSlot identifier.
fadeTime | .
newGlobalDensity | .

### LoadVolumeObject

Loads volume object.

```
Entity.LoadVolumeObject( nSlot, sFilename )
```

Parameter | Description
--- | ---
nSlot | Slot identifier.
sFilename | File name of the volume object.

### SetVolumeObjectMovementProperties

Sets the properties of the volume object movement.

```
Entity.SetVolumeObjectMovementProperties( nSlot, table )
```

Parameter | Description
--- | ---
nSlot | Slot identifier.
table | Table with volume object properties.

### LoadParticleEffect

Loads CGF geometry into the entity slot.

```
Entity.LoadParticleEffect( nSlot, sEffectName, fPulsePeriod, bPrime, fScale )
```

Parameter | Description
--- | ---
nSlot | Slot identifier.
sEffectName | Name of the particle effect (Ex: "explosions/rocket").
(optional) bPrime | Whether effect starts fully primed to equilibrium state.
(optional) fPulsePeriod | Time period between particle effect restarts.
(optional) fScale | Size scale to apply to particles
(optional) fCountScale | Count multiplier to apply to particles
(optional) bScalePerUnit | Scale size by attachment extent
(optional) bCountPerUnit | Scale count by attachment extent
(optional) sAttachType | string for EGeomType
(optional) sAttachForm | string for EGeomForm

### PreLoadParticleEffect

Pre-loads a particle effect.

```
Entity.PreLoadParticleEffect( sEffectName )
```

Parameter | Description
--- | ---
sEffectName | Name of the particle effect (Ex: "explosions/rocket").

### IsSlotParticleEmitter

Checks if the slot is a particle emitter.

```
Entity.IsSlotParticleEmitter( slot )
```

Parameter | Description
--- | ---
slot | Slot identifier.

### IsSlotLight

Checks if the slot is a light.

```
Entity.IsSlotLight( slot )
```

Parameter | Description
--- | ---
slot | Slot identifier.

### IsSlotGeometry

Checks if the slot is a geometry.

```
Entity.IsSlotGeometry( slot )
```

Parameter | Description
--- | ---
slot | Slot identifier.

### IsSlotCharacter

Checks if the slot is a character.

```
Entity.IsSlotCharacter( slot )
```

Parameter | Description
--- | ---
slot | Slot identifier.

### GetSlotCount

Gets the count of the slots.

```
Entity.GetSlotCount()
```

### GetSlotPos

Gets the slot position.

```
Entity.GetSlotPos( nSlot )
```

Parameter | Description
--- | ---
nSlot | nSlot identifier.

### SetSlotPos

Sets the slot position.

```
Entity.SetSlotPos( nSlot, v )
```

Parameter | Description
--- | ---
nSlot | nSlot identifier.
v | Position to be set.

### SetSlotPosAndDir

Sets the slot position and direction.

```
Entity.SetSlotPosAndDir( nSlot, pos, dir )
```

Parameter | Description
--- | ---
nSlot | nSlot identifier.
pos | Position to be set.
dir | Direction to be set.

### GetSlotAngles

Gets the slot angles.

```
Entity.GetSlotAngles( nSlot )
```

Parameter | Description
--- | ---
nSlot | nSlot identifier.

### SetSlotAngles

Sets the slot angles.

```
Entity.GetSlotAngles( nSlot, v )
```

Parameter | Description
--- | ---
nSlot | nSlot identifier.
v | Angle to be set.

### GetSlotScale

Gets the slot scale amount.

```
Entity.GetSlotScale( nSlot )
```

Parameter | Description
--- | ---
nSlot | nSlot identifier.

### SetSlotScale

Sets the slot scale amount.

```
Entity.SetSlotScale( nSlot, fScale )
```

Parameter | Description
--- | ---
nSlot | Slot identifier.
fScale | Scale amount for the slot.

### IsSlotValid

Checks if the slot is valid.

```
Entity.IsSlotValid( nSlot )
```

Parameter | Description
--- | ---
nSlot | Slot identifier.

### CopySlotTM

Copies the TM (Transformation Matrix) of the slot.

```
Entity.CopySlotTM( destSlot, srcSlot, includeTranslation )
```

Parameter | Description
--- | ---
destSlot | Destination slot identifier.
srcSlot | Source slot identifier.
includeTranslation | True to include the translation, false otherwise.

### MultiplyWithSlotTM

Multiplies with the TM (Transformation Matrix) of the slot.

```
Entity.MultiplyWithSlotTM( slot, pos )
```

Parameter | Description
--- | ---
slot | Slot identifier.
pos | Position vector.

### SetSlotWorldTM

Sets the World TM (Transformation Matrix) of the slot.

```
Entity.SetSlotWorldTM( nSlot, pos, dir )
```

Parameter | Description
--- | ---
nSlot | Slot identifier.
pos | Position vector.
dir | Direction vector.

### GetSlotWorldPos

Gets the World position of the slot.

```
Entity.GetSlotWorldPos( nSlot )
```

Parameter | Description
--- | ---
nSlot | Slot identifier.

### GetSlotWorldDir

Gets the World direction of the slot.

```
Entity.GetSlotWorldDir( nSlot )
```

Parameter | Description
--- | ---
nSlot | Slot identifier.

### SetSlotHud3D

Setup flags for use as 3D HUD entity.

```
Entity.SetSlotHud3D( nSlot )
```

Parameter | Description
--- | ---
nSlot | Slot identifier.

### SetPos

Sets the position of the entity.

```
Entity.SetPos( vPos )
```

Parameter | Description
--- | ---
vPos | Position vector.

### GetPos

Gets the position of the entity.

```
Entity.GetPos()
```

### SetAngles

Sets the angle of the entity.

```
Entity.SetAngles( vAngles )
```

Parameter | Description
--- | ---
vAngles | Angle vector.

### GetAngles

Gets the angle of the entity.

```
Entity.GetAngles()
```

### SetScale

Sets the scaling value for the entity.

```
Entity.SetScale( fScale )
```

Parameter | Description
--- | ---
fScale | Scale amount.

### GetScale

Gets the scaling value for the entity.

```
Entity.GetScale()
```

### GetCenterOfMassPos

Gets the position of the entity center of mass.

```
Entity.GetCenterOfMassPos()
```

### GetWorldBoundsCenter

Gets the world bbox center for the entity (defaults to entity position if no bbox present).

```
Entity.GetWorldBoundsCenter()
```

### SetLocalPos

```
Entity.SetLocalPos( vPos )
```

### GetLocalPos

```
Vec3 Entity.GetLocalPos()
```

### SetLocalAngles

```
Entity.SetLocalAngles( vAngles )
```

### GetLocalAngles

```
Vec3 Entity.GetLocalAngles( vAngles )
```

### SetLocalScale

```
Entity.SetLocalScale( fScale )
```

### GetLocalScale

```
float Entity.GetLocalScale()
```

### SetWorldPos

```
Entity.SetWorldPos( vPos )
```

### GetWorldPos

```
Vec3 Entity.GetWorldPos()
```

### GetWorldDir

```
Vec3 Entity.GetWorldDir()
```

### SetWorldAngles

```
Entity.SetWorldAngles( vAngles )
```

### GetWorldAngles

```
Vec3 Entity.GetWorldAngles( vAngles )
```

### SetWorldScale

```
Entity.SetWorldScale( fScale )
```

### GetWorldScale

```
float Entity.GetWorldScale()
```

### GetBoneLocal

```
float Entity.GetBoneLocal( boneName, trgDir )
```

### CalcWorldAnglesFromRelativeDir

```
Ang3 Entity.CalcWorldAnglesFromRelativeDir( dir )
```

### IsEntityInside

```
float Entity.IsEntityInside(entityId)
```

### GetDistance

```
float Entity.GetDistance( entityId )
```

**Returns:** The distance from entity specified with entityId/

### DrawSlot

Enables/Disables drawing of object or character at specified slot of the entity.

```
Entity.DrawSlot( nSlot )
```

Parameter | Description
--- | ---
nSlot | Slot identifier.
nEnable | 1-Enable drawing, 0-Disable drawing.

### IgnorePhysicsUpdatesOnSlot

Ignore physics when it try to update the position of a slot.

```
Entity.IgnorePhysicsUpdatesOnSlot( nSlot )
```

Parameter | Description
--- | ---
nSlot | Slot identifier.

### FreeSlot

Delete all objects from specified slot.

```
Entity.FreeSlot( nSlot )
```

Parameter | Description
--- | ---
nSlot | Slot identifier.

### FreeAllSlots

Delete all objects on every slot part of the entity.

```
Entity.FreeAllSlots()
```

### GetCharacter

Gets the character for the specified slot if there is any.

```
Entity.GetCharacter( nSlot )
```

### DestroyPhysics

```
Entity.DestroyPhysics()
```

### EnablePhysics

```
Entity.EnablePhysics( bEnable )
```

### ResetPhysics

```
Entity.ResetPhysics()
```

### AwakePhysics

```
Entity.AwakePhysics( nAwake )
```

### AwakeCharacterPhysics

```
Entity.AwakeCharacterPhysics( nSlot, sRootBoneName, nAwake )
```

### Physicalize

<param name="physicsParams - Table with physicalization parameters.

```
Entity.Physicalize( int nSlot,int nPhysicsType,table physicsParams )
```

### SetPhysicParams

```
Entity.SetPhysicParams()
```

### SetCharacterPhysicParams

```
Entity.SetCharacterPhysicParams()
```

### ActivatePlayerPhysics

```
Entity.ActivatePlayerPhysics( bEnable )
```

### ReattachSoftEntityVtx

```
Entity.ReattachSoftEntityVtx( partId )
```

### PhysicalizeSlot

```
Entity.PhysicalizeSlot( slot, physicsParams )
```

### UpdateSlotPhysics

```
Entity.UpdateSlotPhysics( slot )
```

### SetColliderMode

```
Entity.SetColliderMode( mode )
```

### SelectPipe

```
Entity.SelectPipe()
```

### IsUsingPipe

```
Entity.IsUsingPipe( pipename )
```

**Returns:** true - if entity is running the given goalpipe or has it inserted false - otherwise

### Activate

Activates or deactivates entity. This calls ignores update policy and forces entity to activate or deactivate All active entities will be updated every frame, having too many active entities can affect performance. <param name="bActivate - if true entity will become active, is false will deactivate and stop being updated every frame.

```
Entity.Activate( bActivate )
```

### IsActive

Retrieve active status of entity.

```
Entity.IsActive( bActivate )
```

**Returns:** true - Entity is active. false - Entity is not active.

### IsFromPool

Returns if the entity came from an entity pool.

```
Entity.IsFromPool()
```

**Returns:** true - Entity is from a pool. (Bookmarked) false - Entity is not from a pool. (Not bookmarked)

### SetUpdatePolicy

Use SetUpdateRadius for update policy that require a radius.

```
Entity.SetUpdatePolicy( nUpdatePolicy )
```

Parameter | Description
--- | ---
nUpdatePolicy | Update policy type.

### SetLocalBBox

```
Entity.SetLocalBBox( vMin, vMax )
```

### GetLocalBBox

```
Entity.GetLocalBBox()
```

### GetWorldBBox

```
Entity.GetWorldBBox()
```

### GetProjectedWorldBBox

```
Entity.GetProjectedWorldBBox()
```

### SetTriggerBBox

```
Entity.SetTriggerBBox( vMin, vMax )
```

### GetTriggerBBox

```
Entity.GetTriggerBBox()
```

### InvalidateTrigger

```
Entity.InvalidateTrigger()
```

### ForwardTriggerEventsTo

```
Entity.ForwardTriggerEventsTo( entityId )
```

### SetUpdateRadius

```
Entity.SetUpdateRadius()
```

### GetUpdateRadius

```
Entity.GetUpdateRadius()
```

### TriggerEvent

```
Entity.TriggerEvent()
```

### GetHelperPos

```
Entity.GetHelperPos()
```

### GetHelperDir

```
Entity.GetHelperDir()
```

### GetHelperAngles

```
Entity.GetHelperAngles()
```

### GetSlotHelperPos

```
Entity.GetSlotHelperPos( slot, helperName, objectSpace )
```

### GetBonePos

```
Entity.GetBonePos()
```

### GetBoneDir

```
Entity.GetBoneDir()
```

### GetBoneVelocity

```
Entity.GetBoneVelocity( characterSlot, boneName )
```

### GetBoneAngularVelocity

```
Entity.GetBoneAngularVelocity( characterSlot, oneName )
```

### GetBoneNameFromTable

```
Entity.GetBoneNameFromTable()
```

### SetName

```
Entity.SetName()
```

### GetName

```
Entity.GetName()
```

### GetRawId

Returns entityId in raw numeric format.

```
Entity.GetRawId()
```

### SetAIName

```
Entity.SetAIName()
```

### GetAIName

```
Entity.GetAIName()
```

### SetFlags

Mode: 0: or 1: and 2: xor

```
Entity.SetFlags( flags, mode )
```

### GetFlags

```
Entity.GetFlags()
```

### HasFlags

```
Entity.HasFlags( flags )
```

### SetFlagsExtended

Mode: 0: or 1: and 2: xor

```
Entity.SetFlagsExtended( flags, mode )
```

### GetFlagsExtended

```
Entity.GetFlagsExtended()
```

### HasFlagsExtended

```
Entity.HasFlags( flags )
```

### GetArchetype

Retrieve the archetype of the entity.

```
Entity.GetArchetype()
```

**Returns:** name of entity archetype, nil if no archetype.

### IntersectRay

```
Entity.IntersectRay( slot, rayOrigin, rayDir, maxDistance )
```

### AttachChild

```
Entity.AttachChild( childEntityId, flags )
```

### DetachThis

```
Entity.DetachThis()
```

### DetachAll

```
Entity.DetachAll()
```

### GetParent

```
Entity.GetParent()
```

### GetChildCount

```
Entity.GetChildCount()
```

### GetChild

```
Entity.GetChild( int nIndex )
```

### EnableInheritXForm

Enables/Disable entity from inheriting transformation from the parent.

```
Entity.EnableInheritXForm()
```

### NetPresent

```
Entity.NetPresent()
```

### RenderShadow

```
Entity.RenderShadow()
```

### SetRegisterInSectors

```
Entity.SetRegisterInSectors()
```

### IsColliding

```
Entity.IsColliding()
```

### GetDirectionVector

```
Entity.GetDirectionVector()
```

### SetDirectionVector

```
Entity.SetDirectionVector( direction )
```

### IsAnimationRunning

```
Entity.IsAnimationRunning( characterSlot, layer )
```

**Returns:** nil or not nil
Parameter | Description
--- | ---
characterSlot | Index of the character slot.
layer | Index of the animation layer.

### AddImpulse

Apply an impulse to the entity. At least four parameters need to be provided for a linear impulse. For an additional angular impulse, at least seven parameters need to be provided.

```
Entity.AddImpulse( ipart, position, direction, linearImpulse, linearImpulseScale, angularAxis, angularImpulse, massScale )
```

Parameter | Description
--- | ---
ipart | The index of the part that receives the impulse.
position | The point (in world coordinates) where the impulse is applied. Set this to (0, 0, 0) to ignore it.
direction | The direction in which the impulse is applied.
linearImpulse | The force of the linear impulse.
linearImpulseScale | Scaling of the linear impulse. (Default: 1.0)
angularAxis | The axis on which the angular impulse is applied.
angularImpulse | The force of the the angular impulse.
massScale | Mass scaling of the angular impulse. (Default: 1.0)

### AddConstraint

```
Entity.AddConstraint()
```

### SetPublicParam

Set a shader parameter

```
Entity.SetPublicParam()
```

Parameter | Description
--- | ---
paramName | The name of the shader parameter.
value | The new value of the parameter.

### GetAllAuxAudioProxiesID

Returns the ID used to address all AuxAudioProxy of the parent EntityAudioProxy.

```
Entity.GetAllAuxAudioProxiesID()
```

**Returns:** Returns the ID used to address all AuxAudioProxy of the parent EntityAudioProxy.

### GetDefaultAuxAudioProxyID

Returns the ID of the default AudioProxy of the parent EntityAudioProxy.

```
Entity.GetDefaultAuxAudioProxyID()
```

**Returns:** Returns the ID of the default AudioProxy of the parent EntityAudioProxy.

### CreateAuxAudioProxy

Creates an additional AudioProxy managed by the EntityAudioProxy. The created AuxAudioProxy will move and rotate with the parent EntityAudioProxy.

```
Entity.CreateAuxAudioProxy()
```

**Returns:** Returns the ID of the additionally created AudioProxy.

### RemoveAuxAudioProxy

Removes the AuxAudioProxy corresponding to the passed ID from the parent EntityAudioProxy.

```
Entity.RemoveAuxAudioProxy( hAudioProxyLocalID )
```

**Returns:** nil
Parameter | Description
--- | ---
hAudioProxyLocalID | hAudioProxyLocalID - ID of the AuxAudioProxy to be removed from the parent EntityAudioProxy.

### ExecuteAudioTrigger

Execute the specified audio trigger and attach it to the entity. The created audio object will move and rotate with the entity.

```
Entity.ExecuteAudioTrigger( hTriggerID, hAudioProxyLocalID )
```

**Returns:** nil
Parameter | Description
--- | ---
hTriggerID | the audio trigger ID handle
hAudioProxyLocalID | ID of the AuxAudioProxy local to the EntityAudioProxy (to address the default AuxAudioProxy pass 1 to address all AuxAudioProxies pass 0)

### StopAudioTrigger

Stop the audio event generated by the trigger with the specified ID on this entity.

```
Entity.StopAudioTrigger( hTriggerID, hAudioProxyLocalID )
```

**Returns:** nil
Parameter | Description
--- | ---
hTriggerID | the audio trigger ID handle
hAudioProxyLocalID | ID of the AuxAudioProxy local to the EntityAudioProxy (to address the default AuxAudioProxy pass 1 to address all AuxAudioProxies pass 0)

### SetAudioSwitchState

Set the specified audio switch to the specified state on the current Entity.

```
Entity.SetAudioSwitchState( hSwitchID, hSwitchStateID, hAudioProxyLocalID )
```

**Returns:** nil
Parameter | Description
--- | ---
hSwitchID | the audio switch ID handle
nSwitchStateID | the switch state ID handle
hAudioProxyLocalID | ID of the AuxAudioProxy local to the EntityAudioProxy (to address the default AuxAudioProxy pass 1 to address all AuxAudioProxies pass 0)

### SetAudioObstructionCalcType

Set the Audio Obstruction/Occlusion calculation type on the underlying GameAudioObject.

```
Entity.SetAudioObstructionCalcType( nObstructionCalcType, hAudioProxyLocalID )
```

**Returns:** nil
Parameter | Description
--- | ---
nObstructionCalcType | Obstruction/Occlusion calculation type; Possible values: 0 - ignore Obstruction/Occlusion 1 - use single physics ray 2 - use multiple physics rays (currently 5 per object)
hAudioProxyLocalID | ID of the AuxAudioProxy local to the EntityAudioProxy (to address the default AuxAudioProxy pass 1 to address all AuxAudioProxies pass 0)

### SetFadeDistance

Sets the distance in which this entity will execute fade calculations.

```
Entity.SetFadeDistance( fFadeDistance )
```

**Returns:** nil
Parameter | Description
--- | ---
fFadeDistance | fade distance in meters

### SetAudioProxyOffset

Set offset on the AudioProxy attached to the Entity.

```
Entity.SetAudioProxyOffset( vOffset, hAudioProxyLocalID )
```

**Returns:** nil
Parameter | Description
--- | ---
vOffset | offset vector
hAudioProxyLocalID | ID of the AuxAudioProxy local to the EntityAudioProxy (to address the default AuxAudioProxy pass 1 to address all AuxAudioProxies pass 0)

### SetEnvironmentFadeDistance

Sets the distance over which this entity will fade the audio environment amount for all approaching entities.

```
Entity.SetEnvironmentFadeDistance( fEnvironmentFadeDistance )
```

**Returns:** nil
Parameter | Description
--- | ---
fEnvironmentFadeDistance | fade distance in meters

### SetAudioEnvironmentID

Sets the ID of the audio environment this entity will set for entities inside it.

```
Entity.SetAudioEnvironmentID( nAudioEnvironmentID )
```

**Returns:** nil
Parameter | Description
--- | ---
nAudioEnvironmentID | audio environment ID

### SetCurrentAudioEnvironments

Sets the correct audio environment amounts based on the entity's position in the world.

```
Entity.SetCurrentAudioEnvironments()
```

**Returns:** nil

### SetAudioRtpcValue

Set the specified audio RTPC to the specified value on the current Entity.

```
Entity.SetAudioRtpcValue( hRtpcID, fValue, hAudioProxyLocalID )
```

**Returns:** nil
Parameter | Description
--- | ---
hRtpcID | the audio RTPC ID handle
fValue | the RTPC value
hAudioProxyLocalID | ID of the AuxAudioProxy local to the EntityAudioProxy (to address the default AuxAudioProxy pass 1 to address all AuxAudioProxies pass 0)

### AuxAudioProxiesMoveWithEntity

Set whether AuxAudioProxies should move with the entity or not.

```
Entity.AuxAudioProxiesMoveWithEntity( bCanMoveWithEntity )
```

**Returns:** nil
Parameter | Description
--- | ---
bCanMoveWithEntity | boolean parameter to enable or disable

### SetGeomCachePlaybackTime

Sets the playback time.

```
Entity.SetGeomCachePlaybackTime()
```

### SetGeomCacheParams

Sets geometry cache parameters.

```
Entity.SetGeomCacheParams()
```

### SetGeomCacheStreaming

Activates/deactivates geom cache streaming.

```
Entity.SetGeomCacheStreaming()
```

### IsGeomCacheStreaming

```
Entity.IsGeomCacheStreaming()
```

**Returns:** true if geom cache is streaming.

### GetGeomCachePrecachedTime

Gets time delta from current playback position to last ready to play frame.

```
Entity.GetGeomCachePrecachedTime()
```

### SetGeomCacheDrawing

Activates/deactivates geom cache drawing.

```
Entity.SetGeomCacheDrawing()
```

### StartAnimation

```
Entity.StartAnimation()
```

### StopAnimation

```
Entity.StopAnimation( characterSlot, layer )
```

### ResetAnimation

```
Entity.ResetAnimation( characterSlot, layer )
```

### RedirectAnimationToLayer0

```
Entity.RedirectAnimationToLayer0( characterSlot, redirect )
```

### SetAnimationBlendOut

```
Entity.SetAnimationBlendOut( characterSlot, layer, blendOut )
```

### EnableBoneAnimation

```
Entity.EnableBoneAnimation( characterSlot, layer, boneName, status )
```

### EnableBoneAnimationAll

```
Entity.EnableBoneAnimationAll( characterSlot, layer, status )
```

### EnableProceduralFacialAnimation

```
Entity.EnableProceduralFacialAnimation( enable )
```

### PlayFacialAnimation

```
Entity.PlayFacialAnimation( name, looping )
```

### SetAnimationEvent

```
Entity.SetAnimationEvent( nSlot, sAnimation )
```

### SetAnimationKeyEvent

```
Entity.SetAnimationKeyEvent( nSlot, sAnimation, nFrameID, sEvent)
```

### DisableAnimationEvent

```
Entity.DisableAnimationEvent( nSlot, sAnimation )
```

### SetAnimationSpeed

```
Entity.SetAnimationSpeed( characterSlot, layer, speed )
```

### SetAnimationTime

```
Entity.SetAnimationTime( nSlot, nLayer, fTime )
```

### GetAnimationTime

```
Entity.GetAnimationTime( nSlot, nLayer )
```

### GetCurAnimation

```
Entity.GetCurAnimation()
```

### GetAnimationLength

```
Entity.GetAnimationLength( characterSlot, animation )
```

### SetAnimationFlip

```
Entity.SetAnimationFlip( characterSlot, flip )
```

### SetTimer

```
Entity.SetTimer()
```

### KillTimer

```
Entity.KillTimer()
```

### SetScriptUpdateRate

```
Entity.SetScriptUpdateRate( nMillis )
```

### GotoState

```
Entity.GotoState( sState )
```

### IsInState

```
Entity.IsInState( sState )
```

### GetState

```
Entity.GetState()
```

### IsHidden

```
Entity.IsHidden()
```

### GetTouchedSurfaceID

```
Entity.GetTouchedSurfaceID()
```

### GetTouchedPoint

Retrieves point of collision for rigid body.

```
Entity.GetTouchedPoint()
```

### CreateBoneAttachment

```
Entity.CreateBoneAttachment( characterSlot, boneName, attachmentName )
```

### CreateSkinAttachment

```
Entity.CreateSkinAttachment( characterSlot, attachmentName )
```

### DestroyAttachment

```
Entity.DestroyAttachment( characterSlot, attachmentName )
```

### GetAttachmentBone

```
Entity.GetAttachmentBone( characterSlot, attachmentName )
```

### GetAttachmentCGF

```
Entity.GetAttachmentCGF( characterSlot, attachmentName )
```

### ResetAttachment

```
Entity.ResetAttachment( characterSlot, attachmentName )
```

### SetAttachmentEffect

```
Entity.SetAttachmentEffect( characterSlot, attachmentName, effectName, offset, dir, scale, flags )
```

### SetAttachmentObject

```
Entity.SetAttachmentObject( characterSlot, attachmentName, entityId, slot, flags )
```

### SetAttachmentCGF

```
Entity.SetAttachmentCGF( characterSlot, attachmentName, filePath )
```

### SetAttachmentLight

```
Entity.SetAttachmentLight( characterSlot, attachmentName, lightTable, flags )
```

### SetAttachmentPos

```
Entity.SetAttachmentPos( characterSlot, attachmentName, pos )
```

### SetAttachmentAngles

```
Entity.SetAttachmentAngles( characterSlot, attachmentName, angles )
```

### SetAttachmentDir

```
Entity.SetAttachmentDir()
```

### HideAttachment

```
Entity.HideAttachment( characterSlot, attachmentName, hide, hideShadow )
```

### HideAllAttachments

```
Entity.HideAllAttachments( characterSlot, hide, hideShadow )
```

### HideAttachmentMaster

```
Entity.HideAttachmentMaster( characterSlot, hide )
```

### PhysicalizeAttachment

```
Entity.PhysicalizeAttachment( characterSlot, attachmentName, physicalize )
```

### Damage

```
Entity.Damage()
```

### GetEntitiesInContact

```
Entity.GetEntitiesInContact()
```

### GetExplosionObstruction

```
Entity.GetExplosionObstruction()
```

### GetExplosionImpulse

```
Entity.GetExplosionImpulse()
```

### SetMaterial

```
Entity.SetMaterial()
```

### GetMaterial

```
Entity.GetMaterial()
```

### GetEntityMaterial

```
Entity.GetEntityMaterial()
```

### ChangeAttachmentMaterial

```
Entity.ChangeAttachmentMaterial(attachmentName, materialName)
```

### ReplaceMaterial

```
Entity.ReplaceMaterial( slot, name, replacement )
```

### ResetMaterial

```
Entity.ResetMaterial( slot )
```

### EnableMaterialLayer

```
Entity.EnableMaterialLayer( enable, layer )
```

### CloneMaterial

Replace material on the slot with a cloned version of the material. Cloned material can be freely changed uniquely for this entity.

```
Entity.CloneMaterial( nSlotId, sSubMaterialName )
```

Parameter | Description
--- | ---
nSlotId | On which slot to clone material.
sSubMaterialName | if non empty string only this specific sub-material is cloned.

### SetMaterialFloat

Change material parameter.

```
Entity.SetMaterialFloat( nSlotId, nSubMtlId, sParamName, fValue )
```

Parameter | Description
--- | ---
nSlot | On which slot to change material.
nSubMtlId | Specify sub-material by Id.
sParamName | Name of the material parameter.
fValue | New material parameter value.

### GetMaterialFloat

Change material parameter.

```
Entity.GetMaterialFloat( nSlotId, nSubMtlId, sParamName )
```

**Returns:** Material parameter value.
Parameter | Description
--- | ---
nSlot | On which slot to change material.
nSubMtlId | Specify sub-material by Id.
sParamName | Name of the material parameter.

### SetMaterialVec3

```
Entity.SetMaterialVec3( nSlotId, nSubMtlId, sParamName, vVec3 )
```

### GetMaterialVec3

```
Entity.GetMaterialVec3( nSlotId, nSubMtlId, sParamName )
```

### MaterialFlashInvoke

```
Entity.MaterialFlashInvoke()
```

### ToLocal

```
Entity.ToLocal( slotId, point )
```

### ToGlobal

```
Entity.ToGlobal( slotId, point )
```

### VectorToLocal

```
Entity.VectorToLocal( slotId, dir )
```

### VectorToGlobal

```
Entity.VectorToGlobal( slotId, dir )
```

### CheckCollisions

```
Entity.CheckCollisions()
```

### AwakeEnvironment

```
Entity.AwakeEnvironment()
```

### GetTimeSinceLastSeen

```
Entity.GetTimeSinceLastSeen()
```

### GetViewDistRatio

```
Entity.GetViewDistRatio()
```

### SetViewDistRatio

```
Entity.SetViewDistRatio()
```

### SetViewDistUnlimited

```
Entity.SetViewDistUnlimited()
```

### SetLodRatio

```
Entity.SetLodRatio()
```

### GetLodRatio

```
Entity.GetLodRatio()
```

### SetStateClientside

```
Entity.SetStateClientside()
```

### InsertSubpipe

```
Entity.InsertSubpipe()
```

### CancelSubpipe

```
Entity.CancelSubpipe()
```

### PassParamsToPipe

```
Entity.PassParamsToPipe()
```

### SetDefaultIdleAnimations

```
Entity.SetDefaultIdleAnimations()
```

### GetVelocity

```
Entity.GetVelocity()
```

### GetVelocityEx

```
Entity.GetVelocityEx()
```

### SetVelocity

```
Entity.SetVelocity(velocity)
```

### SetVelocityEx

```
Entity.GetVelocityEx(velocity, angularVelocity)
```

### GetSpeed

```
Entity.GetSpeed()
```

### GetMass

```
Entity.GetMass()
```

### GetVolume

```
Entity.GetVolume(slot)
```

### GetGravity

```
Entity.GetGravity()
```

### GetSubmergedVolume

```
Entity.GetSubmergedVolume( slot, planeNormal, planeOrigin )
```

### CreateLink

Creates a new outgoing link for this entity.

```
Entity.CreateLink( name, targetId )
```

**Returns:** nothing
Parameter | Description
--- | ---
name | Name of the link. Does not have to be unique among all the links of this entity. Multiple links with the same name can perfectly co-exist.
(optional) targetId | If specified, the ID of the entity the link shall target. If not specified or 0 then the link will not target anything. Default value: 0

### GetLinkName

Returns the name of the link that is targeting the entity with given ID.

```
Entity.GetLinkName( targetId, ith )
```

**Returns:** The name of the i'th link targeting given entity or nil if no such link exists.
Parameter | Description
--- | ---
targetId | ID of the entity for which the link name shall be looked up.
(optional) ith | If specified, the i'th link that targets given entity. Default value: 0 (first entity)

### SetLinkTarget

Specifies the entity that an existing link shall target. Use this function to change the target of an existing link.

```
Entity.SetLinkTarget(name, targetId, ith)
```

**Returns:** nothing
Parameter | Description
--- | ---
name | Name of the link that shall target given entity.
targetId | The ID of the entity the link shall target. Pass in NULL_ENTITY to make the link no longer target an entity.
(optional) ith | If specified, the i'th link with given name that shall target given entity. Default value: 0 (first link with given name)

### GetLinkTarget

Returns the ID of the entity that given link is targeting.

```
Entity.GetLinkTarget( name, ith )
```

**Returns:** The ID of the entity that the link is targeting or nil if no such link exists.
Parameter | Description
--- | ---
name | Name of the link.
(optional) ith | If specified, the i'th link with given name for which to look up the targeted entity. Default value: 0 (first link with given name)

### RemoveLink

Removes an outgoing link from the entity.

```
Entity.RemoveLink( name, ith )
```

**Returns:** nothing
Parameter | Description
--- | ---
name | Name of the link to remove.
(optional) ith | If specified, the i'th link with given name that shall be removed. Default value: 0 (first link with given name)

### RemoveAllLinks

Removes all links of an entity.

```
Entity.RemoveAllLinks()
```

**Returns:** nothing

### GetLink

Returns the link at given index.

```
Entity.GetLink()
```

**Returns:** The script table of the entity that the i'th link is targeting or nil if the specified index is out of bounds.
Parameter | Description
--- | ---
ith | The index of the link that shall be returned.

### CountLinks

Counts all outgoing links of the entity.

```
Entity.CountLinks()
```

**Returns:** Number of outgoing links.

### RemoveDecals

```
Entity.RemoveDecals()
```

### ForceCharacterUpdate

```
Entity.ForceCharacterUpdate( characterSlot, updateAlways )
```

### CharacterUpdateAlways

```
Entity.CharacterUpdateAlways( characterSlot, updateAlways )
```

### CharacterUpdateOnRender

```
Entity.CharacterUpdateOnRender( characterSlot, bUpdateOnRender )
```

### SetAnimateOffScreenShadow

```
Entity.SetAnimateOffScreenShadow( bAnimateOffScreenShadow )
```

### RagDollize

```
Entity.RagDollize(slot)
```

### Hide

```
Entity.Hide()
```

### NoExplosionCollision

```
Entity.NoExplosionCollision()
```

### NoBulletForce

```
Entity.NoBulletForce( state )
```

### UpdateAreas

```
Entity.UpdateAreas()
```

### IsPointInsideArea

```
Entity.IsPointInsideArea( areaId, point )
```

### IsEntityInsideArea

```
Entity.IsEntityInsideArea( areaId, entityId )
```

### GetPhysicalStats

Some more physics related.

```
Entity.GetPhysicalStats()
```

### SetParentSlot

```
Entity.SetParentSlot( child, parent )
```

### GetParentSlot

```
Entity.GetParentSlot( child )
```

### BreakToPieces

Breaks static geometry in slot 0 into sub objects and spawn them as particles or entities.

```
Entity.BreakToPieces()
```

### AttachSurfaceEffect

```
Entity.AttachSurfaceEffect( nSlot, effect, countPerUnit, form, typ, countScale, sizeScale )
```

### ProcessBroadcastEvent

```
Entity.ProcessBroadcastEvent()
```

### ActivateOutput

```
Entity.ActivateOutput()
```

### CreateCameraProxy

Create a proxy camera object for the entity, allows entity to serve as camera source for material assigned on the entity.

```
Entity.CreateCameraProxy()
```

### UnSeenFrames

```
Entity.UnSeenFrames()
```

### DeleteParticleEmitter

Deletes particles emitter from 3dengine.

```
Entity.DeleteParticleEmitter(slot)
```

Parameter | Description
--- | ---
slot | slot number

### RegisterForAreaEvents

Registers the script proxy so that it receives area events for this entity.

```
Entity.RegisterForAreaEvents(enable)
```

Parameter | Description
--- | ---
enable | 0, for disable, any other value for enable.

### RenderAlways

Enables 'always render' on the render node, skipping any kind of culling.

```
Entity.RenderAlways(enable)
```

Parameter | Description
--- | ---
enable | 0, for disable, any other value for enable.

### GetTimeOfDayHour

```
Entity.GetTimeOfDayHour()
```

**Returns:** current time of day as a float value.

### CreateDRSProxy

Creates a Dynamic Response System Proxy

```
Entity.CreateDRSProxy()
```

**Returns:** Returns the ID of the created proxy.
