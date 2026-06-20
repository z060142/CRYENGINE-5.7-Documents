# EaaS 3.7.0 Texture Format Changes

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/47316993/pages/44963003
- Page ID: 44963003
- Breadcrumb: Engine Release Notes (Current) > CRYENGINE 3.x > EaaS 3.7 > EaaS 3.7.0 > EaaS 3.7.0 Texture Format Changes
- Parent: EaaS 3.7.0

## Content

##
Overview

For CRYENGINE 3.7.0 we changed the NormalMaps file format to BC5S (signed). Your existing compiled *.dds files will not work correctly as the format will be the previous 3Dc format.

The RC (Resource Compiler) will need to regenerate them again to the new, correct format.

To do this:

-
Close the editor & launcher. (Makes sure RC is inactive).

-
Select & delete all of the existing *.dds files inside your build (
`
<root>\GameSDK
`
).

-
Launch the Sandbox Editor & open a level. RC will being to process & generate all the *.dds files for the TIFs you have.
This will take some time depending on the amount and type of texture content you have, as well as available processing power.

As with every update, make sure to use the correct matching RC version for the build, and remember to update your
[plugins](/docs)
 and use the
[Settings Manager](/docs/static/engines/cryengine-3/categories/1114113/pages/12124943)
 to point CRYENGINE to the correct build.
