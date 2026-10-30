# Repo map

Tracked files are indexed below; grouped entries list their members.

## Root

- `.dockerignore` — Docker build exclusions for the relay image
- `.editorconfig` — Editor and formatting rules
- `.gitignore` — Git ignore patterns
- `AGENTS.md` — Agent guidance: build, tests, architecture, rules
- `AI-DECLARATION.md` — Statement on AI use in the project
- `AnoMech.sln` — Visual Studio solution (plugin, relay, tests)
- `LICENSE.md` — License
- `README.md` — Project overview and install notes

## .github/workflows

- `pr-build.yml` — CI build for pull requests
- `release-plugin.yml` — Release pipeline for the Dalamud plugin
- `release-fork.yml` — Fork release: on a v* tag push, builds and publishes latest.zip for the DalamudPlogons repo
- `release-relay.yml` — Release pipeline for the relay server

## AnoMech.Relay.Host/

- `AnoMech.Relay.Host.csproj` — Relay host project file
- `Dockerfile` — Container image for the relay host
- `Program.cs` — Standalone relay executable entry point
- `README.md` — Relay host deployment notes

## AnoMech.Relay/

- `AnoMech.Relay.csproj` — Relay library project file
- `Network/RelayGroup.cs` — Relay group membership model
- `Network/RelayWire.cs` — Relay wire format and message framing
- `Server/RelayAdminModel.cs` — Admin status view model
- `Server/RelayHttp.cs` — HTTP endpoints for the relay server
- `Server/RelayOptions.cs` — Relay server configuration options
- `Server/RelayRooms.cs` — Room lifecycle and membership
- `Server/RelayServer.cs` — Relay server accept and dispatch loop

## AnoMech/ (plugin root)

- `AnoMech.csproj` — Plugin project file
- `AnoMechElementalStrats.json` — Dalamud plugin manifest
- `BannedSymbols.txt` — Banned API symbols list for analyzers
- `Configuration.cs` — Persisted plugin configuration
- `Plugin.cs` — Dalamud plugin entry point; installs Natives and the frame hook
- `RunController.cs` — Starts, stops and ticks a practice run
- `ScenarioSelection.cs` — Chosen scenario, strat, waymark and seed for a run

## AnoMech/Core/

- `DiagnosticLog.cs` — Diagnostic logging helpers
- `LogManager.cs` — Log file management
- `MathUtil.cs` — Math helpers

### Core/EnemyActions/

- `CastTarget.cs` — Target of a boss cast
- `CommonActions.cs` — Shared boss action definitions
- `DamageCheck.cs` — Damage-check resolution
- `DamageKind.cs` — Physical, magic, unique and typeless damage kinds
- `Distribution.cs` — Damage distribution shapes
- `EnemyAction.cs` — Boss action definition record
- `EnemyActionCast.cs` — Runtime cast of an enemy action
- `EnemyActionContext.cs` — Context passed to action effects
- `EnemyActionEffect.cs` — Effect interface for enemy actions
- `EnemyActionHandler.cs` — Runs an enemy action's cast and effects
- `RuinSpec.cs` — Ruin (stack-based damage) spec
- `Severity.cs` — Hit severity levels
- `VulnSpec.cs` — Vulnerability status spec

### Core/Game/

- `ActionTimelineId.cs` — Action timeline id constants
- `ActorControl.cs` — Actor control effects sent to characters
- `CastCancelReason.cs` — Reasons a cast is cancelled
- `CharacterFind.cs` — Locates sim characters by query
- `Coordinates.cs` — Coordinate conversions
- `EnemyList.cs` — Per-client enemy list view
- `EventScheduler.cs` — Timed event queue ticked each frame
- `Game.cs` — Game root: ticks session, scheduler, sim world and scenario
- `InstanceSession.cs` — Instance session lifecycle and fall checks
- `MusicPlayer.cs` — BGM playback control
- `Placement.cs` — Position and rotation record
- `PracticeLoop.cs` — Practice loop restart logic
- `ScdOgg.cs` — SCD audio to OGG extraction
- `ScenarioSession.cs` — Session modes and scenario run state
- `SessionStatus.cs` — Session status enum
- `SettleWait.cs` — Waits for entities to settle before continuing
- `SimEvents.cs` — Sim event records (ActionResolved and others)
- `Towers.cs` — Tower resolution shared by scenarios
- `Waymarks.cs` — Waymark slot enum

#### Core/Game/Ai/

- `AiManager.cs` — Runs the selected scenario AI strat
- `AiMove.cs` — Movement, role and position implementation of AI steps
- `IAiMove.cs`, `IAiPositions.cs`, `IAiRoles.cs`, `IScenarioAi.cs` — AI step interfaces
- `RoleAssignment.cs` — Assigns party roles to characters

#### Core/Game/Geometry/

- `CircleObstacle.cs`, `IObstacle.cs`, `ObstacleField.cs` — Obstacle shapes for pathing

#### Core/Game/Motion/

- `CharacterMotion.cs` — Base motion gates (alive, movement lock, animation)
- `ForcedMove.cs` — Forced movement records (knockback and similar)
- `ModelSync.cs` — Syncs sim position to the game model
- `Navigator.cs` — Navigation interface for moving characters
- `PlayerMotion.cs` — Local player motion
- `RemoteMotion.cs` — Steers remote seats from received poses
- `SimulatedMotion.cs` — Simulated (bot and NPC) motion

#### Core/Game/Party/

- `LimitBreakGauge.cs` — Limit break gauge state
- `PartyCreator.cs` — Creates the party for a run
- `PartyPresets.cs` — Preset party compositions
- `PartyRole.cs` — Party role enum
- `PartyRoster.cs` — Party slot roster records

### Core/Map/

- `DutyInitData.cs` — Duty initialization data record
- `EntranceBarrier.cs` — Entrance barrier record
- `HelperPool.cs` — Helper NPC pool record
- `MapController.cs` — Arena and map state controller
- `MapEffectTower.cs` — Map effect tower object
- `SimArenaBoundary.cs` — Arena boundary sim object
- `SimWaymarks.cs` — Sim waymark object

### Core/Native/Implementations/

