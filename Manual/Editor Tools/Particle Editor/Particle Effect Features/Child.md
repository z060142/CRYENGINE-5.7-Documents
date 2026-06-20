# Child

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/36868258
- Page ID: 36868258
- Breadcrumb: Editor Tools > Particle Editor > Particle Effect Features > Child
- Parent: Particle Effect Features

## Content

##
Overview

This feature controls the spawning behavior of the child components based on their parent components. Depending on the user choice, the child particles can spawn on birth or on death of the parent. This feature also allows the child particles to spawn when the parent component collides with a surface.

##
OnBirth

This is the default spawning behavior of child components. It starts spawning particles when a parent particle is born. If a child component has no child feature, then
**
Child: OnBirth
**
 will be automatically assigned to it.

##
OnCollide

Causes a child component to begin spawning particles when a parent particle collides with a surface. This will function only if the parent component has a Collision feature.

Property

 |
Description

 |

**
Surface Requirement
**

 |

-
**
Any -
**
Spawns particles when the parent component collides with any surface.

-
**
Only -
**
 Only spawns particles when the collided surface matches the surface type(s) specified by the Surface parameter that appears after this option is selected.

-
**
Not -
**
 Spawns particles when the collided surface does NOT match the surface type(s) specified by the Surface parameter that appears after this option is selected.
 |

##
OnDeath

Causes a child component to begin spawning particles when a parent particle dies.

[OnBirth](#onbirth)
[OnCollide](#oncollide)
[OnDeath](#ondeath)
