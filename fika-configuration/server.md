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

```json
{
    "client": {
        "useBtr": true, // if the BTR should spawn on streets, default: true
        "friendlyFire": true, // if friendly fire is enabled, default: true
        "dynamicVExfils": false, // if vehicle exfils should scale to the amount of players in raid rather than default to 4, default: false
        "allowFreeCam": false, // if the free cam can be toggled freely, default: false
        "allowSpectateFreeCam": false, // if we are allowed to freecam when spectating players after death or extraction. Freecam is still enabled if all players have died or extracted, default: false
        "allowItemSending": true, // if item sending should be enabled, default: true
        "blacklistedItems": [], // item template ids that cannot be sent, e.g. ["5c94bbff86f7747ee735c08f", "5c1d0f4986f7744bb01837fa"] would not allow players to send access cards and black keycards
        "forceSaveOnDeath": false, // if saving is forced upon death, preventing ALT+F4 cheese, default: false
        "mods": {
            "required": [], // required mods on the server, if enabled you should always include standard SPT mods: ["com.SPT.custom", "com.SPT.singleplayer", "com.SPT.core", "com.SPT.debugging", "com.fika.core", "com.bepis.bepinex.configurationmanager"]
            "optional": [] // mods that are allowed outside of required
        },
        "useInertia": true, // if inertia should be enabled, default: true
        "sharedQuestProgression": false, // if quest progression in raid should be shared, default: false
        "canEditRaidSettings": true, // if editing raid settings is allowed, default: true
        "enableTransists": true // if transit system is enabled, default: true
    },
    "server": {
        "giftedItemsLoseFIR": true, // if sent items should lose their FiR status, default: true
        "launcherListAllProfiles": false, // if launcher should show all profiles, default: false
        "sessionTimeout": 5, // how long the server waits for a keepalive ping from a client until the session is considered crashed, default: 5
        "showDevProfile": false, // if dev profiles can be created, default: false
        "showNonStandardProfile": false // if non-standard EFT profiles can be created, default: false
    },
    "natPunchServer": {
        "enable": false, // if nat punching should be enabled; requires FikaServerTools, default: false
        "port": 6970, // nat punching port, default: 6970
        "natIntroduceAmount": 1
    },
    "dedicated": {
        "profiles": {
            "amount": 0 // how many dedicated client profiles should be generated, default: 0
        },
        "scripts": {
            "generate": true, // if a launch script should be generated upon generating a dedicated client profile, default: true
            "forceIp": "" // ip to set in the launch script, default: empty
        }
    },
    "background": {
        "enable": true, // use fika background in the SPT launcher, default: true
        "easteregg": false // enable easter egg, default: false
    }
}
```
