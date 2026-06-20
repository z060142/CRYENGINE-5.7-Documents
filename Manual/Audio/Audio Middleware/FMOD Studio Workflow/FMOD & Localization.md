# FMOD & Localization

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/44964949
- Page ID: 44964949
- Breadcrumb: Audio > Audio Middleware > FMOD Studio Workflow > FMOD & Localization
- Parent: FMOD Studio Workflow

## Content

## Overview

## Sections

This article explains how to set up localized soundbanks in FMOD Studio and CRYENGINE. CRYENGINE loads localized soundbanks from the localization folder, for example, `localization/english/audio/fmod/`. This allows having multiple languages (not only audio) completely separated from each other to swap them in runtime and also for easier distribution across different countries.

Make sure you download the [CRYENGINE GameSDK FMOD Project](https://www.cryengine.com/marketplace/product/crytek/cryengine-fmod-project) from the Asset Database and copy it to the required location.

[Sections](#sections)[Information About Localized Soundbanks](#information-about-localized-soundbanks)[Setting Up Localized Soundbanks in FMOD Studio](#setting-up-localized-soundbanks-in-fmod-studio)

### Information About Localized Soundbanks

FMOD builds its localized soundbanks into a subfolder of the soundbank location, for example, */audio/fmod/english/*.

The folder of the localized soundbanks cannot be specified in FMOD, therefore it's necessary to move the Soundbanks after generation. To automate this process, the CRYENGINE SDK contains post-generation scripts that move the Soundbanks to the correct folder. These scripts can be found in: */audio/fmod_project/Scripts/*.

The scripts only work when the FMOD project is at the same location as in the SDK: *`/audio/fmod_project/`.* Otherwise, the scripts need to be edited to match the project's location.

Currently only English and German are supported by these scripts, but you can also easily add other languages. You can open the scripts with a text editor like Notepad++, and copy the lines of an existing language and replace the language name. In the SDK FMOD project, these scripts are executed automatically after Soundbank generation.

### Setting Up Localized Soundbanks in FMOD Studio

#### In Windows explorer

- In the FMOD project folder, create a subfolder called Scripts and copy over the following files from the example project/GameSDK:
- crytek_languages.txt
- crytek_localized_banks.js
- crytek_move_banks_pc.bat
- crytek_move_banks_ps4.bat
- crytek_move_banks_xboxone.bat
- Inside crytek_languages.txt, specify all languages needed for the project. Don't use any white spaces, empty lines or special characters.

#### In FMOD Studio

- Create an event with one programmer instrument.
- Create a bank for every language that ends with "_<language name>" where <language name> needs to match the names defined in crytek_languages.txt
For instance:
- c_player_voc_english
- c_player_voc_german
- c_player_voc_french
- In each of these banks create an audio table and populate it with audio files and optionally with the keys.txt files.
Read the FMOD Studio documentation about audio tables for more information on how to set this up.
- After building the banks, the scripts will rename and copy the banks to the correct location.

The scripts only work when the FMOD project is at the same location as in the SDK: */audio/fmod_project/*. Otherwise, the scripts need to be edited to match the project's location.

#### In the Audio Controls Editor of CRYENGINE

- Create Preload Requests for the banks.
For localized banks, the language in the name has been removed by the scripts.
- Drag and drop a key into the Audio System Controls panel to create a new trigger. Or create a trigger manually and drag a key in the connections panel.
The localized sounds are listed under the "Keys" folder.
- In the connection properties of the trigger, select a programmer sound event.
