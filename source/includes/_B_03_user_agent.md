## User Agent object

> Sample User Agent object

```json
{
  "id": "a46c391e4a75e4a3734042b6077e8cfc",
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

### Properties of a User Agent object

Parameter  | Type   | Description
---------- | ------ | --------------------------------------------------------
id         | string | internal identifier
value      | string | the text value
type       | string | browser or robot, detected from the value
agent      | object | with name, icon, version and label as properties
system     | object | with name, icon, version and label as properties