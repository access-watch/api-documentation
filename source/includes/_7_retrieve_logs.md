## Retrieving Logs

```http
POST /1.1/logs?limit=1 HTTP/1.1
Host: api.access.watch
Api-Key: <Api_Key>
Accept: application/json
```

```shell
curl "https://api.access.watch/1.1/logs?limit=1" \
  -H "Api-Key: <Api_Key>"
```

> JSON Response example:

```json
{
  "logs": [
    {
      "request": {
        "protocol": "HTTP\/1.1",
        "method": "GET",
        "scheme": "http",
        "host": "francois.hodierne.net",
        "port": "80",
        "url": "\/resume",
        "headers": {
          "accept": "text\/html,application\/xhtml+xml,application\/xml;q=0.9,image\/webp,*\/*;q=0.8",
          "accept-encoding": "gzip, deflate, sdch",
          "accept-language": "en-US,en;q=0.8",
          "cache-control": "max-age=0",
          "connection": "keep-alive",
          "dnt": "1",
          "host": "francois.hodierne.net",
          "referer": "https:\/\/www.google.com\/",
          "upgrade-insecure-requests": "1",
          "user-agent": "Mozilla\/5.0 (Macintosh; Intel Mac OS X 10_11_3) AppleWebKit\/537.36 (KHTML, like Gecko) Chrome\/49.0.2623.87 Safari\/537.36"
        }
      },
      "response": {
        "status": 200
      },
      "identity": {
        "id": "1244499271eaddd36768ee157403ebe2",
        "type": "browser"
      },
      "address": {
        "id": "e90d9f20cce9c203f439129b0943a8bb",
        "value": "92.78.176.182",
        "hostname": "dslb-092-078-176-182.092.078.pools.vodafone-ip.de",
        "label": "dslb-092-078-176-182.092.078.pools.vodafone-ip.de",
        "as_number": "3209",
        "network_name": "ARCOR-DSL-NET17",
        "country_code": "DE",
        "flags": [
          "broadband"
        ]
      },
      "signature": {
        "id": "7ecc3a36d6eae49e535f7a956778a166",
        "language_code": "en",
        "country_code": "US"
      },
      "user_agent": {
        "id": "b516786e573a426eb842ec2132ed35e2",
        "type": "browser",
        "agent": {
          "name": "chrome",
          "icon": "chrome",
          "label": "Chrome 49.0.2623.87"
        },
        "system": {
          "name": "macosx",
          "icon": "macosx",
          "label": "MacOS X 10.11.3"
        }
      },
      "reputation": {
        "threats": [],
        "status": "nice"
      }
    }
  ]
}
```

This endpoint is used to retrieve logs.

### API Request

`GET https://access.watch/api/1.0/logs`

### URL Parameters

Parameter | Type   | Description
--------- | ------ |-----------
q         | string | full text search
limit     | int    | the maximum number of logs in the response
after     | string | all logs after the Date & Time in [ISO8601 format](https://en.wikipedia.org/wiki/ISO_8601)
before    | string | all logs before the Date & Time in [ISO8601 format](https://en.wikipedia.org/wiki/ISO_8601)
session   | string | filter logs by session id

### API Response

### Properties of the JSON response object

Parameter  | Type   | Description
---------- | ------ | --------------------------------------------------------
logs       | array  | an array of [Log objects](#log-object)
