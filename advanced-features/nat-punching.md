---
description: Step-by-step process for setting up a dedicated SPT server with NAT punching.
layout:
  width: default
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
  metadata:
    visible: true
---

# NAT Punching

## What is NAT punching?

NAT punching is a networking technique that enables two devices behind separate routers to establish a direct peer-to-peer connection. Each device first communicates with a public server to discover its external network address and then exchanges packets to create valid routing entries on both routers.

It is particularly useful if you are unable to port forward due to ISP restrictions. However, NAT Punching does not work on certain type of routers. For example, symmetrical NAT routers may not be able to achieve NAT Punching.

## Requirements

* The SPT server must be hosted on an externally accessible machine, such as a VPS. For NAT punching to work, a public server must be aware of both clients’ external IP addresses.
* The raid host and players connecting using NAT punching must have a compatible router (Full-cone NAT). You can Google your router model to identify its NAT type.

## Notes

This guide covers the installation process for Windows only. Linux is not covered in this article but the principle is the same. Check out our dedicated Linux channel in our Discord for more information.

## Installation

{% stepper %}
{% step %}
### Set up a public Windows server

A publicly reachable server is required for NAT punching. We recommend renting a cheap Windows VPS to run `SPT Server`. Check out [Lowendbox](https://lowendbox.com/).
{% endstep %}

{% step %}
### Download the latest `SPT` standalone release

Obtain the latest standalone `SPT` release [here](https://github.com/sp-tarkov/build/releases/).
{% endstep %}

{% step %}
### Extract the `SPT` archive in a new empty `SPT` folder

<figure><img src="../.gitbook/assets/image (33).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### Download the latest `Fika-Server` standalone release

Obtain the latest `Fika-Server` standalone release [here](https://github.com/project-fika/Fika-Server-CSharp/releases).
{% endstep %}

{% step %}
### Extract the Fika-Server archive in the root of your `SPT` folder

<figure><img src="../.gitbook/assets/image (34).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### Start `SPT.Server.exe` to generate the Fika configuration file

`SPT.Server.exe` is located inside the `SPT` sub folder of your `SPT` installation folder.

<figure><img src="../.gitbook/assets/image (35).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### Wait for `SPT` server to be fully loaded then close it

Close `SPT` server when you see `Server has started, happy playing`.

<figure><img src="../.gitbook/assets/image (36).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### Enable NAT Punching in Fika

* Navigate to `SPT\user\mods\fika-server\assets\configs`.
* Open `fika.jsonc` with your preferred text editor software (`Notepad++` is recommended).
* Find the `natPunchServer` section and set `enable` to `true`.

<figure><img src="../.gitbook/assets/image (37).png" alt=""><figcaption></figcaption></figure>

* Save and exit the text editor.
{% endstep %}

{% step %}
### Start `SPT.Server.exe`

Validate that the `Nat Punch Server` successfully loaded.

<figure><img src="../.gitbook/assets/image (38).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### Validate your network configuration

Make sure that the following ports are port forwarded and opened in your server firewall:

* TCP 6969 (SPT Server)
* UDP 6790 (Nat Punch Server)
{% endstep %}

{% step %}
### Start `SPT.Launcher` on your computer

We assume you already have a working Fika installation or you know how to set up one. If you don't, click [here](../installing-fika/) for Fika installation steps.
{% endstep %}

{% step %}
### Configure your server IP in `SPT Launcher`

`SPT Launcher` needs to connect to the `SPT` server on your VPS/public server. Press the `Settings` button at the top right corner.

<figure><img src="../.gitbook/assets/image (39).png" alt=""><figcaption></figcaption></figure>

Check `Developer Mode` then enter your server IP address in the URL box. Do not remove `https://`, do not add a slash at the end.&#x20;

Press the arrow key at the top right corner to save your settings.

<figure><img src="../.gitbook/assets/image (40).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### Start the game

<figure><img src="../.gitbook/assets/image (42).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### Enable NAT Punching (raid host only)

This setting indicates that any player connecting to your raid must use NAT punching. It is a client-side setting, meaning it only applies to **you**, the raid host. Other players do **not** need to enable this setting unless they intend to host a raid without port forwarding.

* Press F12 to bring up the configuration manager.
* Check the `Advanced settings` box.
* Check the `Nat Punching` box to enable NAT punching.

<figure><img src="../.gitbook/assets/image (41).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### Host a raid and wait for other players to connect

The `SPT Server` console will display the NAT Punching process for every players that joins your raid.
{% endstep %}

{% step %}
### Start the raid when all players are connected
{% endstep %}
{% endstepper %}
