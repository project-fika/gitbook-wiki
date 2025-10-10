---
description: All our APIs (last updated for SPT 4.0, Fika 2.0)
---

# Fika API

## Overview

An API key is automatically generated on first launch. You can find it in the `fika.jsonc` file in the configuration folder.

Use the API key to authenticate when making request. You also need to add the `requestcompressed` header with a value of `0`.

<details>

<summary>Authentication example for C#</summary>

```csharp
client.DefaultRequestHeaders.Authorization = new AuthenticationHeaderValue("Bearer", config.APIKey);
client.DefaultRequestHeaders.Add("requestcompressed", "0");
```

</details>

In e.g. Postman, the authentication type is "API Key", with the key being "`Authorization`" and the value being "`Bearer {apiKey}`".

## Get

### fika/api/items

Returns all items from the SPT database, with the MongoID being the identifier, and the name, description and stackable amount being values.\
\
Example response:

{% code fullWidth="false" %}
```json
{
    "items": {
        "5447a9cd4bdc2dbd208b4567": {
            "name": "Colt M4A1 5.56x45 assault rifle",
            "description": "The Colt M4A1 carbine is a fully automatic variant of the basic M4 Carbine and was primarily designed for special operations use.\nHowever, U.S. Special Operations Command (USSOCOM) was soon to adopt the M4A1 for almost all special operations units, followed later by general introduction of the M4A1 into service with the U.S. Army and Marine Corps.",
            "stackable": 10
        }
}
```
{% endcode %}

### fika/api/raids

Returns all active raids.

### fika/api/headless

Returns all active headless clients.

### fika/api/heartbeat

Checks whether the server is running. Primarily use by the WebApp.

### fika/api/players

Returns all online players.

### fika/api/rawprofile

Returns a raw profile in JSON format.

Input:

<table data-full-width="false"><thead><tr><th>Key</th><th>Value</th><th>Description</th></tr></thead><tbody><tr><td>profileId</td><td>{validMongoID}</td><td>The MongoID to return a raw profile of.</td></tr></tbody></table>

Example input:

`{baseUrl}/fika/api/rawprofile?profileId=68e8f63d941b8a1c94c1d8bf`

## Post

### fika/api/fleaban

Bans a player from the flea for X amount of days. 0 = infinite.

Input example:

```json
{
    "profileId": "68e8f63d941b8a1c94c1d8bf",
    "amountOfDays": 0
}
```

### fika/api/createheadlessprofile

Creates one headless profile. Used by the installer, not recommended to be used.

### fika/api/logout

Logs out the given MongoID from the game.

Input example:

```json
{
    "profileId": "68e8f63d941b8a1c94c1d8bf"
}
```

### fika/api/restartheadless

Restarts the headless with the given MongoID.

Input example:

```json
{
    "profileId": "68e8f63d941b8a1c94c1d8bf"
}
```

### fika/api/senditem

Sends X amount of items to the given MongoID.

Input example:

```json
{
    "itemTpl": "", // itemTpl
    "amount": 1, // how many of item
    "message": "Here is an item", // message, can be empty (max 255 chars)
    "fir": true, // is item found in raid
    "expirationDays": 7, // how long until the message expires
    "profileId": "" // the MongoID to send to
}
```

### fika/api/senditemtoall

Sends X amount of items to the given MongoIDs.

Input example:

```json
{
    "itemTpl": "", // itemTpl
    "amount": 1, // how many of item
    "message": "Here is an item", // message, can be empty (max 255 chars)
    "fir": true, // is item found in raid
    "expirationDays": 7, // how long until the message expires
    "profileIds": [] // the MongoIDs to send to
}
```

### fika/api/sendmessage

Sends a message to a MongoID.

Input example:

```json
{
    "message": "Here is an item", // message, can be empty (max 255 chars),
    "profileId": ""
}
```
