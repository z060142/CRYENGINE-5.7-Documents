# Managing Projects

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/69468348
- Page ID: 69468348
- Breadcrumb: CRYENGINE - Getting Started > Installing CRYENGINE > CRYENGINE Launcher Reference > Managing Projects
- Parent: CRYENGINE Launcher Reference

## Content

To begin working with CRYENGINE, you must first create or import a project. This will be your game's foundation.

##
Creating Projects

Projects can be created through the Launcher or, in the case of more recent CRYENGINE versions, through the Sandbox Editor itself.

To create a new project for a specific version of CRYENGINE via the Launcher
, this is what you need to do:

-
Open the
**
Projects
**
tab in the Launcher and click the  button in the top-right corner of the dashboard. This brings up the
**
Select Engine Version
**
 prompt, as shown:

![Image](https://www.cryengine.com/docs/static/attachments/69468370)

*
Select Engine version
*
*

*

-
Choose which installed version of CRYENGINE you'd like to use for your project.

##
CRYENGINE 5.6 and Later

From CRYENGINE release 5.6 onwards
, projects are created directly in the Sandbox Editor through the Project Browser.

Choosing to create your project through the Launcher with CRYENGINE 5.6 or later versions will bring up the following prompt:

![Image](https://www.cryengine.com/docs/static/attachments/69468361)

*
Create new project - 5.6.x
*

-
Click
**
Launch Sandbox
**
 to open up the Sandbox Editor's Project Browser, which lists templates that can be used to create projects
*

*

![Image](https://www.cryengine.com/docs/static/attachments/69468542)

*
New Project
*

*

*

-
Select a template, set its storage location and name, and click

**
Create Project
**

to complete the process. Your project will then open in the Sandbox Editor, and will also be listed in the Projects library of the Launcher.

##
CRYENGINE Versions Before 5.6

-
Choosing to create a project in CRYENGINE versions earlier than 5.6 will open the following dashboard in the Launcher:

![Image](https://www.cryengine.com/docs/static/attachments/69468535)

*
Create new project dashboard

*

-
Choose a template for your project, set its directory and name, and click
**
Create Project
**
. The project will be added to the Projects library of the Launcher.

-
If the
**
Create Project and Launch in Sandbox Immediately
**
 checkbox is ticked, the project will open in the Sandbox Editor immediately after you click the
**
Create Project
**
 button.

-
To open your project if you didn't tick the checkbox:

-
Navigate to the
**
Projects
**
 tab of the Launcher.

-
Locate your project and click the
![Image](https://www.cryengine.com/docs/static/attachments/69468359)
 icon in its listing.

-
Select the
**
Launch in Sandbox Editor
**
 option from the menu that opens.

![Image](https://www.cryengine.com/docs/static/attachments/69468368)

*
Launch in Sandbox Editor
*

##
Importing Projects

To import a previously created CRYENGINE project that is not listed in the Launcher:

-
Click the
**
Projects
**
 tab in the Launcher to open the Projects library.

-
In the top right corner of the Projects library, click
![Image](https://www.cryengine.com/docs/static/attachments/69468372)
; this opens the file explorer, allowing you to search for an existing CRYENGINE project to import.
The imported project will then be listed in the Projects library.

Importing projects that were created using Launcher versions prior to V.1.6.6 (available from the 18th of May, 2017) may cause their names to be changed; an imported project might be automatically renamed to Blank Game Template, for instance.

To fix this;

-
Select the project you'd like to upgrade.

-
Click the
 button in its listing.

-
Select the
**
Edit Project Details
**
 option from the menu.

-
Change the name of the project in the
**
Project Title
**
field of the Edit Project dashboard that opens.

##
Upgrading Projects

Projects created in
CRYENGINE
version
5.2 and onwards
 can be upgraded to work with newer Engine versions.

To do that, proceed as follows:

-
Click the
**
Projects
**
 tab in the Launcher to open the Projects library.

-
Select the project you'd like to upgrade, click the  button in its listing, and select the
**
Edit Project Details
**
 option from the menu

![Image](https://www.cryengine.com/docs/static/attachments/69468377)
*

Edit project details
*
*

*

-
This opens the Edit Project dashboard; scroll down to the
**
Engine Version
**
 field and select your target Engine version using the dropdown. Click
**
Save Changes
**
 to proceed.

![Image](https://www.cryengine.com/docs/static/attachments/69468378)

*
Engine Version

*

-
You will then be prompted to confirm the Engine version switch. Click
**
Switch Engine Version
**
 to proceed.

![Image](https://www.cryengine.com/docs/static/attachments/69468379)

*
Switch Engine Version confirmation

*

Make sure to tick the
**
Create Backup
**
 checkbox to avoid loss of data. When ticked, this option allows you to create an entire copy of your project and save it in a folder of your choice.

When updating from an older version of the Launcher, some of your assets might need to be migrated in order to sync correctly with the updated Launcher version. When this is the case, you will receive the following prompt:

![Image](https://www.cryengine.com/docs/static/attachments/69468539)

-
Clicking
**
Migrate All
**
will initiate the migration of all your assets following your confirmation. You will see a confirmation once the migration is complete.

-
Clicking
**
Customize
**
 allows you to choose which assets to migrate.

![Image](https://www.cryengine.com/docs/static/attachments/69468538)

-
If you choose to
**
Skip
**
this step, you will see a
[reminder](../CRYENGINE%20Launcher%20Reference.md#CRYENGINELauncherReference-Migrationreminder)
 to complete the migration process in the Asset Library.

Errors might arise while upgrading projects, due to the differing interfaces of different Engine versions; this can be fixed manually. In the event of an unexpected error, an
*
output.log
*
 file will be generated in the project's storage directory, which can be reviewed to determine the cause of the error.

Please note however that,

-
Users inexperienced in handling game code may prefer to create a new project template in their target Engine version via the Launcher, and copy the
*
Assets
*
 folder of their source project to the root directory of the new project.

-
If the source project that is being updated was built using a project template, a new
*
game.dll
*
 file must be generated by recompiling the project's solution after performing the update.

-
To recompile the solution, locate the project's .cryproject file on disk, right-click it, and select the
**
Generate Solution
**
 option from the context menu.
If switching to a newer Engine version still fails, users may revert back to the previous CRYENGINE version by repeating the steps described in this section, and selecting the previous CRYENGINE version from the
[Engine Version](Managing%20Projects.md#ManagingProjects-engine_version)
 dropdown.

[Creating Projects](#creating-projects)
[Importing Projects](#importing-projects)
[Upgrading Projects](#upgrading-projects)