- `ActionTimelinePreload.cs` — Preloads action timelines
- `BattleCharaProxy.cs` — Proxy for a battle character
- `BattleCharas.cs` — Battle character collection access
- `Bgm.cs` — BGM access
- `EventObjectProxy.cs` — Proxy for an event object
- `EventObjects.cs` — Event object collection access
- `GameData.cs` — IGameData implementation (Lumina sheets)
- `GameNatives.cs` — Builds the Natives implementations the plugin installs
- `HaterList.cs` — Enmity hater list access
- `InstanceContentDirector.cs` — Instance content director access
- `JobGaugeEdit.cs` — Job gauge editing
- `LayoutFunctions.cs` — Layout function calls
- `LevelSync.cs` — Level sync handling
- `LimitBreakController.cs` — Limit break control
- `LocalPlayerInputHooks.cs` — Hooks on local player input
- `MapEffects.cs` — Map effect spawning
- `PartyHud.cs` — Party HUD access
- `PlayerConditions.cs` — Player condition access
- `RecastTimes.cs` — Action recast times
- `RsfFunctions.cs`, `RsvFunctions.cs` — Game RSF and RSV function calls
- `Waymarks.cs` — Waymark placement in the game
- `ZoneControl.cs`, `ZoneControl.Guard.cs` — Zone control and zone-change guard
- `Interop/` — `ActionEffects.cs`, `CharacterManagerHelper.cs`, `EventObjectHelper.cs`, `GameObjectHelper.cs`, `InstanceContentDirectorHelper.cs`, `LayoutInstanceDiagnostics.cs`, `LayoutQuery.cs`, `OpcodeUpdater.cs`, `PreloadActionTmbTap.cs`, `SimCharacterPointers.cs`, `TimelineDebug.cs` — raw FFXIVClientStructs helpers for game memory
- `Pointers/` — `EventObjectManagerPointers.cs`, `GameMainPointers.cs`, `ModelContainerPointers.cs`, `PacketDispatcherPointers.cs`, `ResolvedStringPointers.cs` — game memory signature and pointer resolution

### Core/Native/Interfaces/

- `IActionTimelinePreload.cs`, `IBattleCharaProxy.cs`, `IBattleCharas.cs`, `IBgm.cs`, `IEventObjectProxy.cs`, `IEventObjects.cs`, `IGameData.cs`, `IHaterList.cs`, `IInstanceContentDirector.cs`, `ILayoutFunctions.cs`, `ILimitBreakController.cs`, `ILocalPlayerInput.cs`, `IMapEffects.cs`, `IPartyHud.cs`, `IPlayerConditions.cs`, `IRsfFunctions.cs`, `IRsvFunctions.cs`, `IUserActions.cs`, `IWaymarks.cs`, `IZoneControl.cs` — game boundary interfaces
- `Natives.cs` — Static locator for the game boundary
- `*Row.cs` (`ActionRow`, `BNpcBaseRow`, `ClassJobRow`, `ContentFinderConditionRow`, `KnockbackRow`, `ModelCharaRow`, `ModelSkeletonRow`, `StatusRow`, `TerritoryTypeRow`) — Lumina sheet row records
- `ActionEffectData.cs`, `ActorCastData.cs`, `ActorMoveFlags.cs`, `CastType.cs`, `PlayerAction.cs`, `Sign.cs`, `StatusSlot.cs` — game data value types

### Core/SimObjects/

- `DebugBotControl.cs` — Debug bot control
- `IPositioned.cs`, `ISimObject.cs`, `ISimPartyMember.cs` — Sim object interfaces and rules
- `SimBgm.cs` — BGM sim object
- `SimCast.cs` — Sim cast with timing
- `SimCharacter.cs` — Base character sim object
- `SimChildren.cs` — Child object collection
- `SimEnemy.cs` — Boss enemy sim object and spawn visibility
- `SimEventObject.cs` — Event object sim object and spawn config
- `SimHelperPool.cs` — Helper NPC pool sim object
- `SimNetworkPuppet.cs` — Remote player puppet
- `SimNpc.cs` — NPC sim object
- `SimOnlyStatus.cs` — Statuses that exist only in the sim
- `SimParty.cs` — Party sim object
- `SimPartyNpc.cs` — Party NPC sim object
- `SimPlayer.cs` — Local player sim object
- `SimStatus.cs` — Status tracking
- `SimTether.cs` — Tether sim object
- `SimTower.cs` — Tower sim object
- `SimWorld.cs` — Sim root: owns all sim objects and spawns
- `TetherEnd.cs` — Tether end interface

### Core/UserActions/

- `ActionEffect.cs`, `ActionEffectHandler.cs`, `ActionPredicate.cs`, `ActionTargets.cs` — Resolution of the player's own action effects, predicates and targets
- `AutoAttackHandler.cs`, `CastInterruptHandler.cs`, `CastTimeHandler.cs`, `IUserActionHandler.cs`, `JobActionHandler.cs`, `LimitBreakHandler.cs`, `ResetHandler.cs`, `SprintHandler.cs`, `TimedGaugeHandler.cs` — Per-action-type handlers
- `JobActions.cs`, `JobId.cs`, `PlayerCombo.cs`, `Mitigation.cs`, `UserActions.cs` — Job action tables, combos, mitigation and entry point
- `Jobs/` — `AstrologianStateHandler`, `BlackMageStateHandler`, `DancerStateHandler`, `MonkStateHandler`, `NinjaStateHandler`, `PictomancerStateHandler`, `SamuraiStateHandler`, `SummonerStateHandler`, `ViperStateHandler` — per-job gauge and state logic
- `docs/` — per-job coverage notes (AST, BLM, BRD, DNC, DRG, DRK, GNB, MCH, MNK, NIN, PCT, PLD, RDM, RPR, SAM, SCH, SGE, SMN, VPR, WAR, WHM) and `README.md` coverage overview

## AnoMech/Multiplayer/

- `DefaultRelay.cs` — Default relay address
- `EmbeddedRelay.cs` — Relay server embedded in the plugin
- `GamePackets.cs` — Game packet message types
- `IMultiplayerReplayable.cs` — Scenario interface for multiplayer replay
- `IRelayConnection.cs` — Relay connection interface
- `LobbyPartyProvider.cs` — Party provider for lobby members
- `MultiplayerManager.cs` — Multiplayer session root
- `MultiplayerManager.Acted.cs` — Handles acted-on-by-peer events
- `MultiplayerManager.DebugReplay.cs` — Debug replay of recorded packets
- `MultiplayerManager.Dispatch.cs` — Message dispatch
- `MultiplayerManager.HostSnapshot.cs` — Host state snapshot
- `MultiplayerManager.PeerSnapshot.cs` — Peer state snapshot
- `MultiplayerManager.Stream.cs` — Session stream handling
- `MultiplayerManager.Tick.cs` — Per-frame multiplayer tick
- `MultiplayerSession.cs` — Session state
- `NetGuard.cs` — Network input guard
- `PacketRecorder.cs` — Records packets for debugging
- `PacketReplay.cs` — Replays recorded packets
- `PacketRules.cs` — Delivery rules per packet type
- `PeerNatives.cs` — Natives used on peer clients
- `PluginBuildInfo.cs` — Build info for version checks
- `Protocol.cs` — Multiplayer message protocol records
- `RelayClient.cs` — Client connection to the relay
- `RelayGroups.cs` — Relay group info
- `RelayPings.cs` — Relay ping measurement
- `RelayStats.cs` — Relay usage stats
- `SessionStream.cs` — Ordered session message stream
- `SimAssets.cs` — Asset kinds shared with peers

## AnoMech/Windows/

- `ActorControlDebug.cs` — Actor control debug window
- `ConfigWindow.cs` — Settings window
- `DamageDebugWindow.cs` — Damage debug window
- `DebugMenu.cs` — Debug menu
- `FailureBanner.cs` — Failure banner shown on a scenario fail
- `LockReplayDebug.cs` — Replay lock debug window
- `MainWindow.cs` — Main plugin window
- `MultiplayerUi.cs` — Multiplayer UI
- `PacketCaptureDebug.cs` — Packet capture debug window
- `PartyPanelWindow.cs` — Party panel window
- `RelayServerStatus.cs` — Relay server status display
- `RelayUsageReadout.cs` — Relay usage readout
- `ScenarioPanelWindow.cs` — Scenario selection panel

