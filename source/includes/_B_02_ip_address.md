## IP Address object

> Sample Address object

```json
{
  "id": "e90d9f20cce9c203f439129b0943a8bb",
  "value": "92.78.176.182",
  "hostname": "dslb-092-078-176-182.092.078.pools.vodafone-ip.de",
  "as_number": "3209",
  "network_name": "ARCOR-DSL-NET17",
  "country_code": "DE",
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
