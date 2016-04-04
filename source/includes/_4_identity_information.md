## Identity Combination

> Sample Request with IP Address and HTTP Headers

```shell
curl "https://access.watch/api/1.0/identity" \
  -H "Api-Key: 7911c8baebd1754134647625ae36f63e" \
  -H "Content-Type: application/json" \
  -d '{
  "address": "92.78.176.182",
  "headers": {
    "Accept": "text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,*/*;q=0.8",
    "Accept-Encoding": "gzip, deflate, sdch",
    "Accept-Language": "en-US,en;q=0.8",
    "Cache-Control": "max-age=0",
    "Connection": "keep-alive",
    "DNT": "1",
    "Host": "francois.hodierne.net",
    "Referer": "https://www.google.com/",
    "Upgrade-Insecure-Requests": "1",
    "User-Agent": "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_11_3) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/49.0.2623.87 Safari/537.36"
  }
}'
```

> Sample Request with IP Address and User Agent

```shell
curl "https://access.watch/api/1.0/identity" \
  -H "Api-Key: 7911c8baebd1754134647625ae36f63e" \
  -H "Content-Type: application/json" \
  -d '{
  "address": "92.78.176.182",
  "user_agent": "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_11_3) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/49.0.2623.87 Safari/537.36"
}'
```

This endpoint is used to get information about a combination of either:

 * an IP Address and a collection of HTTP Headers
 * an IP Address and a User Agent

### API Request

`POST https://access.watch/api/1.0/identity`

This endpoint accept a JSON object as input.

The expected Content-Type is “application/json”.

### JSON Input Properties

Parameter  | Type   | Required | Description
---------- | ------ | -------- | -----------
address    | string |   yes    | Ipv4 or Ipv6 address
headers    | object |   yes *  | A collection of HTTP headers
user_agent | string |   yes *  | A User Agent

Only one of `headers` or `user-agent` is required. You should always favor passing `headers` over `user_agent`, unless HTTP headers are not available.

### API Response

Return an [Identity object](#identity-combination-object) with extra properties:

 * a [Address object](#ip-address-object)
 * a [Signature object](#headers-signature-object) (if headers were passed)
 * a [User Agent object](#user-agent-object)
 * a [Reputation object](#reputation-object)

### Properties of the JSON response object

Property   | Type    | Description
---------- | ------- | -----------
id         | string  | internal identifier
type       | string  | robot / browser
address    | object  | [Address object](#ip-address-object)
signature  | object  | [Headers Signature object](#headers-signature-object)
user_agent | object  | [User Agent object](#user-agent-object)
reputation | object  | [Reputation object](#reputation-object)
