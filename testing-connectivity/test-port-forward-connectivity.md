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

# Test port forward connectivity

{% stepper %}
{% step %}
### Make sure `SPT Server` is running
{% endstep %}

{% step %}
### Obtain your public IP address

You can obtain your public IP address [here](https://api.ipify.org/).
{% endstep %}

{% step %}
### Test port connectivity

You can test your port connectivity using an [online port checker](https://portchecker.co).&#x20;

Enter your public IP address and port 6969, then click `Check`.
{% endstep %}
{% endstepper %}

{% hint style="warning" %}
If the port is closed, you may have an invalid configuration, Windows Firewall blocking the connection or your ISP does not allow port forwarding. Validate all your network settings or consider using a [VPN client](../hosting-a-fika-server/host-using-a-vpn.md).

Visit our Discord for assistance if you are stuck.
{% endhint %}

<p align="center"><a href="../landing/congratulations.md" class="button primary" data-icon="circle-right">I confirm that my server is accessible</a></p>
