---
description: Step-by-step process for hosting a Fika server in your local network.
---

# Host over LAN

Hosting over LAN allows you to play with someone in the same house/network without internet access and without any real port forwarding other than allowing the application in your local firewall.

## Obtain your local IP

Your local IP address will be required to host over LAN. Follow the steps below to obtain it.

* Press the `Windows key` and type `cmd`.

<figure><img src="../.gitbook/assets/win_run_cmd.png" alt="" width="563"><figcaption></figcaption></figure>

* Type `ipconfig` and then press `enter` in the command prompt.
* Find the network adapter you are using (Ethernet or Wi-Fi). There can be multiple Ethernet adapter - make sure you identify the correct one.
* Find the IPv4 Address entry and take note of the IP address, e.g `192.168.0.152`. This will be referred to as `your_lan_ip` below.

<figure><img src="../.gitbook/assets/fika_ipconfig.png" alt=""><figcaption><p>Your local IP address should appear under Ethernet adapter (if your connection is wired)</p></figcaption></figure>

## Configure Windows Firewall

Installing Fika using Fika-Installer will automatically configure the Windows Firewall.

## Configure your local IP in Fika

* Start `SPT.Server.exe` at least once to generate the configuration files, then close it.

<figure><img src="../.gitbook/assets/https___files.gitbook.com_v0_b_gitbook-x-prod.appspot.com_o_spaces_2FKIBpsnthxy8OSpsWzsDI_2Fuploads_2FtXMCT7qmRaqYnXrLE8Tr_2Fhttps___files.gitbook.com_v0_b_gitbook-x-prod.appspot.com_o_spaces_2FKIBpsnthxy8OSpsWzs.png" alt=""><figcaption></figcaption></figure>

* Navigate to your `user\mods\fika-server\assets\configs`&#x20;
* Open `fika.jsonc`.
* Find the `server` section.
* Change `ip` to `your_lan_ip`.
* Change `backendIp` to `your_lan_ip`.
* Save the file and close it.

<figure><img src="../.gitbook/assets/fika_jsonc_lan.png" alt=""><figcaption></figcaption></figure>

* Launch `SPT Server`

If everything is working properly, you should see something similar in the console output:

```
ModLoader: loading: 1 server mods...
Mod: server version: 2.4.0 by: Fika loaded
Server: executing startup callbacks...
Importing database...
Database import finished
Started webserver at https://<your_lan_ip>:6969
Started websocket at wss://<your_lan_ip>:6969
Server is running, do not close while playing SPT, Happy playing!!
```

{% hint style="warning" %}
If you see errors (red text) then your configuration is invalid or you are unable to host using the configured IP address/port.
{% endhint %}

* Start `SPT Launcher`

<figure><img src="../.gitbook/assets/https___files.gitbook.com_v0_b_gitbook-x-prod.appspot.com_o_spaces_2FKIBpsnthxy8OSpsWzsDI_2Fuploads_2FQIK2fJ1ONoqXIAA3v9tl_2Fhttps___files.gitbook.com_v0_b_gitbook-x-prod.appspot.com_o_spaces_2FKIBpsnthxy8OSpsWzs.png" alt=""><figcaption></figcaption></figure>

* Click the `Settings` button

<figure><img src="../.gitbook/assets/https___files.gitbook.com_v0_b_gitbook-x-prod.appspot.com_o_spaces_2FKIBpsnthxy8OSpsWzsDI_2Fuploads_2FqwHM3gxlwjEsrugHTtc0_2Fimage (1).avif" alt=""><figcaption></figcaption></figure>

* Check the `Developer mode` box.
* Enter your local IP address in the URL section. DO NOT leave out `https://` and do not add a slash at the end. The URL box should look like this: `https://192.168.0.33:6969`.

<figure><img src="../.gitbook/assets/https___files.gitbook.com_v0_b_gitbook-x-prod.appspot.com_o_spaces_2FKIBpsnthxy8OSpsWzsDI_2Fuploads_2FRJRDafOFXrz8sQBMXNfo_2Fimage (1).avif" alt=""><figcaption></figcaption></figure>

* Press the arrow on the right corner.
* You should now be able to create your profile and log in to the server.
* Start the game.

<figure><img src="../.gitbook/assets/https___files.gitbook.com_v0_b_gitbook-x-prod.appspot.com_o_spaces_2FKIBpsnthxy8OSpsWzsDI_2Fuploads_2FVhkOgEbLlzyx9kazRxLl_2Fimage.avif" alt=""><figcaption></figcaption></figure>

* Press `F12` when in-game to bring up the configuration manager.
* Find the `Force IP` and `Force Bind IP` in the `Fika.Core` section of the configuration manager.
* Set both `Force IP` and `Force Bind IP` to `your_lan_ip`.

<figure><img src="../.gitbook/assets/fika_lan_f12.png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
Note: Players willing to host a raid will also need to set the `Force IP` and `Force Bind IP` in their respective Fika configuration.
{% endhint %}

## Testing connectivity

* Ask your friend(s) to ping your local IP address from a computer within the same local network.

If the ping fails then it means that you grabbed the wrong local IP address or that your network configuration is invalid. Validate your network settings.

## Hosting a raid

Your Fika instance is now ready to host a raid.

* [Click here](../playing-fika.md#hosting-a-raid) to learn how to host a raid.
* [Click here](../fika-configuration/) to learn more about additional Fika configurations.
