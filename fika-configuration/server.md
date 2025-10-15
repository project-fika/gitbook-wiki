---
description: A default server configuration file with a description for each setting.
---

# Server

The server configuration can be found in the `SPT\user\mods\fika-server\assets\configs` folder. Open up `fika.jsonc` with a text editor. You need to launch the server at least once for this file to be generated.

{% hint style="info" %}
Be sure to save changes and restart the server when you're done to ensure your changes take effect!
{% endhint %}

{% code fullWidth="true" %}
```json5
{
    "client": {
        "useBtr": true, // if the BTR should spawn
        "friendlyFire": true, // if friendly fire is enabled
        "dynamicVExfils": false, // if vehicle exfils should dynamically scale with the amount of players
        "allowFreeCam": false, // if players can use the free cam while still alive
        "allowSpectateFreeCam": false, // whether players are forced to spectate other players or if they can move freely
        "blacklistedItems": [], // items that cannot be sent
        "forceSaveOnDeath": false, // if a player's inventory is force saved when they die, mitigating ALT+F4 cheating
        "mods": {
            "required": [], // required mods by the client
            "optional": [] // optional mods allowed to connect with
        },
        "useInertia": true, // if inertia should be enabled, if disabled it will act as if you are not wearing anything
        "sharedQuestProgression": false, // if quest progression should be shared, affects shared XP options as well
        "canEditRaidSettings": true, // of clients can modify the raid settings before starting a raid
        "enableTransits": true, // if transits are enabled
        "anyoneCanStartRaid": false // if anyone can click "START RAID"
    },
    "server": {
        "SPT": {
            "http": {
                "ip": "0.0.0.0", // the interface to listen on
                "port": 6969, // the port to host on
                "backendIp": "0.0.0.0", // the ip that is sent to clients to be used for requests
                "backendPort": 6969 // the port that is sent to clients to be used for requests
            },
            "disableSPTChatBots": true // forces chat bots to be off
        },
        "webhook": {
            "enabled": false,
            "name": "Fika Server",
            "avatarUrl": "https://github.com/project-fika/Fika-Server-CSharp/blob/main/FikaWebApp/wwwroot/images/FIKA_LOGO.png?raw=true",
            "url": ""
        },
        "allowItemSending": true, // allows players to send items to each other
        "itemSendingStorageTime": 7, // how long before sent item mail expires
        "sentItemsLoseFIR": true, // if sent items lose their FIR status
        "launcherListAllProfiles": true, // if all accounts are listed in the launcher
        "sessionTimeout": 5, // how long in minutes it takes for a raid to be considered "lost" when not responding
        "showDevProfile": true, // if dev profiles are enabled
        "showNonStandardProfile": true, // if non-standard EFT profiles are enabled
        "adminIds": [], // list of profile ids allowed to interact with Mr Fika admin bot commands
        "apiKey": "" // apiKey for interacting with Fika API
    },
    "natPunchServer": {
        "enable": false, // if the nat punching module is enabled
        "port": 6790, // the port to use
        "natIntroduceAmount": 1
    },
    "headless": {
        "profiles": {
            "amount": 0, // the amount of profiles to be generated / used
            "aliases": {
                "68eac997dc053e6fwhatever" : "NameOfHeadless" // headless profile uid : name you want to appear on raid host screen
            } // the aliases to be show when selecting a headless client
        },
        "scripts": {
            "generate": true, // if the headless scripts should be generated
            "forceIp": "https://127.0.0.1:6969" // the URL the headless connects to
        },
        "setLevelToAverageOfLobby": true, // use average level of all players when spawning bots on headless
        "restartAfterAmountOfRaids": 0 // if the headless should restart after X raids, 0 to disable
    },
    "background": {
        "enable": true, // enables custom launcher background
    }
}
```
{% endcode %}
