---
title: aspace, Inc. API

language_tabs: # must be one of https://git.io/vQNgJ
  - http: HTTP
  - shell: cURL
  - javascript: Node.js (request)
  - python: Python

toc_footers:
  - <a href='https://trya.space/'>Main Website</a>
  - <a href='https://lab.trya.space/'>Data Lab</a>
  - <a href='https://api.trya.space/v1'>API</a>
  - <a href='https://docs.trya.space/'>API Documentations</a>

includes:
  - errors

search: true
---

# Introduction

Welcome to the aspace API! You can use this API to access the authentication, parking information, and administration endpoints, which can give you various information regarding the aspace applications.

To see samples of how to access this API, you can use the code examples on the dark area on the right, using the "HTTP", "cURL", "node.js (request), and Python tabs.

Because this API is still in active development, there may be inconsistincies with actual API behavior and the described/intended behavior. In this case, please [contact](mailto:fedor@trya.space) Fedor Paretsky **as soon as possible** and include the following info:

* The endpoint affected
* All of the information you sent to the endpoint, including the following
  * Parameters/queries
  * Body
  * Headers
* The information you received
* Any error codes you received that aren't documented in this API documentation

<aside class="notice">
The base URL for all API endpoints is: <a href="https://api.trya.space/v1"><b>https://api.trya.space/v1</b></a>
</aside>

# Main Endpoint

## Testing Connection

> To test your connection to the server, use this code:

```http
GET /v1/ping HTTP/1.1
Host: api.trya.space
Cache-Control: no-cache
```

```shell
curl -X GET \
  https://api.trya.space/v1/ping \
  -H 'Cache-Control: no-cache'
```

```javascript
var request = require("request");

var options = { method: 'GET',
  url: 'https://api.trya.space/v1/ping',
  headers:
   {'Cache-Control': 'no-cache' } };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});

```

```python
import http.client

conn = http.client.HTTPConnection("api,trya,space")

headers = {
    'Cache-Control': "no-cache"
    }

conn.request("GET", "v1,ping", headers=headers)

res = conn.getresponse()
data = res.read()

print(data.decode("utf-8"))
```

> If clicking [here](https://api.trya.space/v1) doesn't return anything for you, you probably shouldn't use our API without checking your computer first 😜, or the aspace servers are having a meltdown 😅.

The purpose of this endpoint is to test the network connection with the aspace APIs. With a successful client connection (and if the server is functioning), the server will always return the following body:

`pong`

# Parking

## Update Status

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.get()
```

```shell
curl "http://example.com/api/kittens"
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let kittens = api.kittens.get();
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 1,
    "name": "Fluffums",
    "breed": "calico",
    "fluffiness": 6,
    "cuteness": 7
  },
  {
    "id": 2,
    "name": "Max",
    "breed": "unknown",
    "fluffiness": 5,
    "cuteness": 10
  }
]
```

This endpoint retrieves all kittens.

### HTTP Request

`GET http://example.com/api/kittens`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
include_cats | false | If set to true, the result will also include cats.
available | true | If set to false, the result will include kittens that have already been adopted.

<aside class="success">
Remember — a happy kitten is an authenticated kitten!
</aside>

## Get a Specific Kitten

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get(2)
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.get(2)
```

```shell
curl "http://example.com/api/kittens/2"
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let max = api.kittens.get(2);
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "name": "Max",
  "breed": "unknown",
  "fluffiness": 5,
  "cuteness": 10
}
```

This endpoint retrieves a specific kitten.

<aside class="warning">Inside HTML code blocks like this one, you can't use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside>

### HTTP Request

`GET http://example.com/kittens/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to retrieve

## Delete a Specific Kitten

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.delete(2)
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.delete(2)
```

```shell
curl "http://example.com/api/kittens/2"
  -X DELETE
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let max = api.kittens.delete(2);
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "deleted" : ":("
}
```

This endpoint deletes a specific kitten.

### HTTP Request

`DELETE http://example.com/kittens/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to delete