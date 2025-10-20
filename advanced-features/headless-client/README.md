---
description: >-
  General information about the Fika headless client feature for creating a
  dedicated raid host instance of SPT.
layout:
  width: default
  title:
    visible: true
  description:
    visible: true
  tableOfContents:
    visible: true
  outline:
    visible: false
  pagination:
    visible: false
  metadata:
    visible: true
---

# Headless Client

The headless client plugin is an exclusive Fika feature that allows you to host a raid on a separate Escape From Tarkov instance. You are able to offload the AI calculation and other resource-intensive task to improve game play performance. When hosting the raid on a **separate PC** from where you play, FPS gains are usually around 25% to 50% depending on your computer specifications and amount of bots in the game.

{% hint style="warning" %}
Please note that there is some technical knowledge required to achieve this. If you absolutely have no experience, you will have a hard time.
{% endhint %}

### Specifications

* The headless client is basically another SPT+Fika client instance that will automatically host raids. All players becomes clients (including the player who clicked `HOST RAID`).
* Graphic rendering is disabled to make the headless client as lightweight as possible. However, the headless client is **NOT** a true headless server. It still requires all the game files and a pretty hefty amount of RAM to work (especially for bigger maps such as Streets or Lighthouse).
* It is **strongly** recommended to run the headless client on a separate physical machine. The headless client will NOT work on a VPS. If you really wish to use a paid host, rent a dedicated server.
* A graphic card is NOT required to run the headless client, however it may be helpful for configuring mods.

{% hint style="danger" %}
Using a headless client can create a situation where certain mods either cannot work entirely or become more complicated to properly configure. It is therefore much easier to set up a headless client **before adding any mods** to reduce issues.

If you run into problems during the headless client setup process, consider starting over with a completely fresh SPT+Fika install without any other mods first.
{% endhint %}

More information, guides, and common fixes can be found in the [Headless Client FAQ and Common Issues](../../faqandguides/headless-client-faq-and-common-issues/) section.

### Choose Headless Client Implementation:

{% tabs %}
{% tab title="Headless Client on a Separate PC" %}
{% hint style="success" %}
This is the intended use case for the Fika Headless Client feature and provides the largest and most consistent performance increase.
{% endhint %}

Both SPT.Server and a Headless Client will run on a separate PC independent of your gaming PC. This means you can utilize your gaming PC in any way you wish, including restarting it, without affecting any other players.

<h4 align="center">Click <a href="headless-client.md" class="button primary" data-icon="network-wired">Remote Headless Client Instructions</a> to continue</h4>
{% endtab %}

{% tab title="Local Headless / Headless on Same PC" %}
{% hint style="danger" %}
#### This is not the intended use case for the Fika Headless Client feature!

Please read the warnings at the top of the next page. Support may be limited.
{% endhint %}

If your PC can handle running two EFT clients at the same time, you _may_ see a reduction in stuttering or an increase in performance by running a headless client on the same PC where you are playing SPT. Any performance increase is entirely dependent on your hardware and not guaranteed.

#### <mark style="color:$warning;">Some users see performance degradation. Continue at your own risk.</mark>

<h4 align="center">Click <a href="local-headless-client.md" class="button primary" data-icon="computer">Local Headless Client Instructions</a> to continue</h4>
{% endtab %}
{% endtabs %}
