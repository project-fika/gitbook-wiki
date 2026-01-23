---
description: Step-by-step process for hosting a Fika server using port forwarding.
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

# Host using port forwarding

{% hint style="warning" %}
**WARNING**

Not all Internet Service Providers (ISP) allows port forwarding. If you find yourself unable to port forward, you can use a public VPN service such as Radmin, ZeroTier, etc.). Click [here](host-using-a-vpn.md) to learn how to host using a VPN.
{% endhint %}

{% hint style="info" %}
We do not provide a step-by-step tutorial for port forwarding because the router settings interface varies between different models and manufacturers. You may be able to find guides for your router on [PortForward.com](https://portforward.com/) or by searching Google.
{% endhint %}

{% stepper %}
{% step %}
### Access your router configuration

Your router configuration can be accessed by typing the [gateway IP](https://www.whatismyip.com/finding-your-default-gateway-address/) in your browser.
{% endstep %}

{% step %}
### Access the port forward menu

The port forward menu can have different names; usually "port forwarding" or "virtual server".
{% endstep %}

{% step %}
### Add port forward rules

Add the following port forward rules and make sure they are associated with your computer:

* 6969 TCP (SPT backend server).
* 25565 UDP (Fika in-game networking).
{% endstep %}

{% step %}
### Start `SPT.Server`

If everything is working properly, you should see something similar in the console output:

<pre><code>ModLoader: loading: 1 server mods...
<strong>Mod: server version: 2.2.0 (targets SPT: >=4.0.11) by: Fika loaded
</strong>Loading OnWebAppBuildMods...
[Fika Server] Overriding SPT configuration
Finished loading OnWebAppBuildMods...
Loaded self-signed certificate (./user/certs/server.crt)
Server: executing startup callbacks...
┌─────────────────────────────────────────┐
│ SPT 4.0.11                              │
│ https://discord.sp-tarkov.com           │
│                                         │
│ This work is free of charge             │
│ If you paid money, you were scammed     │
│ Commercial use is prohibited            │
└─────────────────────────────────────────┘
Loading PreSptMods...
Finished loading PreSptMods...
Importing database...
Database import finished
Generating flea offers...
<strong>Started webserver at https://0.0.0.0:6969
</strong><strong>Started websocket at wss://0.0.0.0:6969
</strong><strong>Server has started, happy playing
</strong></code></pre>

{% hint style="warning" %}
If you see errors (red text) then your configuration is invalid or you are unable to host using the configured IP address/port. Please double-check your settings.
{% endhint %}
{% endstep %}

{% step %}
### Start `SPT.Launcher`


{% endstep %}

{% step %}
### Login to your profile


{% endstep %}

{% step %}
### Start game


{% endstep %}
{% endstepper %}

<p align="center"><a href="../testing-connectivity/test-port-forward-connectivity.md" class="button primary" data-icon="circle-right">I followed all the steps</a></p>
