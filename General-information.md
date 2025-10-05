---
layout:
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
---

# General information

## How does Fika work?

Fika is an unofficial mod for SPT. Many features such as profiles, characters, hideouts, inventory, quests, and trading are provided by [SPT](https://sp-tarkov.com/).

Project Fika adds a lobby interface to join other players' raids and provide in-game networking capabilities, along with additional features that do not alter the standard Escape from Tarkov experience by default. In summary:

* SPT is the back-end server that allows you to start the game without using BSG servers - it provides the player profile, inventory, flea market, and many other Escape From Tarkov features.
* Fika is the mod component that adds multiplayer capabilities which allow players to host or join a raid to play together.

{% hint style="danger" %}
\>**3.11** SPT is now using `https` instead of `http`, make sure that you update everything accordingly!
{% endhint %}

## Specifications

* Fika is a combination of a [BepInEx mod](https://github.com/project-fika/Fika-Plugin) (Fika-Plugin) and a [SPT plugin](https://github.com/project-fika/Fika-Server) (Fika-Server).
* Fika uses SPT (with the Fika-Server plugin) as the back-end server for profile and lobby management.
* Fika uses the Client <-> Server UDP networking model for game play. While Fika is still in development, the general consensus is that network performance is better than Escape From Tarkov live (provided the host has proper networking capabilities).

## Main features

* Host your own server.
* Create your own raid (or play solo).
* Join someone else's raid.
* Play together against bots, share items, progress quests together in the same raid.
* Preserve character, quest, inventory, and hideout progression.
* Use client/server mods from [SPT](https://forge.sp-tarkov.com/) (some mods are not compatible - see [Limitations](General-information.md#limitations)).

## Other features

* Item Sending
  * Right-click an item in your stash to send it to another account
  * Can be customized in the [server](https://github.com/project-fika/Fika-Documentation/wiki/6.-Fika-configuration) config
* Free cam (default to `F9` key)
  * In free cam you can teleport to the cam position by pressing `T`
  * You can jump to another player by `Left/Right` clicking
  * You can snap to their head by holding `SPACE` when jumping
  * You can snap to their back in a 3rd position view by holding `CTRL` when jumping
  * You can press the `HOME` key to temporarily toggle free cam controls
* In-game chat system
* Online player list
* Dynamic AI for hosts, which disables AI when no one is near
* Custom AI limits per map
* Culling system to increase performance
* Custom notifications (teammate died, boss got killed by a player, etc.)
* Pinging system to ping an area in the game for your teammates
* Player health bars for your teammates
* Quest progress sharing in raids
* Headless client to offload AI and gain performance (more info [here](advanced-features/headless-client.md))
* Network interpolation for smoother gameplay
* UPnP and NAT Punching

## Limitations

* You cannot play SPT/Fika without owning a legitimate copy of Escape From Tarkov. You will be banned if you're caught.
* There is practically no protection against abuse or cheating. Fika is designed to be played with trusted friends. Hosting a public server is strongly discouraged. We will NEVER support public servers.
* Only one active raid at a time. There are some underlying issues with the back-end server that may corrupt your profile when two or more raids are active at the same time.
* Fika does not include any PvP mechanisms, as supporting PvP is not the goal of this project.
* Fika does not offer a global matchmaking service. Only players connected to the same server can create or join raids.
* Some SPT mods are incompatible with Fika. SPT mods are typically designed for a standard SPT installation, which does not include multiplayer functionality. It is the responsibility of the mod's author to make their mod compatible with Fika if they choose to do so.
