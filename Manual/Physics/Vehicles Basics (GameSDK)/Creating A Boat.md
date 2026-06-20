# Creating A Boat

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/26870705
- Page ID: 26870705
- Breadcrumb: Physics > Vehicles Basics (GameSDK) > Creating A Boat
- Parent: Vehicles Basics (GameSDK)

## Content

![Image](https://www.cryengine.com/docs/static/attachments/29933326)

##
Overview

##
Sections

This article explains how to setup a boat model for a usable vehicle in CRYENGINE.

[Sections](#sections)
[Proxies](#proxies)
[Helpers](#helpers)

##
Proxies

You cannot have multiple proxy nodes for your boat. If you have more than one proxy, the boat will sink immediately.

 |
 |

Multiple Proxies = Bad
 |
Single Proxy = Good
 |

##
Helpers

In vehicle scripts you'll often find references to "Helpers". CRYENGINE has two types of helpers in this case:

-
**
Vehicle Helpers
**
 - These come from the vehicle script.

-
**
Asset Helpers
**
 - These come from the object mesh.
In some cases the vehicle code is looking for helpers inside the vehicle itself, as an example, the propellers for the speedboat require the helpers to be built into the asset.

```

`
    <Particles>
        <Exhaust insideWater="1" outsideWater="0">
            <Helpers>
                <Helper value="propeller_right_pos"/>
                <Helper value="propeller_left_pos"/>
            </Helpers>
`

```

Simply add a Dummy as a child of the main render mesh node and position it where your propeller is. Name it in accordance with the script (or vice versa, the values aren't hard-coded):

And now you'll see the effects working for the left propeller:

*
You can debug vehicle movement with v_profileMovement=1
*

*

*
