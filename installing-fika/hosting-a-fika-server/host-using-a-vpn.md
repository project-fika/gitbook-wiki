# Host using a VPN

A Virtual Private Network (VPN) enables you to join the same network via a public centralized server. You can either set up your own VPN or use a VPN service such as RAdmin, ZeroTier, etc. This method is recommended only as a last resort if you are unable to use any other hosting options.

{% hint style="warning" %}
Free VPNs services are known to cause performance or connectivity problems, so use at your own risk. The officially supported way of playing Fika is with port forwarding. We will not provide support for issues caused by VPN services.
{% endhint %}

### Installing the VPN client

* Navigate to the VPN website and install their client.
* Reboot your computer.
* You might need to create a VPN channel/room that your friends needs to join.
* Take note of your VPN IP (referred to as `your_vpn_ip` below), which is generally shown in the VPS client interface. You will need it in the following steps.

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
Mod: server version: 2.2.8 by: Fika loaded
Server: executing startup callbacks...
Importing database...
Database import finished
Started webserver at http://<your_vpn_ip>:6969
Started websocket at ws://<your_vpn_ip>:6969
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

![](https://github.com/user-attachments/assets/37ebd47c-ec4a-441f-9939-9d5483eec4a9)

At this point, your server should be accessible to your friends, and you can start playing.

Your friends will need to [install Fika](https://github.com/project-fika/Fika-Documentation/wiki/02.-Installing-Fika) as well and follow the steps to [join a Fika server](https://github.com/project-fika/Fika-Documentation/wiki/04.-Joining-a-Fika-server) first.

[Click here](https://github.com/project-fika/Fika-Documentation/wiki/05.-Playing-Fika) to learn how to host a raid.

[Click here](https://github.com/project-fika/Fika-Documentation/wiki/06.-Fika-configuration) to learn more about additional Fika configurations.
