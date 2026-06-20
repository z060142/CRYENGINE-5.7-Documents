# Important 3.8.3 EaaS Code and Data Changes

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/47316993/pages/44962932
- Page ID: 44962932
- Breadcrumb: Engine Release Notes (Current) > CRYENGINE 3.x > EaaS 3.8 > EaaS 3.8.3 > Important 3.8.3 EaaS Code and Data Changes
- Parent: EaaS 3.8.3

## Content

##
Code Interface Changes

##
IAudioSystemImplementation

-
**
Added
**
: EAudioRequestStatus PlayFile(IATLAudioObjectData* const pAudioObjectData, char const* const szFile);

-
**
Added
**
: EAudioRequestStatus StopFile(IATLAudioObjectData* const pAudioObjectData, char const* const szFile);

-
**
Added
**
: Void GamepadConnected(TAudioGamepadUniqueID const deviceUniqueID);

-
**
Added
**
: Void GamepadDisconnected(TAudioGamepadUniqueID const deviceUniqueID);

##
IAudioProxy

-
**
Added
**
: Void PlayFile(char const* const szFile);

-
**
Added
**
: Void StopFile(char const* const szFile);

-
**
Changed
**
: Void SetPosition(
**
SATLWorldPosition

**
const& rPosition);
**
to
**

                 Void SetPosition(
**
Matrix34

**
const& rPosition);

##
IEntityAudioProxy

-
**
Added
**
: Void PlayFile(char const* const szFile);

-
**
Added
**
: Void StopFile(char const* const szFile);

-
**
Changed
**
: Void SetAuxAudioProxyOffset(
**
SATLWorldPosition

**
const& rOffset, TAudioProxyID const nAudioProxyLocalID = DEFAULT_AUDIO_PROXY_ID);
**
to
**

                 Void SetAuxAudioProxyOffset(
**
Matrix34

**
const& rOffset, TAudioProxyID const nAudioProxyLocalID = DEFAULT_AUDIO_PROXY_ID);

-
**
Changed
**
:
**
SATLWorldPosition

**
const& GetAuxAudioProxyOffset(TAudioProxyID const nAudioProxyLocalID = DEFAULT_AUDIO_PROXY_ID);
**
to
**

**
Matrix34

**
const& GetAuxAudioProxyOffset(TAudioProxyID const nAudioProxyLocalID = DEFAULT_AUDIO_PROXY_ID);

##
IEntityProxy

-
**
Changed
**
: Int GetPartId0();
**
to
**

                 Int GetPartId0(int islot=0);
