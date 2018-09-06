# Routing Engine

## Route Service (Car)

```http
GET /route/v1/car/-122.341515,47.755653;-122.335167,47.608013?alternatives=false&steps=false&annotations=false&geometries=polyline6&overview=simplified&continue_straight=default HTTP/1.1
Host: routing.trya.space
```

```shell
curl --request GET \
  --url 'https://routing.trya.space/route/v1/car/-122.341515,47.755653;-122.335167,47.608013?alternatives=false&steps=false&annotations=false&geometries=polyline6&overview=simplified&continue_straight=default'
```

```javascript
var request = require("request");

var options = { method: 'GET',
  url: 'https://routing.trya.space/route/v1/car/-122.341515,47.755653;-122.335167,47.608013',
  qs:
   { alternatives: 'false',
     steps: 'false',
     annotations: 'false',
     geometries: 'polyline6',
     overview: 'simplified',
     continue_straight: 'default' } };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});
```

```python
import requests

url = "https://routing.trya.space/route/v1/car/-122.341515,47.755653;-122.335167,47.608013"

querystring = {"alternatives":"false","steps":"false","annotations":"false","geometries":"polyline6","overview":"simplified","continue_straight":"default"}

payload = ""
response = requests.request("GET", url, data=payload, params=querystring)

print(response.text)
```

> Example JSON return:

```json
{
    "code": "Ok",
    "waypoints": [
        {
            "hint": "5lG_gOlRv4CkAAAAiQAAAAAAAAAAAAAAV40IQpW840EAAAAAAAAAAFEAAABFAAAAAAAAAAAAAACkCwAAOje1-ISx2AJ1N7X4hbHYAgAAfxYb4aWh",
            "location": [
                -122.341574,
                47.755652
            ],
            "name": ""
        },
        {
            "hint": "ySQDgP___38OAAAAIQAAAAAAAAAJAAAAdE53QaqUnEEAAAAA6B0MQg4AAAAhAAAAAAAAAAkAAACkCwAACFC1-Axx1gJBULX4zXDWAgAArwMb4aWh",
            "location": [
                -122.335224,
                47.608076
            ],
            "name": "University Street"
        }
    ],
    "routes": [
        {
            "legs": [
                {
                    "steps": [],
                    "weight": 997.1,
                    "distance": 18374,
                    "summary": "",
                    "duration": 990.3
                }
            ],
            "weight_name": "routability",
            "geometry": "gwwazAjkcjhFaRqeUniXyMnbW}{IttWfNbpPluIffb@ee@buUqnOrjtArtCxiN`~H`l_@bjDh_BrqEdjB_`BsE`cC",
            "weight": 997.1,
            "distance": 18374,
            "duration": 990.3
        }
    ]
}
```

This endpoint is to directly correspond with the aspace (Project-OSRM Routing Engine) route service for car profiles.

### HTTP Request

`GET https://routing.trya.space/route/v1/car/ORIGIN_LNG,ORIGIN_LAT;DEST_LNG,DEST_LAT`

### Path Parameters

| Parameter                 | Description                                   |
| ------------------------- | --------------------------------------------- |
| `ORIGIN_LNG` | The origin longitude for the requested route. |
| `ORIGIN_LAT` | The origin latitude for the requested route. |
| `DEST_LNG` | The destination longitude for the requested route. |
| `DEST_LAT` | The destination latitude for the requested route. |

### URL Parameters

| Parameter                 | Description                                   |
| ------------------------- | --------------------------------------------- |
| `alternatives`  | `true`, `false` (default), or number for searching for alternative routes. Passing a number `alternatives=n` searches for up to `n` alternative routes. If an alternative route is requested, a result cannot be guaranteed. |
| `steps` | `true`, `false` (default) for returning route steps for each route leg. |
| `annotations` | `true`, `false` (default), `nodes`, `distance`, `duration`, `datasources`, `weight`, and/or `speed` for returning additional metadata for each coordinate along the route geometry.
| `geometries` | `polyline` (default), `polyline6`, or `geojson` for returning route geometry format (influencing overview and per step). |
| `overview` | `simplified` (default), `full`, or `false` for adding overview geometry either full, simplified according to highest zoom level it could be displayed on, or not at all. |
| `continue_straight` | `default` (default), `true`, or `false` for forcing the route to keep going straight at waypoint constraining uturns there even if it would be faster. Default value depends on the profile.

## Route Service (Bike)

This endpoint is to directly correspond with the aspace (Project-OSRM Routing Engine) route service for bike profiles. The response objects, Path and URL parameters are identical to the car service API descriptions listed above.

### HTTP Request

`GET https://routing.trya.space/route/v1/bike/ORIGIN_LNG,ORIGIN_LAT;DEST_LNG,DEST_LAT`

### Path Parameters

| Parameter                 | Description                                   |
| ------------------------- | --------------------------------------------- |
| `ORIGIN_LNG` | The origin longitude for the requested route. |
| `ORIGIN_LAT` | The origin latitude for the requested route. |
| `DEST_LNG` | The destination longitude for the requested route. |
| `DEST_LAT` | The destination latitude for the requested route. |

## Route Service (Walk)

This endpoint is to directly correspond with the aspace (Project-OSRM Routing Engine) route service for walk profiles. The response objects, Path and URL parameters are identical to the car service API descriptions listed above.

### HTTP Request

`GET https://routing.trya.space/route/v1/walk/ORIGIN_LNG,ORIGIN_LAT;DEST_LNG,DEST_LAT`

### Path Parameters

| Parameter                 | Description                                   |
| ------------------------- | --------------------------------------------- |
| `ORIGIN_LNG` | The origin longitude for the requested route. |
| `ORIGIN_LAT` | The origin latitude for the requested route. |
| `DEST_LNG` | The destination longitude for the requested route. |
| `DEST_LAT` | The destination latitude for the requested route. |