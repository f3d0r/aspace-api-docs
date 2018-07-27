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

This endpoint is to test the functionality/response of the Routing Sub-API.

### HTTP Request

`GET https://api.trya.space/v1/routing/ping`

<aside class="notice">If you are receiving an error with this endpoint for an extended period of time, please <a href="mailto:help@trya.space">send</a> the error you receive to the API admin.</aside>

## Get Routing Waypoints

```http
  POST /v1/routing/get_route_waypoints HTTP/1.1
  Host: api.trya.space
  Content-Type: application/json
  Content-Length: 117
  {
    "origin": {
      "lng": -122.32,
      "lat": 47.61
    },
    "dest": {
      "lng": -122.45,
      "lat": 37.91
    },
    "car_size": 10
  }
```

```shell
curl --request POST \
  --url https://api.trya.space/v1/routing/get_route_waypoints \
  --header 'content-type: application/json' \
  --data '{
  "origin": {
    "lng": -122.32,
    "lat": 47.61
  },
  "dest": {
    "lng": -122.45,
    "lat": 37.91
  },
  "car_size": 10
}'
```

```javascript
var request = require("request");

var options = { method: 'POST',
  url: 'https://api.trya.space/v1/routing/get_route_waypoints',
  headers: { 'content-type': 'application/json' },
  body:
   { origin: { lng: -122.32, lat: 47.61 },
     dest: { lng: -122.45, lat: 37.91 },
     car_size: 10 },
  json: true };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});
```

```python
import requests

url = "https://api.trya.space/v1/routing/get_route_waypoints"

payload = "{\n\t\"origin\": {\n\t\t\"lng\": -122.32,\n\t\t\"lat\": 47.61\n\t},\n\t\"dest\": {\n\t\t\"lng\": -122.45,\n\t\t\"lat\": 37.91\n\t},\n\t\"car_size\": 10\n}"
headers = {'content-type': 'application/json'}

response = requests.request("POST", url, data=payload, headers=headers)

print(response.text)
```

> Example JSON return:

```json
TO BE UPDATED
```

This endpoint returns a list of route waypoints (latitude and longitude pairs) that are a best-fit along a user's route in accordance with a user's current origin and destination.

### HTTP Request

`POST https://api.trya.space/api/v1/routing/get_route_waypoints`

<aside class="notice">Due to the nature of the long calculations made on the back-end when this endpoint is called, it may take much longer to receive results of this method compared to other endpoints in the aspace API.</aside>