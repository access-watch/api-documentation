## Reputation object

> Sample Reputation object:

```json
{
  "status": "bad",
  "threats": [
    "suspicious_scan",
    "comment_spam",
    "brute_force_login"
  ]
}
```

### Properties of a Reputation object

Parameter    | Type   | Description
----------   | ------ | --------------------------------------------------------
status       | string | see statuses section
threats      | array  | see threats section

### Statuses for a Reputation object

Status            | Description
----------------- | --------------------------------------------------------
nice              | perfect, as far as we know you can trust this entity
ok                | all right, so far no reason to worry about this entity
suspicious        | warning, nothing really bad, but the entity is on our radar
bad               | danger, there is good reasons to watch or block this entity

### Threats for a Reputation object

Value             | Description
----------------- | --------------------------------------------------------
suspicious_scan   | used to scan websites for known software and security holes
comment_spam      | used to post comment spam
referer_spam      | used for referer spam
brute_force_login | used for brute force attacks against login forms
