# CRYENGINE 5.3.2

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/47316993/pages/44962664
- Page ID: 44962664
- Breadcrumb: Engine Release Notes (Current) > CRYENGINE 5 > CRYENGINE 5.3 > CRYENGINE 5.3.2
- Parent: CRYENGINE 5.3

## Child Pages

- [Third-party SDKs in 5.3.2](CRYENGINE%205.3.2/Third-party%20SDKs%20in%205.3.2.md)

## Content

### Release Highlights

**Crash Reporter Now Available**

The new Crash Reporter has now been activated. Should the Engine crash, then the following window will open:

![Image](https://www.cryengine.com/docs/static/attachments/44962665)

This will allow you to send us information (along with the necessary files) and create a bug report that is sent to our QA team. Hence, reporting a crash has never been easier.

### Audio

#### Fmod

- **Fixed:** Fmod dlls now properly added to the build.

### Core/System

#### Engine General

- **Fixed:** Added GeomEntity not visible in GameLauncher.

### Physics

#### PhysX

- **Fixed:** Merge changes from main to main_stabilization - resolve former limitation to just 4-wheeled vehicles in PhysX.

### Network

#### Network General

- **Fixed:** Dedicated crash on start in CEnvironmentProbeEntity.

### Known Issues

- Cryselect Issue. If users do not see 'Generate/repair metadata' (please see: [AssetSystem-GeneratingMetadata](../../../../Manual/Editor%20Tools/Asset%20Browser/Asset%20System.md)) they should then;

- Copy *cryselect.exe* from the latest engine folder <c:\Program Files (x86)\Crytek\CRYENGINE Launcher\Crytek\CRYENGINE_5.3\Tools\CryVersionSelector\cryselect.exe> to the <c:\Program Files (x86)\Crytek\CRYENGINE Launcher\live\cryselect.exe>
- This registers *.cryproject files as a Windows file extension: * cryselect.exe install*
