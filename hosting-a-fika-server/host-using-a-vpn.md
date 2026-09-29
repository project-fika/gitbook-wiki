---
description: Step-by-step process for hosting a Fika server using a VPN client.
layout:
  width: default
  title:
    visible: true
  description:
    visible: false
  tableOfContents:
    visible: true
  outline:
    visible: false
  pagination:
    visible: false
  metadata:
    visible: false
  tags:
    visible: true
  actions:
    visible: true
  anchors:
    visible: false
---

# Host using a VPN

{% hint style="warning" %}
**WARNING**

Free VPNs services are known to cause performance or connectivity problems, so <mark style="color:$warning;">use at your own risk</mark>.&#x20;

The officially supported way of playing Fika is with port forwarding. We will not provide support for issues caused by VPN services.

Custom firewalls such as **BitDefender** may also block your connection while playing. Make sure that you allow the connection or temporarily disable it while playing!

You may also experience issues if you are using another VPN service, even if it is disabled. If you have problems, consider uninstalling any other virtual network adapters.
{% endhint %}

{% stepper %}
{% step %}
### Download Radmin

Navigate to the [Radmin website](https://www.radmin-vpn.com/) and download the Radmin VPN client.
{% endstep %}

{% step %}
### Install Radmin

Run the installer and proceed with the installation steps.
{% endstep %}

{% step %}
### Reboot your computer

This is important to ensure that the virtual network adapter is correctly installed. **Do not skip this step!**
{% endstep %}

{% step %}
### Create a network in Radmin

Open Radmin VPN client (from the taskbar or from the start menu) an Click `Create network`.

<figure><img src="../.gitbook/assets/image (2).png" alt=""><figcaption></figcaption></figure>

Enter a network name and a password. Make sure to note the network name and password, you will need to share it with your friends.

<figure><img src="../.gitbook/assets/image (1) (1).png" alt=""><figcaption></figcaption></figure>


{% endstep %}

{% step %}
### Add Radmin to Windows firewall exclusions

Go to `System` -> `Firewall Exceptions` and click  `Allow All Apps`.

<figure><img src="../.gitbook/assets/image (3).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### Start `SPT.Server` to generate the config file

Wait for `SPT Server` to be fully loaded.

<figure><img src="../.gitbook/assets/https___files.gitbook.com_v0_b_gitbook-x-prod.appspot.com_o_spaces_2FKIBpsnthxy8OSpsWzsDI_2Fuploads_2FlZfa6hVfcUTBztlqMtZ7_2Fhttps___files.gitbook.com_v0_b_gitbook-x-prod.appspot.com_o_spaces_2FKIBpsnthxy8OSpsWzs.png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### Close `SPT.Server`
{% endstep %}

{% step %}
### Open Fika config in editor

Navigate to `<SPT install>\SPT\user\mods\fika-server\assets\configs`.

Open `fika.jsonc` with your preferred text editor (Notepad++ is recommended).


{% endstep %}

{% step %}
### Start `SPT.Server`

Wait for `SPT Server` to be fully loaded.

<div align="left"><figure><img src="../.gitbook/assets/2026-09-29 13-56-42.png" alt=""><figcaption></figcaption></figure></div>
{% endstep %}

{% step %}
### Start `SPT.Launcher`

<figure><img src="../.gitbook/assets/https___files.gitbook.com_v0_b_gitbook-x-prod.appspot.com_o_spaces_2FKIBpsnthxy8OSpsWzsDI_2Fuploads_2F89xf4fwAOWUZlYNbpj1u_2Fimage (1).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### Edit the SPT Launcher settings

Click `Add New Server`

<figure><img src="../.gitbook/assets/2026-09-29 13-57-33.png" alt=""><figcaption></figcaption></figure>

Pick a name for your server and then in the address write `127.0.0.1:6969`

<figure><img src="../.gitbook/assets/2026-09-29 13-59-06.png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### Login to your profile
{% endstep %}

{% step %}
### Start the game

Press the arrow on the right corner. You should now be able to create your profile and log in to the server. Start the game.

<figure><img src="../.gitbook/assets/2026-09-29 13-54-06.png" alt=""><figcaption></figcaption></figure>
{% endstep %}
{% endstepper %}

<p align="center"><a href="../testing-connectivity/test-vpn-connectivity/" class="button primary" data-icon="circle-right">I followed all the steps</a></p>
