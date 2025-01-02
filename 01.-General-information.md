# How does Fika work?

Fika is an unofficial mod for SPT. Many features, such as profiles, characters, hideouts, inventory, quests, and trading, are provided by SPT itself. 

Project Fika builds on this by offering a lobby interface for joining other players' raids and provide in-game networking capabilities, along with additional features that do not alter the standard Escape from Tarkov experience by default.

In summary:
- SPT serves as the backend server that players connect to load their profile.
- Fika serves as the in-game server/client that players use to host or join a raid and play together.

# Specifications
- Fika is a combination of a [BepInEx mod](https://github.com/project-fika/Fika-Plugin) and a [SPT plugin](https://github.com/project-fika/Fika-Server)
- Fika uses SPT (with the Fika-Server plugin) as the backend server for profile and lobby management.
- Fika uses an efficient P2P-UDP networking for in-raid gameplay. While Fika is still in development, the general consensus is that network performance is better than Escape From Tarkov live (provided the host has proper networking capabilities).

# Main features
- Host your own server.
- Create your own raid (or play solo).
- Join someone else's raid.
- Play together against bots, share items, progress quests together in the same raid.
- Preserve character, quest, inventory, and hideout progression.
- Use client/server mods from [SPT](https://hub.sp-tarkov.com/) (some mods are not compatible - see here for the list of incompatible mods).

# Other features
- Item Sending
    - Right-click an item in your stash to send it to another account
    - Can be customized in the [server](https://github.com/project-fika/Fika-Documentation/wiki/6.-Fika-configuration) config
- Free cam (default to `F9` key)
    - In free cam you can teleport to the cam position by pressing `T`
    - You can jump to another player by `Left/Right` clicking
    - You can snap to their head by holding `SPACE` when jumping
    - You can snap to their back in a 3rd position view by holding `CTRL` when jumping
    - You can press the `HOME` key to temporarily toggle free cam controls
- Damage multipliers for crucial areas on yourself
- Dynamic AI for hosts, which disables AI when no one is near
- Custom AI limits per map
- Culling system to increase performance
- Custom notifications (teammate died, boss got killed by a player, etc.)
- Pinging system to ping an area in the game for your teammates
- Player health bars for your teammates
- Quest progress sharing in raids
- Dedicated client (more info here)

# Limitations
- You cannot play SPT/Fika without owning a legitimate copy of Escape From Tarkov. You will be banned if you're caught.
- There is practically no protection against abuse or cheating. Fika is designed to be played with trusted friends. Hosting a public server is strongly discouraged. We will NEVER support public servers.
- Only one active raid at a time. There are some underlying issues with the backend server that may corrupt your profile when two or more raids are active at the same time.
- Fika does not include any PvP mechanisms, as supporting PvP is not the goal of this project.
- Fika does not offer a global matchmaking service. Only players connected to your server can create or join raids.
- Some SPT mods are incompatible with Fika. SPT mods are typically designed for a standard SPT installation, which does not include multiplayer functionality. It is the responsibility of the mod's author to make their mod compatible with Fika if they choose to do so.