# OpenSim-Split-Robust-Example

This repository contains configuration files that can be used as basis for a distributed robust setup of [OpenSimulator](http://opensimulator.org)

They are based on a testing environment maintained by [Zetamex Network](https://zetamex.com) and may contain parameters exclusive to their version of OpenSimulator.

Included are configurations for a [nginx](https://www.nginx.com/) server acting as reverse proxy serving requests to OpenSimulator. Also included are the respective configuration files for a Simulator connecting to the OpenSimulator Robust configured with this configuration.

Code changes to OpenSimulator or the version Zetamex Network maintains may not be reflected here and absolutely no warranty is given on the accuracy of this configuration. Use at your own risk.

# Network Setup

```
Login			Public	8002 -- 80	Private 8003 -- 80
LoginService
GatekeeperService
UserAgentService
AuthenticationService
UserAccountService
GridUserService
AgentPreferencesService
HGAssetService
---------------------------------------------------------------------
User			Public 8021--.		Private 9021--.
				Public 8022--|-- 80	Private 9022--|-- 9029
				Public 8023--´		Private 9023--´
PresenceService
OpenIdService
AvatarService
---------------------------------------------------------------------
Robust			Public 8031--.		Private 9031--.
				Public 8032--|-- 80	Private 9032--|-- 9039
				Public 8033--´		Private 9033--´
GridService
MapImageService
EstateService
---------------------------------------------------------------------
Inventory		Public 8041--.		Private 9041--.
				Public 8042--|-- 80	Private 9042--|-- 9049
				Public 8043--´		Private 9043--´
InventoryService
HGInventoryService
---------------------------------------------------------------------
Comms			Public 8051-- 80	Private 9051
Messaging
HGInstantMessageService
MuteListService
---------------------------------------------------------------------
Profiles		Public 8061-- 80	Private 9061
UserProfileService
---------------------------------------------------------------------
Friends			Public 8071-- 80	Private 9071
FriendsService
HGFriendsService
---------------------------------------------------------------------
Groups			Public 8081-- 80	Private 9081
Groups
---------------------------------------------------------------------
Map				Public 8098-- 80	Private 9098
MapImageService
```

# Port connector setup

```
[Hypergrid]
Gatekeeper..................Public
HomeURI.....................Public
[InventoryService]..........Private
[GridInfo]..................Public
[GridService]...............Private
Gatekeeper..................Public
[EstateService].............Private
[Groups]			
GroupsServerURI.............Private
HomeURI.....................Public
[Messaging]
OfflineMessageURL...........Private
Gatekeeper..................Public
[AvatarService].............Private
[UserProfiles]..............Public
[AgentPreferencesService]...Private
[PresenceService]...........Private
[UserAccountService]........Private
[GridUserService]...........Private
[AuthenticationService].....Private
[FriendsService]............Private
[MapImageService]...........Private
[MuteListService]...........Private
[UserProfiles]..............Private
[XBakes]....................Private
```
