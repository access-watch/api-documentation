## Robot object

> Sample Robot object:

```json
{
  "id": "dcbe4598-3144-4085-b886-80c7d4b31bdd",
  "name": "Google",
  "status": "nice",
  "description": "Google is an internet company operating a famous search engine and many other services.",
  "url": "https://access.watch/database/robots/nice/google",
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
status      | string |    yes   | nice, ok, suspicious or bad
description | string |    yes   | description of the robot, its purpose
url         | string |    no    | url of the robot entry in the Access Watch database
icon        | string |    no    | url of an svg icon representing the robot

### Statuses for a Robot object

Status            | Description
----------------- | --------------------------------------------------------
nice              | we know this robot, its activity is legit and it's verified
ok                | we know this robot, we can't guarantee its activity or verify it
suspicious        | we know this robot, its activity is questionnable but not harmful
bad               | we know this robot, its activity is harmful: spam, scan, attacks, ...

### Deprecated Properties of a Robot object

Parameter   | Type   | Required | Description
----------- | ------ | -------- | --------------------------------------------------------
agent       | string |    yes   | an older identifier
vendor_name | string |    yes   | an older identifier
allowed     | bool   |    yes   | is the robot approved?
disallowed  | bool   |    yes   | is the robot blocked?
