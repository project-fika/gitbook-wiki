---
description: Learn about the features, specifications and limitations of Fika.
icon: circle-info
layout:
  width: default
  title:
    visible: true
  description:
    visible: true
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: false
  metadata:
    visible: true
---

# General information

## What is Fika?

Fika is a cooperative multiplayer mod for [SPT](https://sp-tarkov.com/). Fika adds a lobby interface to join other players' raids and provide in-game networking capabilities, along with additional features that do not alter the standard Escape From Tarkov experience by default.

In summary:

* SPT is the back-end server that allows you to start the game without using BSG servers — it provides the player profile, inventory, flea market, and many other Escape From Tarkov features.
* Fika is the mod component that adds cooperative multiplayer capabilities which allow players to host or join a raid to play together.

## Specifications

* Fika is a combination of a [BepInEx plugin](https://github.com/project-fika/Fika-Plugin) and a [SPT server mod](https://github.com/project-fika/Fika-Server).
* Fika uses SPT as the back-end server to connect players together.
* Fika uses the Client <-> Server UDP networking model for game play. While Fika is still in development, the general consensus is that network performance is better than Escape From Tarkov live (provided the host has proper networking capabilities).

## Main features

* Host your own server or join a local/external server.
* Create your own raid for other players to join (or play solo).
* Join someone else's raid.
* Play together against bots, share items, progress quests together in the same raid.
* Preserve character, quest, inventory, and hideout progression.
* Use client/server mods from [SPT](https://forge.sp-tarkov.com/) (some mods are not compatible - see [Limitations](General-information.md#limitations)).

## Other features

* Item Sending
  * Right-click an item in your stash to send it to another account
  * Can be customized in the [server](fika-configuration/server.md) config
* Free cam (default to `F9` key)
  * In free cam you can teleport to the cam position by pressing `T`
  * You can jump to another player by `Left/Right` clicking
  * You can snap to their head by holding `SPACE` when jumping
  * You can snap to their back in a 3rd position view by holding `CTRL` when jumping
  * You can press the `HOME` key to temporarily toggle free cam controls
* In-game chat system
* In-raid VOIP
* Online player list
* Dynamic AI for hosts, which disables AI when no one is near
* Custom AI limits per map
* Culling system to increase performance
* Custom notifications (teammate died, boss got killed by a player, etc.)
* Pinging system to ping an area in the game for your teammates
* Player health bars for your teammates
* Quest progress sharing in raids
* Optional/Advanced Headless client to offload AI and gain performance (more info [here](advanced-features/headless-client/remote-headless-client.md))
* Network interpolation for smoother gameplay
* UPnP and NAT Punching

## Limitations

* You cannot play Fika without owning a legitimate copy of Escape From Tarkov. You will be banned if you attempt to do so.
* There is no protection against abuse or cheating. Fika is designed to be played with trusted friends. **Hosting a public server is strongly discouraged**. We will NEVER support public servers.
* Fika does not include any PvP mechanisms. Supporting PvP is not the goal of this project.
* Fika does not offer a global matchmaking service. Only players connected to the same server can create or join raids.
* Certain SPT mods are incompatible with Fika. SPT mods are typically designed for a standard SPT installation, which does not include multiplayer functionality. It is the responsibility of the mod's author to make their mod compatible with Fika, if they choose to do so.
