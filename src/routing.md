# Routing

## Test Routing Sub-API (Ping)

```http
GET /v1/routing/ping HTTP/1.1
Host: api.trya.space
```

```shell
curl --request GET \
  --url https://api.trya.space/v1/routing/ping
```

```javascript
var request = require("request");

var options = { method: 'GET', url: 'https://api.trya.space/v1/routing/ping' };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});
```

```python
import requests

url = "https://api.trya.space/v1/routing/ping"

payload = ""
response = requests.request("GET", url, data=payload)

print(response.text)
```

> Example JSON return:

```json
{
  "res_info": {
    "code": 31,
    "code_info": "ROUTING_ENDPOINT_FUNCTION_SUCCESS"
  },
  "res_content": "pong"
}
```

This endpoint is used to test the functionality/response of the Routing Sub-API.

### HTTP Request

`GET https://api.trya.space/v1/routing/ping`

<aside class="notice">If you are receiving an error with this endpoint for an extended period of time, please <a href="mailto:help@trya.space">send</a> the error you receive to the API admin.</aside>

## Get Route Options

```http
POST /v1/get_drive_walk_route?origin_lat=47.7930&origin_lng=-122.3584&dest_lat=47.6057&dest_lng=-122.3336 HTTP/1.1
Host: routing.trya.space
```

```shell
curl --request POST \
  --url 'https://routing.trya.space/v1/get_drive_walk_route?origin_lat=47.7930&origin_lng=-122.3584&dest_lat=47.6057&dest_lng=-122.3336'
```

```javascript
var request = require("request");

var options = { method: 'POST',
  url: 'https://routing.trya.space/v1/get_drive_walk_route',
  qs:
   { origin_lat: '47.7930',
     origin_lng: '-122.3584',
     dest_lat: '47.6057',
     dest_lng: '-122.3336' } };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});
```

```python
import http.client

conn = http.client.HTTPSConnection("routing.trya.space")

payload = ""

conn.request("POST", "/v1/get_drive_walk_route?origin_lat=47.7930&origin_lng=-122.3584&dest_lat=47.6057&dest_lng=-122.3336", payload)

res = conn.getresponse()
data = res.read()

print(data.decode("utf-8"))
```

> Example JSON return:

```json
{
    "res_info": {
        "code": 31,
        "code_info": "ROUTING_ENDPOINT_FUNCTION_SUCCESS"
    },
    "res_content": {
        "waypoint_info": [
            {
                "lng": -122.31804918025684,
                "lat": 47.612520220158785,
                "occupied": "F",
                "parking_price": 2.5,
                "block_id": -1,
                "spot_id": 2792,
                "distance": 0.8642236898045454,
                "driving_time": 1403.7,
                "walking_time": 1037.7
            }
        ],
        "routes": [
            [
                {
                    "name": "drive_park",
                    "pretty_name": "Drive to Parking",
                    "origin": {
                        "lng": "-122.3584",
                        "lat": "47.7930"
                    },
                    "dest": {
                        "meta": {
                            "occupied": "F",
                            "parking_price": 2.5,
                            "block_id": -1,
                            "spot_id": 2792,
                            "distance": 0.8642236898045454,
                            "driving_time": 1403.7,
                            "walking_time": 1037.7
                        },
                        "lng": -122.31804918025684,
                        "lat": 47.612520220158785
                    },
                    "directions": {}
                },
                {
                    "name": "walk_dest",
                    "pretty_name": "Walk to Destination",
                    "origin": {
                        "meta": {
                            "occupied": "F",
                            "parking_price": 2.5,
                            "block_id": -1,
                            "spot_id": 2792,
                            "distance": 0.8642236898045454,
                            "driving_time": 1403.7,
                            "walking_time": 1037.7
                        },
                        "lng": -122.31804918025684,
                        "lat": 47.612520220158785
                    },
                    "dest": {
                        "lng": "-122.3336",
                        "lat": "47.6057"
                    },
                    "directions": {}
                }
            ]
        ]
    }
}
```

This endpoint is used to get the waypoints and fastest route segments for the drive-walk, drive-bike, and drive-direct route options.

### HTTP Request

`POST https://routing.trya.space/v1/ROUTE_OPTION`

### Path Parameters

| Parameter                 | Description                                   |
| ------------------------- | --------------------------------------------- |
| `ROUTE_OPTION` | `get_drive_walk_route`, `get_drive_bike_route`, or `get_drive_direct_route` for the route option you're requesting. |

### URL Parameters

| Parameter                 | Description                                   |
| ------------------------- | --------------------------------------------- |
| `origin_lat` | The origin latitude for the requested route. |
| `origin_lng` | The origin longitude for the requested route. |
| `dest_lat` | The destination latitude for the requested route. |
| `dest_lng` | The destination longitude for the requested route. |