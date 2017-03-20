## Identity Combination object

> Sample Identity Combination object:

```json
{
  "id": "07051caab3d3d1e3a72bf9d635601080",
  "type": "robot",
  "name": "Google",
  "label": "verified robot",
  "description": "Agent operating from a verified IP address."
}
```

### Properties of an Identity Combination object

Parameter   | Type   | Description
----------- | ------ | ----------------------------------------------------------
id          | string | internal unique identifier
type        | string | robot or browser, as detected by our platform, can be null
name        | string | name of the identity
label       | string | label for the identity
description | string | description of the identity
