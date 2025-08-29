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
* You might need to create a VPN channel/room that your friends needs to join. Refer to the VPN client documentation if needed.
* Take note of your VPN IP (referred to as `your_vpn_ip` below), which is generally shown in the VPN client interface. You will need it in the following steps.

### SPT/Fika configuration

* Start the **SPT.Server** at least once to generate the configuration files
* Navigate to your `user\mods\fika-server\assets\configs` and open `fika.jsonc`
* Navigate to the `server` section
* Change `ip` to `your_vpn_ip`.
* Change `backendIp` to `your_vpn_ip`.
* Save the file and close it.

### Windows Firewall

Installing Fika using FIka-Installer will automatically configure the Windows firewall.

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
* Click the "Settings" button.
* Click "Developer mode"
* Enter the server's **VPN address** in the URL section. DO NOT leave out `https://` and do not add a slash at the end.
* The URL box should look like this: `https://20.21.22.23:6969`.
* Press the arrow on the right corner.
* You should now be able to create your profile and log in to the server.
* Start the game.
* Once you are in the main menu, press `F12` to bring up the configuration manager.
* Find the Force IP and Force Bind IP in the "Fika.Core" section of the configuration manager.
* Set both Force IP and Force Bind IP to your VPN IP.

<figure><img src="../.gitbook/assets/forceip.png" alt=""><figcaption></figcaption></figure>

### Testing connectivity

* Ensure that you created a channel/group in the VPN client
* Ensure that your friend(s) have joined the channel/group in the VPN client
* Ask your friend(s) to ping your VPN IP

If the ping fails then it means that the VPN is not working correctly. Reboot your PC (including your friend(s), validate your VPN settings and ensure you all joined the same VPN channel/group in the VPN client. Custom firewalls such as BitDefender can block VPN communication - try turning it off.

### Hosting a raid

Your Fika instance is now ready to host a raid.

[Click here](../playing-fika.md#hosting-a-raid) to learn how to host a raid.

[Click here](../fika-configuration/) to learn more about additional Fika configurations.
