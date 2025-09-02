---
description: Created by Shynd
---

# Guidance on which mods should be used on the headless client

## Note: The headless client is a _client_ -- clients only load things in `BepInEx/`. Any mod that is in `user/mods/` is loaded only by the backend server, SPT.Server.exe.

To expand a bit on what I mean about the difference between a plugin I assume the headless client **needs** vs a plugin I assume the headless client does not need:

* **Does it only have an effect while in stash or hideout? If yes, then it's probably&#x20;**_**not**_**&#x20;necessary for the headless client.**
  * This would be something like QuickSell. It is not necessary to have on the headless client because it only affects in-stash behavior.
  * Plugins in this category may be fine to leave installed on the headless client and they may cause issues. They are unlikely to _solve_ any issues.
*   **Does it only change how information or graphics are displayed, without changing that information? If yes, then it's probably&#x20;**_**not**_**&#x20;necessary for the headless client.**

    * This would include things like MoreCheckmarks, AmandsGraphics, DynamicMaps, ItemSellPrice, et al. These plugins take existing information that is available already in the game client and display it in a different way. They do not add or change any behavior.
    * Plugins in this category also may be fine to leave installed on the headless client, and they also may cause issues. They are unlikely to _solve_ any issues.
    * Remember that the headless client is navigating menus automatically to start a raid and finish a raid. Anything that changes menus or patches menus may cause problems.

    ,
* **Does it change in-raid behavior in some way? If yes, it's probably necessary.**
  * This would be something like SAIN, which affects AI behavior, or bot spawn mods, or UIFixes which changes _how inventory behaves_, or anything else that you think _**might**_ have an effect on in-raid behavior.
  * Plugins in this category are sometimes difficult to spot. Something like UIFixes may not be obvious that it _changes_ inventory behavior, and it may not be apparent to users that the raid host is authoritative on inventory actions.
  * Some plugins that seem to fall in to this category are simply displaying other ways to trigger vanilla behavior and thus do not need to be on the headless client, but often do not hurt to have installed anyway. Things like ItemContextMenuExtended, for instance, make it so that you can right-click a flashlight to toggle it on/off, but they do not _change_ that behavior, only make it accessible in a new way, and thus are not _required_ to be on the headless client.

There are some plugins, like SearchOpenContainers, that are difficult to discern where they need to be or if they'd cause issues. One might reasonably assume that searching a container that is open is changing behavior so it needs to be installed for the headless client; one might also reasonably assume that searching an open container is entirely client-side and since the headless client character will never be searching containers it is not necessary. Plugins that feel ambiguous should be tested to make sure they do not cause issues one way or another.&#x20;

At the end of the day, there is often no _benefit_ to having plugins that do not improve the experience for the headless client to be installed on the headless client, but often there's also no issues. Sometimes more plugins does cause more processing overhead and thus lower in-raid FPS. If that doesn't matter to you, install everything and only remove plugins that cause problems! If that does matter, be selective and test for yourself.&#x20;

I personally use the above logic as a starting point for testing. I remove any plugins that I'm very sure are not necessary and leave in any plugins that I am not sure about, and then I run raids and specifically test plugin behaviors. I look through logs for errors. If everything is working, I move on. Thus far, this has served me well.

Here is an illustration of the modding setup of headless client vs Fika instance:

**Headless client**

<figure><img src="../.gitbook/assets/image (22).png" alt=""><figcaption></figcaption></figure>

**Fika instance**

<figure><img src="../.gitbook/assets/image (23).png" alt=""><figcaption></figcaption></figure>
