## User Agent

This endpoint is used to get metadata about an User Agent string.

### API Request

```shell
curl "https://access.watch/api/1.0/user-agent" \
  -H "Api-Key: 7911c8baebd1754134647625ae36f63e" \
  -d "value=Mozilla/5.0 (Macintosh; Intel Mac OS X 10_11_3) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/49.0.2623.87 Safari/537.36"

curl "https://access.watch/api/1.0/user-agent" \
  -H "Api-Key: 7911c8baebd1754134647625ae36f63e" \
  -H "Content-Type: application/json" \
  -d '{"value": "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_11_3) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/49.0.2623.87 Safari/537.36"}'
```

`POST https://access.watch/api/1.0/user-agent`

Two different Content-Type are supported:

 * default is "application/x-www-form-urlencoded":

`value=<USER-AGENT>`

 * also available is "application/json":

`{"value": "<USER-AGENT>"}`

### API Response

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

Return a User Agent object, see the example on the side.

To learn more about the properties, see [the User Agent object table](#user-agent-object).

Check the examples on the side.
