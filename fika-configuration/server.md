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

# Server

The server configuration can be found in the `user\mods\fika-server\assets\configs` folder. Open up `fika.jsonc` with a text editor.

{% code fullWidth="true" %}
```json5
{
    "client": {
        "useBtr": true, // if the BTR should spawn
        "friendlyFire": true, // if friendly fire is enabled
        "dynamicVExfils": true, // if vehicle exfils should dynamically scale with the amount of players
        "allowFreeCam": true, // if players can use the free cam while still alive
        "allowSpectateFreeCam": true, // whether players are forced to spectate other players or if they can move freely
        "blacklistedItems": [], // items that cannot be sent
        "forceSaveOnDeath": false, // if a player's inventory is force saved when they die, mitigating ALT+F4 cheating
        "mods": {
            "required": [], // required mods by the client
            "optional": [] // optional mods allowed to connect with
        },
        "useInertia": true, // if inertia should be enabled, if disabled it will act as if you are not wearing anything
        "sharedQuestProgression": true, // if quest progression should be shared
        "canEditRaidSettings": true, // of clients can modify the raid settings before starting a raid
        "enableTransits": false, // if transits are enabled
        "anyoneCanStartRaid": false // if anyone can click "START RAID"
    },
    "server": {
        "SPT": {
            "http": {
                "ip": "127.0.0.1", // the interface to listen on
                "port": 6969, // the port to host on
                "backendIp": "127.0.0.1", // the ip that is sent to clients to be used for requests
                "backendPort": 6969 // the port that is sent to clients to be used for requests
            },
            "disableSPTChatBots": false // forces chat bots to be off
        },
        "allowItemSending": true, // allows players to send items to each other
        "sentItemsLoseFIR": true, // if sent items lose their FIR status
        "launcherListAllProfiles": false, // if all accounts are listed in the launcher
        "sessionTimeout": 5, // how long in minutes it takes for a raid to be considered "lost" when not responding
        "showDevProfile": false, // if dev profiles are enabled
        "showNonStandardProfile": false, // if non-standard EFT profiles are enabled
        "logClientModsInConsole": false // if all mods of a client connecting should be printed
    },
    "natPunchServer": {
        "enable": false, // if the nat punching module is enabled
        "port": 6790, // the port to use
        "natIntroduceAmount": 1
    },
    "headless": {
        "profiles": {
            "amount": 0, // the amount of profiles to be generated / used
            "aliases": {} // the aliases to be show when selecting a headless client
        },
        "scripts": {
            "generate": true, // if the headless scripts should be generated
            "forceIp": "" // the ip the headless connects to
        },
        "setLevelToAverageOfLobby": true, // use average level of all players when spawning bots on headless
        "restartAfterAmountOfRaids": 0 // if the headless should restart after X raids, 0 to disable
    },
    "background": {
        "enable": true, // enables custom launcher background
        "easteregg": false
    }
}
```
{% endcode %}