## AnoMech/Scenarios/

### Scenario framework

- `IPhase.cs` — Phase interface (weather, BGM)
- `IScenario.cs` — Scenario interface
- `IZone.cs` — Zone interface (territory, origin, waymarks)
- `PerRoleSetting.cs` — Per-role setting interface
- `Rng.cs` — Seeded random source
- `RoleList.cs` — Role list builder
- `ScenarioCatalog.cs` — Builds the scenario menu tree
- `ScenarioSettingsSummary.cs` — Settings summary text
- `ScenarioSettingsSync.cs` — Settings sync between UI and scenario
- `ScenarioStates.cs` — Scenario state records (e.g. Direction)
- `SettingsConflicts.cs` — Detects conflicting settings
- `SettingsGrid.cs` — Settings grid UI helper

### Scenarios/Top/ (shared)

- `HelloWorld.cs` — HelloWorld mechanic
- `HelloWorldFailures.cs` — HelloWorld failure resolution
- `TopActions.cs` — Top boss action definitions
- `TopConstants.cs` — Top IDs and constants
- `TopRealPackets.cs` — Captured real packets for Top
- `TopReplayData.cs` — Replay data for Top
- `TopZone.cs` — Top zone definition

### Scenarios/Top/ phases

- `P2PartySynergy/` — `TopP2PartySynergyAi.cs`, `TopP2PartySynergyLpduAi.cs` (LPDU variant), `TopP2PartySynergyScenario.cs`, `TopP2PartySynergySettingsWindow.cs`, `TopP2PartySynergyState.cs`, `TopP2PartySynergyStateOverrides.cs` — P2 party synergy
- `P5Delta/` — `TopP5DeltaAi.cs`, `TopP5DeltaTuuflessAi.cs` (Tuufless strat), `TopP5DeltaScenario.cs`, `TopP5DeltaSettingsWindow.cs`, `TopP5DeltaState.cs`, `TopP5DeltaStateOverrides.cs` — P5 Delta
- `P5Omega/` — `TopP5OmegaAi.cs`, `TopP5OmegaScenario.cs`, `TopP5OmegaSettingsWindow.cs`, `TopP5OmegaState.cs`, `TopP5OmegaStateOverrides.cs` — P5 Omega
- `P5Sigma/` — `TopP5SigmaAi.cs`, `TopP5SigmaTuuflessAi.cs` (Tuufless strat), `TopP5SigmaScenario.cs`, `TopP5SigmaSettingsWindow.cs`, `TopP5SigmaState.cs`, `TopP5SigmaStateOverrides.cs` — P5 Sigma
- `P6WaveCannon2/` — `TopP6WaveCannon2Ai.cs`, `...Scenario.cs`, `...SettingsWindow.cs`, `...State.cs`, `...StateOverrides.cs` — P6 Wave Cannon 2

### Scenarios/Fru/ (shared)

- `FruActions.cs`, `FruConstants.cs`, `FruReplayData.cs`, `FruZone.cs` — Fru actions, IDs, replay data and zone
- `FruHolyPuddles.cs`, `Lightsteeped.cs` — Shared Fru mechanics (holy puddles, Lightsteeped)

### Scenarios/Fru/ phases

- `P2DiamondDust/` — `FruP2DiamondDustAi.cs`, `...Scenario.cs`, `...SettingsWindow.cs`, `...State.cs`, `...StateOverrides.cs` — P2 Diamond Dust
- `P2LightRampant/` — same five-file layout — P2 Light Rampant
- `P3Apocalypse/` — same five-file layout — P3 Apocalypse
- `P3UltimateRelativity/` — same five-file layout — P3 Ultimate Relativity
- `P4CrystallizeTime/` — same layout plus `FruP4CrystallizeTimeRoutes.cs` (movement routes) — P4 Crystallize Time
- `P4DarklitDragonsong/` — same five-file layout — P4 Darklit Dragonsong
- `P5FulgentBlade/` — same five-file layout — P5 Fulgent Blade
- `P5ParadiseRegained/` — same five-file layout — P5 Paradise Regained

### Scenarios/Ucob/ (shared)

- `UcobActions.cs`, `UcobConstants.cs`, `UcobReplayData.cs`, `UcobZone.cs` — Ucob actions, IDs, replay data and zone
- `P5Exaflares/` — `UcobP5ExaflaresAi.cs`, `...Scenario.cs`, `...SettingsWindow.cs`, `...State.cs`, `...StateOverrides.cs` — P5 Exaflares

### Scenarios/Umad/ (shared)

- `UmadActions.cs`, `UmadConstants.cs`, `UmadReplayData.cs`, `UmadZone.cs` — Umad actions, IDs, replay data and zone
- `UmadP5ForsakenNull.cs` — Forsaken Null scenario

### Scenarios/Umad/ phases

- `P1TeleTrouncing/` — five-file layout — P1 Tele Trouncing
- `P2Forsaken/` — `UmadP2ForsakenScenario.cs`, `...SettingsWindow.cs`, `...State.cs`, `...StateOverrides.cs`; `Ai/` holds strats (`KroxyRinonAi`, `LpduBuddiesAi`, `P3ZBuddyMeowAi`, `SouthFlexAi`, `YanAi`, `ZP6SouthAdjustAi`) and their helpers (`LpduBuddiesAiHelper`, `P3ZBuddyMeowAiHelper`, `RinonAiHelper`, `YanAiHelper`, `ZP6SouthAdjustAiHelper`) — P2 Forsaken
- `P3BlackHole/` — five-file layout plus `UmadP3BlackHoleScenarioObjects.cs` — P3 Black Hole
- `P3LimitCut/` — five-file layout — P3 Limit Cut
- `P4KefkaSays/` — five-file layout — P4 Kefka Says
- `P5Celestriad/` — five-file layout — P5 Celestriad
- `P5Exaflares/` — five-file layout — P5 Exaflares
- `P5Flood/` — five-file layout — P5 Flood

### Scenarios/Uwu/ (shared)

- `SuperCyclone.cs` — Super Cyclone mechanic
- `UwuActions.cs`, `UwuConstants.cs`, `UwuReplayData.cs`, `UwuUtils.cs`, `UwuZone.cs` — Uwu actions, IDs, replay data, helpers and zone

### Scenarios/Uwu/ phases

- `UltimatePredation/` — `UltimatePredationAi.cs`, `...Scenario.cs`, `...ScenarioObjects.cs`, `...SettingsWindow.cs`, `...State.cs`, `...StateOverrides.cs` — Ultimate Predation
- `UltimateSuppression/` — five-file layout — Ultimate Suppression

## tests/AnoMech.Relay.Tests/

- `AnoMech.Relay.Tests.csproj` — Test project file
- `Network/RelayGroupTests.cs`, `Network/RelayWireTests.cs` — Relay group and wire format tests
- `Server/RelayAdminModelTests.cs`, `Server/RelayOptionsTests.cs`, `Server/RelayRoomsTests.cs`, `Server/RelayServerTests.cs` — Relay server tests
- `Support/QuietLog.cs`, `Support/StubSocket.cs`, `Support/TestWire.cs` — Test helpers

