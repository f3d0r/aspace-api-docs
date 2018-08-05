# User Info

## Test User Info Sub-API (Ping)

```http
GET /v1/user/ping HTTP/1.1
Host: api.trya.space
```

```shell
curl --request GET \
  --url https://api.trya.space/v1/user/ping
```

```javascript
var request = require("request");

var options = { method: 'GET', url: 'https://api.trya.space/v1/user/ping' };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});

```

```python
import requests

url = "https://api.trya.space/v1/user/ping"

payload = ""
response = requests.request("GET", url, data=payload)

print(response.text)
```

> Example JSON return:

```json
{
    "res_info": {
        "code": 35,
        "code_info": "USER_ENDPOINT_FUNCTION_SUCCESS"
    },
    "res_content": "pong"
}
```

This endpoint is used to test the functionality/response of the User Info Sub-API.

### HTTP Request

`GET https://api.trya.space/v1/user/ping`

<aside class="notice">If you are receiving an error with this endpoint for an extended period of time, please <a href="mailto:help@trya.space">send</a> the error you receive to the API admin.</aside>

## Update Profile Pic

```http
POST /v1/user/update_profile_pic?access_code=some-access-code&device_id=some-device-id HTTP/1.1
Host: api.trya.space
Content-Type: multipart/form-data
Content-Length: 242007
```

```shell
curl --request POST \
  --url 'https://api.trya.space/v1/user/update_profile_pic?access_code=some-access-code&device_id=some-device-id' \
  --form photo=some-local-photo-here
```

```javascript
var request = require("request");

var options = { method: 'POST',
  url: 'https://api.trya.space/v1/user/update_profile_pic',
  qs: { access_code: 'some-access-code', device_id: 'some-device-id' },
  headers: { 'content-type': 'multipart/form-data; boundary=---011000010111000001101001' },
  formData: { photo: 'some-local-photo-here' } };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});

```

```python
import requests

url = "https://api.trya.space/v1/user/update_profile_pic"

querystring = {"access_code":"some-access-code","device_id":"some-device-id"}

payload = "-----011000010111000001101001\r\nContent-Disposition: form-data; name=\"photo\"\r\n\r\n"
headers = {'content-type': 'multipart/form-data; boundary=---011000010111000001101001'}

response = requests.request("POST", url, data=payload, headers=headers, params=querystring)

print(response.text)
```

> Example JSON return:

```json
{
    "res_info": {
        "code": 38,
        "code_info": "PROFILE_PIC_UPDATED"
    },
    "res_content": "s3_bucket_url***REMOVED***a90a9e7f11c6d32bde4f23a955d747ad.png"
}
```

This endpoint updates a user's (user_id that matches `access_code` and `device_id`) profile picture that is given in the multi-part body as `photo`. It then returns the URL where that profile pic is accessible.

### HTTP Request

`POST https://api.trya.space/v1/user/update_profile_pic`

### URL Parameters

| Parameter                 | Description                                   |
| ------------------------- | --------------------------------------------- |
| `access_code` | The access code of the user received during authentication. |
| `device_id` | The device ID corresponding to the access key received during authentication. |
| `photo` (body) | The photo to update the profile picture of the user to. |

<aside class="notice">When updating an existing profile picture to a new photo, the URL where the photo is stored doesn't change.</aside>

## Get Profile Pic

```http
GET /v1/user/get_profile_pic?access_code=some-access-code&device_id=some-device-id HTTP/1.1
Host: api.trya.space
Accept: */*
```

```shell
curl --request GET \
  --url 'https://api.trya.space/v1/user/get_profile_pic?access_code=some-access-code&device_id=some-device-id'
```

```javascript
var request = require("request");

var options = { method: 'GET',
  url: 'https://api.trya.space/v1/user/get_profile_pic',
  qs: { access_code: 'some-access-code', device_id: 'some-device-id' } };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});
```

```python
import requests

url = "https://api.trya.space/v1/user/get_profile_pic"

querystring = {"access_code":"some-access-code","device_id":"some-device-id"}

payload = ""
response = requests.request("GET", url, data=payload, params=querystring)

print(response.text)
```

> Example JSON return:

```json
{
    "res_info": {
        "code": 36,
        "code_info": "PROFILE_PIC_EXISTS"
    },
    "res_content": "s3_bucket_url***REMOVED***a90a9e7f11c6d32bde4f23a955d747ad.png"
}
```

This endpoint returns a URL where a user's (user_id that matches `access_code` and `device_id`) current profile picture is stored.

### HTTP Request

`POST https://api.trya.space/v1/user/get_profile_pic`

### URL Parameters

| Parameter                 | Description                                   |
| ------------------------- | --------------------------------------------- |
| `access_code` | The access code of the user received during authentication. |
| `device_id` | The device ID corresponding to the access key received during authentication. |

## Get Vehicles

```http
GET /v1/user/get_vehicles?access_code=some-access-code&device_id=some-device-id HTTP/1.1
Host: api.trya.space
Accept: */*
```

```shell
curl --request GET \
  --url 'https://api.trya.space/v1/user/get_vehicles?access_code=some-access-code&device_id=some-device-id'
```

```javascript
var request = require("request");

var options = { method: 'GET',
  url: 'https://api.trya.space/v1/user/get_vehicles',
  qs: { access_code: 'some-access-code', device_id: 'some-device-id' } };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});
```

```python
import requests

url = "https://api.trya.space/v1/user/get_vehicles"

querystring = {"access_code":"some-access-code","device_id":"some-device-id"}

payload = ""
response = requests.request("GET", url, data=payload, params=querystring)

print(response.text)
```

> Example JSON return:

