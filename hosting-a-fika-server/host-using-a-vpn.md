---
description: Step-by-step process for hosting a Fika server using a VPN client.
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
### Edit IP and port in Fika config

Find the `server` section. As you make the next two edits, refer to the picture below.

* Change the value of the `ip` field from the default `0.0.0.0` to `your_vpn_ip`. Make sure to write it inside the quotes.
* Change the value of the `backendIp` field from the default  `0.0.0.0` to `your_vpn_ip`. Make sure to write it inside the quotes.

Save and close.

<figure><img src="../.gitbook/assets/image (16).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### Start `SPT.Server`

Wait for `SPT Server` to be fully loaded.

<figure><img src="../.gitbook/assets/image (58).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### Start `SPT.Launcher`

<figure><img src="../.gitbook/assets/https___files.gitbook.com_v0_b_gitbook-x-prod.appspot.com_o_spaces_2FKIBpsnthxy8OSpsWzsDI_2Fuploads_2F89xf4fwAOWUZlYNbpj1u_2Fimage (1).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### Edit the SPT Launcher settings

Click the `Settings` button.

<figure><img src="../.gitbook/assets/https___files.gitbook.com_v0_b_gitbook-x-prod.appspot.com_o_spaces_2FKIBpsnthxy8OSpsWzsDI_2Fuploads_2FqwHM3gxlwjEsrugHTtc0_2Fimage.avif" alt="" width="563"><figcaption></figcaption></figure>

Check the `Developer mode` box.

Enter your VPN address in the URL section. This should be the same URL reported by the server.

<figure><img src="../.gitbook/assets/https___files.gitbook.com_v0_b_gitbook-x-prod.appspot.com_o_spaces_2FKIBpsnthxy8OSpsWzsDI_2Fuploads_2FRJRDafOFXrz8sQBMXNfo_2Fimage.avif" alt="" width="563"><figcaption></figcaption></figure>

{% hint style="warning" %}
DO NOT leave out `https://` and do not add a slash or space at the end. The URL box should look like this: `https://20.21.22.23:6969`.
{% endhint %}
{% endstep %}

{% step %}
### Login to your profile
{% endstep %}

{% step %}
### Start the game

Press the arrow on the right corner. You should now be able to create your profile and log in to the server. Start the game.

<figure><img src="../.gitbook/assets/https___files.gitbook.com_v0_b_gitbook-x-prod.appspot.com_o_spaces_2FKIBpsnthxy8OSpsWzsDI_2Fuploads_2FVhkOgEbLlzyx9kazRxLl_2Fimage.avif" alt="" width="563"><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### Configure Fika to use VPN IP

Press `F12` when in-game to bring up the configuration manager.

Find the `Force IP` and `Force Bind IP` in the `Fika.Core` section of the configuration manager.

Set both `Force IP` and `Force Bind IP` to `your vpn ip`.

<figure><img src="../.gitbook/assets/forceip.png" alt=""><figcaption></figcaption></figure>
{% endstep %}
{% endstepper %}

{% hint style="info" %}
Note: Players willing to host a raid will also need to set the `Force IP` and `Force Bind IP` in their respective Fika configuration.
{% endhint %}

<p align="center"><a href="../testing-connectivity/test-vpn-connectivity/" class="button primary" data-icon="circle-right">I followed all the steps</a></p>
