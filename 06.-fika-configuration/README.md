# Client configuration

To open up your client configuration, press the `F12` key while in-game. Head to the `Fika Core` section to configure the settings.

**Coop**

- **Show Notifications**: Enable custom notifications when a player dies, extracts, kills a boss, etc.
- **Auto Extract**: Automatically extracts when playing as a client instead of entering free camera.
- **Show Extract Message**: Whether to show the extract message after dying/extracting.
- **Extract Key**: The key used to extract from the raid.
- **Chat Key**: The key used to open the chat window.

**Coop | Custom**

- **Show Player Name Plates**: Toggle Health-Bars & Names.
- **Hide Health Bar**: Completely hides the health bar.
- **Show HP% instead of bar**: Shows health in % amount instead of using the bar.
- **Show Player Faction Icon**: Shows the player faction icon next to the HP bar.
- **Hide Name Plate in Optic**: Hides the name plate when viewing through PiP scopes.
- **Name Plates Use Optic Zoom**:  name plate location should be displayed using the PiP optic camera.
- **Decrease Opacity In Peripheral**: Decreases the opacity of the name plates when not looking at a player.
- **Name Plate Scale**: Size of the name plates.
- **Opacity in ADS**: The opacity of the name plates when aiming down sights.
- **Ping System**: Toggle Ping System. If enabled you can receive and send pings by pressing the ping key.
- **Ping Button**: Button used to send pings.
- **Ping Color**: The color of your pings when displayed for other players.
- **Ping Size**: The multiplier of the ping size.
- **Play Ping Animation**: Plays the pointing animation automatically when pinging. Can interfere with gameplay.

**Coop | Quest Sharing**
- **Quest Types**: Which quest types to receive and send.

**Coop | Debug**

- **Free Camera Button**: Button used to toggle free camera.
- **AZERTY Mode**: If free camera should use AZERTY keys for input.
- **Keybind Overlay**:  an overlay with all free cam keybinds should show.

**Performance**

- **Dynamic AI**: Use the dynamic AI system, disabling AI when they are outside of any player's range.
- **Dynamic AI Range**: The range at which AI will be disabled dynamically.
- **Dynamic AI Rate**: How often DynamicAI should scan for the range from all players.

**Performance | Max Bots**

- **Enforced Spawn Limits**: Enforces spawn limits when spawning bots, making sure to not go over the vanilla limits. This mainly takes affect when using spawn mods or anything that modifies the bot limits.
- **Despawn Furthest**: When enforcing spawn limits, should the furthest bot be de-spawned instead of blocking the spawn. This will make for a much more active raid on a lower Max Bots count. Helpful for weaker PCs. Will only despawn pmcs and scavs. If you don't run a dynamic spawn mod, this will however quickly exhaust the spawns on the map, making the raid very dead instead.
- **Despawn Minimum Distance**: Don't despawn bots within this distance.
- **Max Bots** `MAP`: Max amount of bots that can be active at the same time on `MAP`. Useful if you have a weaker PC. Set to 0 to disable.

**Network**

- **Native Sockets**:  NativeSockets for gameplay traffic. This uses direct socket calls for send/receive to drastically increase speed and reduce GC pressure. Only for Windows/Linux and might not always work.
- **Force IP**: Forces the server when hosting to use this IP when broadcasting to the backend instead of automatically trying to fetch it. Leave empty to disable. This is required when using a VPN, use your personal VPN IP.
- **Force Bind IP**: Forces the server when hosting to use this local IP when starting the server. Leave empty to disable. This is required when using a VPN, use your personal VPN IP.
- **Auto Server Refresh Rate**: Every X seconds the client will ask the server for the list of matches while at the lobby screen.
- **UDP Port**: Port to use for UDP gameplay packets.
- **Use UPnP**: Attempt to open ports using UPnP. Useful if you cannot open ports yourself but the router supports UPnP.
- **Use NAT Punching**: Use NAT punching when hosting a raid. Only works with fullcone NAT type routers and requires NatPunchServer to be running on the SPT server. UPnP, Force IP and Force Bind IP are disabled with this mode.
- **Connection Timeout**: How long it takes for a connection to be considered dropped if no packets are received.

**Gameplay**

- **Head Damage Multiplier**: X multiplier to damage taken on the head collider. 0.2 = 20%
- **Armpit Damage Multiplier**: X multiplier to damage taken on the armpits collider. 0.2 = 20%
- **Stomach Damage Multiplier**: X multiplier to damage taken on the stomach collider. 0.2 = 20%
- **Disable Bot Metabolism**: Disables metabolism on bots, preventing them from dying from loss of energy/hydration during long raids.

# Server configuration

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
        "sharedQuestProgression": false // if quest progression in raid should be shared, default: false
    },
    "server": {
        "giftedItemsLoseFIR": true, // if sent items should lose their FiR status, default: true
        "launcherListAllProfiles": false, // if launcher should show all profiles, default: false
        "sessionTimeout": 5, // how long the server waits for a keepalive ping from a client until the session is considered crashed, default: 5
        "showDevProfile": false, // if dev profiles can be created, default: false
        "showNonStandardProfile": false // if non-standard EFT profiles can be created, default: false
    },
    "natPunchServer": {
        "enable": false, // if nat punching should be enabled, default: false
        "port": 6970, // nat punching port, default: 6970
        "natIntroduceAmount": 1
    }
}
```