## tests/AnoMech.Tests/

- `AnoMech.Tests.csproj`, `test.runsettings` — Test project and run settings
- `ConfigurationTests.cs` — Configuration tests
- `Core/Game/ScenarioSessionTests.cs` — Scenario session tests
- `Core/Native/Fakes/` — Fakes for game-boundary interfaces (`FakeGame`, `FakeBattleChara`, `FakeBattleCharas`, `FakeCharacter`, `FakeEventObject`, `FakeEventObjects`, `FakeHaterList`, `FakeInstanceContentDirector`, `FakeLayoutFunctions`, `FakeLimitBreakController`, `FakeLocalPlayerInput`, `FakeMapEffects`, `FakePartyHud`, `FakePlayerConditions`, `FakeRsfFunctions`, `FakeRsvFunctions`, `FakeUserActions`, `FakeWaymarks`, `FakeZoneControl`, `FakeBgm`, `FakeActionTimelinePreload`), `DataminingGameData.cs` (IGameData from datamining CSVs), `FakeBattleCharasTests.cs`
- `Core/UserActions/MitigationTests.cs` — Mitigation tests
- `Multiplayer/` — DebugBotReplay, FallingBehind, LinkInterruption, PeerParity, PlayerAction, Protocol, RelayClient, RelayGroups, RelayLoopback, ResultMark, SessionStream tests
- `Scenarios/ScenarioCatalogTests.cs` — Every catalog strat clears its fight with no deaths
- `Scenarios/RngTests.cs` — Seeded RNG tests
- `Scenarios/ScenarioTimelineExportTests.cs` — Timeline export tests
- `Scenarios/<Phase>/` — per-scenario tests for Fru (8 phases), Top (P2 Party Synergy LPDU and scenario, P5 Delta, P5 Omega, P5 Sigma, P6 Wave Cannon 2), Ucob P5 Exaflares, Umad (9 phases), Uwu (Ultimate Predation, Ultimate Suppression)
- `Support/` — Test support: `BadConnections`, `ClientParity`, `ConnectionProfile`, `DalamudServices`, `FakeFramework`, `LinkStalls`, `MultiplayerRun`, `NativesState`, `NegativeRun`, `QuietLog`, `ScenarioArtifacts`, `ScenarioRun`, `SimTimeline`, `TestClient`, `TestRelay`, `TestWire`, `TraceLog`, `WorldSnapshot`
- `tests/Directory.Build.props` — Shared test build properties

## tools/

- `filter.py` — Packet-level drop filter for ACT/IINACT network logs
- `parser.py` — Parses ACT/IINACT network logs and prints pulls for a territory
- `replay_export_duty_init.py` — Extracts duty init packets from a realm recording

