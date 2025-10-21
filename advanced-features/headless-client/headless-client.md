---
description: >-
  Instructions for setting up a headless client to host your raids from a
  separate computer for maximum performance gains. This is the officially
  supported headless client configuration.
hidden: true
layout:
  width: default
  title:
    visible: true
  description:
    visible: true
  tableOfContents:
    visible: true
  outline:
    visible: false
  pagination:
    visible: false
  metadata:
    visible: true
---

# Remote Headless Client

{% hint style="info" %}
Please make sure you have read everything on the general [Headless Client page](./) first.
{% endhint %}

## Recommended Hardware Requirements

* A dedicated machine for running the headless client.
  * Most virtual private servers (VPS) will **not** work because they do not provide the performance needed for the headless client.
* A modern CPU with at least 4 cores @ 4GHz+.
* 32 GB RAM (16 GB RAM _may_ work but will provide reduced performance due to virtual paging).
* 50 GB disk space with SSD/NVME drive. **HDD is NOT supported.**

## Notes

* The installation process below will guide you through the steps to set up the SPT server and headless client on the same machine. It is possible to separate the SPT server and the headless client, but there is no performance benefit, and the steps are more involved. Therefore, this setup will not be covered in this guide.
* Linux is NOT supported and covered by this article. Visit the dedicated Linux channel in our [Discord](https://discord.gg/project-fika) for assistance.

***

## Installation

{% stepper %}
{% step %}
### Install Escape From Tarkov using BSG Launcher

Escape From Tarkov must be installed on the machine/server where you are planning to run the headless client. This is required to ensure that you own the game.&#x20;

**Fika will NOT work if you skip this step!**
{% endstep %}

{% step %}
### Install [SPT](https://hub.sp-tarkov.com/files/file/672-spt-installer/)

If your SPT server is currently located on a different machine, please copy it to the computer where you are planning to install the headless client. It must contain the full game. If you are unable to copy it due to the size, install SPT on the server using the [SPT Installer](https://hub.sp-tarkov.com/files/file/672-spt-installer/) instead.

**Do NOT install SPT in your official Escape From Tarkov folder!**
{% endstep %}

{% step %}
### Download [Fika-Installer](https://github.com/project-fika/Fika-Installer/releases/latest)
{% endstep %}

{% step %}
### Copy `Fika-Installer.exe` to the root of your SPT install folder

Do not copy inside `SPT` folder!

<figure><img src="../../.gitbook/assets/image (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### Run `Fika-Installer.exe`

If you get an admin rights prompt, this is normal. `Fika-Installer` requires admin rights to set up the firewall rules.
{% endstep %}

{% step %}
### Choose `Install Fika`

<figure><img src="../../.gitbook/assets/image (20) (1).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### Confirm installation completion

<figure><img src="../../.gitbook/assets/image (4) (1) (1).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### OPTIONAL: Set URL in [fika.jsonc](../../fika-configuration/server.md) for headless client

If you are using a VPN like Radmin or ZeroTier, you will need to:

1. Navigate to `[SPT root folder]\SPT\user\mods\fika-server\assets\configs\`
   1. If `fika.jsonc` does not exist, run `SPT.Server.exe` from your headless install once and then close it.
2. Open `fika.jsonc` in a text editor.
3. Scroll down to the `scripts -> forceIp` setting and change it to the URL that you set up while following [the hosting instructions](../../hosting-a-fika-server/).
4. Save the file and close the text editor.

<div align="left"><figure><img src="../../.gitbook/assets/image (31).png" alt=""><figcaption></figcaption></figure></div>
{% endstep %}

{% step %}
### Choose `Advanced options`

<figure><img src="../../.gitbook/assets/image (5) (1) (1).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### Choose `Install Fika Headless`

<figure><img src="../../.gitbook/assets/image (6) (1) (1).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### Choose `Create a new headless profile`

<figure><img src="../../.gitbook/assets/image (7) (1) (1).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### Close `Fika-Installer` when installation is completed

<figure><img src="../../.gitbook/assets/image (8) (1) (1).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### Start `SPT.Server.exe`

<figure><img src="../../.gitbook/assets/image (10) (1) (1).png" alt=""><figcaption></figcaption></figure>


{% endstep %}

{% step %}
### Wait for `Server has started, happy playing` message in console

<figure><img src="../../.gitbook/assets/image (12) (1) (1).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### Start the headless client using `Fika Headless Manager`

The `Fika Headless Manager` will start your headless client.

<figure><img src="../../.gitbook/assets/image (11) (1) (1).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### Wait for the headless client to load

Two console windows will appear after running the script: the `Fika Headless Manager` and the headless client console. **Do not close them**. Wait for the headless client to load. Activity will stop in the console when loading is completed.

<figure><img src="../../.gitbook/assets/image (14) (1) (1).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### Start `SPT.Launcher` and your game client

The headless client is now ready to host a raid. Start Fika (`SPT.Launcher`) on your computer.&#x20;

**Do NOT start SPT.Launcher.exe on the headless client server!**

<figure><img src="../../.gitbook/assets/image (15) (1) (1).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### Host a raid using the headless client

Navigate the in-game menu like you would normally do to reach the `Raids` menu and click `Host Raid`.

<figure><img src="../../.gitbook/assets/image (16) (1) (1).png" alt=""><figcaption></figcaption></figure>

Check the `Use Headless Host` box and press `Start`. This will request the headless client to start a raid in the selected location. Wait for the headless client to load the raid.

<figure><img src="../../.gitbook/assets/image (17) (1) (1).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### Start the raid when the headless client is ready

Your friend(s) can join the headless client's raid when you see this screen. When everybody has joined, press `Start Raid`.

<figure><img src="../../.gitbook/assets/image (18) (1) (1).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### Done!
{% endstep %}
{% endstepper %}

***

## Modding

The headless client is very sensitive to modding. Do **NOT** install the same mods you use in Fika. Because the headless client is heavily modified, most mods will likely cause crashes or make it unstable.

**✅ YOU CAN INSTALL:**

* AI mods (SAIN)
* Spawn mods (MOAR, DONUTS)
* Mods that specifically mention headless client support (That's Lit, UIFixes, etc.)
* Any mod that reasonably changes in-raid behavior, like entering custom quest zones or having to do with inventory (VCQL, Pack'n'Strap, etc.)

**❌ DO NOT INSTALL:**

* RAM/VRAM cleaner mods (RAM Cleaner, VRAM Cleaner, etc.)
* Performance mods (DeClutter, etc.)
* Any other mods not listed in the **YOU CAN INSTALL** section

***

## Troubleshooting

* If you are crashing or getting errors when joining a headless hosted raid, make sure that Fika is up-to-date for everyone. Verify that you have the latest version of [Fika-Installer](https://github.com/project-fika/Fika-Installer/releases/latest) and use it both in your normal SPT+Fika folder as well as the headless folder to `Update Fika` and `Advanced` -> `Update Fika Headless`.
* If the `Use Headless Host` checkbox is greyed out, it means that the headless client is unavailable. It could be caused by unsupported mods installed in the headless client, networking issues, or other factors. Note that the headless client can only host one raid at a time. Check `BepInEx/LogOutput.log` for errors, especially warnings about incompatible mods.
* If your headless client is failing to load, launch it in Graphics mode by pressing `G` during the startup of `Fika Headless Manager` if possible. If launching in Graphics mode is not possible, look in the `<timestamp> errors.log` in the SPT log folder for hints. Often this is caused by having a malfunctioning or invalid plugin, and sometimes also from missing a plugin that is required by one of the mods on the server.
* See other common issues in [FAQ and Guides](../../faqandguides/) and [Headless Client FAQ and Common Issues](../../faqandguides/headless-client-faq-and-common-issues/)
