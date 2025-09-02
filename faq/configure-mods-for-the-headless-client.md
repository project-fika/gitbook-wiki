---
description: Created by Shynd
---

# Configure mods for the headless client

## General instructions

* If the server where headless client is installed has a GPU, you can simply open the headless client in graphics mode by pressing G when the headless client script is starting. You can access F12 to configure your mods.
* If the server where headless client is installed does NOT have a GPU, close your headless client console. Install the plugins you wish to configure on the SPT instance where you will be playing (NOT THE HEADLESS), configure the options however you want, then copy the necessary .cfg files from `<SPT Install>/BepInEx/config/` into the `<Headless SPT Install>/BepInEx/config/` folder for your headless client install.

## SAIN

* SAIN settings are stored in the `BepInEx/plugins/SAIN/Presets/` folder. I suggest using your main game to configure SAIN options however you want them to be on the headless client, then copy your entire `BepInEx/plugins/SAIN/` folder over to the dedicated client, overwriting all when prompted.

## Donuts

* Donuts settings are stored in the `BepInEx/plugins/dvize.Donuts/Config` folder. Same as SAIN above, I suggest configuring Donuts settings using the GUI from your main game and then copying over the entire `BepInEx/plugins/dvize.Donuts/` folder to the headless client.
