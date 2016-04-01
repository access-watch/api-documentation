## Headers Information

This endpoint is used to get information about an agent, by parsing the HTTP Headers.

Informations about the agent are extracted and you get back an identifier, user agent, mime type and language.

### API Request

```shell
curl "https://access.watch/api/v1/headers" \
  -H "Api-Key: 7911c8baebd1754134647625ae36f63e" \
  -H "Content-Type: application/json" \
  -d '{
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
}'
```

### With raw headers

`POST https://access.watch/api/1.0/headers`

The expected Content-Type is "application/json".

Keys are not case sensitive, so it's ok if you submit them all lowercase or uppercase.

We recommand to not send to us sensitive data like Cookie or Authorization headers.

> JSON Input example:

```json
{
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
```

### With an identifier

If you already have an identifier, you can simply construct a URL like that.

`GET https://access.watch/api/1.0/headers/<ID>`

### API Response

> JSON Response example:

```json
{
  "id": "7ecc3a36d6eae49e535f7a956778a166",
  "user_agent": {
    "id": "480216f",
    "type": "browser",
    "agent_name": "chrome",
    "agent_icon": "chrome",
    "agent_label": "Chrome 49.0.2623.87",
    "system_name": "macosx",
    "system_icon": "macosx",
    "system_label": "MacOS X 10.11.3"
  },
  "language": "en",
  "country": "us",
  "flags": [],
  "reputation": "nice"
}
```

### Properties of a Headers object

Property   | Type     | Description
---------- | -------- | -----------
id         | string   | internal identifier
user-agent | object   | A [User Agent object](#user-agent-object), parsed from the User-Agent header
language   | string   | A language code, parsed from the Accept-Language header
country    | string   | A country code, parsed from the Accept-Language header
reputation | string   | nice, ok, suspicious or bad
flags      | array    | see flags section

### Flags for a Headers object

Flag            | Description
--------------- | --------------------------------------------------------------
suspicious_scan | used to scan websites for known software and security holes
comment_spam    | used to post comment spam
brute_force     | used for brute force attacks (eg: against login forms)
referer_spam    | used for referer spam
