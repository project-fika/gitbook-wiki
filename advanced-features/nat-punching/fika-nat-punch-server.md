---
description: >-
  Step-by-step process for hosting a Fika server using Fika's public NAT punch
  server
---

# Fika NAT punch server

{% hint style="danger" %}
**DISCLAIMER**

The Fika NAT punch server is a public service offered by the Fika team, free of charge. Availability is not guaranteed.

By using this service, you agree that your public IP address will be shared with the Fika NAT punch server. This is absolutely necessary for NAT punching to work. We do NOT collect and share your IP address with any third party. If you don't like that, consider using the [self-hosted NAT punch server](self-hosted-nat-punch-server.md) instead.
{% endhint %}

## Requirements

* Both the raid host and any players connecting via NAT punching must use a router that supports Full-Cone NAT, as this type is required for proper connectivity. You can check your router’s NAT type by searching online for your specific router model.

## Limitations

The NAT punch server only facilitate connection when joining a raid. It does not allow to join the SPT server itself.

{% hint style="warning" %}
NAT Punching does NOT work on all routers. It depends on the NAT type of your router. If you or a player cannot connect then you can assume that your router or the player's router is incompatible and you should consider an alternative option such as [Hosting using a VPN](../../hosting-a-fika-server/host-using-a-vpn.md).
{% endhint %}

## How to enable the public Fika NAT Punch server

Only the raid host needs to follow the steps below.

{% stepper %}
{% step %}
### Press F12 when in main menu
{% endstep %}

{% step %}
### Enable advanced settings

Check the "Advanced settings" box.

<figure><img src="../../.gitbook/assets/image (1).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### Enable NAT Punching

Check both "Use NAT Punching" and "Use Fika NAT Punch Server".

<figure><img src="../../.gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### Close the configuration panel
{% endstep %}

{% step %}
### Host a raid and wait for players to join

The Fika NAT punch server will take care of the rest.
{% endstep %}
{% endstepper %}

{% hint style="warning" %}
Players connecting to your server do NOT need to enable these settings! These settings are only for the raid host.
{% endhint %}
