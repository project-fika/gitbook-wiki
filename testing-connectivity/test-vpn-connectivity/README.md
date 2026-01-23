---
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
    visible: false
---

# Test VPN connectivity

Before testing VPN connectivity, make sure that your friend(s) have successfully installed Fika and completed the steps [here](../../joining-a-fika-server/join-using-a-vpn/).

{% stepper %}
{% step %}
### Open Radmin


{% endstep %}

{% step %}
### Ping your friend(s)'s device

Right-click their name in Radmin and click `Ping`.

<figure><img src="../../.gitbook/assets/image (13).png" alt="" width="243"><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### Validate ping success

Ensure that the ping is successful in the command prompt. If you see "Request timed out" then the ping failed.
{% endstep %}

{% step %}
### Close command prompt
{% endstep %}
{% endstepper %}

{% hint style="warning" %}
If the ping fails then it means that the VPN connection is not working correctly. Everyone should try rebooting their PC and make sure that everyone joined the same network in Radmin.

Custom firewalls such as `BitDefender` can block VPN communication - try turning it off.
{% endhint %}

<p align="center"><a href="ensuring-direct-connection.md" class="button primary" data-icon="circle-right">I confirm that I can ping everyone</a></p>
