---
icon: comments-question-check
---

# FAQ and Guides

{% hint style="info" %}
## Other Guides and Answers

There are other FAQ and Guides which can be found in the Table of Contents by clicking the <i class="fa-bars">:bars:</i> in the top-left.

If you have a question not covered here, please join us in our [Discord](https://discord.gg/project-fika) server and ask in the #questions channel.
{% endhint %}

### :question:I changed `http.json` but my server still says `0.0.0.0`

{% hint style="warning" %}
Please do not watch video guides, they are often out of date.
{% endhint %}

The only place where IPs need to be edited is in [`fika.jsonc`](../fika-configuration/server.md)

* You must run `SPT.Server.exe` at least once with `fika-server` installed for `fika.jsonc` to generate.

Please follow the instructions for <a href="../hosting-a-fika-server/" class="button primary" data-icon="arrow-right-long">Hosting a Fika server</a>

***

### :question:I do not see my friend(s) on the Online Players list on the main menu / I cannot see my friend's raid in the raid list

{% hint style="warning" %}
<mark style="color:$warning;">**Only one person in the group launches SPT.Server.exe.**</mark>
{% endhint %}

* Decide which person is the server host. That person alone runs `SPT.Server.exe` and follows the [Hosting a Fika server](../hosting-a-fika-server/) instructions.
* Everyone else **does not run `SPT.Server.exe`** and instead follows the [Joining a Fika server](../joining-a-fika-server/) instructions.
* Make sure that everyone has Fika [installed](../installing-fika/). On the main menu, it should say FIKA in the bottom-left of the screen.

***

### :question:There is an error about opening ports when joining a raid

{% hint style="info" %}
**Make sure everyone is following** [**the instructions for hosting/joining a raid**](../playing-fika.md) **correctly.**
{% endhint %}

#### If you are _not_ using a headless client and your group is using Radmin VPN (or any other VPN client)

* Whoever clicks the `HOST RAID` button needs to follow these instructions **exactly as they are written**:
  * Navigate to the Fika.Core plugin settings in your F12 configuration menu and scroll down to the Network header. Select <mark style="color:$warning;">**your own VPN IP**</mark> from the `Force Bind IP` dropdown selection box, then type that <mark style="color:$warning;">**same exact IP**</mark> in the `Force IP` box just above.\
    \
    If you do not see the correct IP available in the `Force Bind IP` selection box, make sure you have the VPN client installed and are connected and then re-read the paragraph above very carefully.\
    \
    If you have enabled Advanced options visibility, both UPnP and NAT Punching should be **disabled.** If you do not see those options, ignore this since they are disabled by default.

#### If you are _not_ using a headless client and your group is port forwarding

* Whoever clicks the `HOST RAID` button needs to ensure that they have port-forwarded 25565/udp in their router to the PC where they are playing SPT. The raid is hosted by the game client of the person who clicks `HOST RAID`, not by the `SPT.Server` backend server.
* Make sure all settings in F12 -> Fika.Core -> Network are **default**:
  * `Force IP` should be blank
  * `Force Bind IP` should be Disabled or `0.0.0.0`
  * Port should match the port for which a port forward rule was created (25565 is default)
  * If you have enabled Advanced options visibility, both UPnP and NAT Punching should be **disabled.** If you do not see those options, ignore this since they are disabled by default.

#### If you are using headless client

* If you are using the headless client to host raids and you are getting this error, you need to make sure the headless client is set up to accept incoming connections the same way any normal client would be.&#x20;
  * **If you are port forwarding**, your port forward rule for 25565/udp needs to go to the PC that is running the headless client. All settings in `BepInEx/config/com.fika.core.cfg -> Network` section should be **default**.
  *   **If you are using a VPN**, you need to open up your `<headless install>/BepInEx/config/com.fika.core.cfg` in a text editor and make sure the VPN IP of the headless client machine is set for both `Force IP` and `Force Bind IP`. The VPN client must also be installed and configured on the headless client PC as well.

      <figure><img src="../.gitbook/assets/image (32).png" alt=""><figcaption></figcaption></figure>

***

### :question:F8 is not successfully extracting me from a raid

This has two common causes: either a mod is causing errors or something is intercepting the F8 key press.

Try pressing F12 to bring up the BepInEx Configuration Manager settings window. If that worked, try finding the Fika.Core setting for extract hotkey and rebinding it to a different key.

If F12 did not work or you were unable to rebind the extract hotkey to a different key (or if it shows it is bound to F13), you likely have something intercepting your F-keys. This is often overlay software like Overwolf or MSI Afterburner or similar, or it could be a joystick / steering wheel / other controller plugged in that is intercepting the F-keys. Try closing all overlay software and unplugging all control peripherals.

If none of the above worked, it is likely a mod that is causing issues. You will have to close your game client via ALT+F4 and then look in your Player.log file found in the folder below:

```
C:\Users\YOURUSERNAME\AppData\LocalLow\Battlestate Games\EscapeFromTarkov\
```

Open Player.log in a text editor and search for `F8 pressed` and see if there are any errors nearby that hint at which mod may be the cause. If you are unsure, come visit us in the [Discord](https://discord.gg/project-fika) #questions channel and explain what you've tried and upload your Player.log for assistance.

***

### :question: I cannot enable quest sharing in F12 -> Fika.Core settings

Review the fika-server mod [configuration options](../fika-configuration/server.md). These changes must be done by the server host.

Open `fika.jsonc` in a text editor and find the option named `sharedQuestProgression` and change it from `false` to `true`, then save your changes and restart the server.

<figure><img src="../.gitbook/assets/image (53).png" alt=""><figcaption></figcaption></figure>

***

### :question:Can I make the launcher not show everyone's profile?

Review the fika-server mod [configuration options](../fika-configuration/server.md). These changes must be done by the server host.

Open `fika.jsonc` in a text editor and find the option named `launcherListAllProfiles` and change it from `true` to `false`, then save your changes and restart the server.

<figure><img src="../.gitbook/assets/image (54).png" alt=""><figcaption></figcaption></figure>

***

### :question:Can I enable SPT chatbots like Commando?

Review the fika-server mod [configuration options](../fika-configuration/server.md). These changes must be done by the server host.

Open `fika.jsonc` in a text editor and find the option named `disableSPTChatBots` and change it from `true` to `false`, then save your changes and restart the server.

<figure><img src="../.gitbook/assets/image (55).png" alt=""><figcaption></figcaption></figure>

***

### :question:How do I uninstall Fika?

Start `Fika-Installer` and choose `Uninstall Fika`.

Alternatively, you can do it manually using the following steps:

* Navigate to `BepInEx/plugins/Fika/` and delete `Fika.Core.dll`
* Navigate to `SPT/user/mods/` and delete the `fika-server/` folder
* Open SPT.Launcher.exe, click Settings in the top-right, and (if applicable) change URL back to `https://127.0.0.1:6969`\
