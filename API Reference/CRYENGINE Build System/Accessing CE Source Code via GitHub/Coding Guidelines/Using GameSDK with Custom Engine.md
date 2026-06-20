# Using GameSDK with Custom Engine

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/25529775
- Page ID: 25529775
- Breadcrumb: CRYENGINE Build System > Accessing CE Source Code via GitHub > Coding Guidelines > Using GameSDK with Custom Engine
- Parent: Coding Guidelines

## Content

This article covers a detailed walk through of the steps required to successfully compile and run the **gamesdk sample project** with a custom engine cloned from GIT. Note: We will not move the gamesdk source code, but will refer to assets located in an external project folder. In addition to the [steps required for C++ projects](/docs/static/engines/cryengine-5/categories/23756813/pages/25529768) you will need to:

- Download the [CRYENGINE GameSDK Sample Project](https://www.cryengine.com/marketplace/product/crytek/cryengine-gamesdk-sample-project) through the CRYENGINE Launcher i.e. from **"Library/My Assets"** Note: If you have not previously downloaded the CRYENGINE GameSDK Sample Project then you will have to do this first. It can be downloaded free of charge from the CRYENGINE [Asset Database.](https://www.cryengine.com/marketplace) You can easily locate the path of the asset by selecting "Reveal in Explorer" from the samples drop-down list
- Go to the newly downloaded GameSDK Sample Project folder and modify your project.cfg's *"engine_version=local"*
- Since we are building the GameSDK using the default WAF settings you will also need to modify project.cfg's *"sys_dll_game=CryGameSDK"*
- Run cry_waf.exe from the custom engine folder and create a **game_sdk** project. Open the generated solution and compile **[GameSDK] Profile x64**
- Add the following Visual Studio project property to your **Debuging/Command Arguments** *-projectroot "path_to_gamesdk_sample_downloaded_from_asset_database"*
- Add "**r_width=1280**", and "** r_height=720**" to system.cfg

You can now run your game project using a custom engine from Visual Studio or the Game.bat file. To load a map type **"+map woodland"** into the in-game console.
