# Creating a new GameRules

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/23306557
- Page ID: 23306557
- Breadcrumb: CRYENGINE Game Code > Miscellaneous Game Code > GameRules > Creating a new GameRules
- Parent: GameRules

## Content

##
New implementation

CryENGINE already provides several basic GameRules implementations, including
*
Singleplayer
*
 and
*
DeathMatch
*
. It's possible to derive from these GameRules to reuse their core functionality.

To implement the Capture The Flags GameRules, we will derive from the TeamDeathMatch GameRules. We need to write the following lines at the beginning of our GameRules implementation.

```

`
Script.ReloadScript("scripts/gamerules/teamdeathmatch.lua");
CaptureTheFlags = new(TeamDeathMatch);

`

```

##
Score

To update the scores based on the flags which have been captures by all teams, we can create a function to be called at a predetermined time period. This time period is defined by the CaptureTheFlags.TICK_TIME variable.

```

`
function CaptureTheFlags.Server.InGame:OnTick()
    CaptureTheFlags.Server.UpdateScores(self);
end

function CaptureTheFlags.Server:UpdateScores()
    for i,flagId in pairs(self.Server.FlagIds) do
        local teamId = self.game:GetTeam(flagId);

        if (teamId) then
            self:SetTeamScore(teamId, self:GetTeamScore(teamId) + 1);
        end
    end
end

`

```

##
Registering with the GameRules system

During the game startup, every file in the GameRules script directory will be parsed. Adding the following line will allow the GameRules to register itself.

```

`
GameRules.RegisterGameRules("CaptureTheFlags", "GameRules");

`

```

The first parameter must match both the name of the GameRules and also the filename excluding the .lua extension.The second parameter will make use of the standard GameRules C++ class which handle most of the lower level side of the GameRules such as network synchronization and player spawning.

The GameRules can now simply be started by typing
**
sv_gamerules CaptureTheFlags
**
 in the console of the server or in the launcher game.

##
GameRulesModulesManager

CryENGINE uses a 'GameRulesModulesManager' to parse an XML file containing definitions of each of the gamerules at runtime, the XML file is located at
`
Game/Scripts/GameRules/GameModes.xml
`
 and contains the name of each gamemode, its aliases, level location directories, a path to a specific XML file that determines the behaviour of the gamemode and finally, a specific HUD, if required.

An example entry would be:

```

`
<GameMode name='DeathMatch'>
  <Alias name='DM' />
  <Alias name='DeathMatch' />
  <LevelLocation path='Multiplayer/' />
  <Rules path='Scripts/GameRules/DeathMatch.xml' />
  <DefaultHudState name="mp_dm" />
</GameMode>

`

```
