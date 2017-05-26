## Headers Signature

> Request with raw headers:

```http
POST /1.1/signature HTTP/1.1
Host: api.access.watch
Api-Key: <Api_Key>
Accept: application/json
Content-Type: application/json

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

```shell
curl "https://api.access.watch/1.1/signature" \
  -H "Api-Key: <Api_Key>" \
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

This endpoint is used to get information about an agent, by parsing the HTTP Headers.

Informations about the agent are extracted and you get back an identifier, user agent, mime type and language.

### API Request

`POST https://api.access.watch/1.1/signature`

The expected Content-Type is "application/json".

Keys are not case sensitive, so it's ok if they are submitted all lowercase or uppercase.

We recommand to remove sensitive data like Cookie or Authorization headers.

### API Response

> JSON Response example (good reputation):

```json
{
  "id": "7ecc3a36d6eae49e535f7a956778a166",
  "language_code": "en",
  "country_code": "US",
  "user_agent": {
    "id": "b516786e573a426eb842ec2132ed35e2",
    "type": "browser",
    "agent": {
      "name": "chrome",
      "icon": "chrome",
      "label": "Chrome 49.0.2623.87"
    },
    "system": {
      "name": "macosx",
      "icon": "macosx",
      "label": "MacOS X 10.11.3"
    }
  },
  "reputation": {
    "threats": [],
    "status": "nice"
  }
}
```

> JSON Response example (bad reputation):

```json
{
  "id": "e487849551a056762249e1d266bef465",
  "language_code": "en",
  "country_code": "US",
  "user_agent": {
    "id": "aee5c2d9c2fc59e1b95d344382a89a31",
    "type": "browser",
    "agent": {
      "name": "firefox",
      "icon": "firefox",
      "label": "Firefox 34.0"
    },
    "system": {
      "name": "windows7",
      "icon": "windows7",
      "label": "Windows 7"
    }
  },
  "reputation": {
    "threats": [
      "comment_spam",
      "brute_force_login"
    ],
    "status": "bad"
  }
}
```

Return a [Signature object](#headers-signature-object) with extra properties:

 * an [User Agent object](#user-agent-object) (if any)
 * a [Reputation object](#reputation-object)

### Properties of the JSON response object

Property      | Type    | Description
------------- | ------- | -----------
id            | string  | internal identifier
language_code | string  | a language code, extract from the Accept-Language header
country_code  | string  | a country code, extract from the Accept-Language header
user_agent    | object  | an [User Agent object](#user-agent-object), parsed from the User-Agent header
reputation    | object  | a [Reputation object](#reputation-object)

Check the examples on the side.
