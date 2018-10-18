# User Authentication

## Test Auth Sub-API (Ping)

```http
GET /v1/auth/ping HTTP/1.1
Host: api.trya.space
```

```shell
curl --request GET \
  --url https://api.trya.space/v1/auth/ping
```

```javascript
var request = require("request");

var options = { method: 'GET', url: 'https://api.trya.space/v1/auth/ping' };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});
```

```python
import requests

url = "https://api.trya.space/v1/auth/ping"

payload = ""
response = requests.request("GET", url, data=payload)

print(response.text)
```

> Example JSON return:

```json
{
  "res_info": {
    "code": 33,
    "code_info": "AUTH_ENDPOINT_FUNCTION_SUCCESS"
  },
  "res_content": "pong"
}
```

This endpoint is used to test the functionality/response of the Auth Sub-API.

### HTTP Request

`GET https://api.trya.space/v1/auth/ping`

<aside class="notice">If you are receiving an error with this endpoint for an extended period of time, please <a href="mailto:help@trya.space">send</a> the error you receive to the API admin.</aside>

## Phone Login

```http
POST /v1/auth/phone_login?phone_number=(206)372-1234&device_id=abcde HTTP/1.1
Host: api.trya.space
Content-Length: 0
```

```shell
curl --request POST \
  --url 'https://api.trya.space/v1/auth/phone_login?phone_number=(206)372-1234&device_id=abcde'
```

```javascript
var request = require("request");

var options = { method: 'POST',
  url: 'https://api.trya.space/v1/auth/phone_login',
  qs: { phone_number: '(206)372-1234', device_id: 'abcde' } };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});
```

```python
import requests

url = "https://api.trya.space/v1/auth/phone_login"

querystring = {"phone_number":"(206)372-1234","device_id":"abcde"}

payload = ""
response = requests.request("POST", url, data=payload, params=querystring)

print(response.text)
```

> Example JSON return:

```json
{
  "res_info": {
    "code": 1,
    "code_info": "NEW_PHONE"
  }
}
```

This endpoint sends a text message with a verification PIN to the given `phone_number`, and uses this along with the unique `device_id` to allow a user to authenticate into their account. The next step of the authentication process is outlined in <a href="https://docs.trya.space/#check-pin">Check PIN</a>. If the `call_verify` query is set to `T`, the `phone_number` is called instead of texted, and the login/verification process continues identically.

<aside class="notice">The format of <code>phone_number</code> does not need to be consistent, it is formatted automatically on the backend.</aside>

<aside class="warning">The <code>device_id</code> used throughout this process needs to stay consistent, and match the PIN request that is made.</aside>

### HTTP Request

`POST https://api.trya.space/v1/auth/phone_login`

### URL Parameters

| Parameter                 | Description                                   |
| ------------------------- | --------------------------------------------- |
| `phone_number` | The phone_number of the device used for the login process. |
| `device_id` | The unique device id of the phone used for the login process. |
| `call_verify` (Must be `T` or `F`) | If `T` (true), the user will be called (instead of texted) with their login PIN. Otherwise, the user will be texted with their PIN. |

## Check PIN

```http
POST /v1/auth/check_pin?phone_number=(206)372-1234&device_id=abcde&verify_pin=12345 HTTP/1.1
Host: api.trya.space
Content-Length: 0
```

```shell
curl --request POST \
  --url 'https://api.trya.space/v1/auth/check_pin?phone_number=(206)372-1234&device_id=abcde&verify_pin=12345'
```

```javascript
var request = require("request");

var options = { method: 'POST',
  url: 'https://api.trya.space/v1/auth/check_pin',
  qs:
   { phone_number: '(206)372-1234',
     device_id: 'abcde',
     verify_pin: '12345' } };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});
```

```python
import requests

url = "https://api.trya.space/v1/auth/check_pin"

querystring = {"phone_number":"(206)372-1234","device_id":"abcde","verify_pin":"12345"}

payload = ""
response = requests.request("POST", url, data=payload, params=querystring)

print(response.text)
```

> Example JSON return:

```json
{
  "res_info": {
    "code": 22,
    "code_info": "NEW_ACCESS_CODE"
  },
  "res_content": {
    "access_code": "dd3dc3146df82c5a2b1c54eb4648939f",
    "expiry": "2018-09-27 16:56:30"
  }
}
```

This endpoint returns an access code for a user that is registered as logged in, after a request with matching the verification PIN, phone number, and device ID from the previous authentication request is sent.

<aside class="notice">The verification PIN is only valid for 5 minutes from the point the "Phone Login" request is made. After that, attempts with the correct verification PIN, phone number, and device ID will <b>not</b> return an access code.</aside>

### HTTP Request

`POST https://api.trya.space/v1/auth/check_pin`

### URL Parameters

| Parameter                 | Description                                   |
| ------------------------- | --------------------------------------------- |
| `phone_number` | The phone number to which the original verification code was sent. |
| `device_id` | The corresponding device ID that made the request for this verification code. |
| `verify_pin` | The verification code/PIN that was received. |