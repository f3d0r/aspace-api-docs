# Parking

## Test Endpoint

```http
GET /v1/parking/ping HTTP/1.1
Host: api.trya.space
Cache-Control: no-cache
```

```shell
curl --request GET \
  --url https://api.trya.space/v1/parking/ping
```

```javascript
var request = require("request");

var options = { method: 'GET', url: 'https://api.trya.space/v1/parking/ping' };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});

```

```python
import requests

url = "https://api.trya.space/v1/parking/ping"

payload = ""
response = requests.request("GET", url, data=payload)

print(response.text)
```

This endpoint returns `pong` if the sub-API is working properly, and an error otherwise.

### HTTP Request

`GET https://api.trya.space/v1/parking/ping`

<aside class="notice">If you are receiving an error with this endpoint for an extended period of time, please <a href="mailto:help@trya.space">send</a> the error you receive to the API admin.</aside>

## Get Status by ID

```http
GET /v1/parking/get_status?block_id=12 HTTP/1.1
Host: api.trya.space
```

```shell
curl --request GET \
  --url 'https://api.trya.space/v1/parking/get_status?block_id=12'
```

```javascript
var request = require("request");

var options = { method: 'GET',
  url: 'https://api.trya.space/v1/parking/get_status',
  qs: { block_id: '12' } };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});
```

```python
import requests

url = "https://api.trya.space/v1/parking/get_status"

querystring = {"block_id":"12"}

payload = ""
response = requests.request("GET", url, data=payload, params=querystring)

print(response.text)
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

## Get Status by Bounding Box

```http
GET /v1/parking/get_status_bbox HTTP/1.1
Host: api.trya.space
Content-Type: application/json
Accept: */*
Content-Length: 110
{
  "sw": {
    "lat": "47.612",
    "lng": "-122.325"
},
  "ne": {
    "lat": "47.615",
    "lng": "-122.321"
  }
}
```

```shell
curl --request GET \
  --url https://api.trya.space/v1/parking/get_status_bbox \
  --header 'content-type: application/json' \
  --data '{
  "sw": {
    "lat": "47.612",
    "lng": "-122.325"
},
  "ne": {
    "lat": "47.615",
    "lng": "-122.321"
  }
}'
```

```javascript
var request = require("request");

var options = { method: 'GET',
  url: 'https://api.trya.space/v1/parking/get_status_bbox',
  headers: { 'content-type': 'application/json' },
  body:
   { sw: { lat: '47.612', lng: '-122.325' },
     ne: { lat: '47.615', lng: '-122.321' } },
  json: true };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});
```

```python
import requests

url = "https://api.trya.space/v1/parking/get_status_bbox"

payload = "{\n\t\"sw\": {\t\t\n\t\t\"lat\": \"47.612\",\n\t\t\"lng\": \"-122.325\"\n\t},\n\t\"ne\": {\n\t\t\"lat\": \"47.615\",\n\t\t\"lng\": \"-122.321\"\t\t\n\t}\n}"
headers = {'content-type': 'application/json'}

response = requests.request("GET", url, data=payload, headers=headers)

print(response.text)
```

> Request Body:

```json
{
  "sw": {
    "lat": "47.612",
    "lng": "-122.325"
  },
  "ne": {
    "lat": "47.615",
    "lng": "-122.321"
  }
}
```

> The above command returns JSON structured like this:

```json
[
  {
  "lng": -122.3215097929318,
    "lat": 47.614974923505294,
    "occupied": "F",
    "block_id": 12,
    "spot_id": 1286
  },
  {
    "lng": -122.32145348673973,
    "lat": 47.614935365765646,
    "occupied": "F",
    "block_id": 12,
    "spot_id": 1287
  },
]
```

This endpoint returns a subset of parking spots that are inside of a bounding box formed by the southwest and northeast latitude/longitude pairs given in the body.

<aside class="warning">The format of the body must exactly match the one described below for the request to successfully process.</aside>

### HTTP Request

`GET https://api.trya.space/v1/parking/get_status_bbox`

### Request Body

See on right after sample code.

## Get Status by Radius

```http
GET /parking/get_status_radius?radius_feet=500 HTTP/1.1
Host: localhost:3000
Content-Type: application/json
Accept: */*
Content-Length: 63
{
  "lat": "47.612887841508865",
  "lng": "-122.32079463302121"
}
```

```shell
curl --request GET \
  --url 'http://localhost:3000/parking/get_status_radius?radius_feet=500' \
  --header 'content-type: application/json' \
  --data '{
  "lat": "47.612887841508865",
  "lng": "-122.32079463302121"
}'
```

```javascript
var request = require("request");

var options = { method: 'GET',
  url: 'http://localhost:3000/parking/get_status_radius',
  qs: { radius_feet: '500' },
  headers: { 'content-type': 'application/json' },
  body: { lat: '47.612887841508865', lng: '-122.32079463302121' },
  json: true };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});
```

```python
import requests

url = "http://localhost:3000/parking/get_status_radius"

querystring = {"radius_feet":"500"}

payload = "{\n\t\"lat\": \"47.612887841508865\",\n\t\"lng\": \"-122.32079463302121\"\n}"
headers = {'content-type': 'application/json'}

response = requests.request("GET", url, data=payload, headers=headers, params=querystring)

print(response.text)
```

> Request Body:

```json
{
  "lat": "47.612887841508865",
  "lng": "-122.32079463302121"
}
```

> The above command returns JSON structured like this:

```json
[
  {
    "lng": -122.32079463302121,
    "lat": 47.612887841508865,
    "occupied": "F",
    "block_id": 12,
    "spot_id": 823,
    "distance": 0
  },
  {
    "lng": -122.32079513188872,
    "lat": 47.61294266304671,
    "occupied": "N",
    "block_id": 12,
    "spot_id": 824,
    "distance": 0.003788020161908459
  }
]
```

This endpoint returns a subset of parking spots that are inside of a circle with radius (in feet) centered at the latitude/longitude pair given in the body.

<aside class="warning">The format of the body must exactly match the one described below for the request to successfully process.</aside>

### HTTP Request

`GET https://api.trya.space/v1/parking/get_status_radius`

### URL Parameters

| Parameter | Description                    |
| --------- | ------------------------------ |
| `radius_feet` | The bounding circle's radius in feet. |

### Request Body

See on right after sample code.

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
