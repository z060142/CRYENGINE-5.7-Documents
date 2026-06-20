# Rich Presence

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/76448635
- Page ID: 76448635
- Breadcrumb: Projects and Plug-ins > GamePlatform Plugin > GamePlatform Features (Discord/Steam) > Rich Presence
- Parent: GamePlatform Features (Discord/Steam)

## Content

##
Overview

The Rich Presence abstraction attempts to unify the functionality of presenting the status of local users to other clients on a platform.

The implementation and corresponding options of Rich Presence vary across each platform in terms of what and how data is shown to other clients. For this reason, currently only Discord has full Rich Presence functionality as it provides the most options. Other platforms will make use of the Status (or the Headline Data) interface to provide basic presence information.

##
Rich Presence Service Functions

##
GetRichPresence

Gets the rich presence data for the local user on the specified platform.

Platforms
 |
Discord
 |

API
 |
Cry::GamePlatform::IService::GetRichPresence
 |

Flow Graph Nodes
 |
GamePlatform:Account:RichPresence
 |

Schematyc Nodes
 |
Function::GamePlatform::Service::Accounts::GetRichPresence
 |

##
SetRichPresence

Sets the rich presence data for the local user on the specified platform.

Platforms
 |
Discord
 |

API
 |
Cry::GamePlatform::IService::SetRichPresence
 |

Flow Graph Nodes
 |
GamePlatform:Account:RichPresence
 |

Schematyc Nodes
 |
Function::GamePlatform::Service::Accounts::SetRichPresence
 |

##
SetStatus

Sets the status string for the local user on the specified platform.

-
The status string is the displayed text that shows what the user is currently doing in a game. For example, playing on a certain map, etc. Each platform implements this differently.

-
To retrieve the status, use
[/docs/static/engines/cryengine-5/categories/23756813/pages/76448635#RichPresence-getrichpresence](
 GetRichPresence
)
and read the "headline" output.

-
On most, if not all platforms, setting the status string for the local user is not instant and make take up to 3 minutes to be visible by other users on the platform.

-
Executing this too often will cause some calls to be ignored. As a rule of thumb, only execute this function at most every 3 minutes as needed. If the text you want displayed doesn't change, there is no need to set it again.
Platforms
 |
Discord, Steam
 |

API
 |
Cry::GamePlatform::IService::SetStatus
 |

Flow Graph Nodes
 |
GamePlatform:Account:SetStatus
 |

Schematyc Nodes
 |
Function::GamePlatform::Service::Accounts::SetStatus
 |

[#rich-presence-service-functions](
Rich Presence Service Functions
)
[#getrichpresence](
GetRichPresence
)
[#setrichpresence](
SetRichPresence
)
[#setstatus](
SetStatus
)
