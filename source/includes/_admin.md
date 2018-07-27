# Administration

## Test Admin Sub-API (Ping)

```http
  GET /v1/admin/ping HTTP/1.1
  Host: api.trya.space
  Authorization: Basic ZmVkb3I6MTIzNA==
```

```shell
curl --request GET \
  --url https://api.trya.space/v1/admin/ping \
  --header 'authorization: Basic ZmVkb3I6MTIzNA=='
```

```javascript
var request = require("request");

var options = { method: 'GET',
  url: 'https://api.trya.space/v1/admin/ping',
  headers: { authorization: 'Basic ZmVkb3I6MTIzNA==' } };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});
```

```python
import requests

url = "https://api.trya.space/v1/admin/ping"

payload = ""
headers = {'authorization': 'Basic ZmVkb3I6MTIzNA=='}

response = requests.request("GET", url, data=payload, headers=headers)

print(response.text)
```

> This endpoint returns the following JSON when functioning correctly:

```json
{
  "res_info": {
    "code": 32,
    "code_info": "ADMIN_ENDPOINT_FUNCTION_SUCCESS"
  },
  "res_content": "pong"
}
```