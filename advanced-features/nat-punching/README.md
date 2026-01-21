---
description: Step-by-step process for setting up a dedicated SPT server with NAT punching.
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

# NAT Punching

## What is NAT punching?

NAT punching is a [NAT traversal technique](https://en.wikipedia.org/wiki/NAT_traversal) that allows two devices located behind separate routers to establish a direct peer-to-peer connection. It is particularly useful in cases where port forwarding is not possible due to ISP or network restrictions.

However, NAT punching is not supported on all routers. For instance, **symmetric NAT** routers often prevent successful NAT punching due to the way they handle external port mappings.

## How does it work?

A public server listens for incoming connections from clients and records their external IP addresses and ports. It then introduces each client by sharing the other’s external IP address. For example, `Client 1` receives `Client 2`’s external IP address, and vice versa.

This is when NAT punching occurs: upon receiving `Client 2`’s IP address, `Client 1` begins sending multiple packets (the “punching”) to `Client 2`. At the same time, `Client 2` sends packets to `Client 1`, creating a routing entry in both clients’ routers.

At this point, both routers allow communication through this specific route, which can then be leveraged to host a `Fika` raid.

## Choosing the NAT Punching method

See below for the different methods for NAT Punching.

{% tabs %}
{% tab title="Fika NAT punch server" %}
Fika offers a public NAT punch server to facilitate connection between players and the raid host. You can use the Fika NAT punch server simply by toggling it on inside Fika's configuration menu.

**Pros**

* Easy to use, no set up required

**Cons**

* The public IP address of the raid host and players will be shared with the Fika NAT punch server. We do not collect and share your IP address with any third party.
* Relies on the Fika NAT punch server to be available. Downtime can happen with any online service

<a href="fika-nat-punch-server.md" class="button primary" data-icon="up-right-from-square">Use Fika NAT punch server</a>
{% endtab %}

{% tab title="Self-hosted NAT punch server" %}
Fika provides a built-in NAT punch server that will run inside SPT server. It is provided by the Fika-Server plugin.

**Pros**

* Ownership of the NAT punch server
* Privacy (don't share IP address with an external server you do not own)

**Cons**

* Requires configuration and set up
* Requires a VPS or a self-hosted server accessible externally

<a href="self-hosted-nat-punch-server.md" class="button primary" data-icon="up-right-from-square">Use self-hosted NAT punch server</a>
{% endtab %}
{% endtabs %}

