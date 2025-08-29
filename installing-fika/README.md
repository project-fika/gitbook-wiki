# Installing Fika

## Before installing Fika

**Always** keep in mind that Fika is an unofficial [SPT](https://sp-tarkov.com/#download) mod. You **must** have a working SPT installation before attempting to install Fika. There is absolutely no point in trying to install Fika before you ensure that SPT is working first.

This means that you must be able to start a game in SPT without any issues, and you should not be running any mods before installing Fika. Please ensure this is the case before continuing with the next steps.

{% hint style="info" %}
If you are unsure how to install SPT, please follow their instructions [here](https://hub.sp-tarkov.com/files/file/672-spt-installer/) and come back here once they are completed. Again, make sure that your SPT installation works before continuing.
{% endhint %}

We recommend reading the [General information](../General-information.md) section so you have a better understanding of how Fika works.

## Prerequisites

* You must have an up-to-date and working installation of [SPT](https://hub.sp-tarkov.com/files/file/672-spt-installer/) **with no mods installed**.
* Bleeding edge versions of SPT are _**NOT**_ supported by Fika.
* Locate your SPT installation folder. This will be referred to as `SPT folder` in the steps below.

## Hardware Requirements

* **CPU**: i7 8700k / Ryzen 5 3600X
* **GPU**: GTX 2070 / RX 5700 XT
* **Memory**: 32 GB RAM
* **Storage**: SSD is mandatory, no support is given for installations on a HDD

The biggest gain in Fika (and in SPT in general) will be getting a stronger CPU and RAM. The AMD X3D series will provide the best performance due to the cache speed.

## Installation

{% stepper %}
{% step %}
### Install [SPT](https://hub.sp-tarkov.com/files/file/672-spt-installer/)

A fresh installation of SPT is **required** before installing Fika.

**Do not install mods yet!**
{% endstep %}

{% step %}
### Download [Fika-Installer](https://github.com/project-fika/Fika-Installer/releases/latest)
{% endstep %}

{% step %}
### Copy `Fika-Installer.exe` inside your SPT folder

<figure><img src="../.gitbook/assets/image (7).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### Start `Fika-Installer.exe`

If you get an admin rights prompt, this is normal. Fika-Installer requires admin rights to set up the firewall rules.
{% endstep %}

{% step %}
### Choose `Install Fika` (option 1)

<figure><img src="../.gitbook/assets/image (7) (1).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### Close `Fika-Installer` when installation is completed

<figure><img src="../.gitbook/assets/image (8).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### Start `SPT.Server.exe`

You should see: `Mod: server version: <Fika version> by: Fika loaded` in the console window.

<figure><img src="../.gitbook/assets/sptserver_loaded_ss.png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### Start `SPT.Launcher.exe`

Create and/or login to your account, then start the game.

<figure><img src="../.gitbook/assets/sptlauncher_ss.png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### Validate that Fika successfully loaded

You should get a Fika disclaimer upon entering the menu. Read the disclaimer and wait until the timer runs out.

<figure><img src="../.gitbook/assets/tos_fika_ss.png" alt="" width="290"><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/fika_mainmenu_version_ss.png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### Exit the game and continue with the next steps
{% endstep %}
{% endstepper %}

## Setting up Fika

In order to host or join a Fika server, you must follow the necessary steps.

[Click here](../hosting-a-fika-server/) if you're hosting a Fika server.

[Click here](../joining-a-fika-server/) if you're joining a Fika server.
