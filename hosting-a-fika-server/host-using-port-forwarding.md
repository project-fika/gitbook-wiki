---
description: Step-by-step process for hosting a Fika server using port forwarding.
---

# Host using port forwarding

Port forwarding is a networking process that allows external devices to access one or multiple ports of a machine within your home network. Port forwarding can be configured through your router's settings interface, which is usually accessible by entering the gateway IP address into a web browser.

{% hint style="warning" %}
Not all Internet Service Providers (ISP) allows port forwarding. If you find yourself unable to port forward, you can use a public VPN service such as Radmin, ZeroTier, etc.). Click [here](host-using-a-vpn.md) to learn how to host using a VPN.
{% endhint %}

## Router configuration

{% hint style="info" %}
We do not provide a step-by-step tutorial for port forwarding because the router settings interface varies between different models and manufacturers. Make sure to research how to achieve port forwarding for your specific router model.

You may be able to find guides for your router on [PortForward.com](https://portforward.com/) or by searching Google.
{% endhint %}

* Go in your router's configuration interface (open browser and type the [gateway IP](https://www.whatismyip.com/finding-your-default-gateway-address/)).
* Access the port forward menu.
* Port forward the following ports to your computer:
  * 6969 TCP (SPT backend server).
  * 25565 UDP (Fika in-game networking).

{% hint style="info" %}
If you are playing on a PC separate from where your `SPT.server.exe` is running, you will need to forward UDP (default of 25565) to the gaming PC, instead of the machine `SPT.server.exe` is running on.
{% endhint %}

## Windows Firewall

Installing Fika using Fika-Installer will automatically configure the Windows firewall.

## Testing connectivity

* Launch `SPT.Server.exe`.

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
If you see errors (red text) then your configuration is invalid or you are unable to host using the configured IP address/port.
{% endhint %}

* Make sure `SPT.Server` is running.
* Obtain your public IP address [here](https://api.ipify.org/).
* Go to an [online port checker](https://portchecker.co).
* Enter your public IP address and port 6969.
* Test the port connectivity.

If the port is closed, you may have an invalid configuration, Windows Firewall blocking the connection or your ISP does not allow port forwarding. Validate all your network settings or host using a [VPN client](host-using-a-vpn.md).

If the port shows as Open, your server is available for connections from friends. You will need to send them your Public IPv4 formatted like `https://your.pub.lic.ip:6969` for them to enter into their Launcher -> Settings -> URL field to connect to your server.

## Hosting a raid

Your Fika instance is now ready to host a raid.

* [Click here](../playing-fika.md#hosting-a-raid) to learn how to host a raid.
* [Click here](../fika-configuration/) to learn more about additional Fika configurations.
