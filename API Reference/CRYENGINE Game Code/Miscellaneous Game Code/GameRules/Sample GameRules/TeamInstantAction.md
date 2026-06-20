# TeamInstantAction

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/23306560
- Page ID: 23306560
- Breadcrumb: CRYENGINE Game Code > Miscellaneous Game Code > GameRules > Sample GameRules > TeamInstantAction
- Parent: Sample GameRules

## Content

### Overview

TeamInstantAction is a nickname in the Crysis series given to the infamous "Team DeathMatch" type of game mode. It is, as suggested, a Team oriented version of the InstantAction game mode.

It's rules are simple - Two teams fight against each other, the team with the highest kill count/score at the end of the match is the winner.

### Script - XML

Here you'll find the example TeamInstantAction.xml script that is provided with the SDK. Below it you'll find information on what each of these sections mean.

```
<Mode name='TeamInstantAction'>
<Spawning class='MPRSSpawning' teamGame='1' teamSpawnsType='None' usingLua='0' />
<Scoring class='StandardScoring'>
<Player>
<Event type='PlayerKill'              points='200' />
<Event type='PlayerTeamKill'          points='0' />
<Event type='PlayerKillAssist'        points='40' />
<Event type='Tagged_PlayerKillAssist' points='25' />
</Player>
<Team>
<Event type='PlayerKill' points='1' />
</Team>
</Scoring>
<ScoreRewards enabled='1' />
<AssistScoring class='AssistScoring' maxTimeBetweenAttackAndKillForAssist='7000' maxAssistScore='99' assistScoreMultiplier='0.5' />
<PlayerStats class='StandardPlayerStats' />
<StatsRecording class='StandardStatsRecording' />
<Teams class='StandardTwoTeams' />
<State class='StandardState'>
<StartStrings startMatch='ui_msg_tia_matchstart' />
</State>
<VictoryConditions class='StandardVictoryConditionsTeam' />
<PlayerSetup class='StandardSetup' />
<DamageHandling class='MPDamageHandling'>
<Table path='Scripts/GameRules/MPDamageTable.xml' />
</DamageHandling>
<ActorAction class='MPActorAction' />
<Spectator class='MPSpectator' eatsActorActions='1' enableFree='0' enableFollow='1' enableKiller='1' timeFromDeathTillAutoSpectate='5000' />
</Mode>
```

### Script - Lua

```
Script.ReloadScript("scripts/gamerules/GameRulesUtils.lua");

TeamInstantAction = {};

GameRulesSetStandardFuncs(TeamInstantAction);
```
