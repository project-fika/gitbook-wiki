# Host using port forwarding

Port forwarding is a networking process that allows external devices to access services on a private network by redirecting specific communication requests from an external IP address and port to an internal IP address and port. Port forwarding can be configured through your router's settings interface, which is usually accessible by entering the gateway IP address into a web browser.

{% hint style="info" %}
We do not provide a step-by-step tutorial for port forwarding because the router settings interface varies between different models and manufacturers. Make sure to research how to achieve port forwarding for your specific router model.
{% endhint %}

{% hint style="warning" %}
Not all ISP allows port forwarding. If you find yourself unable to port forward, you can rent a VPS to host your backend server or alternatively, use a VPN (ZeroTier, Radmin, Playit.gg, etc.). Free VPNs are known to cause performance or connectivity problems, so use at your own risk.
{% endhint %}

### Router configuration

* Go in your router's configuration interface (open browser and type the [gateway IP](https://www.whatismyip.com/finding-your-default-gateway-address/))
* Access the port forward menu
* Port forward the following ports to your computer:
  * 6969 TCP (SPT backend server)
  * 25565 UDP (Fika in-game networking)

### SPT/Fika configuration

* Navigate to your `<SPT Folder>\SPT_Data\Server\configs` and open `http.json`
* Change `ip` to `0.0.0.0`
* Change `backendIp` to your [WAN IP](https://ipv4.icanhazip.com/)
* Save the file and close it

### Windows Firewall

You will need to configure the Windows Firewall to allow inbound traffic to the 6969 TCP and 25565 UDP ports. If you don't know how, you can use [FikaUtils](https://github.com/Lacyway/FikaUtils/releases/latest).

### Last steps

Launch `SPT.Server.exe`.

If everything is working properly, you should see something similar in the console output:

```
ModLoader: loading: 1 server mods...
Mod: server version: 2.2.8 by: Fika loaded
Server: executing startup callbacks...
Importing database...
Database import finished
Started webserver at http://0.0.0.0:6969
Started websocket at ws://0.0.0.0:6969
Server is running, do not close while playing SPT, Happy playing!!
```

{% hint style="warning" %}
If you see errors (red text) then that means your configuration is invalid or you are unable to host using the configured IP address/port. We recommend visiting the "Troubleshooting" section of the Wiki or join our Discord for assistance.
{% endhint %}

**Validate that your server is accessible.** To do this, you can try to access the port 6969 using an [online port checker](https://portchecker.co). Make sure the SPT server is running first before attempting this. If the port is closed, you may have an invalid configuration, Windows Firewall blocking the connection or your ISP does not allow port forwarding. See the Troubleshooting section for more details.

Your friends will need to [install Fika](https://github.com/project-fika/Fika-Documentation/wiki/02.-Installing-Fika) as well and follow the steps to [join a Fika server](https://github.com/project-fika/Fika-Documentation/wiki/04.-Joining-a-Fika-server) first.

[Click here](https://github.com/project-fika/Fika-Documentation/wiki/05.-Playing-Fika) to learn how to host a raid.

[Click here](https://github.com/project-fika/Fika-Documentation/wiki/06.-Fika-configuration) to learn more about additional Fika configurations.
