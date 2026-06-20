# Achievements

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/76448466
- Page ID: 76448466
- Breadcrumb: Projects and Plug-ins > GamePlatform Plugin > GamePlatform Features (Discord/Steam) > Achievements
- Parent: GamePlatform Features (Discord/Steam)

## Content

##
Overview

The Achievements abstraction handles statistics and achievements (trophies on PlayStation, for example).

To facilitate a more fluid experience with the interface, a local configuration of achievements by way of an XML file has been opted for; you can populate the XML file with platform-specific achievement and statistical information. This will be read by the Flow Graph and Schematyc (Experimental) systems to create specialized nodes that you can use in your graphs.

-
Properly filling out the Achievements configuration file is required if you want to use the GamePlatformNodes plugin (Flow Graph/Schematyc Nodes and Achievement Detail cache).

-
Since the functionality of achievements varies with each platform, we recommend reading the platform vendor's documentation on how achievements and statistics are implemented on it.

##
Achievement Configuration

The Achievements data XML file (
*
statistics.xml)
*
 can be stored anywhere (relative to your project's
*
Assets
*
directory) using the g_PlatformStatsFile CVar.

**
g_PlatformStatsFile
**

Lets you specify the path (relative to the
*
Assets
*
 directory) where the
*
statistics.xml
*
Achievements data file should be located.

-
**
Usage
**
:
*
g_PlatformStatsFile <filepath>
*

-
Default:
*
l
*
*
ibs/config
*

##
Example Achievements Config File

```

`
<Statistics>
    <!--
        This file is used by the game platform nodes plugin to specify achievements (or trophies) and statistics for each platform.

        <Achievement
            guid            A unique GUID of format: xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx (0-9 A-F, can be enclosed in curly braces)
            platform        One of: Steam, Playstation or Xbox.
            label           A label that can be used to display in-game. (Can be a localization string for example).
            description     A description that can be used to display in-game. (Can be a localization string for example).
            apiid           Unique Id number of the achievement.
            apiname         Unique platform specific name for the achievement. (May be the same as apiid if no name is available).
            min             The minimum progress of an achievement (used as a lower limit for accumulating progress).
            max             The maximum progress of an achievement that denotes achieving the challenge and being awarded.
        />

        <Statistic
            guid            A unique GUID of format: xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx (0-9 A-F, can be enclosed in curly braces)
            platform        Must be: Steam (Only platform this is implemented for).
            label           A label that can be used to display in-game. (Can be a localization string for example).
            description     A description that can be used to display in-game. (Can be a localization string for example).
            apiname         Unique platform specific name for the achievement.
            type            One of: Integer or Float.
        />
    -->

    <!-- STEAM -->
  <Statistic guid="{08CCF79F-E894-4440-B08A-9D0437205045}" platform="Steam" label="FeetTravelled" description="Number of feet travelled in game" apiname="feet" type="Float"/>
  <Statistic guid="{A43EE317-CDAD-408A-B0F3-3BB123214C77}" platform="Steam" label="GamesWon" description="Number of games won" apiname="gameswon" type="Integer"/>

  <Achievement guid="{3766F186-7D46-472F-B0D7-AFA568FFA351}" platform="Steam" label="Win One Game" description="Win a single game" apiid="0" apiname="ACH_WIN_ONE_GAME" min="0" max="1" />
  <Achievement guid="{B6781FDF-F519-4882-9F15-A9918AEF1CF9}" platform="Steam" label="Win 100 Games" description="Win 100 games" apiid="1" apiname="ACH_WIN_100_GAMES" min="0" max="100" />
  <Achievement guid="{8A86DFF1-6C57-4534-B482-A9A141CA980A}" platform="Steam" label="Travel 1 Mile" description="Travel a single mile (1400 meters)" apiid="2" apiname="ACH_TRAVEL_FAR_ACCUM" min="0" max="5280" />
  <Achievement guid="{48DC0FA4-1D0F-409C-B6CC-19C581D5D3C1}" platform="Steam" label="Travel 500ft" description="Travel 500 feet (152 meters)" apiid="3" apiname="ACH_TRAVEL_FAR_SINGLE" min="0" max="500" />

    <!-- XBOX -->
  <Achievement guid="{D1C06456-9281-494F-BAF8-40B896D9E5A5}" platform="Xbox" label="Achievement 1" description="Description for Achievement 1" apiid="0" apiname="ACH_Test_1" min="0" max="1" />
  <Achievement guid="{DA4CC303-59A8-4F4A-A2EC-95393C2EE913}" platform="Xbox" label="Achievement 2" description="Description for Achievement 2" apiid="1" apiname="ACH_Test_2" min="0" max="10" />

    <!-- PLAYSTATION -->
  <Achievement guid="{41A118D8-FB84-4777-BFEC-AFCB1C7E9AAC}" platform="Playstation" label="Achievement 1" description="Description for Achievement 1" apiid="0" apiname="ACH_Test_1" min="0" max="1" />
  <Achievement guid="{AB929FDA-DD87-4C5E-B18B-5B9705D7D0A6}" platform="Playstation" label="Achievement 2" description="Description for Achievement 2" apiid="1" apiname="ACH_Test_2" min="0" max="10" />

</Statistics>
`

```

As you can see, some platforms like Steam use statistics as a method of recording data; other platforms can have their own implementations and methods of recording statistical data and using this data to trigger achievement unlocks.

On most platforms, achievements can be awarded directly, and in some cases revoked.
Usually, it is preferred to only allow achievements to be unlocked by an authoritative server so that a user cannot bypass requirements and unlock achievements that they have not legitimately earned.

Please see the corresponding platform documentation for info. on how to implement this and if it is a viable option.

##
Achievement Service Functions

##
Download

