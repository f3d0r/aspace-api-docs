# Parking

## Test Parking Sub-API (Ping)

```http
GET /v1/parking/ping HTTP/1.1
Host: api.trya.space
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
GET /v1/parking/get_status?block_id=3 HTTP/1.1
Host: api.trya.space
```

```shell
curl --request GET \
  --url 'https://api.trya.space/v1/parking/get_status?block_id=3'
```

```javascript
var request = require("request");

var options = { method: 'GET',
  url: 'https://api.trya.space/v1/parking/get_status',
  qs: { block_id: '3' } };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});
```

```python
import requests

url = "https://api.trya.space/v1/parking/get_status"

querystring = {"block_id":"3"}

payload = ""
response = requests.request("GET", url, data=payload, params=querystring)

print(response.text)
```

> The above command returns JSON structured like this:

```json
[
  {
    "lng": -122.31808264747308,
    "lat": 47.61426461982815,
    "occupied": "F",
    "parking_price": 2.5,
    "block_id": 3,
    "spot_id": 2620
  },
  {
    "lng": -122.31808272044786,
    "lat": 47.61427558423165,
    "occupied": "F",
    "parking_price": 2.5,
    "block_id": 3,
    "spot_id": 2621
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
POST /v1/parking/get_status_bbox HTTP/1.1
Host: api.trya.space
Content-Type: application/json
Content-Length: 84
{
  "sw": {
      "lng": -180,
      "lat": -180
  },
  "ne": {
      "lng": 180,
      "lat": 180
  }
}
```

```shell
curl --request POST \
  --url https://api.trya.space/v1/parking/get_status_bbox \
  --header 'content-type: application/json' \
  --data '{
  "sw": {
    "lng": -180,
    "lat": -180
  },
  "ne": {
    "lng": 180,
    "lat": 180
  }
}'
```

```javascript
var request = require("request");

var options = { method: 'POST',
  url: 'https://api.trya.space/v1/parking/get_status_bbox',
  headers: { 'content-type': 'application/json' },
  body: { sw: { lng: -180, lat: -180 }, ne: { lng: 180, lat: 180 } },
  json: true };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});
```

```python
import requests

url = "https://api.trya.space/v1/parking/get_status_bbox"

payload = "{\n\t\"sw\": {\n\t\t\"lng\": -180,\n\t\t\"lat\": -180\n\t},\n\t\"ne\": {\n\t\t\"lng\": 180,\n\t\t\"lat\": 180\n\t}\n}"
headers = {'content-type': 'application/json'}

response = requests.request("POST", url, data=payload, headers=headers)

print(response.text)
```

> Request Body:

```json
{
  "sw": {
    "lng": -180,
    "lat": -180
  },
  "ne": {
    "lng": 180,
    "lat": 180
  }
}
```

> The above command returns JSON structured like this:

```json
[
  {
    "lng": -122.32080361279635,
    "lat": 47.613874629189766,
    "occupied": "N",
    "parking_price": 3.25,
    "block_id": 12,
    "spot_id": 841
  },
  {
    "lng": -122.32080411168269,
    "lat": 47.613929450727575,
    "occupied": "F",
    "parking_price": 3.25,
    "block_id": 12,
    "spot_id": 842
  }
]
```

This endpoint returns a subset of parking spots that are inside of a bounding box formed by the southwest and northeast latitude/longitude pairs given in the body of the request.

<aside class="warning">The format of the body must exactly match the one described below for the request to successfully process.</aside>

### HTTP Request

`POST https://api.trya.space/v1/parking/get_status_bbox`

### Request Body

See on right after sample code.

## Get Status by Radius

```http
POST /v1/parking/get_status_radius?radius_feet=50 HTTP/1.1
Host: api.trya.space
Content-Type: application/json
Content-Length: 40
{
    "lng": -122.3208,
    "lat": 47.613874
}
```

```shell
curl --request POST \
  --url 'https://api.trya.space/v1/parking/get_status_radius?radius_feet=50' \
  --header 'content-type: application/json' \
  --data '{
  "lng": -122.3208,
  "lat": 47.613874
}'
```

```javascript
var request = require("request");

var options = { method: 'POST',
  url: 'https://api.trya.space/v1/parking/get_status_radius',
  qs: { radius_feet: '50' },
  headers: { 'content-type': 'application/json' },
  body: { lng: -122.3208, lat: 47.613874 },
  json: true };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});
```

```python
import requests

url = "https://api.trya.space/v1/parking/get_status_radius"

querystring = {"radius_feet":"50"}

payload = "{\n\t\"lng\": -122.3208,\n\t\"lat\": 47.613874\n}"
headers = {'content-type': 'application/json'}

response = requests.request("POST", url, data=payload, headers=headers, params=querystring)

print(response.text)
```

> Request Body:

```json
{
  "lng": -122.3208,
  "lat": 47.613874
}
```

