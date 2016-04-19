## Request Screening

```http
POST /api/1.0/request HTTP/1.1
Host: access.watch
Api-Key: <Api_Key>
Accept: application/json
Content-Type: application/json

{
  "address": "92.78.176.182",
  "request": {
    "protocol": "HTTP/1.1",
    "method": "GET",
    "scheme": "http",
    "host": "francois.hodierne.net",
    "port": "80",
    "url": "/resume",
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
}
```

```shell
curl "https://access.watch/api/1.0/request" \
  -H "Api-Key: <Api_Key>" \
  -H "Content-Type: application/json" \
  -d '{
  "address": "92.78.176.182",
  "request": {
    "protocol": "HTTP/1.1",
    "method": "GET",
    "scheme": "http",
    "host": "francois.hodierne.net",
    "port": "80",
    "url": "/resume",
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
}'
```

> JSON Response example:

```json
{
  "identity": {
    "id": "1244499271eaddd36768ee157403ebe2",
    "type": "browser"
  },
  "address": {
    "id": "e90d9f20cce9c203f439129b0943a8bb",
    "value": "92.78.176.182",
    "hostname": "dslb-092-078-176-182.092.078.pools.vodafone-ip.de",
    "as_number": "3209",
    "network_name": "ARCOR-DSL-NET17",
    "country_code": "DE",
    "flags": [
        "broadband"
    ]
  },
  "signature": {
    "id": "7ecc3a36d6eae49e535f7a956778a166",
    "language": "en",
    "country": "us"
  },
  "user_agent": {
    "id": "b516786e573a426eb842ec2132ed35e2",
    "type": "browser",
    "agent": {
      "name": "chrome",
      "icon": "chrome",
      "label": "Chrome 49.0.2623.87",
    },
    "system": {
      "name": "macosx",
      "icon": "macosx",
      "label": "MacOS X 10.11.3",
    }
  },
  "reputation": {
    "threats": [],
    "status": "nice"
  }
}
```

This endpoint is used to get information about an HTTP Request.

It's usually used in real time to gather knowledge before processing the request.

It can also be used offline to enrich data sets.

### API Request

`POST https://access.watch/api/1.0/request`

This endpoint accept a JSON object as input.

### JSON Input Parameters

Parameter  | Type   | Required | Description
---------- | ------ |--------- | ---------------------------
address    | string |   yes    | a valid Ipv4 or Ipv6 address
request    | object |   yes    | a [Request object](#request-object)

### API Response

Return a collection of several objects:

 * a [Identity object](#identity-combination-object)
 * a [Address object](#ip-address-object)
 * a [Signature object](#headers-signature-object) (if headers were passed in the request)
 * a [User Agent object](#user-agent-object)
 * a [Reputation object](#reputation-object)

### Properties of the JSON response object

Property   | Type    | Description
---------- | ------- | -----------
identity   | object  | [Identity object](#identity-combination-object)
address    | object  | [Address object](#ip-address-object)
signature  | object  | [Signature object](#headers-signature-object)
user_agent | object  | [User Agent object](#user-agent-object)
reputation | object  | [Reputation object](#reputation-object)
