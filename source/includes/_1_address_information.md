## IP Address

This endpoint is used to get metadata and reputation of an IP Address.

### API Request

```http
GET /1.1/address/92.78.176.182 HTTP/1.1
Host: api.access.watch
Api-Key: <Api_Key>
Accept: application/json
```

```shell
curl "https://api.access.watch/1.1/address/92.78.176.182" \
  -H "Api-Key: <Api_Key>"
```

`GET https://access.watch/api/1.0/address/<ADDRESS>`

### API Response

> JSON Response example (ok IP address):

```json
{
  "id": "e90d9f20cce9c203f439129b0943a8bb",
  "value": "92.78.176.182",
  "hostname": "dslb-092-078-176-182.092.078.pools.vodafone-ip.de",
  "label": "dslb-092-078-176-182.092.078.pools.vodafone-ip.de",
  "as_number": "3209",
  "network_name": "ARCOR-DSL-NET17",
  "country_code": "DE",
  "flags": [
    "broadband"
  ],
  "reputation": {
    "status": "ok",
    "threats": []
  }
}
```

> JSON Response example (suspicious IP address):

```json
{
  "id": "a46c391e4a75e4a3734042b6077e8cfc",
  "value": "91.200.12.5",
  "hostname": "4.xrfuwuqi.com",
  "label": "4.xrfuwuqi.com",
  "as_number": "35804",
  "network_name": "VHOSTER-NET",
  "country_code": "UA",
  "flags": [
    "server"
  ],
  "reputation": {
    "status": "bad",
    "threats": [
      "suspicious_scan",
      "comment_spam",
      "brute_force_login"
    ]
  }
}
```

Return an [Address object](#ip-address-object) with a [Reputation object](#reputation-object) as extra property:

 * a detailed list of the Address properties is available in [the Address object section](#ip-address-object).
 * a detailed list of the Reputation properties is available in [the Reputation object section](#reputation-object).

Check the examples on the side.

### Properties of the JSON response object

Parameter    | Type   | Description
----------   | ------ | --------------------------------------------------------
id           | string | internal identifier
value        | string | the ipv4 or ipv6 address
hostname     | string | the reverse hostname for the address
label        | string | a human label for the address (currently hostname or value)
as_number    | string | the autonomous system number
network_name | string | the network name
country_code | string | the country code, two letter (ISO 3166-1 alpha-2)
flags        | array  | see flags in the [the Address object section](#ip-address-object)
reputation   | object | a [Reputation object](#reputation-object)
