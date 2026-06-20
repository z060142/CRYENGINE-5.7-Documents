# InstantAction

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/23306559
- Page ID: 23306559
- Breadcrumb: CRYENGINE Game Code > Miscellaneous Game Code > GameRules > Sample GameRules > InstantAction
- Parent: Sample GameRules

## Content

### Overview

InstantAction is a nickname in the Crysis series given to the infamous "DeathMatch" or "Free For All" type of game mode.

It's rules are simple - every player is an enemy, the player with the highest kill count/score at the end of the match is the winner.

### Script - XML

Here you'll find the example InstantAction.xml script that is provided with the SDK. Below it you'll find information on what each of these sections mean.

```
<Mode name='InstantAction'>
<StatsRecording class='StandardStatsRecording' />
<Spawning class='MPRSSpawning' teamGame='0' teamSpawnsType='None' usingLua='0' />
<Scoring class='StandardScoring'>
<Player>
<Event type='PlayerKill' points='200' xp='200' />
</Player>
</Scoring>
<ScoreRewards enabled='1' />
<!-- NO ASSIST scoring in instant action -->
<!-- <AssistScoring class='AssistScoring' maxTimeBetweenAttackAndKillForAssist='7000'  maxAssistScore='99' assistScoreMultiplier='0.5'/> -->
<PlayerStats class='StandardPlayerStats' />
<State class='StandardState'>
<StartStrings startMatch='ui_msg_ia_matchstart' />
</State>
<VictoryConditions class='StandardVictoryConditionsPlayer' killsAsScore='1' />
<PlayerSetup class='StandardSetup' />
<DamageHandling class='MPDamageHandling'>
<Table path='Scripts/GameRules/MPDamageTable.xml' />
</DamageHandling>
<ActorAction class='MPActorAction' />
<Spectator class='MPSpectator' eatsActorActions='1' enableFree='0' enableFollow='0' enableKiller='1' timeFromDeathTillAutoSpectate='5000' />
</Mode>
```

### Script - Lua

```
Script.ReloadScript("scripts/gamerules/GameRulesUtils.lua");

InstantAction= {};

GameRulesSetStandardFuncs(InstantAction);
```
