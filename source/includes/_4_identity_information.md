## Identity Combination

> Request with IP Address and HTTP Headers:

```http
POST /1.1/identity HTTP/1.1
Host: api.access.watch
Api-Key: <Api_Key>
Accept: application/json
Content-Type: application/json

{
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
}
```

```shell
curl "https://api.access.watch/1.1/identity" \
  -H "Api-Key: <Api_Key>" \
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

> Request with IP Address and User Agent:

```http
POST /1.1/identity HTTP/1.1
Host: api.access.watch
Api-Key: <Api_Key>
Accept: application/json
Content-Type: application/json

{
  "address": "92.78.176.182",
  "user_agent": "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_11_3) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/49.0.2623.87 Safari/537.36"
}
```

```shell
curl "https://api.access.watch/1.1/identity" \
  -H "Api-Key: <Api_Key>" \
  -H "Content-Type: application/json" \
  -d '{
  "address": "92.78.176.182",
  "user_agent": "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_11_3) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/49.0.2623.87 Safari/537.36"
}'
```

> JSON Response example:

```json
{
  "id": "1244499271eaddd36768ee157403ebe2",
  "type": "browser",
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

This endpoint is used to get information about a combination of either:

 * an IP Address and a collection of HTTP Headers
 * an IP Address and a User Agent

### API Request

`POST https://api.access.watch/1.1/identity`

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

 * an [Address object](#ip-address-object)
 * a [Signature object](#headers-signature-object) (if headers were passed)
 * an [User Agent object](#user-agent-object)
 * a [Reputation object](#reputation-object)

### Properties of the JSON response object

Property   | Type    | Description
---------- | ------- | -----------
id         | string  | internal identifier
type       | string  | robot or browser, as detected by our platform
address    | object  | an [Address object](#ip-address-object)
signature  | object  | a [Signature object](#headers-signature-object) (if headers were passed)
user_agent | object  | an [User Agent object](#user-agent-object)
reputation | object  | a [Reputation object](#reputation-object)
