# Settings Manager

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/25535313
- Page ID: 25535313
- Breadcrumb: System Utilities > System Utilities Overview > Settings Manager
- Parent: System Utilities Overview

## Content

![Image](https://www.cryengine.com/docs/static/attachments/29934094)

##
Overview

##
Sections

In order for the Resource Compiler to know where the ENGINE is currently located, a key is written to the registry which contains the current ENGINE path information.

This key is obtained and written through the CRYENGINE Settings Manager which is located in:
`
<root>\Tools\SettingsMgr.exe
`

[Sections](#sections)
[Dialog](#dialog)

##
Dialog

The first time you run the Settings Manager the dialog will state that an "Active build setup for CRYENGINE is not found" it should look something like the screenshot below:

![Image](https://www.cryengine.com/docs/static/attachments/35401701)

This indicates that there is no CRYENGINE path information written to the registry and gives you two options:

-
Use the path where the SettingsMgr was run from

-
Or scan for builds in other locations
We recommend, and it's easiest, to use the SettingsMgr.exe's location. It is most likely that you would want to run the ENGINE from that location anyway.

If "all is well" with the build, then you will see two green ticks for the two different components:

![Image](https://www.cryengine.com/docs/static/attachments/35401699)

Should some RC files be missing or you cannot locate the tools, then the Settings Manager will see this and report the problem:

![Image](https://www.cryengine.com/docs/static/attachments/35401700)

For extra functionality you can also add additional RC commands from the Resource Compiler tab:

![Image](https://www.cryengine.com/docs/static/attachments/35401702)
