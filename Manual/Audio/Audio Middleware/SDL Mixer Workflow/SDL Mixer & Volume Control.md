# SDL Mixer & Volume Control

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/53542972
- Page ID: 53542972
- Breadcrumb: Audio > Audio Middleware > SDL Mixer Workflow > SDL Mixer & Volume Control
- Parent: SDL Mixer Workflow

## Content

In SDL_mixer users can manipulate a file's volume by connecting it to a parameter:

![Image](https://www.cryengine.com/docs/static/attachments/53543011)

*
Connecting a file to a parameter
*

Tweaking that parameter between 0 and 1 will effectively change the volume between -96dB (complete silence) and the maximum volume that has been set in the
**
Properties
**
 of the
**
Connection
**
 between that file and the connected
**
Trigger
**
:

![Image](https://www.cryengine.com/docs/static/attachments/53543012)

*
The max volume when Parameter is set to 1
*