## Additional tracked files
- `AnoMech/Core/Native/Interfaces/ActionRow.cs` — Game data row or native boundary declaration (ActionRow)
- `AnoMech/Core/Native/Interfaces/BNpcBaseRow.cs` — Game data row or native boundary declaration (BNpcBaseRow)
- `AnoMech/Core/Native/Interfaces/ClassJobRow.cs` — Game data row or native boundary declaration (ClassJobRow)
- `AnoMech/Core/Native/Interfaces/ContentFinderConditionRow.cs` — Game data row or native boundary declaration (ContentFinderConditionRow)
- `AnoMech/Core/Native/Interfaces/KnockbackRow.cs` — Game data row or native boundary declaration (KnockbackRow)
- `AnoMech/Core/Native/Interfaces/ModelCharaRow.cs` — Game data row or native boundary declaration (ModelCharaRow)
- `AnoMech/Core/Native/Interfaces/ModelSkeletonRow.cs` — Game data row or native boundary declaration (ModelSkeletonRow)
- `AnoMech/Core/Native/Interfaces/StatusRow.cs` — Game data row or native boundary declaration (StatusRow)
- `AnoMech/Core/Native/Interfaces/TerritoryTypeRow.cs` — Game data row or native boundary declaration (TerritoryTypeRow)
- `AnoMech/Core/UserActions/Jobs/AstrologianStateHandler.cs` — Per-job action and gauge state handler (AstrologianStateHandler)
- `AnoMech/Core/UserActions/Jobs/BlackMageStateHandler.cs` — Per-job action and gauge state handler (BlackMageStateHandler)
- `AnoMech/Core/UserActions/Jobs/DancerStateHandler.cs` — Per-job action and gauge state handler (DancerStateHandler)
- `AnoMech/Core/UserActions/Jobs/MonkStateHandler.cs` — Per-job action and gauge state handler (MonkStateHandler)
- `AnoMech/Core/UserActions/Jobs/NinjaStateHandler.cs` — Per-job action and gauge state handler (NinjaStateHandler)
- `AnoMech/Core/UserActions/Jobs/PictomancerStateHandler.cs` — Per-job action and gauge state handler (PictomancerStateHandler)
- `AnoMech/Core/UserActions/Jobs/SamuraiStateHandler.cs` — Per-job action and gauge state handler (SamuraiStateHandler)
- `AnoMech/Core/UserActions/Jobs/SummonerStateHandler.cs` — Per-job action and gauge state handler (SummonerStateHandler)
- `AnoMech/Core/UserActions/Jobs/ViperStateHandler.cs` — Per-job action and gauge state handler (ViperStateHandler)
- `AnoMech/Core/UserActions/docs/AST.md` — Action coverage notes for AST
- `AnoMech/Core/UserActions/docs/BLM.md` — Action coverage notes for BLM
- `AnoMech/Core/UserActions/docs/BRD.md` — Action coverage notes for BRD
- `AnoMech/Core/UserActions/docs/DNC.md` — Action coverage notes for DNC
- `AnoMech/Core/UserActions/docs/DRG.md` — Action coverage notes for DRG
- `AnoMech/Core/UserActions/docs/DRK.md` — Action coverage notes for DRK
- `AnoMech/Core/UserActions/docs/GNB.md` — Action coverage notes for GNB
- `AnoMech/Core/UserActions/docs/MCH.md` — Action coverage notes for MCH
- `AnoMech/Core/UserActions/docs/MNK.md` — Action coverage notes for MNK
- `AnoMech/Core/UserActions/docs/NIN.md` — Action coverage notes for NIN
- `AnoMech/Core/UserActions/docs/PCT.md` — Action coverage notes for PCT
- `AnoMech/Core/UserActions/docs/PLD.md` — Action coverage notes for PLD
- `AnoMech/Core/UserActions/docs/RDM.md` — Action coverage notes for RDM
- `AnoMech/Core/UserActions/docs/RPR.md` — Action coverage notes for RPR
- `AnoMech/Core/UserActions/docs/SAM.md` — Action coverage notes for SAM
- `AnoMech/Core/UserActions/docs/SCH.md` — Action coverage notes for SCH
- `AnoMech/Core/UserActions/docs/SGE.md` — Action coverage notes for SGE
- `AnoMech/Core/UserActions/docs/SMN.md` — Action coverage notes for SMN
- `AnoMech/Core/UserActions/docs/VPR.md` — Action coverage notes for VPR
- `AnoMech/Core/UserActions/docs/WAR.md` — Action coverage notes for WAR
- `AnoMech/Core/UserActions/docs/WHM.md` — Action coverage notes for WHM
- `AnoMech/Scenarios/Fru/P2DiamondDust/FruP2DiamondDustScenario.cs` — Fight timeline and entities for P2DiamondDust
- `AnoMech/Scenarios/Fru/P2DiamondDust/FruP2DiamondDustSettingsWindow.cs` — Settings UI for P2DiamondDust
- `AnoMech/Scenarios/Fru/P2DiamondDust/FruP2DiamondDustState.cs` — Per-run mechanic state for P2DiamondDust
- `AnoMech/Scenarios/Fru/P2DiamondDust/FruP2DiamondDustStateOverrides.cs` — User-forced rolls for P2DiamondDust
- `AnoMech/Scenarios/Fru/P2LightRampant/FruP2LightRampantAi.cs` — AI strat decisions for P2LightRampant
- `AnoMech/Scenarios/Fru/P2LightRampant/FruP2LightRampantScenario.cs` — Fight timeline and entities for P2LightRampant
- `AnoMech/Scenarios/Fru/P2LightRampant/FruP2LightRampantSettingsWindow.cs` — Settings UI for P2LightRampant
- `AnoMech/Scenarios/Fru/P2LightRampant/FruP2LightRampantState.cs` — Per-run mechanic state for P2LightRampant
- `AnoMech/Scenarios/Fru/P2LightRampant/FruP2LightRampantStateOverrides.cs` — User-forced rolls for P2LightRampant
- `AnoMech/Scenarios/Fru/P3Apocalypse/FruP3ApocalypseAi.cs` — AI strat decisions for P3Apocalypse
- `AnoMech/Scenarios/Fru/P3Apocalypse/FruP3ApocalypseScenario.cs` — Fight timeline and entities for P3Apocalypse
- `AnoMech/Scenarios/Fru/P3Apocalypse/FruP3ApocalypseSettingsWindow.cs` — Settings UI for P3Apocalypse
- `AnoMech/Scenarios/Fru/P3Apocalypse/FruP3ApocalypseState.cs` — Per-run mechanic state for P3Apocalypse
- `AnoMech/Scenarios/Fru/P3Apocalypse/FruP3ApocalypseStateOverrides.cs` — User-forced rolls for P3Apocalypse
- `AnoMech/Scenarios/Fru/P3UltimateRelativity/FruP3UltimateRelativityAi.cs` — AI strat decisions for P3UltimateRelativity
- `AnoMech/Scenarios/Fru/P3UltimateRelativity/FruP3UltimateRelativityScenario.cs` — Fight timeline and entities for P3UltimateRelativity
- `AnoMech/Scenarios/Fru/P3UltimateRelativity/FruP3UltimateRelativitySettingsWindow.cs` — Settings UI for P3UltimateRelativity
- `AnoMech/Scenarios/Fru/P3UltimateRelativity/FruP3UltimateRelativityState.cs` — Per-run mechanic state for P3UltimateRelativity
- `AnoMech/Scenarios/Fru/P3UltimateRelativity/FruP3UltimateRelativityStateOverrides.cs` — User-forced rolls for P3UltimateRelativity
- `AnoMech/Scenarios/Fru/P4CrystallizeTime/FruP4CrystallizeTimeAi.cs` — AI strat decisions for P4CrystallizeTime
- `AnoMech/Scenarios/Fru/P4CrystallizeTime/FruP4CrystallizeTimeScenario.cs` — Fight timeline and entities for P4CrystallizeTime
- `AnoMech/Scenarios/Fru/P4CrystallizeTime/FruP4CrystallizeTimeSettingsWindow.cs` — Settings UI for P4CrystallizeTime
- `AnoMech/Scenarios/Fru/P4CrystallizeTime/FruP4CrystallizeTimeState.cs` — Per-run mechanic state for P4CrystallizeTime
- `AnoMech/Scenarios/Fru/P4CrystallizeTime/FruP4CrystallizeTimeStateOverrides.cs` — User-forced rolls for P4CrystallizeTime
- `AnoMech/Scenarios/Fru/P4DarklitDragonsong/FruP4DarklitDragonsongAi.cs` — AI strat decisions for P4DarklitDragonsong
- `AnoMech/Scenarios/Fru/P4DarklitDragonsong/FruP4DarklitDragonsongScenario.cs` — Fight timeline and entities for P4DarklitDragonsong
- `AnoMech/Scenarios/Fru/P4DarklitDragonsong/FruP4DarklitDragonsongSettingsWindow.cs` — Settings UI for P4DarklitDragonsong
- `AnoMech/Scenarios/Fru/P4DarklitDragonsong/FruP4DarklitDragonsongState.cs` — Per-run mechanic state for P4DarklitDragonsong
- `AnoMech/Scenarios/Fru/P4DarklitDragonsong/FruP4DarklitDragonsongStateOverrides.cs` — User-forced rolls for P4DarklitDragonsong
- `AnoMech/Scenarios/Fru/P5FulgentBlade/FruP5FulgentBladeAi.cs` — AI strat decisions for P5FulgentBlade
- `AnoMech/Scenarios/Fru/P5FulgentBlade/FruP5FulgentBladeScenario.cs` — Fight timeline and entities for P5FulgentBlade
- `AnoMech/Scenarios/Fru/P5FulgentBlade/FruP5FulgentBladeSettingsWindow.cs` — Settings UI for P5FulgentBlade
- `AnoMech/Scenarios/Fru/P5FulgentBlade/FruP5FulgentBladeState.cs` — Per-run mechanic state for P5FulgentBlade
- `AnoMech/Scenarios/Fru/P5FulgentBlade/FruP5FulgentBladeStateOverrides.cs` — User-forced rolls for P5FulgentBlade
- `AnoMech/Scenarios/Fru/P5ParadiseRegained/FruP5ParadiseRegainedAi.cs` — AI strat decisions for P5ParadiseRegained
- `AnoMech/Scenarios/Fru/P5ParadiseRegained/FruP5ParadiseRegainedScenario.cs` — Fight timeline and entities for P5ParadiseRegained
- `AnoMech/Scenarios/Fru/P5ParadiseRegained/FruP5ParadiseRegainedSettingsWindow.cs` — Settings UI for P5ParadiseRegained
- `AnoMech/Scenarios/Fru/P5ParadiseRegained/FruP5ParadiseRegainedState.cs` — Per-run mechanic state for P5ParadiseRegained
- `AnoMech/Scenarios/Fru/P5ParadiseRegained/FruP5ParadiseRegainedStateOverrides.cs` — User-forced rolls for P5ParadiseRegained
- `AnoMech/Scenarios/Top/P6WaveCannon2/TopP6WaveCannon2Scenario.cs` — Fight timeline and entities for P6WaveCannon2
- `AnoMech/Scenarios/Top/P6WaveCannon2/TopP6WaveCannon2SettingsWindow.cs` — Settings UI for P6WaveCannon2
- `AnoMech/Scenarios/Top/P6WaveCannon2/TopP6WaveCannon2State.cs` — Per-run mechanic state for P6WaveCannon2
- `AnoMech/Scenarios/Top/P6WaveCannon2/TopP6WaveCannon2StateOverrides.cs` — User-forced rolls for P6WaveCannon2
- `AnoMech/Scenarios/Ucob/P5Exaflares/UcobP5ExaflaresScenario.cs` — Fight timeline and entities for P5Exaflares
- `AnoMech/Scenarios/Ucob/P5Exaflares/UcobP5ExaflaresSettingsWindow.cs` — Settings UI for P5Exaflares
- `AnoMech/Scenarios/Ucob/P5Exaflares/UcobP5ExaflaresState.cs` — Per-run mechanic state for P5Exaflares
- `AnoMech/Scenarios/Ucob/P5Exaflares/UcobP5ExaflaresStateOverrides.cs` — User-forced rolls for P5Exaflares
- `AnoMech/Scenarios/Umad/P1TeleTrouncing/UmadP1TeleTrouncingAi.cs` — AI strat decisions for P1TeleTrouncing
- `AnoMech/Scenarios/Umad/P1TeleTrouncing/UmadP1TeleTrouncingScenario.cs` — Fight timeline and entities for P1TeleTrouncing
- `AnoMech/Scenarios/Umad/P1TeleTrouncing/UmadP1TeleTrouncingSettingsWindow.cs` — Settings UI for P1TeleTrouncing
- `AnoMech/Scenarios/Umad/P1TeleTrouncing/UmadP1TeleTrouncingState.cs` — Per-run mechanic state for P1TeleTrouncing
- `AnoMech/Scenarios/Umad/P1TeleTrouncing/UmadP1TeleTrouncingStateOverrides.cs` — User-forced rolls for P1TeleTrouncing
- `AnoMech/Scenarios/Umad/P2Forsaken/Ai/UmadP2ForsakenKroxyRinonAi.cs` — AI strat decisions for Ai
- `AnoMech/Scenarios/Umad/P2Forsaken/Ai/UmadP2ForsakenLpduBuddiesAi.cs` — AI strat decisions for Ai
- `AnoMech/Scenarios/Umad/P2Forsaken/Ai/UmadP2ForsakenLpduBuddiesAiHelper.cs` — Shared mechanic or data helper for Ai
- `AnoMech/Scenarios/Umad/P2Forsaken/Ai/UmadP2ForsakenP3ZBuddyMeowAi.cs` — AI strat decisions for Ai
- `AnoMech/Scenarios/Umad/P2Forsaken/Ai/UmadP2ForsakenP3ZBuddyMeowAiHelper.cs` — Shared mechanic or data helper for Ai
- `AnoMech/Scenarios/Umad/P2Forsaken/Ai/UmadP2ForsakenRinonAiHelper.cs` — Shared mechanic or data helper for Ai
- `AnoMech/Scenarios/Umad/P2Forsaken/Ai/UmadP2ForsakenSouthFlexAi.cs` — AI strat decisions for Ai
- `AnoMech/Scenarios/Umad/P2Forsaken/Ai/UmadP2ForsakenYanAi.cs` — AI strat decisions for Ai
- `AnoMech/Scenarios/Umad/P2Forsaken/Ai/UmadP2ForsakenYanAiHelper.cs` — Shared mechanic or data helper for Ai
- `AnoMech/Scenarios/Umad/P2Forsaken/Ai/UmadP2ForsakenZP6SouthAdjustAi.cs` — AI strat decisions for Ai
- `AnoMech/Scenarios/Umad/P2Forsaken/Ai/UmadP2ForsakenZP6SouthAdjustAiHelper.cs` — Shared mechanic or data helper for Ai
- `AnoMech/Scenarios/Umad/P2Forsaken/UmadP2ForsakenSettingsWindow.cs` — Settings UI for P2Forsaken
- `AnoMech/Scenarios/Umad/P2Forsaken/UmadP2ForsakenState.cs` — Per-run mechanic state for P2Forsaken
- `AnoMech/Scenarios/Umad/P2Forsaken/UmadP2ForsakenStateOverrides.cs` — User-forced rolls for P2Forsaken
- `AnoMech/Scenarios/Umad/P3BlackHole/UmadP3BlackHoleAi.cs` — AI strat decisions for P3BlackHole
- `AnoMech/Scenarios/Umad/P3BlackHole/UmadP3BlackHoleScenario.cs` — Fight timeline and entities for P3BlackHole
- `AnoMech/Scenarios/Umad/P3BlackHole/UmadP3BlackHoleSettingsWindow.cs` — Settings UI for P3BlackHole
- `AnoMech/Scenarios/Umad/P3BlackHole/UmadP3BlackHoleState.cs` — Per-run mechanic state for P3BlackHole
- `AnoMech/Scenarios/Umad/P3BlackHole/UmadP3BlackHoleStateOverrides.cs` — User-forced rolls for P3BlackHole
- `AnoMech/Scenarios/Umad/P3LimitCut/UmadP3LimitCutAi.cs` — AI strat decisions for P3LimitCut
- `AnoMech/Scenarios/Umad/P3LimitCut/UmadP3LimitCutScenario.cs` — Fight timeline and entities for P3LimitCut
- `AnoMech/Scenarios/Umad/P3LimitCut/UmadP3LimitCutSettingsWindow.cs` — Settings UI for P3LimitCut
- `AnoMech/Scenarios/Umad/P3LimitCut/UmadP3LimitCutState.cs` — Per-run mechanic state for P3LimitCut
- `AnoMech/Scenarios/Umad/P3LimitCut/UmadP3LimitCutStateOverrides.cs` — User-forced rolls for P3LimitCut
- `AnoMech/Scenarios/Umad/P4KefkaSays/UmadP4KefkaSaysAi.cs` — AI strat decisions for P4KefkaSays
- `AnoMech/Scenarios/Umad/P4KefkaSays/UmadP4KefkaSaysScenario.cs` — Fight timeline and entities for P4KefkaSays
- `AnoMech/Scenarios/Umad/P4KefkaSays/UmadP4KefkaSaysSettingsWindow.cs` — Settings UI for P4KefkaSays
- `AnoMech/Scenarios/Umad/P4KefkaSays/UmadP4KefkaSaysState.cs` — Per-run mechanic state for P4KefkaSays
- `AnoMech/Scenarios/Umad/P4KefkaSays/UmadP4KefkaSaysStateOverrides.cs` — User-forced rolls for P4KefkaSays
- `AnoMech/Scenarios/Umad/P5Celestriad/UmadP5CelestriadAi.cs` — AI strat decisions for P5Celestriad
- `AnoMech/Scenarios/Umad/P5Celestriad/UmadP5CelestriadScenario.cs` — Fight timeline and entities for P5Celestriad
- `AnoMech/Scenarios/Umad/P5Celestriad/UmadP5CelestriadSettingsWindow.cs` — Settings UI for P5Celestriad
- `AnoMech/Scenarios/Umad/P5Celestriad/UmadP5CelestriadState.cs` — Per-run mechanic state for P5Celestriad
- `AnoMech/Scenarios/Umad/P5Celestriad/UmadP5CelestriadStateOverrides.cs` — User-forced rolls for P5Celestriad
- `AnoMech/Scenarios/Umad/P5Exaflares/UmadP5ExaflaresAi.cs` — AI strat decisions for P5Exaflares
- `AnoMech/Scenarios/Umad/P5Exaflares/UmadP5ExaflaresScenario.cs` — Fight timeline and entities for P5Exaflares
- `AnoMech/Scenarios/Umad/P5Exaflares/UmadP5ExaflaresSettingsWindow.cs` — Settings UI for P5Exaflares
- `AnoMech/Scenarios/Umad/P5Exaflares/UmadP5ExaflaresState.cs` — Per-run mechanic state for P5Exaflares
- `AnoMech/Scenarios/Umad/P5Exaflares/UmadP5ExaflaresStateOverrides.cs` — User-forced rolls for P5Exaflares
- `AnoMech/Scenarios/Umad/P5Flood/UmadP5FloodAi.cs` — AI strat decisions for P5Flood
- `AnoMech/Scenarios/Umad/P5Flood/UmadP5FloodScenario.cs` — Fight timeline and entities for P5Flood
- `AnoMech/Scenarios/Umad/P5Flood/UmadP5FloodSettingsWindow.cs` — Settings UI for P5Flood
- `AnoMech/Scenarios/Umad/P5Flood/UmadP5FloodState.cs` — Per-run mechanic state for P5Flood
- `AnoMech/Scenarios/Umad/P5Flood/UmadP5FloodStateOverrides.cs` — User-forced rolls for P5Flood
- `AnoMech/Scenarios/Uwu/UltimatePredation/UltimatePredationScenario.cs` — Fight timeline and entities for UltimatePredation
- `AnoMech/Scenarios/Uwu/UltimatePredation/UltimatePredationScenarioObjects.cs` — Shared mechanic or data helper for UltimatePredation
- `AnoMech/Scenarios/Uwu/UltimatePredation/UltimatePredationSettingsWindow.cs` — Settings UI for UltimatePredation
- `AnoMech/Scenarios/Uwu/UltimatePredation/UltimatePredationState.cs` — Per-run mechanic state for UltimatePredation
- `AnoMech/Scenarios/Uwu/UltimatePredation/UltimatePredationStateOverrides.cs` — User-forced rolls for UltimatePredation
- `AnoMech/Scenarios/Uwu/UltimateSuppression/UltimateSuppressionAi.cs` — AI strat decisions for UltimateSuppression
- `AnoMech/Scenarios/Uwu/UltimateSuppression/UltimateSuppressionScenario.cs` — Fight timeline and entities for UltimateSuppression
- `AnoMech/Scenarios/Uwu/UltimateSuppression/UltimateSuppressionSettingsWindow.cs` — Settings UI for UltimateSuppression
- `AnoMech/Scenarios/Uwu/UltimateSuppression/UltimateSuppressionState.cs` — Per-run mechanic state for UltimateSuppression
- `AnoMech/Scenarios/Uwu/UltimateSuppression/UltimateSuppressionStateOverrides.cs` — User-forced rolls for UltimateSuppression
- `AnoMech/packages.lock.json` — Resolved NuGet dependency versions
- `images/icon.png` — Plugin icon artwork
- `repo-map.md` — Project guidance or documentation (repo-map.md)
- `tests/AnoMech.Tests/Core/Native/Fakes/FakeActionTimelinePreload.cs` — Source implementation (FakeActionTimelinePreload)
- `tests/AnoMech.Tests/Core/Native/Fakes/FakeBattleChara.cs` — Source implementation (FakeBattleChara)
- `tests/AnoMech.Tests/Core/Native/Fakes/FakeBattleCharas.cs` — Source implementation (FakeBattleCharas)
- `tests/AnoMech.Tests/Core/Native/Fakes/FakeBgm.cs` — Source implementation (FakeBgm)
- `tests/AnoMech.Tests/Core/Native/Fakes/FakeCharacter.cs` — Source implementation (FakeCharacter)
- `tests/AnoMech.Tests/Core/Native/Fakes/FakeEventObject.cs` — Source implementation (FakeEventObject)
- `tests/AnoMech.Tests/Core/Native/Fakes/FakeEventObjects.cs` — Source implementation (FakeEventObjects)
- `tests/AnoMech.Tests/Core/Native/Fakes/FakeGame.cs` — Source implementation (FakeGame)
- `tests/AnoMech.Tests/Core/Native/Fakes/FakeHaterList.cs` — Source implementation (FakeHaterList)
- `tests/AnoMech.Tests/Core/Native/Fakes/FakeInstanceContentDirector.cs` — Source implementation (FakeInstanceContentDirector)
- `tests/AnoMech.Tests/Core/Native/Fakes/FakeLayoutFunctions.cs` — Source implementation (FakeLayoutFunctions)
- `tests/AnoMech.Tests/Core/Native/Fakes/FakeLimitBreakController.cs` — Source implementation (FakeLimitBreakController)
- `tests/AnoMech.Tests/Core/Native/Fakes/FakeLocalPlayerInput.cs` — Source implementation (FakeLocalPlayerInput)
- `tests/AnoMech.Tests/Core/Native/Fakes/FakeMapEffects.cs` — Source implementation (FakeMapEffects)
- `tests/AnoMech.Tests/Core/Native/Fakes/FakePartyHud.cs` — Source implementation (FakePartyHud)
- `tests/AnoMech.Tests/Core/Native/Fakes/FakePlayerConditions.cs` — Source implementation (FakePlayerConditions)
- `tests/AnoMech.Tests/Core/Native/Fakes/FakeRsfFunctions.cs` — Source implementation (FakeRsfFunctions)
- `tests/AnoMech.Tests/Core/Native/Fakes/FakeRsvFunctions.cs` — Source implementation (FakeRsvFunctions)
- `tests/AnoMech.Tests/Core/Native/Fakes/FakeUserActions.cs` — Source implementation (FakeUserActions)
- `tests/AnoMech.Tests/Core/Native/Fakes/FakeWaymarks.cs` — Source implementation (FakeWaymarks)
- `tests/AnoMech.Tests/Core/Native/Fakes/FakeZoneControl.cs` — Source implementation (FakeZoneControl)
- `tests/AnoMech.Tests/Multiplayer/DebugBotReplayTests.cs` — Source implementation (DebugBotReplayTests)
- `tests/AnoMech.Tests/Multiplayer/FallingBehindTests.cs` — Source implementation (FallingBehindTests)
- `tests/AnoMech.Tests/Multiplayer/LinkInterruptionTests.cs` — Source implementation (LinkInterruptionTests)
- `tests/AnoMech.Tests/Multiplayer/PeerParityTests.cs` — Source implementation (PeerParityTests)
- `tests/AnoMech.Tests/Multiplayer/PlayerActionTests.cs` — Source implementation (PlayerActionTests)
- `tests/AnoMech.Tests/Multiplayer/ProtocolTests.cs` — Source implementation (ProtocolTests)
- `tests/AnoMech.Tests/Multiplayer/RelayClientTests.cs` — Source implementation (RelayClientTests)
- `tests/AnoMech.Tests/Multiplayer/RelayGroupsTests.cs` — Source implementation (RelayGroupsTests)
- `tests/AnoMech.Tests/Multiplayer/RelayLoopbackTests.cs` — Source implementation (RelayLoopbackTests)
- `tests/AnoMech.Tests/Multiplayer/ResultMarkTests.cs` — Source implementation (ResultMarkTests)
- `tests/AnoMech.Tests/Multiplayer/SessionStreamTests.cs` — Source implementation (SessionStreamTests)
- `tests/AnoMech.Tests/Scenarios/Fru/P2DiamondDust/FruP2DiamondDustScenarioTests.cs` — Shared mechanic or data helper for P2DiamondDust
- `tests/AnoMech.Tests/Scenarios/Fru/P2LightRampant/FruP2LightRampantScenarioTests.cs` — Shared mechanic or data helper for P2LightRampant
- `tests/AnoMech.Tests/Scenarios/Fru/P3Apocalypse/FruP3ApocalypseScenarioTests.cs` — Shared mechanic or data helper for P3Apocalypse
- `tests/AnoMech.Tests/Scenarios/Fru/P3UltimateRelativity/FruP3UltimateRelativityScenarioTests.cs` — Shared mechanic or data helper for P3UltimateRelativity
- `tests/AnoMech.Tests/Scenarios/Fru/P4CrystallizeTime/FruP4CrystallizeTimeScenarioTests.cs` — Shared mechanic or data helper for P4CrystallizeTime
- `tests/AnoMech.Tests/Scenarios/Fru/P4DarklitDragonsong/FruP4DarklitDragonsongScenarioTests.cs` — Shared mechanic or data helper for P4DarklitDragonsong
- `tests/AnoMech.Tests/Scenarios/Fru/P5FulgentBlade/FruP5FulgentBladeScenarioTests.cs` — Shared mechanic or data helper for P5FulgentBlade
- `tests/AnoMech.Tests/Scenarios/Fru/P5ParadiseRegained/FruP5ParadiseRegainedScenarioTests.cs` — Shared mechanic or data helper for P5ParadiseRegained
- `tests/AnoMech.Tests/Scenarios/Top/P2PartySynergy/TopP2PartySynergyLpduAiTests.cs` — Shared mechanic or data helper for P2PartySynergy
- `tests/AnoMech.Tests/Scenarios/Top/P2PartySynergy/TopP2PartySynergyScenarioTests.cs` — Shared mechanic or data helper for P2PartySynergy
- `tests/AnoMech.Tests/Scenarios/Top/P5Delta/TopP5DeltaScenarioTests.cs` — Shared mechanic or data helper for P5Delta
- `tests/AnoMech.Tests/Scenarios/Top/P5Omega/TopP5OmegaScenarioTests.cs` — Shared mechanic or data helper for P5Omega
- `tests/AnoMech.Tests/Scenarios/Top/P5Sigma/TopP5SigmaScenarioTests.cs` — Shared mechanic or data helper for P5Sigma
- `tests/AnoMech.Tests/Scenarios/Top/P6WaveCannon2/TopP6WaveCannon2ScenarioTests.cs` — Shared mechanic or data helper for P6WaveCannon2
- `tests/AnoMech.Tests/Scenarios/Ucob/P5Exaflares/UcobP5ExaflaresScenarioTests.cs` — Shared mechanic or data helper for P5Exaflares
- `tests/AnoMech.Tests/Scenarios/Umad/P1TeleTrouncing/UmadP1TeleTrouncingScenarioTests.cs` — Shared mechanic or data helper for P1TeleTrouncing
- `tests/AnoMech.Tests/Scenarios/Umad/P2Forsaken/UmadP2ForsakenScenarioTests.cs` — Shared mechanic or data helper for P2Forsaken
- `tests/AnoMech.Tests/Scenarios/Umad/P3BlackHole/UmadP3BlackHoleScenarioTests.cs` — Shared mechanic or data helper for P3BlackHole
- `tests/AnoMech.Tests/Scenarios/Umad/P3LimitCut/UmadP3LimitCutScenarioTests.cs` — Shared mechanic or data helper for P3LimitCut
- `tests/AnoMech.Tests/Scenarios/Umad/P4KefkaSays/UmadP4KefkaSaysScenarioTests.cs` — Shared mechanic or data helper for P4KefkaSays
- `tests/AnoMech.Tests/Scenarios/Umad/P5Celestriad/UmadP5CelestriadScenarioTests.cs` — Shared mechanic or data helper for P5Celestriad
- `tests/AnoMech.Tests/Scenarios/Umad/P5Exaflares/UmadP5ExaflaresScenarioTests.cs` — Shared mechanic or data helper for P5Exaflares
- `tests/AnoMech.Tests/Scenarios/Umad/P5Flood/UmadP5FloodScenarioTests.cs` — Shared mechanic or data helper for P5Flood
- `tests/AnoMech.Tests/Scenarios/Uwu/UltimatePredation/UltimatePredationScenarioTests.cs` — Shared mechanic or data helper for UltimatePredation
- `tests/AnoMech.Tests/Scenarios/Uwu/UltimateSuppression/UltimateSuppressionScenarioTests.cs` — Shared mechanic or data helper for UltimateSuppression
- `tests/AnoMech.Tests/Support/BadConnections.cs` — Source implementation (BadConnections)
- `tests/AnoMech.Tests/Support/ClientParity.cs` — Source implementation (ClientParity)
- `tests/AnoMech.Tests/Support/ConnectionProfile.cs` — Source implementation (ConnectionProfile)
- `tests/AnoMech.Tests/Support/DalamudServices.cs` — Source implementation (DalamudServices)
- `tests/AnoMech.Tests/Support/FakeFramework.cs` — Source implementation (FakeFramework)
- `tests/AnoMech.Tests/Support/LinkStalls.cs` — Source implementation (LinkStalls)
- `tests/AnoMech.Tests/Support/MultiplayerRun.cs` — Source implementation (MultiplayerRun)
- `tests/AnoMech.Tests/Support/NativesState.cs` — Source implementation (NativesState)
- `tests/AnoMech.Tests/Support/NegativeRun.cs` — Source implementation (NegativeRun)
- `tests/AnoMech.Tests/Support/ScenarioArtifacts.cs` — Source implementation (ScenarioArtifacts)
- `tests/AnoMech.Tests/Support/ScenarioRun.cs` — Source implementation (ScenarioRun)
- `tests/AnoMech.Tests/Support/SimTimeline.cs` — Source implementation (SimTimeline)
- `tests/AnoMech.Tests/Support/TestClient.cs` — Source implementation (TestClient)
- `tests/AnoMech.Tests/Support/TestRelay.cs` — Source implementation (TestRelay)
- `tests/AnoMech.Tests/Support/TraceLog.cs` — Source implementation (TraceLog)
- `tests/AnoMech.Tests/Support/WorldSnapshot.cs` — Source implementation (WorldSnapshot)
