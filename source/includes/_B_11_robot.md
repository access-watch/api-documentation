## Robot object

> Sample Robot object:

```json
{
  "name": "exabot",
  "description": "Exabot is Exalead's robot. Its role is to collect and index data from all around the world to supply Exalead's search engine. ",
  "allowed": true,
  "disallowed": false
}
```

### Properties of a Robot object

Parameter   | Type   | Required | Description
----------- | ------ | -------- | --------------------------------------------------------
name        | string |    yes   | the id for the robot
description | string |    yes   | description of the robot, itspurpose
allowed     | bool   |    yes   | is the robot approved?
disallowed  | bool   |    yes   | is the robot blocked?
