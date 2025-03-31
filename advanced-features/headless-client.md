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

# Headless client

The headless client is an exclusive Fika feature that allows you to host a raid on a separate Escape From Tarkov instance. You are able to offload the AI calculation and other resource-intensive task to improve game play performance. FPS gains are usually around 25% to 50% depending on your computer specifications and amount of bots in the game.

{% hint style="warning" %}
Please note that there is some technical knowledge required to achieve this. If you absolutely have no experience, you will have a hard time.
{% endhint %}

### General info

* The headless client is basically another Fika instance that will automatically host raids. All players becomes clients (including the host).
* Graphic rendering is disabled in order to make the headless client as lightweight as possible. However, the headless client is **NOT** a true headless headless server. It still requires all the game files and a pretty hefty amount of RAM in order to work (especially for bigger maps such as Streets).
* In other words, it's a patched Escape From Tarkov instance that poorly imitates a headless server. The benefits are still huge and we recommend using it if you have the resources to improve your game play experience.
* It is recommended to run the headless client on a separate physical machine. We do not recommend using a VPS; as stated above, this is not a real headless server and resources needed to run the headless client are generally too big for a typical VPS.

### Hardware requirements

* A modern CPU with at least 4 cores @ >3.2GHz.
* 16GB of RAM (virtual paging can alleviate this requirement but will degrade performance).
* 50GB disk space with SSD/NVME drive. HDD is NOT sutiable for Fika or Tarkov in general.
* Graphics card not required.

### Installation

* Install Escape From Tarkov on the server that you're planning to host the headless client on using the official BSG launcher. This is required to validate that you own the game.
* Copy your working Fika installation to the server in a separate folder. This will be referred to as `headless folder` in the steps below. If this is not possible, please follow the [Installing Fika](../installing-fika/) procedure on the server and make sure to run the game using `SPT.Launcher.exe` at least once.
* Remove all the DLLs inside `<headless folder>\BepInEx\plugins` except for `Fika.Core.dll` and the `spt` subfolder.
* Download [Fika.Headless](https://github.com/project-fika/Fika-Headless/releases/tag/v1.3.0)
* Extract `Fika.Headless`to your `headless folder`.
* Go to the machine where the SPT server is hosted.
* Navigate to `<SPT folder>\user\mods\fika-server\assets\configs` and open `fika.jsonc`.
* Find the `headless` section.
* Set the `amount` of profiles to at least `1`. This will generate headless client profiles during next SPT server start.
* Set the `forceIp` to the IP of your SPT server. This will tell the headless client which IP to connect to.
* Save and close `fika.jsonc`.
* Start `SPT.Server.exe`.
* You should see the following output in the console:

```
ModLoader: loading: 1 server mods...
Mod: server version: 2.4.0 by: Fika loaded
Server: executing startup callbacks...
Importing database...
Database import finished
Found 0 headless client profiles.
Created 1 headless client profiles!
Generated launch script: /fika-server/assets/scripts/Start_headless_67d61ef943bed350dc0455f1.ps1
Started webserver at https://0.0.0.0:6969
Started websocket at wss://0.0.0.0:6969
Server is running, do not close while playing SPT, Happy playing!!
```

* Navigate to `<SPT folder>\user\mods\fika-server\assets\scripts` and copy the .ps1 file.
* Paste the script file inside your `headless folder`. It must be in the same directory as `EscapeFromTarkov.exe`.
* Right-click the .ps1 file and select `Run with Powershell`. A console window should show up. <mark style="color:red;">**Do not close it!**</mark>

{% hint style="warning" %}
**WARNING**

If the PowerShell window briefly appears and then disappears then your **ExecutionPolicy** might be set to **Restricted**. This should be **RemoteSigned** by default but used to be **Restricted**, so if your Windows installation is not recent or you do not have PowerShell updated it will be set to **Restricted**.

To update your execution policy, open a PowerShell window and write:

```powershell
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser
```

Once done, press **ENTER** and close the window. You can read more about Execution Policies [here](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_execution_policies?view=powershell-7.5).
{% endhint %}

* Go back to your normal Fika folder and start the game using `SPT.Launcher.exe` as you normally would.
* Go to the lobby screen and click `Host Raid`. Tick the `Use headless host` checkbox to start a raid using the headless host.

### Additional information

{% hint style="danger" %}
**NOTICE**

Generally, the headless client does not need to have the same client mods as the players (clients). The only exceptions to this rule are **AI mods (SAIN)**, **spawn mods (MOAR, DONUTS)** and mods that have **implemented synchronization with Fika (That's Lit, UIFixes)**. Always make sure to look at the SPT mod page or the mod's thread in our Discord to confirm.

Using mods that are designed for game play experience on the headless **will** cause issues with the headless client. The headless client does not function the same way as a normal Fika instance and will cause issues with the mods. A few notable examples: **Amanda.Graphics**, **MoreCheckmarks**, **EFTApi**, **GamePanelHud**, **DynamicMaps**, **LootValue**, **Ram Cleaner Interval**, **DeClutter**, etc.
{% endhint %}

* If the `Use headless host` check box is greyed out, the headless client was unable to connect to your SPT server OR the headless client is already hosting a raid.
* Troubleshoot connectivity issues the same way you would do for a normal Fika instance.
