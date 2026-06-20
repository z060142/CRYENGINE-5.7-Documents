# Tips, Tricks and Experiences Using Stereo - 3D

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/44959257
- Page ID: 44959257
- Breadcrumb: Graphics & Rendering > Stereoscopic Rendering > Tips, Tricks and Experiences Using Stereo - 3D
- Parent: Stereoscopic Rendering

## Content

### Overview

The only internal project available right now is the Crysis demo so I will use this, but the issues also exists elsewhere, which prompted this article.

The realigned examples are altered in post, this is possible because the camera rig was parallel, but it does re-crop the image.

Here the character is what you are focusing your eyes on, however, the window is not set to his helmet.

![Image](https://www.cryengine.com/docs/static/attachments/53542941)

Here are some examples with the Stereo Window altered using 'Easy Adjustment' in SPM to the closest object:

![Image](https://www.cryengine.com/docs/static/attachments/53542945)

Here are some other examples:

![Image](https://www.cryengine.com/docs/static/attachments/53542942) The stereo window is so deep, it takes a second to adjust, whereas below, you instantly see and there is less ghosting.

![Image](https://www.cryengine.com/docs/static/attachments/53542946)

![Image](https://www.cryengine.com/docs/static/attachments/53542947)

A change like this doesn't alter the image much (depth, crop) but it does improve things a lot on devices with ghosting.

![Image](https://www.cryengine.com/docs/static/attachments/53542947)

![Image](https://www.cryengine.com/docs/static/attachments/53542944)

Tough call, I would say set it to the hand, and deal with the violation of the bar, in practice, we should try to keep things from coming this close to camera.

![Image](https://www.cryengine.com/docs/static/attachments/53542948)
