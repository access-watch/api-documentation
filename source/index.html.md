---
title: API Reference

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/tripit/slate'>Documentation Powered by Slate</a>

includes:
  - address_information
  - user_agent_information
  - headers_information
  - basic_combined_information
  - detailed_combined_information
  - basic_request_screening
  - detailed_request_screening
  - detailed_request_logging
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
curl "https://access.watch/api/v1/hello" \
  -H "Api-Key: 7911c8baebd1754134647625ae36f63e"

curl "https://access.watch/api/v1/hello?api_key=7911c8baebd1754134647625ae36f63e"
```

Access Watch use API keys to authorize accesses to our API.

You can get an API key directly on our [home page](https://access.watch/).

The API key is expected to be passed in each request with the `Api-Key` HTTP Header:

`Api-Key: <API_KEY>`

We also support the `api_key` parameter in the URL:

`GET https://access.watch/api/v1/hello?api_key=<API_KEY>`

# Objects

## Address object

> Sample address object

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

Parameter  | Type   | Description
---------- | ------ | --------------------------------------------------------
id         | string | internal identifier
value      | string | the ipv4 or ipv6 address
hostname   | string | the reverse hostname for the address
as         | int    | the autonomous system number
network    | string | the network name
country    | string | the country code, two letter (ISO 3166-1 alpha-2)
reputation | string | nice, ok, suspicious or bad
flags      | array  | see flags section

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
suspicious_scan | IP used to scan websites for known software and security holes
comment_spam    | IP used to post comment spam
brute_force     | IP used for brute force attacks (eg: against login forms)
referer_spam    | IP used for referer spam

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
type       | string | browser or robot
agent      | object | with name, icon, version and label as properties
system     | object | with name, icon, version and label as properties

## Request object

> Sample detailed Request object:

```json
{
  "protocol": "HTTP/1.1",
  "method": "GET",
  "scheme": "http",
  "host": "francois.hodierne.net",
  "port": "80",
  "url": "/resume",
  "headers": {
    "User-Agent": "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_11_3) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/49.0.2623.87 Safari/537.36",
    "Accept": "text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,*/*;q=0.8",
    "Accept-Language": "en-US,en;q=0.8",
    "Accept-Encoding": "gzip, deflate, sdch",
    "Connection": "keep-alive"
  }
}
```

> Sample basic Request object:

```json
{
  "protocol": "HTTP/1.1",
  "method": "GET",
  "scheme": "http",
  "host": "francois.hodierne.net",
  "port": "80",
  "url": "/resume",
  "user-agent": "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_11_3) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/49.0.2623.87 Safari/537.36"
}
```

There is two type of request object:

 * detailed: with all HTTP headers
 * simple: with just the User Agent

You should always use the detailed request object unless the HTTP headers are not available.

### Properties of a detailed request object

Parameter  | Type   | Required | Description
---------- | ------ | -------- | --------------------------------------------------------
protocol   | string |    no    | HTTP/1.0, HTTP/1.1 or HTTP/2. Default to null.
method     | string |    yes   | the HTTP Method: HEAD, GET, POST, ...
scheme     | string |    yes   | http or https
host       | string |    yes   | the host for the request
port       | int    |    no    | default to 80/443 (http/https)
url        | string |    yes   | The relative URL (path + query string)
headers    | object |    yes   | All HTTP headers as key value pair

### Properties of a basic request object

Parameter  | Type   | Required | Description
---------- | ------ |----------|---------------------------------------------------------
protocol   | string |    no    | HTTP/1.0, HTTP/1.1 or HTTP/2. Default to null.
method     | string |    yes   | the HTTP Method: HEAD, GET, POST, ...
scheme     | string |    yes   | http or https
host       | string |    yes   | the host for the request
port       | int    |    no    | default to 80/443 (http/https)
url        | string |    yes   | The relative URL (path + query string)
user-agent | string |    yes   | The User Agent used for the request

# Endpoints
