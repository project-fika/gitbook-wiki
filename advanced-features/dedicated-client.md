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

# Dedicated client

The dedicated client is an exclusive Fika feature that allows you to host a raid on a separate Escape From Tarkov instance. You are able to offload the AI calculation and other resource-intensive task to improve game play performance. FPS gains are usually around 25% to 50% depending on your computer specifications and amount of bots in the game.

{% hint style="warning" %}
Please note that there is some technical knowledge required to achieve this. If you absolutely have no experience, you will have a hard time. Our Discord provides support in such cases.
{% endhint %}

### General info

* The dedicated client is basically another Fika instance that will automatically host raids. All players becomes clients (including the host).
* Graphic rendering is disabled in order to make the dedicated client as lightweight as possible. However, the dedicated client is **NOT** a true dedicated headless server. It still requires all the game files and a pretty hefty amount of RAM in order to work (especially for maps such as Streets).
* In other words, it's a patched Escape From Tarkov instance that poorly imitates a dedicated server. The benefits are still huge and we recommend using it if you have the resources to improve your game play experience.
* It is recommended to run the dedicated client on a separate machine. We do not recommend using a VPS; as stated above this is not a real dedicated headless server and resources needed to run the dedicated client are quite huge for a VPS.

### Hardware requirements

* A modern CPU with at least 4 cores @ 3.2GHz +.
* 16GB of RAM (virtual paging can alleviate this requirement but will degrade performance).
* 50GB disk space with SSD/NVME drive. HDD is NOT recommended for Fika in any shape or form.
* Graphics card not required.

### Installation

* Install Escape From Tarkov on the server that you're planning to host the dedicated client on using the official BSG launcher. This is required to validate that you own the game.
* Copy your working Fika installation to the server in a separate folder. This will be referred to as `dedicated folder` in the steps below. If this is not possible, please follow the [Installing Fika](../installing-fika/) procedure on the server.
* Download [Fika.Dedicated](https://github.com/project-fika/Fika-Dedicated/releases/latest)
* Extract `Fika.Dedicated` to your `dedicated folder`.
* Go to the machine where the SPT server is hosted.
* Navigate to `<SPT folder>\user\mods\fika-server\assets\configs` and open `fika.jsonc`.
* Find the "dedicated" section.
* Set the `amount` of profiles to at least `1`. This will generate dedicated client profiles during next SPT server start.
* Set the `forceIp` to the IP of your SPT server. This will tell the dedicated client which IP to connect to.
* Save and close `fika.jsonc`.
* Start `SPT.Server.exe`.
* You should see the following output in the console:

```
ModLoader: loading: 1 server mods...
Mod: server version: 2.2.8 by: Fika loaded
Server: executing startup callbacks...
Importing database...
Database import finished
Found 0 dedicated client profiles.
Created 1 dedicated client profiles!
Generated launch script: /fika-server/assets/scripts/Start_dedicated_674e72ab0001917ea42a90fa.bat
Started webserver at http://0.0.0.0:6969
Started websocket at ws://0.0.0.0:6969
Server is running, do not close while playing SPT, Happy playing!!
```

* Navigate to `<SPT folder>\user\mods\fika-server\assets\scripts` and copy the batch file.
* Paste the batch file inside your `dedicated folder`. It must be inside the same directory as `EscapeFromTarkov.exe`.
* Run the batch file to start the dedicated client.
* Start the game using your regular profile and click "Host Raid" in the lobby screen. Tick the "Use dedicated host" checkbox to start a raid using the dedicated host. If the check box is greyed out, the dedicated client was not able to connect to your SPT server. See the [troubleshooting](../Troubleshooting.md) section for more information.

### Additional information

* Only install mods on the dedicated client that are necessary for a raid host, such as SAIN or SWAG+DONUTS. General rule of thumb is to install AI or spawn mods.
* Do not install mods that are designed for game play experience such as Amanda.Graphics, MoreCheckmarks, EFTApi, GamePanelHud, DynamicMaps, LootValue, Ram Cleaner Interval, DeClutter, etc.). They will conflict and/or will not be necessary.
