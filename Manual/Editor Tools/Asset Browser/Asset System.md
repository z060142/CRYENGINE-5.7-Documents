# Asset System

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/29447695
- Page ID: 29447695
- Breadcrumb: Editor Tools > Asset Browser > Asset System
- Parent: Asset Browser

## Content

## Overview

The Asset System aims to unify file management across the range of tools present in CRYENGINE. For this purpose we have decided to break down the content of CRYENGINE projects into assets, and organize our workflow around them.

Assets are the "unit of work" of a CRYENGINE project and represent one or several files on disk, as well as a *.cryasset metadata file to carry extra information relevant to this asset. Note that only one person should be working on a specific asset at a given time and all files related to an asset must be checked in and out of source control simultaneously.

The goal of this system is to hide the files from the Designers and have them reason about assets only - this should be a much more simple and intuitive representation of their work.

Using the tools available in the Sandbox Editor, Designers can then import, create, edit and submit assets to the main repository of the project.

The main tool and the front-end for the Asset System is the Asset Browser.**[See here](../Asset%20Browser.md)** for information on how this works.

### Implementation

The Asset System needs to store metadata for every asset. To achieve this, every asset comes with a *.cryasset file that contains all the relevant information for the asset.

- In order for the Asset System to function properly, these *.cryasset metadata files MUST be submitted to source control. *.cryasset files can be regenerated, but some information may be lost in the process. Currently losing a cryasset file is recoverable, but it may not be in the future.
- The *.cryasset files are not necessary for the game to run, and should not be deployed with the final builds of the game. These files are only necessary for the Editor during production.

### Generating Metadata

Before being able to use the Asset Browser on an existing project you'll have to generate *.cryasset files.

Any project created using Engine version 5.2 or earlier doesn't have the metadata required, so if your project was created using one of those Engine versions you'll have to follow this procedure.

This procedure is unnecessary if your project was created with Engine version 5.3 or later, as metadata will automatically be created for assets made in Engine versions 5.3 and later.

In the Asset Browser, choose **Edit -> Generate/Repair All Metadata**.

Your assets should now be displayed in the Asset Browser.

#### Missing or Corrupted Cryasset Files

If the cryasset files are missing, something is corrupted or if some assets do not show in the content browser, then you can either re-import/re-save individual assets or use the repair button mentioned above.

[Implementation](#implementation)[Generating Metadata](#generating-metadata)[Missing or Corrupted Cryasset Files](#missing-or-corrupted-cryasset-files)
