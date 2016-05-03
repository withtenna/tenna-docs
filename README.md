# Tenna API documentation

* Devices
    * [Your devices](#your-devices)
    * [Create a device](#create-a-device)
* Channels
    * [Your channels](#your-channels)
    * [Device channels](#device-channels)
    * [Create a channel](#create-a-channel)
* Events
    * [Your event stream](#your-event-stream)
    * [Device events](#device-events)
    * [Channel events](#channel-events)
    * [Create an event](#create-an-event)
* Subscriptions
    * [Device subscriptions](#device-subscriptions)
    * [Channel subscriptions](#channel-subscriptions)
    * [Create a device subscription](#create-a-device-subscription)
    * [Create a channel subscription](#create-a-channel-subscription)

## Overview

### API keys

Every request requires  an API key to authenticate. The API key can be passed in any URL as a query parameter, e.g.

    http://api.tenna.io/devices.json?api_key=[API_KEY]
    
or by providing the API key in the HTTP headers:

    api-key: [API_KEY]

Generate an API key by visiting [your settings page](http://api.tenna.io/settings).

## Devices

### Your devices

    GET /devices.json

Response: `[Device]`

```json
[
    {
        _id: "570c4223ecd694f46f863350",
        avatar: "http://i.imgur.com/aJgYIZ8.jpg",
        name: "Hallway motion",
        user_id: "56943c7b52cfc9f36540bf26"
    },
    ...
]
```

### Create a device

    POST /devices.json

Body: `Device`

Response: `Device`

## Channels

### Your channels

    GET /channels.json

Response: `[Channel]`

```json
[
    {
        _id: "5719186f6ab7ba112776160e",
        name: "Silicon Valley weather",
        description: "Weather conditions around the Bay Area.",
        device_ids: [
            "571916b6821672841359909b",
            "571900ce821672841359904f"
        ]
    },
    ...
]
```

### Device channels

    GET /devices/[device_id]/channels.json

Response: `[Channel]`

### Create a channel

    POST /channels.json

Body: `Channel`

```json
{
    name: "Garden",
    description: "Helping the plants grow with sensors"
}
```

Response: `Channel`

## Events

### Your event stream

    GET /events.json

Response: `[Event]`

### Device events

    GET /devices/[device_id]/events.json

Response: `[Event]`

```json
[
    {
        _id: "572642f02ab4788d0fc74dc0",
        device_id: "56943e8e52cfc9f36540bf28",
        kind: "humidity",
        data: {
            value: 47.7,
            unit: "%"
        },
        created_at: 1462125296000
    },
    ...
]
```

### Channel events

    GET /channels/[channel_id]/events.json

Response: `[Event]`

### Create an event

    POST /devices/[device_id]/events/[kind].json

Body: `Data` (common examples given)

```json
{
    value: 53.6,
    unit: "USD"
}
```

```json
{
    on: false
}
```

Response: `Event`

```json
{
    _id: "572806472ab4788d0fc753d9",
    device_id: "56943c9252cfc9f36540bf27",
    kind: "temperature",
    data: {
        value: 75.1999,
        unit: "F"
    },
    created_at: 1462240839000
}
```

## Subscriptions

### Device subscriptions

    GET /devices/[device_id]/subscriptions.json

Response: `[Subscription]`

### Channel subscriptions

    GET /channels/[channel_id]/subscriptions.json

Response: `[Subscription]`

### Create a device subscription

    POST /devices/[device_id]/subscriptions.json

Body: `Subscription`

Response: `Subscription`

### Create a channel subscription

    POST /channels/[channel_id]/subscriptions.json

Body: `Subscription`

Response: `Subscription`
