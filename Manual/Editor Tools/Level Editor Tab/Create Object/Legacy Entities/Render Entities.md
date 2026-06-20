# Render Entities

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/29796945
- Page ID: 29796945
- Breadcrumb: Editor Tools > Level Editor Tab > Create Object > Legacy Entities > Render Entities
- Parent: Legacy Entities

## Content

## Overview

Render Entities available in CRYENGINE give designers quick ways of introducing various effects and visuals.

### Flash

The entity flashes the users screen making it white for a few seconds. Very bright explosions can be simulated with the Flash Entity. Trigger strikes through [Flow Graph](../../../Flow%20Graph.md).

**Property** | **Description**
--- | ---
**SkyHighlightAtten** | Specifies attenuation amount on the sky highlighting.
**SkyHighlightColor** | Specifies in which color the skybox will be lit by the lightning effect.
**SkyHighlightMultiplier** | Specifies how bright the skybox will be lit by the lightning effect.
**Sound** | Specifies a sound to play when triggered.
**FadeInTime** | Sets up the amount of time (in sec.) how long it takes to fade in the effect.
**FadeOutTime** | Sets up the amount of time (in sec.) how long it takes to fade out the effect.
**FadeDuration** | Sets up the amount of time (in sec.) fade in and out takes the effect.

### FogVolume

See [Fog](../../../../Graphics%20%26%20Rendering/Lighting/Lighting%20Overview/Volumetric%20Fog.md) for more information.

### Lightning

Lightning entities simulate Thunder/Lightning effects, with lightning strikes, large scale lights and thunder sounds which can be delayed.

**Property** | **Description**
--- | ---
**Active** | Activate/Deactivate the lightning entity.
**Distance** | Specifies how far away from point where the entity was placed that the lighting effect should happen.
**DistanceVariation** | Adds a random value to the distance, for example 20 means +-20% if the Distance is set to 100.
**RelativeToPlayer** | Sets the effect relative to the player so always with the same distance from the players current position.
**Effects** |
**LightIntensity** | Specifies how bright the light should be.
**LightRadius** | Within this radius objects will be lit.
**ParticleEffect** | Specifies the lightning bolt effect.
**ParticleScale** | Specifies the scale of the lightning bolt effect.
**ParticleScaleVariation** | Varies the scale of the lightning bolt effect.
**SkyHighlightAtten** | Attenuate the SkyHighlight effect.
**SkyHighlightColor** | Specifies which color the skybox will be lit by the lightning effect.
**SkyHighlightMultiplier** | Specifies how bright the skybox will be lit by the lightning effect.
**SkyHighlightVerticalOffset** | Offsets the SkyHighlightColor effect vertically. '50' will raise the effect 50m above the entity position.
**Sound** | Sets up a sound effect that should be played when each lightning strike occurs. This would typically be a thunder sound.
**Timing** |
**Delay** | Frequency of the lightning strikes, measured in seconds.
**DelayVariation** | Varies the frequency of the lightning strikes.
**LightningDuration** | Defines how long the visual effect of the lightning strike should last, in seconds. If set to '5' there will be 5 seconds of lightning, then 5 seconds of no lightning. Does not effect PFX, only the light.
**ThunderDelay** | Delay time, in seconds, for the thunder sound to reach the player. This is the sound that is defined just above the Timing section.
**ThunderDelayVariation** | Varies the delay time for the ThunderDelay sound.

### ViewDist

The ViewDist entity limits how far the player can see. Using the ViewDistance entity can significantly increase the frame rate in specific areas.

This entity can be used in two ways, by linking it to an [area shape](../../../../Entities%20and%20Tools/Entities%20Overview/Area%20Objects.md) or triggered through [Flow Graph](../../../Flow%20Graph.md).

**Property** | **Description**
--- | ---
**FadeTime** | Specifies the amount of time it takes to fade from the current level ViewDistance settings to the MaxViewDist setting in the entity.
**MaxViewDist** | Sets up the rendering View Distance in meters.

[Flash](#flash)[FogVolume](#fogvolume)[Lightning](#lightning)[ViewDist](#viewdist)
