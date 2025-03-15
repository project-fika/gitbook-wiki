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

# Host using a VPN

A Virtual Private Network (VPN) enables you to join the same network via a public centralized server. You can either set up your own VPN or use a VPN service such as [Radmin VPN](https://www.radmin-vpn.com/), [ZeroTier](https://www.zerotier.com/download/), etc. This method is recommended only as a last resort if you are unable to use any other hosting options.

{% hint style="warning" %}
Free VPNs services are known to cause performance or connectivity problems, so use at your own risk. The officially supported way of playing Fika is with port forwarding. We will not provide support for issues caused by VPN services.\
\
Custom firewalls such as **BitDefender** may also block your connection while playing. Make sure that you allow the connection or temporarily disable it while playing!
{% endhint %}

### Installing the VPN client

* Navigate to the VPN website of your choice and install their client.
* Reboot your computer.
* You might need to create a VPN channel/room that your friends needs to join.
* Take note of your VPN IP (referred to as `your_vpn_ip` below), which is generally shown in the VPN client interface. You will need it in the following steps.

### SPT/Fika configuration

* Navigate to your `<SPT Folder>\SPT_Data\Server\configs` and open `http.json`.
* Change `ip` to `your_vpn_ip`.
* Change `backendIp` to `your_vpn_ip`.
* Save the file and close it.

### Windows Firewall

You will need to configure the Windows Firewall to allow inbound traffic to the port 6969 TCP and 25565 UDP. If you don't know how, you can use [FikaUtils](https://github.com/Lacyway/FikaUtils/releases/latest).

Alternatively, the VPN client may offer a way to open ports in the Windows Firewall. Make sure to double check your VPN client settings.

### Last steps

Launch `SPT.Server.exe`.

If everything is working properly, you should see something similar in the console output:

```
ModLoader: loading: 1 server mods...
Mod: server version: 2.4.0 by: Fika loaded
Server: executing startup callbacks...
Importing database...
Database import finished
Started webserver at https://<your_vpn_ip>:6969
Started websocket at wss://<your_vpn_ip>:6969
Server is running, do not close while playing SPT, Happy playing!!
```

{% hint style="warning" %}
If you see errors (red text) then that means your configuration is invalid or you are unable to host using the configured IP address/port. You may need to create a channel/room first. We recommend visiting the "Troubleshooting" section of the Wiki or join our Discord for assistance.
{% endhint %}

* Launch `SPT.Launcher.exe`.
* Start the game.
* Once you are in the main menu, press `F12` to bring up the configuration manager.
* Find the Force IP and Force Bind IP in the "Fika.Core" section of the configuration manager.
* Set both Force IP and Force Bind IP to your VPN IP. <- THIS IS A VERY IMPORTANT STEP, DO NOT SKIP IT.

<figure><img src="../../.gitbook/assets/forceip.png" alt=""><figcaption></figcaption></figure>

At this point, your server should be accessible to your friends, and you can start playing.

Your friends will need to [install Fika](../) as well and follow the steps to [join a Fika server](../joining-a-fika-server/).

[Click here](../../Playing-Fika.md) to learn how to host a raid.

[Click here](../../fika-configuration/) to learn more about additional Fika configurations.
