# System Requirements

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/44963076
- Page ID: 44963076
- Breadcrumb: CRYENGINE - Getting Started > System Requirements
- Parent: CRYENGINE - Getting Started

## Content

##
Your PC and its System Requirements?

Check the following system requirements. Your PC
**
MUST
**
 meet at least the minimum specification before you install CRYENGINE.

**
Minimum:
**
 |
**
Recommended:
**
 |

-
**
OS (to run Game):
**
 Windows 7, 8.1, 10 (64-bit)

-
**
OS (to run Editor):
**
Windows 7, 8.1, 10 (64-bit)

-
**
Processor:
**
 Intel Dual-Core min 2GHz (Core 2 Duo and above) or AMD Dual-Core min 2GHz (Phenom II X2 and above)

-
**
Memory:
**
 4 GB RAM

-
**
Graphics:
**
 NVIDIA GeForce 450 series or AMD Radeon HD 5750 series or higher (minimum 1 GB dedicated VRAM GDDR5)

-
**
DirectX:
**
 Version 11

-
**
Hard Drive:
**
 8 GB available space

-
**
Sound Card:
**
 DirectX Compatible Sound Card with latest drivers
 |

-
**
OS (to run Game):
**
 Windows 7, 8.1, 10 (64-bit)

-
**
OS (to run Editor):
**
Windows 7, 8.1, 10 (64-bit)

-
**
Processor:
**
 Intel Quad-Core (i5 2300) or AMD Octo-Core (FX 8150)

-
**
Memory:
**
 8 GB RAM

-
**
Graphics:
**
  NVIDIA GeForce 660Ti or higher, AMD Radeon HD 7950 or higher (minimum 2 GB dedicated VRAM GDDR5)

-
**
DirectX:
**
 Version 11

-
**
Hard Drive:
**
 8 GB available space

-
**
Sound Card:
**
 DirectX Compatible Sound Card with latest drivers
 |

Windows Vista SP1
As of CRYENGINE version 5.3.0 Windows Vista SP1 is no longer supported.

Video and Sound Card Drivers
Ensure that you have the most up to date video and sound card drivers installed on your PC.

Integrated GPUs and DirectX 11
CRYENGINE might run on the integrated GPUs from Intel and AMD (3
rd
 Generation Intel i-Core CPUs and above, AMD APUs that support DX11), but they are not officially supported and we advise you to not run CRYENGINE on integrated Graphics solutions due to non-optimal performance.

Please also keep in mind, that integrated GPUs share RAM with the CPU, thus resulting in less available RAM for the CPU and OS. Hence, 4 GB of RAM might not be enough and therefore minimum System Requirements will not be met.

Furthermore, for full DirectX 11 compatibility not only does the OS have to support it, but so does the GPU and at a hardware feature level. Hence, it doesn’t matter that the Windows OS is DX11 capable, the GPU MUST be too.

Check your GPU manufacturer’s website for more info (
[http://www.nvidia.com/content/global/global.php](
NVidia
)
 or
[https://www.amd.com/en/home](
AMD
)
)

Software
Ensure that you have the most
[https://support.microsoft.com/en-us/help/179113/how-to-install-the-latest-version-of-directx](
up to date version of Direct X
)
installed on your PC - this is particularly important after installing Windows from scratch when it is advisable to re-run the installation manually.

It’s also advisable to install all Visual C++ redistributables, these are available
[https://support.microsoft.com/en-us/kb/2977003](
here.
)
 This is particularly important if you have performed a new installation of Windows (minimum version Visual C++ 2015).

.NET Framework should be installed and up to date, it's available from
[https://www.microsoft.com/net/download/framework](
here
)
.

Windows Update
If you encounter issues with API-MS-WIN-CRT-RUNTIME-L1-1-0.DLL or similar missing on launch, ensure that Windows Update is enabled.

Specifically, this
[https://support.microsoft.com/en-us/help/2999226/update-for-universal-c-runtime-in-windows](
update
)
 is required to be installed.
