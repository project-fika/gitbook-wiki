---
description: >-
  Below you will find common questions and solutions. More in-depth guides can
  be found under the table of contents links on the left.
---

# FAQ and Guides

## General Common Issues

### ❓I changed `http.json` but my server still says `0.0.0.0`

{% hint style="warning" %}
Please do not watch video guides, they are often out of date.
{% endhint %}

There is no longer any need to edit `http.json` (or anything else) in `SPT_Data\` — anything entered in `http.json` is overwritten by the `ip` and `backendIp` values in `user/mods/fika-server/assets/configs/fika.jsonc`.

* Server mod configuration documentation can be found [here](../fika-configuration/server.md).
  * You must run `SPT.Server.exe` at least once with `fika-server` installed for `fika.jsonc` to generate.

Please follow the instructions for hosting <a href="../hosting-a-fika-server/" class="button primary" data-icon="arrow-right-long">Hosting a Fika server</a>

***

### ❓I do not see my friend(s) on the Online Players list on the main menu / I cannot see my friend's raid in the raid list

{% hint style="warning" %}
<mark style="color:$warning;">**Only one person in the group launches SPT.Server.exe.**</mark>
{% endhint %}

* Decide which person is the server host. That person alone runs `SPT.Server.exe` and follows the [Hosting a Fika server](../hosting-a-fika-server/) instructions.
* Everyone else **does not run `SPT.Server.exe`** and instead follows the [Joining a Fika server](../joining-a-fika-server/) instructions.
* Make sure that everyone has Fika [installed](../installing-fika/). On the main menu, it should say FIKA in the bottom-left of the screen.

***

### ❓My friend is getting an error about open ports when trying to join my raid

{% hint style="info" %}
**Make sure everyone is following** [**the instructions for hosting/joining a raid**](../playing-fika.md) **correctly.**
{% endhint %}

#### If you are _not_ using a headless client and your group is using Radmin VPN (or any other VPN client)

* Whoever clicks the `HOST RAID` button needs to follow these instructions **exactly as they are written**:
  * Navigate to the Fika.Core plugin settings in your F12 configuration menu and scroll down to the Network header. Select <mark style="color:$warning;">**your own VPN IP**</mark> from the `Force Bind IP` dropdown selection box, then type that <mark style="color:$warning;">**same exact IP**</mark> in the `Force IP` box just above.\
    \
    If you do not see the correct IP available in the `Force Bind IP` selection box, make sure you have the VPN client installed and are connected and then re-read the paragraph above very carefully.\
    \
    Also verify that the settings Use UPnP and Use NAT Punching are both unchecked/disabled.

#### If you are _not_ using a headless client and your group is port forwarding

* Whoever clicks the `HOST RAID` button needs to ensure that they have port forwarded 25565/udp in their router to the PC where they are playing SPT. The raid is hosted by the person who presses `HOST RAID`, not by the `SPT.Server` host.
* Make sure all settings in F12 -> Fika.Core -> Network are **default**:
  * `Force IP` should be blank
  * `Force Bind IP` should be Disabled or `0.0.0.0`
  * Port should match the port for which a port forward rule was created (25565 is default)
  * Both UPnP and NAT Punching should be **disabled**

#### If you are using headless client

* If you are using the headless client to host raids and you are getting this error, you need to make sure the headless client is set up to accept incoming connections the same way any normal client would be.&#x20;
  * **If you are port forwarding**, your port forward rule for 25565/udp needs to go to the PC that is running the headless client. All settings in `BepInEx/config/com.fika.core.cfg -> Network` section should be **default**.
  * **If you are using a VPN**, you need to open up your `<headless install>/BepInEx/config/com.fika.core.cfg` in a text editor and make sure the VPN IP of the headless client machine is set for both `Force IP` and `Force Bind IP`. The VPN client must also be installed and configured on the headless client PC as well.

***

### ❓F8 is not successfully extracting me from a raid

This has two common causes: either a mod is causing errors or something is intercepting the F8 key press.

Try pressing F12 to bring up the BepInEx Configuration Manager settings window. If that worked, try finding the Fika.Core setting for extract hotkey and rebinding it to a different key.

If F12 did not work or you were unable to rebind the extract hotkey to a different key (or if it shows it is bound to F13), you likely have something intercepting your F-keys. This is often overlay software like Overwolf or MSI Afterburner or similar, or it could be a joystick / steering wheel / other controller plugged in that is intercepting the F-keys. Try closing all overlay software and unplugging all control peripherals.

If none of the above worked, it is likely a mod that is causing issues. You will have to close your game client via ALT+F4 and then look in your Player.log file found in the folder below:

```
C:\Users\YOURUSERNAME\AppData\LocalLow\Battlestate Games\EscapeFromTarkov\
```

Open Player.log in a text editor and search for `F8 pressed` and see if there are any errors nearby that hint at which mod may be the cause. If you are unsure, come visit us in the [Discord](https://discord.gg/project-fika) #questions channel and explain what you've tried and upload your Player.log for assistance.

***

### ❓ I cannot see SPT chat bots like Commando / I cannot create the type of profile I want / I cannot enable quest sharing in F12

Review the fika-server mod [configuration options](../fika-configuration/server.md).

***

### ❓I cannot use transits

Transits are disabled with Fika for SPT 3.11.x unless you are using a [headless client](../advanced-features/headless-client.md) as a raid host.

* Simply because transits are fragile & host migration is complex, transits are currently disabled under most circumstances. If you are just trying to complete quests that require transiting from one map to another, you can utilize a mod like [Skipper](https://hub.sp-tarkov.com/files/file/1861-skipper/) to mark those quests complete. Play both raids, complete the task to the best of your ability, then skip it. Or just ignore these quests.\
  \
  You can also solve this with the mod [No Transit Tasks](https://hub.sp-tarkov.com/files/file/2616-no-transit-tasks/).

***

### ❓How do I uninstall Fika?

1. Navigate to `BepInEx/plugins/` and delete `Fika.Core.dll`
2. Navigate to `user/mods/` and delete the `fika-server/` folder
3. Open SPT.Launcher.exe, click Settings in the top-right, and (if applicable) change URL back to `https://127.0.0.1:6969`\


