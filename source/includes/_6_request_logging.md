## Request Logging

```http
POST /api/1.0/log HTTP/1.1
Host: access.watch
Api-Key: <Api_Key>
Accept: application/json
Content-Type: application/json

{
  "time": "2016-04-05T17:49:14.800Z",
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
  },
  "response": {
    "status" : "200"
  }
}
```

```shell
curl "https://access.watch/api/1.0/log" \
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
  },
  "response": {
    "status" : 200
  }
}'
```

> JSON Response example:

```json
{
  "message": "Ok"
}
```

This endpoint is used to log and index an HTTP request.

### API Request

`POST https://access.watch/api/1.0/log`

This endpoint accept a JSON object as input.

### JSON Input Parameters

Parameter | Type   | Description
--------- | ------ |-----------
time      | string | Date & Time in [ISO8601 format](https://en.wikipedia.org/wiki/ISO_8601)
address   | string | a valid Ipv4 or Ipv6 address
request   | object | a [Request object](#request-object)
response  | object | a [Response object](#response-object)

### API Response

The request is processed asynchronously and there is nothing to expect in the response.
