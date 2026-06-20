# Upgrading to CRYENGINE 5.1 - Code Formatting

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/47316993/pages/44962623
- Page ID: 44962623
- Breadcrumb: Engine Release Notes (Current) > CRYENGINE 5 > CRYENGINE 5.1 > CRYENGINE 5.1.0 > Upgrading to CRYENGINE 5.1 - Code Formatting
- Parent: CRYENGINE 5.1.0

## Content

### Introduction

With CRYENGINE 5.1 we have improved overall code quality and applied a new unified coding standard across all Engine modules. This page describes the most convenient way of upgrading from a previous Engine version (3.8.x) to CRYENGINE 5.1 or later code base.

### Auto-formatting in Visual Studio

By integrating *uncrustify* with Visual Studio it is possible to have your code auto-formatted in accordance with the guidelines and every time you save your work. This takes away any effort involved in complying with the standard.

#### Step 1: Preparation

You can find the tool at root`/Code/Tools/uncrustify`.

Get and store it at in a temporary location. Open it and change the *executable* and * parameters* paths so that they match your CRYENGINE installation directory (4 spots in total).

#### Step 2: Download "Code Beautifier" Extension

Download and install the "Code Beautifier" from the following page: [Code Beautifier extension for Visual Studio 2015.](https://visualstudiogallery.msdn.microsoft.com/febc2d81-34bd-4324-aadb-0a942eb39d43)

#### Step 3: Open Code Beautifier Options

#### Step 4: Import Settings

Click the **Import...** button and load your customized ** CodeBeautifierSettings.xml**.

#### Step 5: Verifying Settings

Verify that the application path and arguments path are valid, then **Save.**

#### Now You Are Ready!

You can now format documents from the menu as shown in step 3 (or you can bind this to a hotkey/make a button in a toolbar with the default VS customization features).