> The above command returns JSON structured like this:

```json
[
  {
    "lng": -122.32080361279635,
    "lat": 47.613874629189766,
    "occupied": "N",
    "parking_price": 3.25,
    "block_id": 12,
    "spot_id": 841,
    "distance": 0.00017698109149932864
  },
  {
    "lng": -122.32080411168269,
    "lat": 47.613929450727575,
    "occupied": "F",
    "parking_price": 3.25,
    "block_id": 12,
    "spot_id": 842,
    "distance": 0.0038368586332700873
  }
]
```

This endpoint returns a subset of parking spots that are inside of a circle with radius (in feet) centered at the latitude/longitude pair given in the body.

<aside class="warning">The format of the body must exactly match the one described below for the request to successfully process.</aside>

### HTTP Request

`POST https://api.trya.space/v1/parking/get_status_radius`

### URL Parameters

| Parameter | Description                    |
| --------- | ------------------------------ |
| `radius_feet` | The bounding circle's radius in feet. |

## Get Min-Sized Parking Spots by Radius

```http
POST /v1/parking/get_min_size_parking?radius_feet=5000&spot_size_feet=10 HTTP/1.1
Host: api.trya.space
Content-Type: application/json
Content-Length: 41
{
    "lng": -122.3208,
    "lat": 47.613874
}
```

```shell
curl --request POST \
  --url 'https://api.trya.space/v1/parking/get_min_size_parking?radius_feet=5000&spot_size_feet=10' \
  --header 'content-type: application/json' \
  --data '{
  "lng": -122.3208,
  "lat": 47.613874
}
```

```javascript
var request = require("request");

var options = { method: 'POST',
  url: 'https://api.trya.space/v1/parking/get_min_size_parking',
  qs: { radius_feet: '5000', spot_size_feet: '10' },
  headers: { 'content-type': 'application/json' },
  body: { lng: -122.3208, lat: 47.613874 },
  json: true };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});
```

```python
import requests

url = "https://api.trya.space/v1/parking/get_min_size_parking"

querystring = {"radius_feet":"5000","spot_size_feet":"10"}

payload = "{\n\t\"lng\": -122.3208,\n\t\"lat\": 47.613874\n}\n"
headers = {'content-type': 'application/json'}

response = requests.request("POST", url, data=payload, headers=headers, params=querystring)

print(response.text)
```

> Request Body:

```json
{
  "lng": -122.3208,
  "lat": 47.613874
}
```

> The above command returns JSON structured like this:

```json
[
  {
    "lng": -122.31808286639756,
    "lat": 47.6142975130387,
    "occupied": "F",
    "parking_price": 2.5,
    "block_id": 3,
    "spot_id": 2623,
    "distance": 0.12990350497275932
  },
  {
    "lng": -122.31808323127233,
    "lat": 47.614352335056275,
    "occupied": "F",
    "parking_price": 2.5,
    "block_id": 3,
    "spot_id": 2628,
    "distance": 0.13079241931625346
  }
]
```

This endpoint returns a subset of parking spots that are inside of a circle with radius (in feet) centered at the latitude/longitude pair given in the body and are large enough for a car of `spot_size_feet`.

<aside class="warning">The format of the body must exactly match the one described below for the request to successfully process.</aside>

### HTTP Request

`POST https://api.trya.space/v1/parking/get_status_radius`

### URL Parameters

| Parameter | Description                    |
| --------- | ------------------------------ |
| `radius_feet` | The bounding circle's radius in feet. |
| `spot_size_feet` | The minimum open parking spot size in feet to search. |

### Request Body

See on right after sample code.

## Check Block ID Exists

```http
GET /v1/parking/block_id_exists?block_id=5 HTTP/1.1
Host: api.trya.space
```

```shell
curl --request GET \
  --url 'https://api.trya.space/v1/parking/block_id_exists?block_id=5'
```

```javascript
var request = require("request");

var options = { method: 'GET',
  url: 'https://api.trya.space/v1/parking/block_id_exists',
  qs: { block_id: '5' } };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});
```

```python
import requests

url = "https://api.trya.space/v1/parking/block_id_exists"

querystring = {"block_id":"5"}

payload = ""
response = requests.request("GET", url, data=payload, params=querystring)

print(response.text)
```

> The above command returns JSON structured like this:

```json
{
  "block_id_exists": "T"
}
```

This endpoint returns whether the Block ID given exists. It returns true (`T`) if there is at least one spot exists that is assigned to the `block_id` or false (`F`) if there are no spots assigned to it.

### HTTP Request

`GET https://api.trya.space/v1/parking/block_id_exists`

### URL Parameters

| Parameter | Description                    |
| --------- | ------------------------------ |
| `block_id` | The block ID you're checking exists. |

## Update Spot Status

<aside class="warning">This endpoint method requires an auth_key with the <code>update_status</code> permission. Please go <a href="https://api.trya.space/v1/admin/get_auth_key">here</a> if you need a new auth_key.</aside>

