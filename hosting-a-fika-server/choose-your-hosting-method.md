---
description: Getting started with hosting a Fika server.
layout:
  width: default
  title:
    visible: true
  description:
    visible: false
  tableOfContents:
    visible: true
  outline:
    visible: false
  pagination:
    visible: false
  metadata:
    visible: false
---

# Choose your hosting method

See below for the different methods for hosting a Fika server. Choose the one that is appropriate to your network configuration.

{% hint style="warning" %}
**WARNING**

Some technical knowledge is required to host a Fika server. If you are unsure, please visit our Discord for assistance.
{% endhint %}

{% tabs %}
{% tab title="Port Forwarding" %}
Port Forwarding is the process of opening a port externally to a device within your network. Players can enter your external IP and connect directly to the server running on your computer.

**Pros**

* Direct connection between players and your server (best performance).
* No software dependencies.

**Cons**

* Requires access to your router configuration.
* Certain ISP or network configuration such as CGNAT/shared public IP cannot port forward.
* Your device local IP may change which will break the port forwarding rule (can be addressed by static IP allocation).

<a href="host-using-port-forwarding.md" class="button primary" data-icon="up-right-from-square">Host using Port Forwarding</a>
{% endtab %}

{% tab title="Virtual Private Network (VPN)" %}
A Virtual Private Network (VPN) allows you to join a virtual network provided by a centralized server. All communication goes through the centralized server and then is shared between peers connected to the same network.

**Pros**

* No port forwarding required
* Easy to set up and use
* Works with restricted networks such as CGNAT/shared public IP

**Cons**

* Direct connection is not possible in some instances. Communication will be relayed through the centralized server, which can severely degrade performance
* Requires all players to install and configure the VPN client
* Your external IP address is shared with the VPN service

<a href="host-using-a-vpn.md" class="button primary" data-icon="up-right-from-square">Host using VPN</a>
{% endtab %}

{% tab title="LAN (Local)" %}
Fika supports hosting on a local server with or without access to Internet. A router is required to be able to establish a connection to the local IP address of the server.

<a href="host-over-lan.md" class="button primary" data-icon="up-right-from-square">Host over LAN</a>
{% endtab %}
{% endtabs %}
