# Getting started

This section is dedicated to setting up Fika for hosting. There are different ways to allow players to join your server. Please read the different sections below to determine which method you will be using.

> [!IMPORTANT]
> Please note that there is some technical knowledge required to achieve this. If you absolutely have no experience, you will have a hard time. Our Discord provides support in such cases.

Before continuing, make sure: 
- You have followed **ALL** the steps in "Installing Fika."
- You can start the game and reach the main menu.
- You can see the Fika watermark in the bottom-left corner.
- You have **NO** other mods than Fika installed.

# Host using port forwarding (preferred)

Port forwarding is a networking process that allows external devices to access services on a private network by redirecting specific communication requests from an external IP address and port to an internal IP address and port. Port forwarding can be configured through your router's settings interface, which is usually accessible by entering the gateway IP address into a web browser.

> [!WARNING]
> We do not provide a step-by-step tutorial for port forwarding because the router settings interface varies between different models and manufacturers. Make sure to research how to achieve port forwarding for your specific router model.

> [!CAUTION]
> Not all ISP allows port forwarding. If you find yourself unable to port forward, you can rent a VPS to host your backend server or alternatively, use a VPN (ZeroTier, Radmin, Playit.gg, etc.). Free VPNs are known to cause performance or connectivity problems, so use at your own risk.

## Router configuration

- Go in your router's configuration interface (open browser and type the [gateway IP](https://www.whatismyip.com/finding-your-default-gateway-address/))
- Access the port forward menu
- Port forward the following ports to your computer:
  - 6969 TCP (SPT backend server)
  - 25565 UDP (Fika in-game networking)

## SPT/Fika configuration