```http
POST /v1/parking/update_status?spot_id=841&occupied=N&auth_key=some-authentication-key HTTP/1.1
Host: api.trya.space
Content-Length: 0
```

```shell
curl --request POST \
  --url 'https://api.trya.space/v1/parking/update_status?spot_id=841&occupied=N&auth_key=some-authentication-key'
```

```javascript
var request = require("request");

var options = { method: 'POST',
  url: 'https://api.trya.space/v1/parking/update_status',
  qs:
   { spot_id: '841',
     occupied: 'N',
     auth_key: 'some-authentication-key' } };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});
```

```python
import requests

url = "https://api.trya.space/v1/parking/update_status"

querystring = {"spot_id":"841","occupied":"N","auth_key":"some-authentication-key"}

payload = ""
response = requests.request("POST", url, data=payload, params=querystring)

print(response.text)
```

> The above command returns JSON structured like this:

```json
{
  "error": {
    "error_code": 19,
    "error_info": "spot_status_changed"
  }
}
```

This endpoint is used to update a single parking spot with an updated occupancy status. It requires an auth_key with authority to change parking spot statuses (`update_status`). The only allowable values for the `occupied` parameter are `T` (true), `F` (false), and `N` (not available). If a request is made to change the status of a spot that doesn't exist or the `occupied` parameter is not one of the allowed values, an error is returned.

### HTTP Request

`POST https://api.trya.space/v1/parking/update_status`

### URL Parameters

| Parameter | Description                    |
| --------- | ------------------------------ |
| `spot_id` | The spot ID of the spot status you're changing. |
| `occupied` (Must be `T`, `F`, or `N`) | The updated occupancy status of the spot. |
| `auth_key` | An auth_key that has the authority to change spot statuses (`update_status`). |

## Upload Spots

<aside class="warning">This endpoint method requires an auth_key with the <code>upload_spots</code> permission. Please go <a href="https://api.trya.space/v1/admin/get_auth_key">here</a> if you need a new auth_key.</aside>

```http
POST /v1/parking/upload_spots?block_id=11&auth_key=***REMOVED*** HTTP/1.1
Host: api.trya.space
Content-Type: application/json
Content-Length: 166
[
    {
      "lng": -122.32145622348536,
      "lat": 47.61524252172283,
      "block_id": 40
    },
    {
      "lng": -122.32144809134007,
      "lat": 47.61524258185267,
      "block_id": 40
  }
]
```

```shell
curl --request POST \
  --url 'https://api.trya.space/v1/parking/upload_spots?block_id=11&auth_key=***REMOVED***' \
  --header 'content-type: application/json' \
  --data '[
  {
    "lng": -122.32145622348536,
    "lat": 47.61524252172283,
    "block_id": 40
  },
  {
    "lng": -122.32144809134007,
    "lat": 47.61524258185267,
    "block_id": 40
  }
]'
```

```javascript
var request = require("request");

var options = { method: 'POST',
  url: 'https://api.trya.space/v1/parking/upload_spots',
  qs: { block_id: '11', auth_key: '***REMOVED***' },
  headers: { 'content-type': 'application/json' },
  body:
   [ { lng: -122.32145622348536,
       lat: 47.61524252172283,
       block_id: 40 },
     { lng: -122.32144809134007,
       lat: 47.61524258185267,
       block_id: 40 } ],
  json: true };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});
```

```python
import requests

url = "https://api.trya.space/v1/parking/upload_spots"

querystring = {"block_id":"11","auth_key":"***REMOVED***"}

payload = "[\n\t{\n\t\t\"lng\": -122.32145622348536,\n\t\t\"lat\": 47.61524252172283,\n\t\t\"block_id\": 40\n\t},\n\t{\n\t\t\"lng\": -122.32144809134007,\n\t\t\"lat\": 47.61524258185267,\n\t\t\"block_id\": 40\n\t}\n]"
headers = {'content-type': 'application/json'}

response = requests.request("POST", url, data=payload, headers=headers, params=querystring)

print(response.text)
```

This endpoint is used to upload/add new spots to the aspace database. It requires an `auth_key` with authority to upload parking spot statuses (`upload_spots`). The request body must be in the exact form as the code examples, or the request will fail. Upon the completion of a successful request, all the spots in the body will be added to the database with the given `block_id`. Upon success, the request will return the raw text `SUCCESS`. The `block_id` given in this request **does not** need to be unique for the request to be successful, but it is highly recommended to be unique.

### HTTP Request

`POST https://api.trya.space/v1/parking/upload_spots`

### URL Parameters

| Parameter | Description                    |
| --------- | ------------------------------ |
| `block_id` | The block ID assigned to be assigned to the uploaded spots. |
| `auth_key` | An auth_key that has the authority to upload new spots (`upload_spots`). |