---
description: >-
  This page will describe how Fika facilitates clients connecting to the raid
  host. This may help troubleshooting issues if you have a non-standard network
  setup (proxy, tunnels, ddns, docker, etc).
layout:
  width: default
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
  metadata:
    visible: true
---

# ADVANCED: How Fika Establishes Raid Connections

{% hint style="warning" %}
This article is intended for Advanced Users who have a non-standard network setup. Whereas it may be interesting for others, if you have a simple network you may be better off just following the [hosting instructions](../hosting-a-fika-server/choose-your-hosting-method.md) and not worrying about the inner-workings of Fika. If port forwarding isn't working, use a [VPN like Radmin](../hosting-a-fika-server/host-using-a-vpn.md).
{% endhint %}

### Definition of Terms

* **SPT Server / backend server**
  * SPT Server or backend server refers to `SPT.Server.exe` which handles synchronizing profiles and stash management. It is modified by the fika-server mod to allow for players to host and join raids.
* **fika-server mod**
  * This is a modification of the backend server that allows for hosted raids to populate in a list and be joinable by clients. It forwards information about connection methods from the raid host to joining clients.
* **Fika client plugin**
  * The client plugin is a BepInEx plugin in the form of a .dll file that lives in `BepInEx\plugins\Fika\` and hosts the networking functionality for the raid. It is what listens for connections for the raid host or establishes a connection for a joining client. When you are changing settings in the F12 configuration menu, you are changing settings for the cilent plugin.
* **Plugin configuration**
  * This is the list of settings that can be changed in the BepInEx Configuration Manager, often accessed by pressing F12 inside your gaming client. These values can also be modified by opening `BepInEx/config/com.fika.core.cfg` in a text editor and editing the values directly.

## Fika Network Workflow

### How the Raid is Advertised to Clients

When the raid host starts setting up a raid for others to connect, it first looks in the `Force IP` field for the client plugin configuration for the client that is to be the host. If that field is populated, it stores that IP in memory, hereafter referred to as `IP_1`. If the `Force IP` field is blank, the plugin will attempt to resolve the Public/WAN IP by querying (at the time of writing) three IP resolution services and then it stores the Public IP as `IP_1`.

The client plugin will also query local network adapter(s) and store a LAN IP (generally `192.168.x.x` or `10.0.x.x`) as `IP_2`. If the PC where this is happening has multiple local network adapters then you may experience connection issues if someone is trying to connect via the same network.

{% hint style="info" %}
For instance, if the PC has both an ethernet connection and a Wi-Fi connection, with both enabled and connected, the client plugin may record the wrong LAN IP. It is important that the PC has only one active LAN adapter for things to work correctly in all cases.
{% endhint %}

Then the client plugin will look at the `Port` field in the plugin configuration and record that to memory.

Next, the client plugin will look at the `Force Bind IP` field. If that field has a value other than 'Disabled', it will start listening for connections on the adapter related to the IP selected.

* For `0.0.0.0` it will listen to connections that come from anywhere. This is also the behavior if `Force Bind IP` is set to 'Disabled'.
* For a specific IP, like `192.168.x.x` or `26.x.x.x`, it will listen for connections that only come from that network adapter. This is generally only used when a VPN network adapter is utilized, otherwise `0.0.0.0` is preferred.

Once all of the values have been recorded to memory, the client plugin will attempt to establish a service that listens for incoming connections. Then the plugin will send a list of available IP:Port combinations to the fika-server mod so that the backend server can forward that information to any other client that may want to connect. The list will look like:

* `IP_1:Port` - This is generally either the value in `Force IP` or your Public/WAN IP + Port from plugin configuration
* `IP_2:Port` - This is your LAN IP + Port from plugin configuration

{% hint style="danger" %}
None of the settings in Fika.Core -> Network affect the client that is **joining** the raid. They only affect the raid host.
{% endhint %}

### How a Client Connects to an Advertised Raid

When a client navigates to the raid screen and clicks the `JOIN` button on a particular raid in the list of available raids, the backend server forwards the information discussed above to the joining client's Fika plugin, which includes a list of IP:Port combinations to which they will attempt to connect.

The connecting client will then attempt to connect to `IP_1:Port` and `IP_2:Port` in series. If neither works, an error will be displayed suggesting to confirm that all ports are open and incoming connections are allowed by the raid host.

{% hint style="info" %}
Note: a **direct connection** between game clients is being established, not a connection that is routed through the backend server. If the path of the direct connection is obstructed or unavailable it will fail, even if both clients are able to connect to the backend server.
{% endhint %}

### Further Troubleshooting

If you or a friend are still getting errors when attempting to join a raid, you should open the Player.log of the person getting the error and look for which IPs are being sent to them. Player.log can be found at the location below, and the picture below that shows an example of the log lines for which you are looking.

```
C:\Users\YOURUSERNAME\AppData\LocalLow\Battlestate Games\EscapeFromTarkov\
```

<figure><img src="../.gitbook/assets/image (56).png" alt=""><figcaption></figcaption></figure>

The two IPs listed will be `IP_1` and `IP_2` from the [Fika Network Workflow](advanced-how-fika-establishes-raid-connections.md#fika-network-workflow) section.

## Why This Matters

This is very different from the way most 'dedicated server' game hosting scenarios play out. If you've ever hosted another game server — like Minecraft or Valheim or ARK or Palworld or 7D2D — you may be surprised to learn that Fika hosting is completely different, and thus nearly all of the knowledge you've acquired from hosting for your group of friends in the past is less than useful.

In most other games, the 'dedicated server' application takes care of all network synchronization. You and a friend both connect to the server and neither of you have to be able to accept incoming connections to play together. With SPT+Fika, this is not the case: you can both connect to the backend server, interact with traders and send each other items, but you will not be able to play in raids together unless one of you is able to accept incoming connections **to your EscapeFromTarkov.exe game client.** This is because raids are hosted by Fika Plugin on your game client, not the backend server.

If the PC where the raid is being hosted is only accessible behind a proxy or tunnel, you may have to utilize the information above to come up with a value to enter in to `Force IP` such that other clients can connect to the advertised raid. This may be as simple as creating a dynamic DNS entry that resolves differently inside your network than it does outside — for instance, `fika.yourdomain.com` that is resolved to a LAN IP for users inside your network (locally by your router) but your public IP for users outside your network via an A record from your domain registrar.

{% hint style="success" %}
If any of the above information still does not help you figure out what values you can enter for Force IP or Force Bind IP, come join us in the [Fika Discord](https://discord.gg/project-fika) and explain your network setup, what you're trying to do, what you've tried, and what's not working.
{% endhint %}
