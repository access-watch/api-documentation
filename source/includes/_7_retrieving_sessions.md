## Retrieving Sessions

```http
POST /1.1/sessions?limit=1 HTTP/1.1
Host: api.access.watch
Api-Key: <Api_Key>
Accept: application/json
```

```shell
curl "https://api.access.watch/1.1/sessions?limit=1" \
  -H "Api-Key: <Api_Key>"
```

> JSON Response example:

```json
{
  "sessions": [
    {
      "id": "8efe0f2ac4767f4e1131f4d6a5186767",
      "count": 137,
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
          "version": "49.0.2623.87",
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

This endpoint is used to retrieve sessions.

### API Request

`GET https://api.access.watch/1.1/sessions`

### URL Parameters

Parameter | Type   | Description
--------- | ------ |-----------
limit     | int    | the maximum number of entries in the response

### API Response

### Properties of the JSON response object

Parameter  | Type   | Description
---------- | ------ | --------------------------------------------------------------------
sessions   | array  | a collection of [Session objects](#session-object) with extra properties

### Properties of the JSON objects in the collection

Parameter  | Type   | Required | Description
---------- | ------ | -------- | ---------------------------------------------
id         | string |     y    | an internal session identifier
count      | int    |     y    | number of requests
updated    | string |     y    | last Date & Time of activity, [ISO8601 format](https://en.wikipedia.org/wiki/ISO_8601)
identity   | object |     y    | an [Identity Combination object](#identity-combination-object)
address    | object |     y    | an [IP Address object](#ip-address-object)
signature  | object |     n    | a [Signature object](#headers-signature-object)
user_agent | object |     n    | a [User Agent object](#user-agent-object)
speed      | object |     n    | a [Speed object](#speed-object)
reputation | object |     y    | a [Reputation object](#reputation-object)
