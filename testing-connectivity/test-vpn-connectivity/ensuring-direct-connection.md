---
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

# Ensuring direct connection

{% stepper %}
{% step %}
### Open Radmin
{% endstep %}

{% step %}
### Open your friend(s)'s connection properties

Right-click your friend's name in Radmin and click `Properties`.

<figure><img src="../../.gitbook/assets/image (5).png" alt="" width="245"><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### Validate channel type

Validate that the Channel type is `TCP/out` or `UDP/out`. This mean you have a direct connection to this peer.

<figure><img src="../../.gitbook/assets/image (6).png" alt=""><figcaption></figcaption></figure>
{% endstep %}
{% endstepper %}

{% hint style="warning" %}
If you see `TCP/relay`, then the communication is relayed through Radmin's servers. The performance will be severely degraded. Try disabling any firewall and/or antivirus in your system and reconnect to the network in Radmin.

You _can_ play with TCP/relay, but expect lag. You have been warned.
{% endhint %}

<p align="center"><a href="../../landing/congratulations.md" class="button primary" data-icon="circle-right">I validated the channel type</a></p>
