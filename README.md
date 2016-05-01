# Tenna API documentation

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

Response:

    [
        {
            _id: '570c4223ecd694f46f863350',
            avatar: 'http://i.imgur.com/aJgYIZ8.jpg',
            name: 'Hallway motion',
            user_id: '56943c7b52cfc9f36540bf26'
        },
        ...
    ]

### Creating a device

    POST /devices.json

## Channels

### Your channels

    GET /channels.json

Response:

    [
        {
            _id: '5719186f6ab7ba112776160e',
            description: 'Weather conditions around the Bay Area.',
            device_ids: [
                '571916b6821672841359909b',
                '571900ce821672841359904f'
            ],
            name: 'Silicon Valley weather'
        },
        ...
    ]

### Device channels

    GET /devices/[device_id]/channels.json

### Creating a channel

    POST /channels.json

## Events

### Your events stream

    GET /events.json

### Device events

    GET /devices/[device_id]/events.json

Response:

    [
        {
            _id: '572642f02ab4788d0fc74dc0',
            device_id: '56943e8e52cfc9f36540bf28',
            kind: 'humidity',
            data: {
                value: 47.7,
                unit: '%'
            },
            created_at: 1462125296000
        },
        ...
    ]

### Channel events

    GET /channels/[channel_id]/events.json

### Creating an event

    POST /devices/[device_id]/events/[kind].json

## Subscriptions

### Device subscriptions

    GET /devices/[device_id]/subscriptions.json

### Channel subscriptions

    GET /channels/[channel_id]/subscriptions.json

### Creating a device subscription

    POST /devices/[device_id]/subscriptions.json

### Creating a channel subscription

    POST /channels/[channel_id]/subscriptions.json
