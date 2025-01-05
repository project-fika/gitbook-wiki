# Host over LAN

Hosting over LAN allows you to play with someone in the same house/network without internet access and without any real port forwarding other than allowing the application in your local firewall. You can get your LAN IP by opening `cmd` and typing `ipconfig`. Your LAN address is usually the **IPv4 address** returned, e.g. `192.168.1.150`.

### SPT/Fika configuration

* Navigate to your `<SPT Folder>\SPT_Data\Server\configs` and open `http.json`.
* Change `ip` to `your_lan_ip`.
* Change `backendIp` to `your_lan_ip`.
* Save the file and close it.

### Windows Firewall

You will need to configure the Windows Firewall to allow inbound traffic to the port 6969 TCP and 25565 UDP. If you don't know how, you can use [FikaUtils](https://github.com/Lacyway/FikaUtils/releases/latest).

### Last steps

Launch `SPT.Server.exe`.

If everything is working properly, you should see something similar in the console output:

```
ModLoader: loading: 1 server mods...
Mod: server version: 2.2.8 by: Fika loaded
Server: executing startup callbacks...
Importing database...
Database import finished
Started webserver at http://<your_lan_ip>:6969
Started websocket at ws://<your_lan_ip>:6969
Server is running, do not close while playing SPT, Happy playing!!
```

{% hint style="warning" %}
If you see errors (red text) then that means your configuration is invalid or you are unable to host using the configured IP address/port.
{% endhint %}

* Launch `SPT.Launcher.exe`.
* Start the game.
* Once you are in the main menu, press `F12` to bring up the configuration manager.
* Find the Force IP and Force Bind IP in the "Fika.Core" section of the configuration manager.
* Set both Force IP and Force Bind IP to your LAN IP. <- THIS IS A VERY IMPORTANT STEP, DO NOT SKIP IT.

![](https://github.com/user-attachments/assets/37ebd47c-ec4a-441f-9939-9d5483eec4a9)

At this point, your server should be accessible to your friends, and you can start playing.

Your friends will need to [install Fika](https://github.com/project-fika/Fika-Documentation/wiki/02.-Installing-Fika) as well and follow the steps to [join a Fika server](https://github.com/project-fika/Fika-Documentation/wiki/04.-Joining-a-Fika-server) first.

[Click here](../../Playing-Fika.md#hosting-a-raid) to learn how to host a raid.

[Click here](../../fika-configuration/) to learn more about additional Fika configurations.
