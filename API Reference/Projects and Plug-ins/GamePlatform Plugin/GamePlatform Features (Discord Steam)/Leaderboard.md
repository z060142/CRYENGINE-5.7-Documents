# Leaderboard

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/76448580
- Page ID: 76448580
- Breadcrumb: Projects and Plug-ins > GamePlatform Plugin > GamePlatform Features (Discord/Steam) > Leaderboard
- Parent: GamePlatform Features (Discord/Steam)

## Content

##
Overview

The Leaderboard abstraction unifies the functionality of leaderboard statistics across different platforms to provide a more consistent experience. This allow retrieving and updating leaderboards, as well as sorting the results.

Some platforms will vary in terms of how to track data on a leaderboard, and will therefore have different options for setting it up. As always, it is recommended to read the documentation associated with each of the platforms you intend to publish your game on.

##
Leaderboard Service Functions

##
GetLeaderboardData

Retrieves leaderboard information as requested.

Listen for the
[/docs/static/engines/cryengine-5/categories/23756813/pages/76448580#Leaderboard-onentry](
OnLeaderboardEntryDownloaded
)
 event after the request.
Platform(s)
 |
Steam
 |

API
 |
Cry::GamePlatform
::ILeaderboards
::GetLeaderboardData
 |

Flow Graph Nodes
 |
GamePlatform:Leaderboard:GetData
 |

Schematyc Nodes
 |
Function::GamePlatform::Leaderboards::Accounts::GetLeaderboardData
 |

##
UpdateLeaderboardScore

Updates leaderboard data for the local user.

Platform(s)
 |
Steam
 |

API
 |
Cry::GamePlatform
::ILeaderboards
::UpdateLeaderboardScore
 |

Flow Graph Nodes
 |
GamePlatform:Leaderboard:UpdateScore
 |

Schematyc Nodes
 |
Function::GamePlatform::
Leaderboards
::Accounts::UpdateLeaderboardScore
 |

##
Leaderboard Service Events

##
OnLeaderboardEntryDownloaded

Fired when a leaderboard entry has been received via a
[/docs/static/engines/cryengine-5/categories/23756813/pages/76448580#Leaderboard-getdata](
 GetLeaderboardData
)
request.

Platform(s)
 |
Steam
 |

API
 |
Cry::GamePlatform
::ILeaderboards::IListener
::OnLeaderboardEntryDownloaded
 |

Flow Graph Nodes
 |
GamePlatform:Listener:Leaderboard:OnLeaderboardEntryDownloaded
 |

Schematyc Nodes
 |
Signal::Receive::[EntityName]::Accounts::PlatformSignalReceiver::Leaderboard::OnLeaderboardEntryDownloaded
 |

[#leaderboard-service-functions](
Leaderboard Service Functions
)
[#getleaderboarddata](
GetLeaderboardData
)
[#updateleaderboardscore](
UpdateLeaderboardScore
)
[#leaderboard-service-events](
Leaderboard Service Events
)
[#onleaderboardentrydownloaded](
OnLeaderboardEntryDownloaded
)
