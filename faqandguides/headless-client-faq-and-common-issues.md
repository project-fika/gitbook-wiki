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
    visible: true
  pagination:
    visible: false
  metadata:
    visible: true
---

# Headless Client FAQ and Common Issues

## :question:My headless client cannot connect to my server.

{% hint style="danger" %}
#### Ensure SPT.Server is running and able to accept connections. Test connectivity using SPT.Launcher, make sure you can launch the game and reach your stash and access traders.
{% endhint %}

If you have already generated `HeadlessConfig.json` and it is in the root directory of your headless install, open it in a text editor, and change the URL to match how you connect to your server. This may include a VPN IP or the public IP of the server. Save the changes to the file and restart `FikaHeadlessManager.exe`

If you have not generated `HeadlessConfig.json` or the headless profile yet, revisit the [steps for installing the Headless client](../advanced-features/headless-client.md) and pay close attention to the [step about editing `fika.jsonc`](../advanced-features/headless-client.md#optional-set-url-in-fika.jsonc)