***

***

## Headless Client Common Issues

### ❓The headless client launch script just opens and closes

Run the following command in an elevated Powershell window:&#x20;

```powershell
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned
```

You can find more information about [Powershell Execution Policy here](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_execution_policies?view=powershell-7.5).

***

### ❓I get an error popup about `A patch in SPTCustomPlugin FAILED` when starting the headless client

Look at the red error text in the headless client console, try to find a match of the two common errors below:

* <mark style="color:red;">**`The type initializer for SPT.Custom.Patches.CustomAiPatch...`**</mark>\
  Your headless client is not able to connect to the backend server. Make sure `SPT.Server.exe` is running and loaded and able to be connected to. Open the launch .ps1 script in a text editor and check the `BackendUrl` at the top of the launch .ps1 script is correct. Also make sure you are not running `_TEMPLATE.ps1`; the launch script should be named `Start_headless_someuid.ps1`.
  * SPT.Server.exe and headless client on the same machine:
    * If you're using a VPN, `BackendUrl` should be `https://your.vpn.ip.addr:6969`.
    * If you're port forwarding, `BackendUrl` should be `https://127.0.0.1:6969`.
  * SPT.Server.exe and headless client are on different machines:
    * Within the same network, `BackendUrl` should be `https://your.LAN.IPv4.addr:6969`,
    * Different network, `BackendUrl` should either be `https://your.vpn.ip.addr:6969` (VPN) or `https://some.pub.lic.ip:6969` (port forwarding).
* <mark style="color:red;">**`The type initializer for SPT.Custom.Patches.EasyAssetsPatch...`**</mark>
  * Either reinstall following [the directions here](../advanced-features/headless-client.md), or copy these two DLL files from your working and already-launched SPT install to your headless client.

<figure><img src="../.gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>

