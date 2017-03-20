## Robot object

> Sample Robot object:

```json
{
  "id": "dcbe4598-3144-4085-b886-80c7d4b31bdd",
  "name": "Google",
  "description": "Google is an internet company operating a famous search engine and many other services.",
  "icon": "https://api.access.watch/1.1/icon/robot/dcbe4598-3144-4085-b886-80c7d4b31bdd",
  "agent": "google",
  "allowed": true,
  "disallowed": false
}
```

### Properties of a Robot object

Parameter   | Type   | Required | Description
----------- | ------ | -------- | --------------------------------------------------------
id          | string |    yes   | a unique identifier
name        | string |    yes   | name of the robot for humans
description | string |    yes   | description of the robot, its purpose
icon        | string |    no    | url of an svg icon representing the robot

### Deprecated Properties of a Robot object

Parameter   | Type   | Required | Description
----------- | ------ | -------- | --------------------------------------------------------
agent       | string |    yes   | an older identifier
allowed     | bool   |    yes   | is the robot approved?
disallowed  | bool   |    yes   | is the robot blocked?
