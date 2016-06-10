---
title: API Documentation

language_tabs:
  - http: HTTP
  - shell: cURL

toc_footers:
  - <a href='https://access.watch/'>Sign Up for an API Key</a>
  - <a href='https://github.com/tripit/slate'>Documentation Powered by Slate</a>

includes:
  - 1_address_information
  - 2_user_agent_information
  - 3_headers_signature
  - 4_identity_information
  - 5_request_screening
  - 6_request_logging
  - 7_retrieve_logs
  - 7_retrieving_sessions
  - B_01_objects
  - B_02_ip_address
  - B_03_user_agent
  - B_04_headers_signature
  - B_05_identity_combination
  - B_05_request
  - B_06_response
  - B_07_reputation
  - B_08_log
  - B_09_session
  - B_10_speed
  - errors

search: true
---

# Introduction

Welcome to the Access Watch API!

Our API is primarily about analyzing web traffic:

* in one way you use it to log HTTP requests
* in the other you get back augmented logs and statistics

You can also use our API to get information about IP Addresses and User Agents.

# Authentication

```http
GET /api/1.0/hello HTTP/1.1
Host: access.watch
Api-Key: <Api_Key>
Accept: application/json
```

```shell
curl "https://access.watch/api/1.0/hello" \
  -H "Api-Key: <Api_Key>"
```

Access Watch use API keys to authorize access to our API.

You can get an API key directly on our [home page](https://access.watch/).

The API key is expected to be passed in each request with the `Api-Key` HTTP Header:

`Api-Key: <API_KEY>`

We also support the `api_key` parameter in the URL:

`GET https://access.watch/api/1.0/hello?api_key=<API_KEY>`

# Endpoints
