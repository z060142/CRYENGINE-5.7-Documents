# Important CRYENGINE V Data and Code Changes

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/47316993/pages/44962603
- Page ID: 44962603
- Breadcrumb: Engine Release Notes (Current) > CRYENGINE 5 > CRYENGINE 5.0 > Important CRYENGINE V Data and Code Changes
- Parent: CRYENGINE 5.0

## Content

### Overview

Below are some important code and data changes that you should be aware of when moving to future releases of CRYENGINE.

### Deprecating Visual Studio 2012 and 2013

After CRYENGINE 5.1 we will no longer support Visual Studio 2012 and 2013. Please upgrade your projects to Visual Studio 2015 as previous versions will be completely removed in later Engine releases. Please refer to [Visual Studio Supported Versions](../../../../API%20Reference/CRYENGINE%20Build%20System/Visual%20Studio%20Supported%20Versions.md)for more information.

When building for Windows with the VS2012 or VS2013 toolchain: Currently the use of the 3rd-party Oculus library requires the use of the VS2015 toolchain. If you plan to use VS2012 or VS2013 with CRYENGINE 5.1 (and you agree to not having Oculus support), then please remove the Oculus library from the WAF spec file for your project and remove it as a dependency from CryRenderD3D11 and CrySystem. We are planning to automate this part of the setup when not using the VS2015 toolchain in the next Engine release.
