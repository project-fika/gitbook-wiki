---
description: Step-by-step process for joining a Fika server using a VPN client.
---

# Join using a VPN

## Install the Radmin VPN client

* Navigate to the [Radmin website](https://www.radmin-vpn.com/) and download the Radmin VPN client.
* Run the installer and proceed with the installation steps.
* Reboot your computer. This is important to ensure that the virtual network adapter is correctly installed. **Do not skip this step!**
* Open Radmin VPN client from the taskbar or from the start menu.
* Click `Join network`.

<figure><img src="../.gitbook/assets/image (7).png" alt=""><figcaption></figcaption></figure>

* Enter the network name and password used by the host.

<figure><img src="../.gitbook/assets/image (8).png" alt=""><figcaption></figcaption></figure>

* You should now be able to see the list of connected peers including the host.

<figure><img src="../.gitbook/assets/image (9).png" alt=""><figcaption></figcaption></figure>

* Go to `System` -> `Firewall Exceptions` and click  `Allow All Apps`.

<figure><img src="../.gitbook/assets/image (10).png" alt=""><figcaption></figcaption></figure>

## Testing connectivity

* Right-click the host's name in Radmin and click `Ping`.

<figure><img src="../.gitbook/assets/image (14).png" alt=""><figcaption></figcaption></figure>

* Close the command prompt when ping is successful.

{% hint style="warning" %}
If the ping fails then it means that the VPN is not working correctly. Everyone should try rebooting their PC and make sure that everyone joined the same network in Radmin.

Custom firewalls such as `BitDefender` can block VPN communication - try turning it off.
{% endhint %}

## Ensuring direct connection

It is important to ensure that you are communicating directly with your friend(s) through Radmin for optimal performance.

* Right-click the host's name in Radmin and click `Properties`.

<figure><img src="../.gitbook/assets/https___files.gitbook.com_v0_b_gitbook-x-prod.appspot.com_o_spaces_2FKIBpsnthxy8OSpsWzsDI_2Fuploads_2FzCgqmu3LxK8ZdsRiLKjm_2Fimage.avif" alt=""><figcaption></figcaption></figure>

* Validate that the Channel type is `TCP/out`. This mean you have a direct connection to this peer.

<figure><img src="../.gitbook/assets/https___files.gitbook.com_v0_b_gitbook-x-prod.appspot.com_o_spaces_2FKIBpsnthxy8OSpsWzsDI_2Fuploads_2FcYerBNYv2Eeg8Sz1TYL4_2Fimage.png" alt=""><figcaption></figcaption></figure>

{% hint style="warning" %}
If you see `TCP/relay`, then the communication is relayed through Radmin's servers. The performance will be severely degraded. Try disabling any firewall and/or antivirus in your system and reconnect to the network in Radmin.
{% endhint %}

## Configure SPT Launcher

* Launch `SPT.Launcher`

<figure><img src="../.gitbook/assets/https___files.gitbook.com_v0_b_gitbook-x-prod.appspot.com_o_spaces_2FKIBpsnthxy8OSpsWzsDI_2Fuploads_2F89xf4fwAOWUZlYNbpj1u_2Fimage.png" alt=""><figcaption></figcaption></figure>

* Click the `Settings` button.

<figure><img src="../.gitbook/assets/image (29).png" alt=""><figcaption></figcaption></figure>

* Check the `Developer Mode` box.

<figure><img src="../.gitbook/assets/image (2) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

* Enter the host's VPN address in the URL section. **DO NOT** leave out `https://`, do not forget to append the port `:6969` and do not add a slash at the end. The URL box should look like this: `https://20.21.22.23:6969`.

<figure><img src="../.gitbook/assets/image (5) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

* Press the arrow on the right corner.

<figure><img src="../.gitbook/assets/image (4) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

* You should now be able to create your profile and log in to the server.
* Start the game.

<figure><img src="../.gitbook/assets/https___files.gitbook.com_v0_b_gitbook-x-prod.appspot.com_o_spaces_2FKIBpsnthxy8OSpsWzsDI_2Fuploads_2FVhkOgEbLlzyx9kazRxLl_2Fimage (1).avif" alt=""><figcaption></figcaption></figure>

## Joining a raid

* [Click here](../playing-fika.md#joining-a-raid) to learn how to join a raid.
