## Request object

> Sample Request object:

```json
{
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
```
### Properties of a Request object

Parameter  | Type   | Required | Description
---------- | ------ | -------- | --------------------------------------------------------
protocol   | string |   no     | HTTP/1.0, HTTP/1.1 or HTTP/2.
method     | string |   yes    | HTTP Method: HEAD, GET, POST, ...
scheme     | string |   yes    | http or https
host       | string |   yes    | the host for the request
port       | int    |   no     | default to 80/443 (http/https)
url        | string |   yes    | The relative URL (path + query string)
user_agent | string |   yes *  | a User Agent string
headers    | object |   yes *  | a collection of HTTP headers

Only one of `headers` or `user-agent` is required. `headers` should always be favored over `user_agent`, unless HTTP headers are not available.
