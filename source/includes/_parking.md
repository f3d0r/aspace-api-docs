# Parking

## Test Endpoint

```http
GET /v1/parking/ping HTTP/1.1
Host: api.trya.space
Cache-Control: no-cache
```

```shell
curl -X GET \
  https://api.trya.space/v1/parking/ping \
  -H 'Cache-Control: no-cache'
```

```javascript
var request = require('request');

var headers = {
    'Cache-Control': 'no-cache'
};

var options = {
    url: 'https://api.trya.space/v1/parking/ping',
    headers: headers
};

function callback(error, response, body) {
    if (!error && response.statusCode == 200) {
        console.log(body);
    }
}

request(options, callback);
```

```python
import requests

headers = {
    'Cache-Control': 'no-cache',
}

response = requests.get('https://api.trya.space/v1/parking/ping', headers=headers)
```

This endpoint returns `pong` if the sub-API is working properly, and an error otherwise.

### HTTP Request

`GET https://api.trya.space/v1/parking/ping`

<aside class="notice">If you are receiving an error with this endpoint for an extended period of time, please <a href="mailto:help@trya.space">send</a> the error you receieve to the API admin.</aside>

## Get Status by ID

```http
GET /v1/parking/get_status?block_id=14 HTTP/1.1
Host: api.trya.space
Cache-Control: no-cache
```

```shell
curl -X GET \
  'https://api.trya.space/v1/parking/get_status?block_id=14' \
  -H 'Cache-Control: no-cache'
```

```javascript
var request = require('request');

var headers = {
    'Cache-Control': 'no-cache'
};

var options = {
    url: 'https://api.trya.space/v1/parking/get_status?block_id=14',
    headers: headers
};

function callback(error, response, body) {
    if (!error && response.statusCode == 200) {
        console.log(body);
    }
}

request(options, callback);
```

```python
import requests

headers = {
    'Cache-Control': 'no-cache',
}

params = (
    ('block_id', '14')
)

response = requests.get('https://api.trya.space/v1/parking/get_status', headers=headers, params=params)
```

> The above command returns JSON structured like this:

```json
[
    {
        "lng": -122.32494723593786,
        "lat": 47.61643451627367,
        "occupied": "F",
        "block_id": 14,
        "spot_id": 1292
    },
    {
        "lng": -122.32489910551402,
        "lat": 47.61639032483804,
        "occupied": "F",
        "block_id": 14,
        "spot_id": 1293
    }
]
```

This endpoint returns a subset of parking spots matching the given spot_id, block_id, or both.

<aside class="notice">Only one of the parameters <code>spot_id</code> or <code>block_id</code> is required to complete this request.</aside>

### HTTP Request

`GET https://api.trya.space/v1/parking/get_status`

### URL Parameters

| Parameter                 | Description                                   |
| ------------------------- | --------------------------------------------- |
| `spot_id` (one required)  | The spot_id of the parking spot.              |
| `block_id` (one required) | The block_id of a selection of parking spots. |

## Check Block ID Exists

```http
GET /v1/parking/block_id_exists?block_id=1 HTTP/1.1
Host: api.trya.space
Cache-Control: no-cache
```

```shell
curl -X GET \
  'https://api.trya.space/v1/parking/block_id_exists?block_id=1' \
  -H 'Cache-Control: no-cache'
```

```javascript
var request = require('request');

var headers = {
    'Cache-Control': 'no-cache'
};

var options = {
    url: 'https://api.trya.space/v1/parking/block_id_exists?block_id=1',
    headers: headers
};

function callback(error, response, body) {
    if (!error && response.statusCode == 200) {
        console.log(body);
    }
}

request(options, callback);
```

```python
import requests

headers = {
    'Cache-Control': 'no-cache',
}

params = (
    ('block_id', '1'),
)

response = requests.get('https://api.trya.space/v1/parking/block_id_exists', headers=headers, params=params)
```

> The above command returns JSON structured like this:

```json
{
    "block_id_exists": "F"
}
```

This endpoint returns whether the given Block ID exists. It return `block_id_exists = "F"` if it doesn't and `block_id_exists = "T"` if it does.

### HTTP Request

`GET https://api.trya.space/v1/parking/block_id_exists`

### URL Parameters

| Parameter | Description                    |
| --------- | ------------------------------ |
| `block_id` | The block ID you're checking exists. |
