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

# Host using port forwarding

Port forwarding is a networking process that allows external devices to access services on a private network by redirecting specific communication requests from an external IP address and port to an internal IP address and port. Port forwarding can be configured through your router's settings interface, which is usually accessible by entering the gateway IP address into a web browser.

{% hint style="info" %}
We do not provide a step-by-step tutorial for port forwarding because the router settings interface varies between different models and manufacturers. Make sure to research how to achieve port forwarding for your specific router model.
{% endhint %}

{% hint style="warning" %}
Not all Internet Service Providers (ISP) allows port forwarding. If you find yourself unable to port forward, you can use a public VPN service such as ZeroTier, Radmin, Playit.gg, etc.).&#x20;

Free VPNs are known to cause performance or connectivity problems, so use at your own risk. Click [here](host-using-a-vpn.md) to learn how to host using a VPN.
{% endhint %}

### Router configuration

* Go in your router's configuration interface (open browser and type the [gateway IP](https://www.whatismyip.com/finding-your-default-gateway-address/))
* Access the port forward menu
* Port forward the following ports to your computer:
  * 6969 TCP (SPT backend server)
  * 25565 UDP (Fika in-game networking)

### SPT/Fika configuration

* Start the **SPT.Server** at least once to generate the configuration files
* Navigate to your `user\mods\fika-server\assets\configs` and open `fika.jsonc`
* Navigate to the `server` section
* Change `ip` to `0.0.0.0`
* Change `backendIp` to `0.0.0.0` (use your [WAN IP](https://www.whatismyip.com/) instead if you are having issues)
* Save the file and close it

### Windows Firewall

You will need to configure the Windows Firewall to allow inbound traffic to the 6969 TCP and 25565 UDP ports. If you don't know how, you can use [FikaUtils](https://github.com/Lacyway/FikaUtils/releases/latest).

### Last steps

Launch `SPT.Server.exe`.

If everything is working properly, you should see something similar in the console output:

```
ModLoader: loading: 1 server mods...
Mod: server version: 2.4.0 by: Fika loaded
Server: executing startup callbacks...
Importing database...
Database import finished
Started webserver at https://0.0.0.0:6969
Started websocket at wss://0.0.0.0:6969
Server is running, do not close while playing SPT, Happy playing!!
```

{% hint style="warning" %}
If you see errors (red text) then that means your configuration is invalid or you are unable to host using the configured IP address/port. We recommend visiting the "Troubleshooting" section of the Wiki or join our Discord for assistance.
{% endhint %}

**Validate that your server is accessible.** To do this, you can try to access the port 6969 using an [online port checker](https://portchecker.co). Make sure the SPT server is running first before attempting this. If the port is closed, you may have an invalid configuration, Windows Firewall blocking the connection or your ISP does not allow port forwarding. See the Troubleshooting section for more details.

Your friends will need to [install Fika](../installing-fika/) as well and follow the steps to [join a Fika server](../joining-a-fika-server/).

[Click here](../playing-fika.md#hosting-a-raid) to learn how to host a raid.

[Click here](../fika-configuration/) to learn more about additional Fika configurations.