Attempts to download current statistical data from the remote platform service.

**
Platform(s)
**
 |
Steam
 |

API
 |
Cry::GamePlatform::IStatistics::Download
 |

Flow Graph Nodes
 |
GamePlatform::Stats::Download
 |

Schematyc Nodes
 |
Function::GamePlatform::Service::Statistics::Download
 |

##
Get

Retrieves the float or integer value of a statistic using the API name or ID.

**
Platform(s)
**
 |
Steam
 |

API
 |
Cry::GamePlatform::IStatistics::Get
 |

Flow Graph Nodes
 |
N/A
 |

Schematyc Nodes
 |
N/A
 |

##
GetAchievement

Retrieves the achievement corresponding to the specified API name or ID.

**
Platform(s)
**
 |
Steam
 |

API
 |
Cry::GamePlatform::IStatistics::GetAchievement
 |

Flow Graph Nodes
 |
N/A (Nodes auto generated from configuration data)
 |

Schematyc Nodes
 |
N/A (Auto generated data type values for the Achievement Data Type)
 |

##
ResetAchievements

Resets all achievements associated with the local user.

Platform(s)
 |
Steam
 |

API
 |
Cry::GamePlatform::IStatistics::ResetAchievements
 |

Flow Graph Nodes
 |
N/A
 |

Schematyc Nodes
 |
N/A
 |

##
ResetStatistics

Resets all statistical data associated with the local user.

**
Platform(s)
**
 |
Steam
 |

API
 |
Cry::GamePlatform::IStatistics::
ResetStatistics
 |

Flow Graph Nodes
 |
N/A
 |

Schematyc Nodes
 |
N/A
 |

##
Set

Sets the float or integer value of a statistic using the API name or ID.

**
Platform(s)
**
 |
Steam
 |

API
 |
Cry::GamePlatform::IStatistics::Set
 |

Flow Graph Nodes
 |
N/A
 |

Schematyc Nodes
 |
N/A
 |

##
Upload

Attempts to upload current statistical data to the remote platform service.

**
Platform(s)
**
 |
Steam
 |

API
 |
Cry::GamePlatform::IStatistics::Upload
 |

Flow Graph Nodes
 |
GamePlatform::Stats::Upload
 |

Schematyc Nodes
 |
Function::GamePlatform::Service::Statistics::Upload
 |

##
Achievement Specific Functions

Implementation of Achievement specific function differs between the API, Flow Graph and Schematyc:

-
In the API, you retrieve an achievement directly based on its name or ID, and then also call actions on it directly (eg, to award the achievement).

-
In Flow Graph, nodes are generated in the GamePlatform::Stats::[Platform] node category. You can then trigger certain actions by activating specific pins on the node.

-
In Schematyc (Experimental), an Achievement is a Data Type (similar to the API). The Data Type Selection is generated via the Achievement configuration file, so only valid options are available. You can then call service functions and pass to them the achievement you wish to act on.
Flow Graph and Schematyc provide extra data that is stored inside the configuration file. The default GamePlatformPlugin API does not know of the configuration file and therefore, has no option to provide that data. The GamePlatformNodes plugin however has an interface you can pull this data from, if you wish to do so programmatically.

##
Achieve

Awards the achievement on the platform service if not awarded already.

**
Platform(s)
**
 |
Steam
 |

API
 |
Cry::GamePlatform::IAchievement::Achieve
 |

Flow Graph Nodes
 |
Set Achieved (input trigger pin on generated node)
 |

Schematyc Nodes
 |
Function::GamePlatform::Service::Statistics::SetAchievementCompleted
 |

##
GetName

Retrieves the name of the achievement.

**
Platform(s)
**
 |
Steam
 |

API
 |
Cry::GamePlatform::IAchievement::GetName
 |

Flow Graph Nodes
 |
Label
 (output pin on generated node)
 |

Schematyc Nodes
 |
Function::GamePlatform::DataTypes::Achievement::Expand
 |

##
GetProgress

Retrieves the current progress value of the achievement.

**
Platform(s)
**
 |
Steam
 |

API
 |
Cry::GamePlatform::IAchievement::
GetProgress
 |

Flow Graph Nodes
 |
Progress

(output pin on generated node)
 |

Schematyc Nodes
 |
Function::GamePlatform::Service::Statistics::GetAchievementProgress
 |

##
IsCompleted

Returns true if the achievement has been awarded to the local user already.

**
Platform(s)
**
 |
Steam
 |

API
 |
Cry::GamePlatform::IAchievement::
IsCompleted
 |

Flow Graph Nodes
 |
Is Achieved

(output pin on generated node)
 |

Schematyc Nodes
 |
Function::GamePlatform::Service::Statistics::GetAchievementProgress
 |

##
Reset

Resets the achievement, if possible, on the platform service.

**
Platform(s)
**
 |
Steam
 |

API
 |
Cry::GamePlatform::IAchievement::Reset
 |

Flow Graph Nodes
 |
Reset
 (input trigger pin on generated node)
 |

Schematyc Nodes
 |
Function::GamePlatform::Service::Statistics::ResetAchievementProgress
 |

##
SetProgress

S
ets the current progress value of the achievement. The achievement is unlocked if th
e progress value is above the maximum specified value in the Achievement configuration file.

**
Platform(s)
**
 |
Steam
 |

API
 |
Cry::GamePlatform::IAchievement::
SetProgress
 |

Flow Graph Nodes
 |
Set Progress

(input trigger pin on generated node)
 |

Schematyc Nodes
 |
Function::GamePlatform::Service::Statistics::SetAchievementProgress
 |

[#achievement-configuration](
Achievement Configuration
)
[#achievement-service-functions](
Achievement Service Functions
)
[#achievement-specific-functions](
Achievement Specific Functions
)
