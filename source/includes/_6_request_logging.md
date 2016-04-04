## Request logging

```shell
curl "https://access.watch/api/1.0/log" \
  -H "Api-Key: 7911c8baebd1754134647625ae36f63e" \
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

> JSON Input example:

```json
{
  "address": "92.78.176.182",
  "request": {
    "protocol": "HTTP/1.1",
    "method": "GET",
    "scheme": "http",
    "domain": "francois.hodierne.net",
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
}
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
address   | string | A valid Ipv4 or Ipv6 address
request   | object | A [Request object](#request-object)
response  | object | A [Response object](#response-object)

### API Response

The request is processed asynchronously and there is nothing to expect in the response.