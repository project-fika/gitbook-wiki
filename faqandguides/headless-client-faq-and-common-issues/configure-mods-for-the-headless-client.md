---
description: Created by Shynd
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

# Configure mods for the headless client

## General instructions

* If the PC where the headless client is installed has a GPU, you can simply open the headless client in graphics mode by pressing G when prompted by FikaHeadlessManager during startup. In graphics mode you can access F12 (or F6 for SAIN) to configure your mods.
* If the PC where headless client is installed does NOT have a GPU, close FikaHeadlessManager and the headless client. Install the plugins you wish to configure on the SPT instance where you will be playing (NOT THE HEADLESS), configure the options however you want, then copy the necessary .cfg files from `<SPT Install>/BepInEx/config/` into the `<Headless SPT>/BepInEx/config/` folder for your headless client install.

## SAIN

* SAIN settings are stored in the `BepInEx/plugins/SAIN/Presets/` folder. I suggest using your main game to configure SAIN options however you want them to be on the headless client, then copy your entire `BepInEx/plugins/SAIN/` folder over to the dedicated client, overwriting all when prompted.

## Donuts

* Donuts settings are stored in the `BepInEx/plugins/dvize.Donuts/Config` folder. Same as SAIN above, I suggest configuring Donuts settings using the GUI from your main game and then copying over the entire `BepInEx/plugins/dvize.Donuts/` folder to the headless client.

***
