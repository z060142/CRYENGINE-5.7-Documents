# Life

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/36868279
- Page ID: 36868279
- Breadcrumb: Editor Tools > Particle Editor > Particle Effect Features > Life
- Parent: Particle Effect Features

## Content

##
Overview

This feature controls the duration of a particle after it spawns
.

The following options are available under the Life
category:

##
Time

This feature sets the lifetime of a new born particle. It functions similarly to the
[/docs/static/engines/cryengine-5/categories/23756816/pages/36868265](
Field
)
feature, this feature is specifically designed to be used with
[/docs/static/engines/cryengine-5/categories/23756816/pages/36868151](
Modifiers
)
 for further control on how particles should spawn and die.

Property

 |
Description

 |

**
Life Time
**

 |
Defines a base value in seconds as the lifetime of the particle it is assigned to before it gets modified.

 |

**
Kill On Parent Death
**

 |
Kills the component if its parent dies.

 |

##
GPU Support

The Time category is supported in the GPU Pipeline, although currently there is no support for modifiers on the Life: Time feature.

[#time](
Time
)
[#gpu-support](
GPU Support
)
