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
    visible: true
  metadata:
    visible: true
---

# Headless Client FAQ and Common Issues

## :question:My headless client cannot connect to my server.

{% hint style="danger" %}
#### Ensure SPT.Server is running and able to accept connections

Test connectivity using SPT.Launcher: make sure you can launch the game and reach your stash and access traders.

If your SPT.Launcher is not able to connect to your server, figure out why and address that issue first. If the server is currently running but SPT.Launcher cannot connect, revisit the [Hosting a Fika server](../../hosting-a-fika-server/) instructions.



**NOTE**: the headless client **does not replace SPT.Server**. The backend server is required to be running at all times.
{% endhint %}

If you have already generated `HeadlessConfig.json` and it is in the root directory of your headless install, open it in a text editor, and change the URL to match how you connect to your server. This may include a VPN IP or the public IP of the server. Save the changes to the file and restart `FikaHeadlessManager.exe`

If you have not generated `HeadlessConfig.json` or the headless profile yet, revisit the [steps for installing the Headless client](../../advanced-features/headless-client/headless-client.md) and pay close attention to the [step about editing `fika.jsonc`](../../advanced-features/headless-client/headless-client.md#optional-set-url-in-fika.jsonc)

## :question:How do I change the name of the headless client that is displayed when hosting a raid?

1. Open [fika.jsonc](../../fika-configuration/server.md) in a text editor.
2. Find the `headless` -> `profiles` -> `aliases` section.
3.  Add one line per headless client in the format `"ID": "Alias"`

    1. The `ID` is the profile ID of the headless character profile for which you wish to change the name.
    2. You can find the profile ID by opening `HeadlessConfig.json` in a text editor.
    3. If you are adding multiple profiles, each line needs to end in a comma `,` except the last line.

    <div align="left" data-full-width="false"><figure><img src="../../.gitbook/assets/image (18).png" alt=""><figcaption></figcaption></figure></div>
4. Save changes to `fika.jsonc` and close the text editor.
5. Restart SPT.Server.
