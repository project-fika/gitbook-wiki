# Headless client

The headless client is an exclusive Fika feature that allows you to host a raid on a separate Escape From Tarkov instance. You are able to offload the AI calculation and other resource-intensive task to improve game play performance. FPS gains are usually around 25% to 50% depending on your computer specifications and amount of bots in the game.

{% hint style="warning" %}
Please note that there is some technical knowledge required to achieve this. If you absolutely have no experience, you will have a hard time.
{% endhint %}

### Specifications

* The headless client is basically another Fika instance that will automatically host raids. All players becomes clients (including the player host).
* Graphic rendering is disabled to make the headless client as lightweight as possible. However, the headless client is **NOT** a true headless headless server. It still requires all the game files and a pretty hefty amount of RAM to work (especially for bigger maps such as Streets or Lighthouse).
* It is recommended to run the headless client on a separate physical machine. The headless client will NOT work on a VPS. If you really wish to use a paid host, rent a dedicated server.
* A graphic card is NOT required to run the headless client, however it is helpful for configuring mods.

### Recommended hardware requirements

* A modern CPU with at least 4 cores @ 4GHz+.
* 32 GB RAM (16 GB can work but will provide reduced performance due to virtual paging).
* 50 GB disk space with SSD/NVME drive. HDD is NOT supported.

### Notes

* The installation process below will guide you through the steps to set up the SPT server and headless client on the same machine. It is possible to separate the SPT server and the headless client, but there is no performance benefit, and the steps are more involved. Therefore, this setup will not be covered in this guide.
* Linux is NOT supported and covered by this article. Visit the dedicated Linux channel in our Discord for assistance.

### Installation

{% stepper %}
{% step %}
### Install Escape From Tarkov using BSG Launcher

Escape From Tarkov must be installed on the server where you are planning to install the headless client. This is required to ensure that you own the game.
{% endstep %}

{% step %}
### Install [SPT](https://hub.sp-tarkov.com/files/file/672-spt-installer/)

If your SPT server is currently located on a different machine, please copy it to the server where you are planning to install the headless client. It must contain the full game. If you are unable to copy it due to the size, install SPT on the server using the [SPT Installer](https://hub.sp-tarkov.com/files/file/672-spt-installer/) instead.

**Do NOT install SPT in your official Escape From Tarkov folder!**
{% endstep %}

{% step %}
### Download [Fika-Installer](https://github.com/project-fika/Fika-Installer/releases/latest)
{% endstep %}

{% step %}
### Copy `Fika-Installer.exe` inside the `SPT folder`

<figure><img src="../.gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### Run `Fika-Installer.exe`

If you get an admin rights prompt, this is normal. Fika-Installer requires admin rights to set up the firewall rules.
{% endstep %}

{% step %}
### Choose `Install Fika` (option 1)

<figure><img src="../.gitbook/assets/image (7).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### Go back to the main menu when installation is completed

<figure><img src="../.gitbook/assets/image (8).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### Choose `Advanced options` (option 2)

<figure><img src="../.gitbook/assets/image (9).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### Choose `Install Fika Headless` (option 1)

<figure><img src="../.gitbook/assets/image (10).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### Choose `Create a new headless profile`

<figure><img src="../.gitbook/assets/image (11).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### Close `Fika-Installer` when installation is completed

<figure><img src="../.gitbook/assets/image (12).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### Start `SPT.Server.exe`

<figure><img src="../.gitbook/assets/image (13).png" alt=""><figcaption></figcaption></figure>

Wait for "Server is running, happy playing" message in the console.

<figure><img src="../.gitbook/assets/image (14).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### Right-click `Start_headless_xxx.ps1` and click `Run with Powershell`

<figure><img src="../.gitbook/assets/image (16).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (15).png" alt=""><figcaption></figcaption></figure>

{% hint style="warning" %}
**WARNING**

If the PowerShell window briefly appears and then disappears then your **ExecutionPolicy** might be set to **Restricted**. This should be **RemoteSigned** by default but used to be **Restricted**, so if your Windows installation is not recent or you do not have PowerShell updated it will be set to **Restricted**.

To update your execution policy, open a PowerShell window and write:

```powershell
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser
```

Once done, press **ENTER** and close the window. You can read more about Execution Policies [here](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_execution_policies?view=powershell-7.5).
{% endhint %}
{% endstep %}

{% step %}
### Fika Headless Watcher will automatically start the headless client

There will be two console windows: the Fika Headless Watcher and the headless client console. Do not close them. Wait for the headless client to load. Activity will stop in the console when loading is completed.

<figure><img src="../.gitbook/assets/image (17).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### Start Fika on your computer

The headless client is now ready to host a raid. Start Fika (SPT.Launcher) on your computer.&#x20;

**Do NOT start SPT.Launcher.exe on the headless client server!**

<figure><img src="../.gitbook/assets/image (18).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### Click `Host Raid`, check `Use headless host` and click `Start Raid`

This will request the headless client to start a raid in the selected location. Please wait for the headless client to load the raid.

<figure><img src="../.gitbook/assets/image (19).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (20).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### Your friend(s) can join when the raid is initialized

Your friend(s) can join the headless client's raid when you see this screen. When everybody has joined, press `Start Raid`.

<figure><img src="../.gitbook/assets/image (21).png" alt=""><figcaption></figcaption></figure>
{% endstep %}
{% endstepper %}

### Additional information

{% hint style="danger" %}
**NOTICE**

The headless client does not need to have the same client mods as the players (clients). The only exceptions to this rule are **AI mods (SAIN)**, **spawn mods (MOAR, DONUTS)** and mods that have **implemented synchronization with Fika (That's Lit, UIFixes)**. Always make sure to look at the SPT mod page or the mod's thread in our Discord to confirm if you should install the mod on your headless client.

Using mods that are designed for game play experience on the headless **will** cause issues with the headless client. The headless client does not function the same way as a normal Fika instance and will cause issues with the mods. A few notable examples: **Amanda.Graphics**, **MoreCheckmarks**, **EFTApi**, **GamePanelHud**, **DynamicMaps**, **LootValue**, **Ram Cleaner Interval**, **DeClutter**, etc.
{% endhint %}

* If the `Use headless host` check box is greyed out, the headless client was unable to connect to your SPT server OR the headless client is already hosting a raid.
* Troubleshoot connectivity issues the same way you would do for a normal Fika instance.
