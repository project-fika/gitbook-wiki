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

# Set up required/optional mods

Setting up the required/optional mods section in `fika.jsonc` can be frustrating. What do I put there? How do I find mod GUIDs? What's the difference between required and optional. Let's attempt to demystify this powerful feature and make it more widely used. First, let's start with a simple Powershell script that will snag all the plugin GUIDs that you currently have loaded.&#x20;

Before executing this script, make sure you have **all the plugins you want the names of** installed and launch your SPT client. This will refresh your Player.log with currently installed plugin information, which we will pull with the script below. Copy and paste the script below directly into a Powershell command window and execute it. It'll print out a string of mod GUIDs properly formatted for pasting directly into `fika.jsonc`.

```powershell
$LocalLow = [System.Environment]::GetFolderPath("LocalApplicationData").Replace("Local", "LocalLow")
$LogFile = Join-Path $LocalLow "\Battlestate Games\EscapeFromTarkov\Player.log"

$ModGuids = @()

Get-Content $LogFile | ForEach-Object {
    if ($_ -match '^\[Info\s+:FikaModHandler\].*?GUID \[([^\]]+)\]') {
        $ModGuids += '"' + $matches[1] + '"'
    }
}

$CSVOutput = $ModGuids -join ', '

Write-Host $CSVOutput
```

<figure><img src="../.gitbook/assets/image (1).png" alt=""><figcaption></figcaption></figure>

Copy and paste the output into `fika.jsonc` -> `"mods": { "required": [ <HERE> ]` if you want everyone who joins the server to be required to have the same plugins that you have loaded. You can move some of the GUIDs down to the `"optional": [ ]` section if you don't want to enforce certain plugins but still have them allowed. Anyone who has a plugin loaded that is not in either of these lists or missing a plugin in the required list will get an error message with a large `EXIT` button:

> Your client doesn't meet server requirements, check logs for more details

This way you can keep friends from installing mods that may give an unfair advantage or at least make sure that everyone has the same mods, which avoids issues.

