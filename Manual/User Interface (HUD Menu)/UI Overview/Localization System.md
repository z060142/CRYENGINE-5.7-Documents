# Localization System

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/25534808
- Page ID: 25534808
- Breadcrumb: User Interface (HUD/Menu) > UI Overview > Localization System
- Parent: UI Overview

## Content

![Image](https://www.cryengine.com/docs/static/attachments/29934091)

##
Overview

##
Sections

CRYENGINE is able to localize text and sound for different languages. All of the necessary localization data is stored inside pak files, stored in the
`
<root>/Localization
`
 folder (example:
`
GameSDK/Localization/English_XML.pak
`
).

Inside of the pak files all files contained in the Languages folder can be directly translated except
*
dialog_recording_list.xml
*
 and
*
ai_dialog_recording_list.xml
*
. These two files are used by the dialog system and need further explanation.

The
g_language
 console variable can be used to load a specific language, which is addressed by the name of the language pak file (example:
g_language = german
for German.pak).

The dialog recording lists as well as translated text are loaded and handled by the LocalizationManager class. Make sure that new files are correctly loaded in the
*
CSystem::OpenLanguagePak()
*
 function.

[Sections](#sections)
[Usage](#usage)
[PAK/Folder structure](#pakfolder-structure)
[Texture Localization](#texture-localization)

##
Usage

Inside certain scripts shipped with the SDK, you'll find references to localization strings. One example can be found in the InteractiveEntity object:
`
GameSDK/Scripts/Entities/Others/InteractiveEntity.lua
`

```

`
UseMessage = "@use_object",
`

```

The localization string for this reference is located inside:
`
<root>\Localization\English_XML.pak\text_ui_ingame.xml
`

Key

 |
Original Text

 |
Translated Text

 |

use_object

 |
Use object

 |
Use object

 |

This table is used to define strings of text which are then displayed in game. When the player walks up to the InteractiveEntity Entity, "Use object" will be displayed on the screen.

If the string is defined in alternate languages and the player use using an alternate language, it will be displayed as such.

##
PAK/Folder structure

Using the localization files inside pak files allows you to create multiple language packs. For example, CRYENGINE SDK ships with 3 language packs, English (default), German and Korean. The structure of these pak files is the same for each language.

For testing purposes though, you are not required to use .pak files. You can place .xml files for example in the main Localization folder and the engine will read these by default (similar to extracting objects from pak files, the engine will prioritize external content).

<root>

 |

..

 |
**
**
Localization
**
**

 |

..

 |
..

 |
**
English.pak / English_XML.pak

**

 |

..

 |
..

 |
..

 |
text_ui_warnings.xml

 |

..

 |
..

 |
..

 |
dialog folder

 |

..

 |
..

 |
..

 |
etc

 |

..

 |
..

 |
**
German.pak / German_XML.pak

**

 |

..

 |
..

 |
..

 |
text_ui_warnings.xml

 |

..

 |
..

 |
..

 |
dialog folder

 |

..

 |
..

 |
..

 |
etc

 |

..

 |
..

 |
**
Korean.pak / Korean_XML.pak

**

 |

..

 |
..

 |
..

 |
text_ui_warnings.xml

 |

..

 |
..

 |
..

 |
dialog folder

 |

..

 |
..

 |
..

 |
etc

 |

..

 |
..

 |
text_ui_warnings.xml

 |

..

 |
..

 |
dialog folder

 |

..

 |
..

 |
etc

 |

When you don't use pak files but rather xml files in a folder structure, you need to copy the files of the language of choice to the root folder (not
`
Localization/<language
`
>), example: <root>/Localization/text_ui_warnings.xml

##
Texture Localization

For detailed information on localizing textures, refer to the
[Texture Localization](Texture%20Localization.md)
 article.
