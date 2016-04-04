---
title: API Reference

toc_footers:
  - <a href='https://access.watch/'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/tripit/slate'>Documentation Powered by Slate</a>

includes:
  - 1_address_information
  - 2_user_agent_information
  - 3_headers_signature
  - 4_identity_information
  - 5_request_screening
  - 6_request_logging
  - errors

search: true
---

# Introduction

Welcome to the Access Watch API!

Our API is primarily about analysing web traffic:

* in one way you use it to log HTTP requests
* in the other you get back augmented logs and statistics

You can also use our API to get information about IP Addresses and User Agents.

# Authentication

```shell
curl "https://access.watch/api/1.0/hello" \
  -H "Api-Key: 7911c8baebd1754134647625ae36f63e"

curl "https://access.watch/api/1.0/hello?api_key=7911c8baebd1754134647625ae36f63e"
```

Access Watch use API keys to authorize access to our API.

You can get an API key directly on our [home page](https://access.watch/).

The API key is expected to be passed in each request with the `Api-Key` HTTP Header:

`Api-Key: <API_KEY>`

We also support the `api_key` parameter in the URL:

`GET https://access.watch/api/1.0/hello?api_key=<API_KEY>`

# Objects

## IP Address object

> Sample Address object

```json
{
  "id": "e90d9f20cce9c203f439129b0943a8bb",
  "value": "92.78.176.182",
  "hostname": "dslb-092-078-176-182.092.078.pools.vodafone-ip.de",
  "as": "3209",
  "network": "ARCOR-DSL-NET17",
  "country": "DE",
  "reputation": "ok",
  "flags": [
    "broadband",
  ]
}
```

### Properties of an Address object

Parameter    | Type   | Description
----------   | ------ | --------------------------------------------------------
id           | string | internal identifier
value        | string | the ipv4 or ipv6 address
hostname     | string | the reverse hostname for the address
as_number    | string | the autonomous system number
network_name | string | the network name
country_code | string | the country code, two letter (ISO 3166-1 alpha-2)
flags        | array  | see flags section

### Flags for an Address object

Flag            | Description
--------------- | --------------------------------------------------------
broadband       | IP from a broadband connection (cable, dsl)
mobile          | IP from a mobile connection (GSM, GPRS, 3G, LTS)
server          | IP from a server in a data center
business        | IP from a business broadband connection
corporate       | IP from the network of a big corporation
institution     | IP from a public institution (federal, national, local)
education       | IP from an education institution (university, school)
wifi            | IP from a commercial Wifi provider
wimax           | IP from a commercial Wimax provider
sat             | IP from a satellite provider
vpn             | IP from a VPN provider
proxy           | IP from a commercial proxy (like Opera Mini or Google)
cloud           | IP from a cloud server like AWS or Google Cloud
tor             | IP used a a Tor exit
crawler         | IP from a known crawler
robot           | IP used by robot agent

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

### Properties of an User Agent object

Parameter  | Type   | Description
---------- | ------ | --------------------------------------------------------
id         | string | internal identifier
value      | string | the text value
type       | string | browser or robot, detected from the value
agent      | object | with name, icon, version and label as properties
system     | object | with name, icon, version and label as properties

## Headers Signature object

> Sample Headers Signature object:

```json
{
  "id": "7ecc3a36d6eae49e535f7a956778a166",
  "language": "en",
  "country": "us"
}
```

### Properties of an Headers Signature object

Parameter  | Type   | Description
---------- | ------ | --------------------------------------------------------
id         | string | internal identifier
language   | string | a language code, parsed from the Accept-Language header
country    | string | a country code, parsed from the Accept-Language header

## Identity Combination object

> Sample Identity Combination object:

```json
{
  "id": "7ecc3a36d6eae49e535f7a956778a166",
  "type": "browser"
}
```

### Properties of an Identity Combination object

Parameter  | Type   | Description
---------- | ------ | --------------------------------------------------------
id         | string | internal identifier
type       | string | robot or browser, detected by our platform

## Request object

> Sample Request object:

```json
{
  "protocol": "HTTP/1.1",
  "method": "GET",
  "scheme": "http",
  "host": "francois.hodierne.net",
  "port": "80",
  "url": "/resume",
  "headers": {
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
}
```
### Properties of a Request object

Parameter  | Type   | Required | Description
---------- | ------ | -------- | --------------------------------------------------------
protocol   | string |   no     | HTTP/1.0, HTTP/1.1 or HTTP/2.
method     | string |   yes    | HTTP Method: HEAD, GET, POST, ...
scheme     | string |   yes    | http or https
host       | string |   yes    | the host for the request
port       | int    |   no     | default to 80/443 (http/https)
url        | string |   yes    | The relative URL (path + query string)
user_agent | string |   yes *  | a User Agent
headers    | object |   yes *  | a collection of HTTP headers

Only one of `headers` or `user-agent` is required. `headers` should always be favored over `user_agent`, unless HTTP headers are not available.

## Response object

> Sample Response object:

```json
{
  "status": "200"
}
```

This object is Work in Progress, more properties will be added as soon as they are supported.

### Properties of a Response object

Parameter  | Type   | Required | Description
---------- | ------ | -------- | --------------------------------------------------------
status     | string |   yes    | the HTTP status code for the response

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
status       | string | nice, ok, suspicious or bad
threats      | array  | see threats section

### Threats for a Reputation object

Flag              | Description
----------------- | --------------------------------------------------------
suspicious_scan   | used to scan websites for known software and security holes
comment_spam      | used to post comment spam
referer_spam      | used for referer spam
brute_force_login | used for brute force attacks against login forms

# Endpoints
