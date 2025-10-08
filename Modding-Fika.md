---
description: Updated for 4.0
icon: wrench
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
    visible: false
  metadata:
    visible: true
---

# Creating Fika-Compatible Mods

## Fika Events

Fika has a lot of events that you can subscribe to, which makes it easier to run code at certain key moments of the raid. To subscribe to an event, use:

{% code overflow="wrap" %}
```cs
public static void SubscribeEvent<TEvent>(Action<TEvent> callback) where TEvent : FikaEvent
```
{% endcode %}

To unsubscribe, use:

{% code overflow="wrap" %}
```cs
public static void UnsubscribeEvent<TEvent>(Action<TEvent> callback) where TEvent : FikaEvent
```
{% endcode %}

The event triggered will usually pass an important object related to the event, e.g. `FikaNetworkManagerCreatedEvent` passes a `IFikaNetworkManager` (named `Manager` in the object). This object can then be accessed if needed.

You can read the source code [here](https://github.com/project-fika/Fika-Plugin/tree/main/Fika.Core/Modding) to find all events.

## Registering Packets

To register packets, subscribe to the `FikaNetworkManagerCreatedEvent` and access the `IFikaNetworkManager`. In the manager you can call either of these methods:

{% code overflow="wrap" fullWidth="false" %}
```cs
void RegisterPacket<T>(Action<T> handle) where T : INetSerializable, new();
```
{% endcode %}

{% code overflow="wrap" fullWidth="false" %}
```cs
void RegisterPacket<T, TUserData>(Action<T, TUserData> handle) where T : INetSerializable, new();
```
{% endcode %}

The `INetSerializable` needs to be a packet that you have created, and these methods are invoked when that packet is received. The second method also passes the `NetPeer`, which is useful on the `FikaServer`. You handle the logic however you want when receiving the packet with these methods.

{% hint style="danger" %}
Failing to register a packet will result in endless `exceptions` being thrown. Please register your packets correctly!
{% endhint %}

## Creating a Packet

To create a packet, implement the `INetSerializable` interface into a new `class`. For packets that are sent often, I highly recommend using a `struct`. Add the data that you need in the form of `Field` and make all of them `Public`. Use the `Serialize()` and `Deserialize()` methods to write/read data. You can find an example [here](https://github.com/project-fika/Fika-Plugin/blob/main/Fika.Core/Networking/Packets/Communication/BotStatePacket.cs), which also includes how to write an `enum`. There are also a lot of extensions to write EFT/Unity specific data (e.g. `Vector3`) that you can find [here](https://github.com/project-fika/Fika-Plugin/blob/main/Fika.Core/Networking/FikaSerializationExtensions.cs).

Do not instantiate and send new collections in packets that are sent often, e.g. `List<T>` or `T[]`. The allocations will become expensive. Fika has an interface `IReusable` that you can use to reuse a single instance of a packet, and only mutate the collections that exist in it.

{% code overflow="wrap" %}
```csharp
void RegisterReusable<T, TUserData>(Action<T, TUserData> handle) where T : class, IReusable, new();
```
{% endcode %}

An example of these packets can be found [here](https://github.com/project-fika/Fika-Plugin/blob/47a9d37aa40e2e7cc0b9628c7114115cd3805cd4/Fika.Core/Networking/Packets/World/WorldPacket.cs). Create the class somewhere, keep track of it and reuse it. You can find an example of that in the [FikaClientWorld](https://github.com/project-fika/Fika-Plugin/blob/47a9d37aa40e2e7cc0b9628c7114115cd3805cd4/Fika.Core/Main/ClientClasses/FikaClientWorld.cs).

## Sending a Packet

To send a packet, you need a `IFikaNetworkManager`. This is either a `FikaServer` or `FikaClient` that you can access with the `Comfort.Common` namespace using `Singleton<IFikaNetworkManager>.Instance`. To determine whether you are a server or client, use `FikaBackendUtils.IsServer`.

Use this method to send packets:

{% code overflow="wrap" %}
```cs
void SendData<T>(ref T packet, DeliveryMethod deliveryMethod, bool broadcast = false) where T : INetSerializable;
```
{% endcode %}

The `broadcast` argument determines whether it will be sent to _all other clients_. As the server, this is always `true`.

If you want to send to just one specific `NetPeer`, e.g. after receiving a packet and you want to respond to that peer:

{% code overflow="wrap" %}
```csharp
void SendDataToPeer<T>(ref T packet, DeliveryMethod deliveryMethod, NetPeer peer) where T : INetSerializable;
```
{% endcode %}

```mermaid
flowchart LR

A[Send from Client 1] --->|Packet| B[Receive on Server]
B --> C{Broadcast?}
C -->|Yes| D[Send to Client 2 & 3]
C -->|No| E[Done]
```

{% hint style="warning" %}
A client only has one `NetPeer` and it is _**always**_ the server! A client is never aware of other clients.
{% endhint %}

Some specific functions are class specific, and cannot be called from the interface singleton. You can access the specific `FikaServer` or `FikaClient` using e.g. `Singleton<FikaServer>.Instance`.

The specific methods are:

#### Client

{% code overflow="wrap" %}
```csharp
public void SendReusable<T>(T packet, DeliveryMethod deliveryMethod) where T : class, IReusable, new()
```
{% endcode %}

#### Server

{% code overflow="wrap" %}
```csharp
public void SendReusableToAll<T>(T packet, DeliveryMethod deliveryMethod, NetPeer peerToExlude = null) where T : class, IReusable, new()
```
{% endcode %}

***

## General Information About Data

{% hint style="info" %}
Keep in mind that performance and bandwidth is not free! Do not send redundant data every `Update()` unless you have to.&#x20;

Fika has a class that you can inherit called `ThrottledMono`, where you can set an `UpdateRate` which is how many times it should update per seconds. This can dramatically increase performance and reduce bandwidth used.
{% endhint %}

### Calculating Packet Size (UDP with Headers)

When sending data over a network using UDP, each packet consists of:

1. Your payload (the actual data, e.g., floats)
2. Packet-specific overhead (1–4 bytes depending on the type, e.g. `Unreliable` or `ReliableOrdered`)
3. UDP header (8 bytes)
4. IP header (20–60 bytes, depending on IPv4 options)

It’s important to account for all headers, not just the payload, because small payloads can become inefficient due to header overhead.

#### Formula

Let:

* _**N**_ = number of elements being sent
* _**S**_<sub>element</sub> = size of one element in bytes (e.g., 4 bytes for a `float`)
* _**H**_<sub>packet​</sub> = packet-specific overhead (1–4 bytes)
* _**H**_<sub>UDPH​</sub> = UDP header size (8 bytes)
* _**H**_<sub>IPH</sub>​ = IP header size (20–60 bytes)

Then, the **total packet size in bytes** is:

$$
Packet Size (bytes)=N×Selement​+Hpacket​+HUDP​+HIP​
$$

To convert to **bits**:

$$
Packet Size (bits)=8×(N×Selement+Hpacket+HUDP+HIP)
$$

***

#### Example

Suppose you are sending a `Vector3`, which is 3 floats (4 bytes each), with 2 bytes of packet-specific overhead, 8 bytes UDP header, and 20 bytes IP header:

$$
Packet Size=3×4+2+8+20=42 bytes
$$

$$
Packet Size in bits=42×8=336 bits
$$

Even this small payload, if sent frequently (e.g., every frame in a game), can consume significant bandwidth. Notice that even though the payload is only 12 bytes, headers increase the total packet size almost _**4×**_.\
\
Now imagine this being unthrottled, and the client is running at 120 FPS:\
We already have:

$$
Packet Size=42 bytes
$$

If we send 120 packets per second:

$$
Data per second (bytes)=42×120
$$

#### Step-by-step

* Packet size is 42 bytes.
* Sending 120 packets per second.
* Multiply packet size by number of packets: 42 × 120.
* Break it down:&#x20;

$$
42×120=42×(12×10)=(42×12)×10
$$

$$
42×12=504
$$

$$
504×10=5,040
$$

* Total data per second in bytes = 5,040 bytes.

Convert to bits:

$$
5,040×8=40,320 bits per second (bps)
$$

This is _**a lot**_ of wasted bandwidth and CPU usage. Unless it's critical, do not send data every tick. Rather, interpolate values on the receiving end if needed. Breaking it down further:

$$
Data transferred=5KB/s×60s=300KB
$$

That is 300KB per minute for _**one**_, _**single**_ `Vector3`. That is almost ¼ of the bandwidth that Fika sends for _**all bots states**_ every minute.

The size of one entire player state (52 bytes), 20/s:

$$
52×20=1040bytes/sec per entity
$$

Assuming we have 20 bots:

$$
1040×20=20,800bytes/sec total
$$

Now per minute:

$$
20,800×60=1,248,000bytes/minute ≈ 1,248MB/minute (1.19 MiB)
$$

### Interpolation

As you can see from the breakdown, this is a lot of wasted data that could be throttled and sent less frequently, and potentially interpolated instead by lerping the values and sending the time when sending and comparing with the time when received.

Interpolation factor _**t**_:

$$
t = \frac{\text{currentTime} - \text{sentTime}}{\text{receivedTime} - \text{sentTime}}
$$

Clamp _**t**_ between 0 and 1

$$
t = \max(0, \min(1, t))
$$

Linear interpolation formula:

$$
\text{lerpedValue} = \text{oldValue} + (\text{newValue} - \text{oldValue}) \cdot t
$$

You can then send the current time (`Time.unscaledTime`) and compare it with current time when received, and smooth out differences using the equations above.

#### Now comparing the different methods of sending:

20 messages/sec at 16 bytes:

$$
16 \times 20 = 320\ \text{bytes/sec}
$$

120 messages/sec at 12 bytes:

$$
12 \times 120 = 1{,}440\ \text{bytes/sec}
$$

That is \~1080bytes saved per second:

$$
1{,}440 - 320 = 1{,}120\ \text{bytes/sec}
$$

### Summary

Even though saving **1,12 KB per second** might seem small for a single message stream, network usage scales linearly.\
Each actor (or entity) may send several of these updates — position, rotation, state, velocity, and so on.\
When you multiply that by **dozens of properties per actor** and **many actors active at once**, the total bandwidth grows rapidly.

Optimizing even a few bytes or reducing send frequency per update can therefore lead to **massive overall savings** across the entire simulation or multiplayer session.

## Tips and useful classes

* [FikaBackendUtils](https://github.com/project-fika/Fika-Plugin/blob/main/Fika.Core/Coop/Utils/FikaBackendUtils.cs) has tons of useful methods/properties/fields that can be used.
* [FikaGlobals](https://github.com/project-fika/Fika-Plugin/blob/main/Fika.Core/Coop/Utils/FikaGlobals.cs) has some helper methods that can be useful during development.
* [CoopHandler](https://github.com/project-fika/Fika-Plugin/blob/main/Fika.Core/Coop/Components/CoopHandler.cs) has useful properties and methods, mainly to track players (especially human). It can be accessed on the `Singleton<IFikaNetworkManager>.Instance` or [CoopHandler.TryGetCoopHandler()](https://github.com/project-fika/Fika-Plugin/blob/18f02d5713b0e13cc02998b9e79489a55ac8249d/Fika.Core/Coop/Components/CoopHandler.cs#L62C40-L62C67) depending on your code style preference.
* [FikaSerializationExtensions](https://github.com/project-fika/Fika-Plugin/blob/47a9d37aa40e2e7cc0b9628c7114115cd3805cd4/Fika.Core/Networking/FikaSerializationExtensions.cs) have tons of good extension methods to handle data, e.g. packing a `float`. If precision is not important to the last decimal, it's recommended to pack your primitives.