- Navigate to your `<SPT Folder>\SPT_Data\Server\configs` and open `http.json`
- Change `ip` to `0.0.0.0`
- Change `backendIp` to your [WAN IP](https://ipv4.icanhazip.com/)
- Save the file and close it

## Windows Firewall

You will need to configure the Windows Firewall to allow inbound traffic to the 6969 TCP and 25565 UDP ports. If you don't know how, you can use [FikaUtils](https://github.com/Lacyway/FikaUtils/releases/latest).

## Last steps

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

> [!WARNING]
> If you see errors (red text) then that means your configuration is invalid or you are unable to host using the configured IP address/port. We recommend visiting the "Troubleshooting" section of the Wiki or join our Discord for assistance.

**Validate that your server is accessible.** To do this, you can try to access the port 6969 using an [online port checker](https://portchecker.co). Make sure the SPT server is running first before attempting this. If the port is closed, you may have an invalid configuration, Windows Firewall blocking the connection or your ISP does not allow port forwarding. See the Troubleshooting section for more details.

Your friends will need to [install Fika](https://github.com/project-fika/Fika-Documentation/wiki/02.-Installing-Fika) as well and follow the steps to [join a Fika server](https://github.com/project-fika/Fika-Documentation/wiki/04.-Joining-a-Fika-server) first.

[Click here](https://github.com/project-fika/Fika-Documentation/wiki/05.-Playing-Fika) to learn how to host a raid.

[Click here](https://github.com/project-fika/Fika-Documentation/wiki/06.-Fika-configuration) to learn more about additional Fika configurations.

# Host using a VPN
A Virtual Private Network (VPN) enables you to join the same network via a public centralized server. You can either set up your own VPN or use a service like RAdmin, ZeroTier, etc. This method is recommended only as a last resort if you are unable to use any other hosting options.

> [!CAUTION]
> Free VPNs services are known to cause performance or connectivity problems, so use at your own risk. The officially supported way of playing Fika is with port forwarding. We will not provide support for issues caused by VPN services.

## Installing the VPN client

- Navigate to the VPN website and install their client.
- Reboot your computer.
- You might need to create a VPN channel/room that your friends needs to join.
- Take note of your VPN IP (referred to as `your_vpn_ip` below), which is generally shown in the VPS client interface. You will need it in the following steps.

## SPT/Fika configuration

- Navigate to your `<SPT Folder>\SPT_Data\Server\configs` and open `http.json`.
- Change `ip` to `your_vpn_ip`.
- Change `backendIp` to `your_vpn_ip`.
- Save the file and close it.

## Windows Firewall

You will need to configure the Windows Firewall to allow inbound traffic to the port 6969 TCP and 25565 UDP. If you don't know how, you can use [FikaUtils](https://github.com/Lacyway/FikaUtils/releases/latest).

Alternatively, the VPN client may offer a way to open ports in the Windows Firewall. Make sure to double check your VPN client settings.

## Last steps

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

> [!WARNING]
> If you see errors (red text) then that means your configuration is invalid or you are unable to host using the configured IP address/port. You may need to create a channel/room first. We recommend visiting the "Troubleshooting" section of the Wiki or join our Discord for assistance.

- Launch `SPT.Launcher.exe`.
- Start the game.
- Once you are in the main menu, press `F12` to bring up the configuration manager.
- Find the Force IP and Force Bind IP in the "Fika.Core" section of the configuration manager.
- Set both Force IP and Force Bind IP to your VPN IP. <- THIS IS A VERY IMPORTANT STEP, DO NOT SKIP IT.

<img src="https://github.com/user-attachments/assets/37ebd47c-ec4a-441f-9939-9d5483eec4a9"></img>

At this point, your server should be accessible to your friends, and you can start playing.

Your friends will need to [install Fika](https://github.com/project-fika/Fika-Documentation/wiki/02.-Installing-Fika) as well and follow the steps to [join a Fika server](https://github.com/project-fika/Fika-Documentation/wiki/04.-Joining-a-Fika-server) first.

[Click here](https://github.com/project-fika/Fika-Documentation/wiki/05.-Playing-Fika) to learn how to host a raid.

[Click here](https://github.com/project-fika/Fika-Documentation/wiki/06.-Fika-configuration) to learn more about additional Fika configurations.

# Host using Playit.gg

> [!WARNING]
> This is not officially supported by Fika. No support will be provided.

[Playit.gg](https://playit.gg/) is a proxy that makes it possible to host servers without having to port forward, by relaying the game traffic over one of their datacenters. [This guide](https://discuss.playit.gg/t/setup-an-escape-from-tarkov-multiplayer-server-with-spt-fika/3352) will teach you how to use Playit.gg to host a SPT/Fika Server. Editing your http.json is not required.

# Advanced hosting methods

This section is dedicated for advanced users with proper networking knowledge. Do not attempt if you are not an advanced user.

## UPnP
UPnP is a feature that allows Fika to request the router to open ports, specifically the 25565 UDP port (for in-game networking). However, this does not open the 6969 port (SPT server). Therefore, the SPT server must be hosted on a public server (VPS, bare metal, etc). You can then host your raid on your computer and UPnP will open the necessary port for other players to join your raid.

To enable this feature, press the "F12" hotkey while in-game to bring up the configuration manager. Then navigate to Fika.Core, find the UPnP setting and enable it.

## Nat Punching
Nat Punching is a NAT traversal technique used to establish communication between restricted NAT clients. By connecting to a public server, a temporary public port is opened on the client's router. This port will then be shared to all the clients attempting to connect.

This method can only work if your router NAT type is Fullcone and your SPT server is hosted on a public server and reachable by all clients (VPS, bare metal, etc).

More info to come.# Getting started

This section is dedicated to setting up Fika for hosting. There are different ways to allow players to join your server. Please read the different sections below to determine which method you will be using.

> [!IMPORTANT]
> Please note that there is some technical knowledge required to achieve this. If you absolutely have no experience, you will have a hard time. Our Discord provides support in such cases.

Before continuing, make sure: 
- You have followed **ALL** the steps in "Installing Fika."
- You can start the game and reach the main menu.
- You can see the Fika watermark in the bottom-left corner.
- You have **NO** other mods than Fika installed.

# Host using port forwarding (preferred)

Port forwarding is a networking process that allows external devices to access services on a private network by redirecting specific communication requests from an external IP address and port to an internal IP address and port. Port forwarding can be configured through your router's settings interface, which is usually accessible by entering the gateway IP address into a web browser.

> [!WARNING]
> We do not provide a step-by-step tutorial for port forwarding because the router settings interface varies between different models and manufacturers. Make sure to research how to achieve port forwarding for your specific router model.

> [!CAUTION]
> Not all ISP allows port forwarding. If you find yourself unable to port forward, you can rent a VPS to host your backend server or alternatively, use a VPN (ZeroTier, Radmin, Playit.gg, etc.). Free VPNs are known to cause performance or connectivity problems, so use at your own risk.

## Router configuration

- Go in your router's configuration interface (open browser and type the [gateway IP](https://www.whatismyip.com/finding-your-default-gateway-address/))
- Access the port forward menu
- Port forward the following ports to your computer:
  - 6969 TCP (SPT backend server)
  - 25565 UDP (Fika in-game networking)

## SPT/Fika configuration

- Navigate to your `<SPT Folder>\SPT_Data\Server\configs` and open `http.json`
- Change `ip` to `0.0.0.0`
- Change `backendIp` to your [WAN IP](https://ipv4.icanhazip.com/)
- Save the file and close it

## Windows Firewall

You will need to configure the Windows Firewall to allow inbound traffic to the 6969 TCP and 25565 UDP ports. If you don't know how, you can use [FikaUtils](https://github.com/Lacyway/FikaUtils/releases/latest).

## Last steps

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

> [!WARNING]
> If you see errors (red text) then that means your configuration is invalid or you are unable to host using the configured IP address/port. We recommend visiting the "Troubleshooting" section of the Wiki or join our Discord for assistance.

**Validate that your server is accessible.** To do this, you can try to access the port 6969 using an [online port checker](https://portchecker.co). Make sure the SPT server is running first before attempting this. If the port is closed, you may have an invalid configuration, Windows Firewall blocking the connection or your ISP does not allow port forwarding. See the Troubleshooting section for more details.

Your friends will need to [install Fika](https://github.com/project-fika/Fika-Documentation/wiki/02.-Installing-Fika) as well and follow the steps to [join a Fika server](https://github.com/project-fika/Fika-Documentation/wiki/04.-Joining-a-Fika-server) first.

[Click here](https://github.com/project-fika/Fika-Documentation/wiki/05.-Playing-Fika) to learn how to host a raid.

[Click here](https://github.com/project-fika/Fika-Documentation/wiki/06.-Fika-configuration) to learn more about additional Fika configurations.

# Host using a VPN
A Virtual Private Network (VPN) enables you to join the same network via a public centralized server. You can either set up your own VPN or use a service like RAdmin, ZeroTier, etc. This method is recommended only as a last resort if you are unable to use any other hosting options.

> [!CAUTION]
> Free VPNs services are known to cause performance or connectivity problems, so use at your own risk. The officially supported way of playing Fika is with port forwarding. We will not provide support for issues caused by VPN services.

## Installing the VPN client

- Navigate to the VPN website and install their client.
- Reboot your computer.
- You might need to create a VPN channel/room that your friends needs to join.
- Take note of your VPN IP (referred to as `your_vpn_ip` below), which is generally shown in the VPS client interface. You will need it in the following steps.

## SPT/Fika configuration

- Navigate to your `<SPT Folder>\SPT_Data\Server\configs` and open `http.json`.
- Change `ip` to `your_vpn_ip`.
- Change `backendIp` to `your_vpn_ip`.
- Save the file and close it.

## Windows Firewall

You will need to configure the Windows Firewall to allow inbound traffic to the port 6969 TCP and 25565 UDP. If you don't know how, you can use [FikaUtils](https://github.com/Lacyway/FikaUtils/releases/latest).

Alternatively, the VPN client may offer a way to open ports in the Windows Firewall. Make sure to double check your VPN client settings.

## Last steps

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

> [!WARNING]
> If you see errors (red text) then that means your configuration is invalid or you are unable to host using the configured IP address/port. You may need to create a channel/room first. We recommend visiting the "Troubleshooting" section of the Wiki or join our Discord for assistance.

- Launch `SPT.Launcher.exe`.
- Start the game.
- Once you are in the main menu, press `F12` to bring up the configuration manager.
- Find the Force IP and Force Bind IP in the "Fika.Core" section of the configuration manager.
- Set both Force IP and Force Bind IP to your VPN IP. <- THIS IS A VERY IMPORTANT STEP, DO NOT SKIP IT.

<img src="https://github.com/user-attachments/assets/37ebd47c-ec4a-441f-9939-9d5483eec4a9"></img>

At this point, your server should be accessible to your friends, and you can start playing.

Your friends will need to [install Fika](https://github.com/project-fika/Fika-Documentation/wiki/02.-Installing-Fika) as well and follow the steps to [join a Fika server](https://github.com/project-fika/Fika-Documentation/wiki/04.-Joining-a-Fika-server) first.

[Click here](https://github.com/project-fika/Fika-Documentation/wiki/05.-Playing-Fika) to learn how to host a raid.

[Click here](https://github.com/project-fika/Fika-Documentation/wiki/06.-Fika-configuration) to learn more about additional Fika configurations.

# Host over LAN
Playing over LAN allows you to play with someone in the same house without any real port forwarding other than allowing the application in your local firewall. You can get your LAN IP by opening `cmd` and typing `ipconfig`. Your LAN address is usually the **IPv4 address** returned, e.g. `192.168.1.150`.

## SPT/Fika configuration

- Navigate to your `<SPT Folder>\SPT_Data\Server\configs` and open `http.json`.
- Change `ip` to `your_lan_ip`.
- Change `backendIp` to `your_lan_ip`.
- Save the file and close it.

## Windows Firewall

You will need to configure the Windows Firewall to allow inbound traffic to the port 6969 TCP and 25565 UDP. If you don't know how, you can use [FikaUtils](https://github.com/Lacyway/FikaUtils/releases/latest).

## Last steps

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

> [!WARNING]
> If you see errors (red text) then that means your configuration is invalid or you are unable to host using the configured IP address/port.

- Launch `SPT.Launcher.exe`.
- Start the game.
- Once you are in the main menu, press `F12` to bring up the configuration manager.
- Find the Force IP and Force Bind IP in the "Fika.Core" section of the configuration manager.
- Set both Force IP and Force Bind IP to your LAN IP. <- THIS IS A VERY IMPORTANT STEP, DO NOT SKIP IT.

<img src="https://github.com/user-attachments/assets/37ebd47c-ec4a-441f-9939-9d5483eec4a9"></img>

At this point, your server should be accessible to your friends, and you can start playing.

Your friends will need to [install Fika](https://github.com/project-fika/Fika-Documentation/wiki/02.-Installing-Fika) as well and follow the steps to [join a Fika server](https://github.com/project-fika/Fika-Documentation/wiki/04.-Joining-a-Fika-server) first.

[Click here](https://github.com/project-fika/Fika-Documentation/wiki/05.-Playing-Fika) to learn how to host a raid.

[Click here](https://github.com/project-fika/Fika-Documentation/wiki/06.-Fika-configuration) to learn more about additional Fika configurations.

# Host using Playit.gg

> [!WARNING]
> This is not officially supported by Fika. No support will be provided.

[Playit.gg](https://playit.gg/) is a proxy that makes it possible to host servers without having to port forward, by relaying the game traffic over one of their datacenters. [This guide](https://discuss.playit.gg/t/setup-an-escape-from-tarkov-multiplayer-server-with-spt-fika/3352) will teach you how to use Playit.gg to host a SPT/Fika Server. Editing your http.json is not required.

# Advanced hosting methods

This section is dedicated for advanced users with proper networking knowledge. Do not attempt if you are not an advanced user.

## UPnP
UPnP is a feature that allows Fika to request the router to open ports, specifically the 25565 UDP port (for in-game networking). However, this does not open the 6969 port (SPT server). Therefore, the SPT server must be hosted on a public server (VPS, bare metal, etc). You can then host your raid on your computer and UPnP will open the necessary port for other players to join your raid.

To enable this feature, press the "F12" hotkey while in-game to bring up the configuration manager. Then navigate to Fika.Core, find the UPnP setting and enable it.

## Nat Punching
Nat Punching is a NAT traversal technique used to establish communication between restricted NAT clients. By connecting to a public server, a temporary public port is opened on the client's router. This port will then be shared to all the clients attempting to connect.

This method can only work if your router NAT type is Fullcone and your SPT server is hosted on a public server and reachable by all clients (VPS, bare metal, etc).

More info to come.