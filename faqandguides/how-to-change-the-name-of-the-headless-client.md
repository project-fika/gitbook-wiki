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

# How to change the name of the headless client

* Edit [fika.jsonc](../fika-configuration/server.md).
* Find the `headless` -> `profiles` > `aliases` section.
* The format is "ID": "Alias".
* ID is the profile id of the headless profile, which you can find in `user/profiles/` and Alias is the name you want to appear.

<figure><img src="../.gitbook/assets/image (24).png" alt=""><figcaption></figcaption></figure>

* If you have multiple headless profiles, use the name of the headless client launch script (`Start_headless_xxx.ps1`) to identify the profile id you're looking for.
