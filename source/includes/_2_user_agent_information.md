## User Agent

```http
POST /1.1/user-agent HTTP/1.1
Host: api.access.watch
Api-Key: <Api_Key>
Accept: application/json
Content-Type: application/json

{
  "value": "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_11_3) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/49.0.2623.87 Safari/537.36"
}
```

```shell
curl "https://api.access.watch/1.1/user-agent" \
  -H "Api-Key: <Api_Key>" \
  -H "Content-Type: application/json" \
  -d '{"value": "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_11_3) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/49.0.2623.87 Safari/537.36"}'
```

> JSON Response example:

```json
{
  "id": "480216f",
  "value": "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_11_3) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/49.0.2623.87 Safari/537.36",
  "type": "browser",
  "agent": {
    "name": "chrome",
    "icon": "chrome",
    "version": "49.0.2623.87",
    "label": "Chrome 49"
  },
  "system": {
    "name": "macosx",
    "icon": "macosx",
    "version": "10.11.3",
    "label": "OS X 10.11"
  }
}
```

This endpoint is used to get metadata about a User Agent string.

### API Request

`POST https://api.access.watch/1.1/user-agent`

This endpoint accept a JSON object as input.

The expected Content-Type is “application/json”.

### JSON Input Properties

Parameter  | Type   | Required | Description
---------- | ------ | -------- | -----------
value      | string |   yes    | the user agent string

### API Response

Return a User Agent object, see the example on the side.

To learn more about the properties, see [the User Agent object table](#user-agent-object).

Check the examples on the side.
