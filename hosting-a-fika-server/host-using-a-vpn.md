---
description: Step-by-step process for hosting a Fika server using a VPN client.
---

# Host using a VPN

A Virtual Private Network (VPN) enables you to join the same network via a public centralized server. You can either set up your own VPN or use a VPN service such as [Radmin VPN](https://www.radmin-vpn.com/), [ZeroTier](https://www.zerotier.com/download/), etc. This method is recommended only as a last resort if you are unable to use any other hosting options.

{% hint style="warning" %}
Free VPNs services are known to cause performance or connectivity problems, so use at your own risk. The officially supported way of playing Fika is with port forwarding. We will not provide support for issues caused by VPN services.

\
Custom firewalls such as **BitDefender** may also block your connection while playing. Make sure that you allow the connection or temporarily disable it while playing!

You may also experience issues if you are using another VPN service, even if it is disabled. If you have problems, consider uninstalling any other virtual network adapters.
{% endhint %}

### Installing the VPN client

* Navigate to the VPN website of your choice and install their client. Recommended options: [Radmin VPN](https://www.radmin-vpn.com/), [ZeroTier](https://www.zerotier.com/download/). Do not use Hamachi - it's objectively bad.
* Reboot your computer. This is important to ensure that the virtual network adapter is correctly installed.
* You might need to create a VPN channel/room that your friends needs to join. Refer to the VPN client documentation if needed.
* Take note of your VPN IP (referred to as `your_vpn_ip` below), which is generally shown in the VPN client interface. You will need it in the following steps.

### Windows Firewall

Installing Fika using FIka-Installer will automatically configure the Windows firewall.

Alternatively, the VPN client may offer a way to open ports in the Windows Firewall. Make sure to double check your VPN client settings.

### Set your VPN IP in Fika

* Start `SPT.Server.exe` at least once to generate the configuration files, then close it.
* Navigate to `user\mods\fika-server\assets\configs` and open `fika.jsonc`.
* Find the `server` section.
* Change `ip` to `your_vpn_ip`.
* Change `backendIp` to `your_vpn_ip`.
* Save the file and close it.
* Start `SPT.Launcher.exe`.
* Click the "Settings" button.
* Check the `Developer mode` box.
* Enter your VPN address in the URL section. DO NOT leave out `https://` and do not add a slash at the end. The URL box should look like this: `https://20.21.22.23:6969`.
* Press the arrow on the right corner.
* You should now be able to create your profile and log in to the server.
* Start the game.
* Press `F12` when in-game to bring up the configuration manager.
* Find the `Force IP` and `Force Bind IP` in the `Fika.Core` section of the configuration manager.
* Set both Force IP and Force Bind IP to `your_vpn_ip`.

<figure><img src="../.gitbook/assets/forceip.png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
Note: Players willing to host a raid will also need to set the `Force IP` and `Force Bind IP` in their respective Fika configuration.
{% endhint %}

### Testing connectivity

* Start the VPN client.
* Ensure that you created a channel/group in the VPN client.
* Ensure that your friend(s) started the VPN client and joined the channel/group.
* Ask your friend(s) to ping your VPN IP.

If the ping fails then it means that the VPN is not working correctly. Everyone should try rebooting their PC and make sure that everyone joined the same VPN channel/group in the VPN client.&#x20;

Custom firewalls such as `BitDefender` can block VPN communication - try turning it off.

### Hosting a raid

Your Fika instance is now ready to host a raid.

[Click here](../playing-fika.md#hosting-a-raid) to learn how to host a raid.

[Click here](../fika-configuration/) to learn more about additional Fika configurations.