```json
{
    "res_info": {
        "code": 35,
        "code_info": "USER_ENDPOINT_FUNCTION_SUCCESS"
    },
    "res_content": [
        {
            "vehicle_id": "9e297fc824c894efeb9ddeedae9e6c26",
            "vehicle_vin": "7J3ZZ56T7834500003",
            "vehicle_year": 2012,
            "vehicle_make": "Toyota",
            "vehicle_model": "Corolla",
            "vehicle_color": "Black",
            "vehicle_length_feet": 16
        },
        {
            "vehicle_id": "a26cb6954fdb62cd4035e8f0e73a4c09",
            "vehicle_vin": "1HGCM82633A004352",
            "vehicle_year": 2017,
            "vehicle_make": "Honda",
            "vehicle_model": "Accord",
            "vehicle_color": "Silver",
            "vehicle_length_feet": 15
        }
    ]
}
```

This endpoint returns a list of stored cars belonging to a user (user_id that matches `access_code` and `device_id`) in JSON format with individual car specifications.

### HTTP Request

`POST https://api.trya.space/v1/user/get_vehicles`

### URL Parameters

| Parameter                 | Description                                   |
| ------------------------- | --------------------------------------------- |
| `access_code` | The access code of the user received during authentication. |
| `device_id` | The device ID corresponding to the access key received during authentication. |

## Add Vehicle

```http
POST /v1/user/add_vehicle?access_code=some-access-code&device_id=some-device-id&vehicle_vin=some-vin&vehicle_year=2012&vehicle_make=Toyota&vehicle_model=Corolla&vehicle_color=Black HTTP/1.1
Host: api.trya.space
Content-Length: 0
```

```shell
curl --request POST \
  --url 'https://api.trya.space/v1/user/add_vehicle?access_code=some-access-code&device_id=some-device-id&vehicle_vin=some-vin&vehicle_year=2012&vehicle_make=Toyota&vehicle_model=Corolla&vehicle_color=Black'
```

```javascript
var request = require("request");

var options = { method: 'POST',
  url: 'https://api.trya.space/v1/user/add_vehicle',
  qs:
   { access_code: 'some-access-code',
     device_id: 'some-device-id',
     vehicle_vin: 'some-vin',
     vehicle_year: '2012',
     vehicle_make: 'Toyota',
     vehicle_model: 'Corolla',
     vehicle_color: 'Black' } };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});
```

```python
import requests

url = "https://api.trya.space/v1/user/add_vehicle"

querystring = {"access_code":"some-access-code","device_id":"some-device-id","vehicle_vin":"some-vin","vehicle_year":"2012","vehicle_make":"Toyota","vehicle_model":"Corolla","vehicle_color":"Black"}

payload = ""
response = requests.request("POST", url, data=payload, params=querystring)

print(response.text)
```

> Example JSON return:

```json
{
    "res_info": {
        "code": 35,
        "code_info": "USER_ENDPOINT_FUNCTION_SUCCESS"
    },
    "res_content": "5a80bf1ac213de38cf1cfcd4b8838f5a"
}
```

This endpoint accepts a list of parameters defining a new car that is added to a list of cars belonging to a user (user_id that matches `access_code` and `device_id`), and returns the `vehicle_id` to be used to reference that car.

### HTTP Request

`POST https://api.trya.space/v1/user/add_vehicle`

### URL Parameters

| Parameter                 | Description                                   |
| ------------------------- | --------------------------------------------- |
| `access_code` | The access code of the user received during authentication. |
| `device_id` | The device ID corresponding to the access key received during authentication. |
| `vehicle_vin` | The Vehicle Identification Number (VIN) of the vehicle being added. |
| `vehicle_year` (optional) | The year of the vehicle being added. |
| `vehicle_make` (optional) | The make/manufacturer of the vehicle being added. |
| `vehicle_model` (optional) | The model of the vehicle being added. |
| `vehicle_color` (optional) | The color of the vehicle being added. |

## Remove Vehicle

```http
POST /v1/user/remove_vehicle?access_code=some-access-code&device_id=some-device-id&vehicle_id=some-vehicle-id HTTP/1.1
Host: api.trya.space
Accept: */*
Content-Length: 0
```

```shell
curl --request POST \
  --url 'https://api.trya.space/v1/user/remove_vehicle?access_code=some-access-code&device_id=some-device-id&vehicle_id=some-vehicle-id'
```

```javascript
var request = require("request");

var options = { method: 'POST',
  url: 'https://api.trya.space/v1/user/remove_vehicle',
  qs:
   { access_code: 'some-access-code',
     device_id: 'some-device-id',
     vehicle_id: 'some-vehicle-id' } };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});
```

```python
import requests

url = "https://api.trya.space/v1/user/remove_vehicle"

querystring = {"access_code":"some-access-code","device_id":"some-device-id","vehicle_id":"some-vehicle-id"}

payload = ""
response = requests.request("POST", url, data=payload, params=querystring)

print(response.text)
```

> Example JSON return:

```json
{
    "res_info": {
        "code": 35,
        "code_info": "USER_ENDPOINT_FUNCTION_SUCCESS"
    }
}
```

This endpoint removes a vehicle matching vehicle_id belonging to a user (user_id that matches `access_code` and `device_id`). The `vehicle_id` must exist in the database for this endpoint to return a success response.

### HTTP Request

`POST https://api.trya.space/v1/user/remove_vehicle`

### URL Parameters

| Parameter                 | Description                                   |
| ------------------------- | --------------------------------------------- |
| `access_code` | The access code of the user received during authentication. |
| `device_id` | The device ID corresponding to the access key received during authentication. |
| `vehicle_id` | The vehicle ID that is being removed. |