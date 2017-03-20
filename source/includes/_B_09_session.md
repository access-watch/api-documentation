## Session object

> Sample Session object:

```json
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
```

### Properties of a Session object

Parameter  | Type   | Required | Description
---------- | ------ | -------- | --------------------------------------------------------
id         | string |    yes   | an internal session identifier
count      | int    |    no    | a number of requests
identity   | object |    yes   | an [Identity Combination object](#identity-combination-object)
address    | object |    yes   | an [IP Address object](#ip-address-object)
signature  | object |    no    | a [Signature object](#headers-signature-object)
user_agent | object |    no    | a [User Agent object](#user-agent-object)
robot      | object |    no    | a [Robot object](#robot-object)
speed      | object |    no    | a [Speed object](#speed-object)
reputation | object |    yes   | a [Reputation object](#reputation-object)
