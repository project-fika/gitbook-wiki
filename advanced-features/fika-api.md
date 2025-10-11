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

<details>

<summary>Schema</summary>

```json
{
  "$schema": "https://json-schema.org/draft/2020-12/schema",
  "title": "Flea Ban Request",
  "description": "Schema for banning a player from the flea market for a specified number of days.",
  "type": "object",
  "properties": {
    "profileId": {
      "type": "string",
      "description": "Unique identifier for the player's profile."
    },
    "amountOfDays": {
      "type": "integer",
      "minimum": 0,
      "description": "Number of days the player is banned. 0 means the ban is infinite."
    }
  },
  "required": ["profileId", "amountOfDays"],
  "additionalProperties": false
}
```



</details>

### fika/api/createheadlessprofile

Creates one headless profile. Used by the installer, not recommended to be used.

### fika/api/logout

Logs out the given MongoID from the game.

<details>

<summary>Schema</summary>

```json
{
  "$schema": "https://json-schema.org/draft/2020-12/schema",
  "title": "Logout Request",
  "description": "Schema for logging out a player from the game using their MongoID profile ID.",
  "type": "object",
  "properties": {
    "profileId": {
      "type": "string",
      "description": "The MongoDB ObjectID of the player to log out."
    }
  },
  "required": ["profileId"],
  "additionalProperties": false
}
```



</details>

### fika/api/restartheadless

Restarts the headless with the given MongoID.

<details>

<summary>Schema</summary>

```json
{
  "$schema": "https://json-schema.org/draft/2020-12/schema",
  "title": "Restart Headless Request",
  "description": "Schema for restarting the headless instance associated with a given player profile ID.",
  "type": "object",
  "properties": {
    "profileId": {
      "type": "string",
      "description": "The MongoDB ObjectID of the player whose headless instance should be restarted."
    }
  },
  "required": ["profileId"],
  "additionalProperties": false
}
```



</details>

### fika/api/senditem

Sends X amount of items to the given MongoID.

<details>

<summary>Schema</summary>

{% code fullWidth="false" %}
```json
{
  "$schema": "https://json-schema.org/draft/2020-12/schema",
  "title": "Send Item Request",
  "description": "Schema for sending an item to a player with a given MongoID profile ID.",
  "type": "object",
  "properties": {
    "itemTpl": {
      "type": "string",
      "description": "Template ID of the item being sent."
    },
    "amount": {
      "type": "integer",
      "minimum": 1,
      "description": "Number of items to send."
    },
    "message": {
      "type": "string",
      "maxLength": 255,
      "description": "Optional message sent with the item. Can be empty."
    },
    "fir": {
      "type": "boolean",
      "description": "Whether the item is marked as Found In Raid (FIR)."
    },
    "expirationDays": {
      "type": "integer",
      "minimum": 1,
      "description": "Number of days before the message expires."
    },
    "profileId": {
      "type": "string",
      "description": "The MongoDB ObjectID of the player to send the item to."
    }
  },
  "required": [
    "itemTpl",
    "amount",
    "message",
    "fir",
    "expirationDays",
    "profileId"
  ],
  "additionalProperties": false
}
```
{% endcode %}



</details>

### fika/api/senditemtoall

Sends X amount of items to the given MongoIDs.

<details>

<summary>Schema</summary>

```json
{
  "$schema": "https://json-schema.org/draft/2020-12/schema",
  "title": "Send Item To Multiple Players Request",
  "description": "Schema for sending items to multiple players using their MongoID profile IDs.",
  "type": "object",
  "properties": {
    "itemTpl": {
      "type": "string",
      "description": "Template ID of the item being sent."
    },
    "amount": {
      "type": "integer",
      "minimum": 1,
      "description": "Number of items to send to each player."
    },
    "message": {
      "type": "string",
      "maxLength": 255,
      "description": "Optional message sent with the item. Can be empty."
    },
    "fir": {
      "type": "boolean",
      "description": "Whether the item is marked as Found In Raid (FIR)."
    },
    "expirationDays": {
      "type": "integer",
      "minimum": 1,
      "description": "Number of days before the message expires."
    },
    "profileIds": {
      "type": "array",
      "description": "List of MongoDB ObjectIDs representing the player profiles to send the items to.",
      "items": {
        "type": "string"
      },
      "minItems": 1
    }
  },
  "required": [
    "itemTpl",
    "amount",
    "message",
    "fir",
    "expirationDays",
    "profileIds"
  ],
  "additionalProperties": false
}
```



</details>

### fika/api/sendmessage

Sends a message to a MongoID.

<details>

<summary>Schema</summary>

```json
{
  "$schema": "https://json-schema.org/draft/2020-12/schema",
  "title": "Send Message Request",
  "description": "Schema for sending a message to a player using their MongoID profile ID.",
  "type": "object",
  "properties": {
    "message": {
      "type": "string",
      "maxLength": 255,
      "description": "Message to send to the player. Can be empty."
    },
    "profileId": {
      "type": "string",
      "description": "The MongoDB ObjectID of the player to send the message to."
    }
  },
  "required": ["message", "profileId"],
  "additionalProperties": false
}
```



</details>
