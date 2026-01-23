---
description: Step-by-step process for joining a Fika server using a VPN client.
layout:
  width: default
  title:
    visible: true
  description:
    visible: false
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: false
  metadata:
    visible: false
---

# Connect using a VPN

{% hint style="warning" %}
Free VPNs services are known to cause performance or connectivity problems, so use at your own risk. The officially supported way of playing Fika is with port forwarding. We will not provide support for issues caused by VPN services.

Custom firewalls such as **BitDefender** may also block your connection while playing. Make sure that you allow the connection or temporarily disable it while playing!

You may also experience issues if you are using another VPN service, even if it is disabled. If you have problems, consider uninstalling any other virtual network adapters.
{% endhint %}

{% stepper %}
{% step %}
### Download Radmin client

Navigate to the [Radmin website](https://www.radmin-vpn.com/) and download the Radmin VPN client.
{% endstep %}

{% step %}
### Install Radmin client

Run the installer and proceed with the installation steps.
{% endstep %}

{% step %}
### Reboot your computer

This is important to ensure that the virtual network adapter is correctly installed. **Do not skip this step!**
{% endstep %}

{% step %}
### Open Radmin

Open Radmin VPN client from the taskbar or from the start menu.
{% endstep %}

{% step %}
### Join the server host's Radmin network

Click `Join network`.

<figure><img src="../../.gitbook/assets/image (48).png" alt="" width="243"><figcaption></figcaption></figure>

Enter the network name and password used by the server host.

<figure><img src="../../.gitbook/assets/image (8).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### Validate that you can see server host

You should now be able to see the list of connected peers including the host.

<figure><img src="../../.gitbook/assets/image (9).png" alt="" width="243"><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### Add Radmin to Windows firewall exclusions

Go to `System` -> `Firewall Exceptions` and click  `Allow All Apps`.

<figure><img src="../../.gitbook/assets/image (10).png" alt="" width="243"><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### Start `SPT.Launcher`

<figure><img src="../../.gitbook/assets/https___files.gitbook.com_v0_b_gitbook-x-prod.appspot.com_o_spaces_2FKIBpsnthxy8OSpsWzsDI_2Fuploads_2F89xf4fwAOWUZlYNbpj1u_2Fimage.png" alt="" width="455"><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### Open `SPT Launcher` settings

Click the `Settings` button.

<figure><img src="../../.gitbook/assets/image (29).png" alt="" width="563"><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### Configure the VPN IP in `SPT Launcher`

Check the `Developer Mode` box.

<figure><img src="../../.gitbook/assets/image (2) (1) (1) (1) (1) (1).png" alt="" width="563"><figcaption></figcaption></figure>

Enter the host's VPN address in the URL section. **DO NOT** leave out `https://`, do not forget to append the port `:6969` and do not add a slash at the end. The URL box should look like this: `https://20.21.22.23:6969`.

<figure><img src="../../.gitbook/assets/image (5) (1) (1) (1).png" alt="" width="563"><figcaption></figcaption></figure>

Press the arrow on the right corner.

<figure><img src="../../.gitbook/assets/image (4) (1) (1) (1).png" alt="" width="563"><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### Create your profile


{% endstep %}

{% step %}
### Start the game

<figure><img src="../../.gitbook/assets/https___files.gitbook.com_v0_b_gitbook-x-prod.appspot.com_o_spaces_2FKIBpsnthxy8OSpsWzsDI_2Fuploads_2FVhkOgEbLlzyx9kazRxLl_2Fimage (1).avif" alt="" width="563"><figcaption></figcaption></figure>
{% endstep %}
{% endstepper %}

<p align="center"><a href="ensuring-direct-connection.md" class="button primary" data-icon="circle-right">I confirm I was able to connect to the server</a></p>
