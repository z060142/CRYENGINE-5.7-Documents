# Audio & Particles

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/44964916
- Page ID: 44964916
- Breadcrumb: Audio > Audio Overview > Audio & Particles
- Parent: Audio Overview

## Content

![Image](https://www.cryengine.com/docs/static/attachments/44964922)

##
Overview

This section describes how to add Audio in the Particle Editor.

You can find more about the concept of the Particle Editor under
[Particles](../../Graphics%20%26%20Rendering/Particles.md)
 as well as more details about the Tool under
[Particle Editor](../../Editor%20Tools/Particle%20Editor.md)
.

##
Adding an Audio Trigger

Create a new Effect using the New Effect button in the top-left corner of the toolbar.

This will spawn a new untitled Particle Effect with following Components:

![Image](https://www.cryengine.com/docs/static/attachments/44964921)

First, you have to add the respective Audio Components by clicking the drop-down list next to the
Component
 field.

![Image](https://www.cryengine.com/docs/static/attachments/44964920)

There are two options available. Audio Trigger and RTPC. Selecting the
Trigger
 will create an additional
Audio: Trigger
 component. Double-click it to expand and show the Audio Trigger properties.

![Image](https://www.cryengine.com/docs/static/attachments/44964919)

Field
 |
Description
 |

Name
 |
Click to select an Audio Trigger from the Audio Controls
 |

Trigger
 |
Defines when the Trigger is executed
 |

Occlusion
 |
Allows selecting amount of occlusion Raycast Options
 |

Follow Particle

 |
When checked it will follow the Entity Position
 |

Clicking in the
Name
 field will open the Audio Controls to choose the Audio Trigger from.

##
Adding an Audio RTPC

Similar to the Audio Trigger we can also add a component named Audio: RTPC to each particle effect via the Dropdown Menu.

*
![Image](https://www.cryengine.com/docs/static/attachments/44964918)

*
Double-click it to expand and show the Audio: RTPC Properties.

![Image](https://www.cryengine.com/docs/static/attachments/44964917)

Field
 |
Description
 |

Name
 |
Click to select a RTPC from the Audio Controls
 |

Value
 |
Allows to set a value or curve for advanced behavior
 |

Clicking the
Name
 field will open the Audio Controls to choose the RTPC.
