# Component

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/36868260
- Page ID: 36868260
- Breadcrumb: Editor Tools > Particle Editor > Particle Effect Features > Component
- Parent: Particle Effect Features

## Content

## Overview

The Component category contains features which dynamically manipulate the component behavior as opposed to individual particles in that component. With this feature, particles can be activated based on certain conditions and probabilities.

To fully understand this category, it is recommended to study the difference between Component, Feature, Runtime and Emitter concepts on the [Key Concepts](../../../Graphics%20%26%20Rendering/Particles/Key%20Concepts.md) section.

### ActivateIf

This feature specifies if a Runtime can spawn new particles based on an Attribute Value.

Property | Description
--- | ---
**Attribute** | Enables the option to add an Attribute that specifies a condition needed for the particles to be activated. Any attribute can be used, but it is recommended to use Boolean attributes.

### ActivateRandom

Allows a component to be randomly activated.

Property | Description
--- | ---
**Probability** | Defines how frequently a particle effect can be activated.
**Group** | Groups multiple components together, which can be activated or ignored as a group. If the **Group** value is ** greater than 0**, then all components with the same Group value will be activated together,with one random generation. Otherwise, each component with the Group value set to 0 is activated with an independent random generation.
**Selection Start** | It appears when the Group option is enabled. Lets the components in a group to be activated separately. A component is activated only if the randomly generated number is between **Selection Start** and ** Selection Start + Probability** value.

### EnableByConfig

This feature specifies if a Runtime should be instantiated based on the current particle quality settings of the platform type. Use this feature to create different variations of the same Component for different platforms and quality settings.

Property | Description
--- | ---
**PC** | Specifies if this Component is to be active on a PC platform.
**Minimum** ** and Maximum** | Specifies the minimum and maximum quality settings allowed for this Component to be active. This option is visible only when the PC option is enabled.
**XBox One** | Specifies if this Component is to be active on an XBox One platform.
**PlayStation 4** | Specifies if this Component is to be active on a PlayStation 4 platform.

### EnableIf

This feature specifies if a Runtime should be instantiated for this component during emitter creation, based on an attribute value.

Property | Description
--- | ---
**Attribute** | Enables the option to add an attribute that specifies a condition needed for a particle to be activated. This attribute has to be set before the emitter starts updating as EnableIf is only evaluated during instantiation. Any attribute can be used, but it is recommended to use Boolean attributes.

The main difference between EnableIf and SpawnIf is that ActivateIf is evaluated during instantiation of the Emitter and will not create the Runtime. This saves on resources, but does not allow changing the condition dynamically. ActivateIf, on the other hand, will create a Runtime regardless of the condition. This makes ActivateIf a dynamic feature.

[ActivateIf](#activateif)[ActivateRandom](#activaterandom)[EnableByConfig](#enablebyconfig)[EnableIf](#enableif)
