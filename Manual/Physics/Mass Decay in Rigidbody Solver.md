# Mass Decay in Rigidbody Solver

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/36869313
- Page ID: 36869313
- Breadcrumb: Physics > Mass Decay in Rigidbody Solver
- Parent: Physics

## Content

##
Overview

This feature dynamically alters the masses of bodies participating in a group contact solver, progressively decreasing the masses of bodies that are further away from heavy or static colliders. This only affects internal body helpers used by the solver (i.e. not the actual persistent bodies), and is only applied after a specified amount of solver "honest" passes over all contacts were made. This allows to preserve the physical nature of the impulse solver while significantly improving stack stability.

The downside of using this feature is that stacks can become
*
more
*
 stable than they should be. To some extent this can be fixed by increasing the amount of undecayed passes.

![Image](https://www.cryengine.com/docs/static/attachments/36848965)

*
Mass decay in action
*

##
Usage

By adjusting the CVars listed below mass decay strength and thresholds can be tweaked (the variables can also be changed from code, in
*
physics vars
*
 structure). By default mass decay is disabled (set to 1). Generally 0.9 is quite a strong decay, and for larger stacks values of 0.95 and more should be used.

However, it's also relatively safe to experiment with low decay values if necessary, since prepasses and yhe temporary nature of the decay will amortize the degeneracy of extremely small masses.

Instead of or in addition to Mass Decay, stability for/in complex scenes can be increased by:

-
Increasing the main solver's iteration count via p_max_MC_iters

-
Decreasing the maximum step allowed per entity
these options are less "powerful", more expensive, but more physically accurate.

##
CVars

CVar/Command Name
 |
Description
 |
Comments
 |

**
p_mass_decay
**

 |
The main decay value (per level).

 |
 <0 - stabilizing decay

1 = no decay

>1 - negative decay (mass increase)

Default value = 1.

 |

**
p_mass_decay_prepasses
**

 |
The number of solver passes over all contacts before mass decay is considered.

 |
More prepasses is more expensive (though this method is still fairly affordable in general), but makes the simulation more realistic.

Fewer prepasses could mean that stacks are more stable than physically accurate.

Default value = 5.

 |

**
p_mass_decay_min_level
**

 |
The minimum required group "depth" to trigger mass decay on a group.

 |
Group depth is the number of "layers" of objects that are "chained" contact-wise, not necessarily vertically.

Generally, the larger the depth, the harder it is to resolve the group.

Default value = 12.

 |

**
p_mass_decay_max_level
**

 |
The maximum body level, after which mass decay is no longer applied.

 |
Capped at 100.

Default value = 100.

 |

**
p_mass_decay_heavy_threshold
**

 |
Mass difference for assigning objects 0 depth level for mass decay purposes.

 |
Default value = 20.

 |

[Usage](#usage)
[CVars](#cvars)
