# Administration

## Test Admin Sub-API (Ping)

```http
GET /v1/admin/ping HTTP/1.1
Host: api.trya.space
Authorization: Basic dXNlcjpwYXNzd29yZA==
```

```shell
curl --request GET \
  --url https://api.trya.space/v1/admin/ping \
  --header 'authorization: Basic dXNlcjpwYXNzd29yZA=='
```

```javascript
var request = require("request");

var options = { method: 'GET',
  url: 'https://api.trya.space/v1/admin/ping',
  headers: { authorization: 'Basic dXNlcjpwYXNzd29yZA==' } };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});
```

```python
import requests

url = "https://api.trya.space/v1/admin/ping"

payload = ""
headers = {'authorization': 'Basic dXNlcjpwYXNzd29yZA=='}

response = requests.request("GET", url, data=payload, headers=headers)

print(response.text)
```

This endpoint returns `pong` if the sub-API is working properly, and an error otherwise.