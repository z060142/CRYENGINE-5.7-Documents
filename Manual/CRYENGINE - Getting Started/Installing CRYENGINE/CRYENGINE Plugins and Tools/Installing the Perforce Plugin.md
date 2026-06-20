# Installing the Perforce Plugin

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/44963515
- Page ID: 44963515
- Breadcrumb: CRYENGINE - Getting Started > Installing CRYENGINE > CRYENGINE Plugins and Tools > Installing the Perforce Plugin
- Parent: CRYENGINE Plugins and Tools

## Content

Perforce support is only available for full Engine code packages and requires additional *.dll files.

##
Overview

Perforce is a version control software that is integrated into the Sandbox Editor. Sandbox automatically detects whether Perforce is available or not.

##
Installation and Setup

In order to integrate Perforce with the Sandbox Editor, then Perforce must be properly configured on your PC and with the environment variables P4CLIENT, P4PORT, and P4USER set to the correct settings.

To test if the setup is correct, then you should be able to use the P4.exe command-line utility (supplied by Perforce) to sync the files.

Once the
`
GameSDK\Levels
`
\ directory syncs with Perforce, then the Sandbox Editor can be started.

##
Sandbox Settings

Go to the Preferences window under
**
Edit → Preferences
**
.

Under
**
General Settings → General
**
 make sure that the
**
Enable Source Control
**
checkbox is checked. This integrates Perforce with the Sandbox Editor.

![Image](https://www.cryengine.com/docs/static/attachments/44963516)

If the checkbox is enabled but without a proper Perforce server setup, then users can experience slowdowns in the Material Editor or in other Tools that take advantage of source control. In this case just uncheck the checkbox to return to normal non-source control operation.

 While saving a level that was synced from Perforce, a message box will prompt you about replacing the *.cry file. Click either the
**
Overwrite
**
 or
**
Check Out
**
boxes.

![Image](https://www.cryengine.com/docs/static/attachments/44963521)

Once the *.cry file has been checked out or overwritten using the Sandbox Editor, then the Perforce client should be used to prepare to submit the files.

[Installation and Setup](#installation-and-setup)
[Sandbox Settings](#sandbox-settings)
