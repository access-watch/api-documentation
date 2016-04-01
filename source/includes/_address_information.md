## IP Address information

This endpoint is used to get information about an IP Address.

### API Request

```shell
curl "https://access.watch/api/v1/address/92_78_176_182" \
  -H "Api-Key: 7911c8baebd1754134647625ae36f63e"
```

`GET https://access.watch/api/1.0/address/<ADDRESS>`

### API Response

> JSON Response example (good ip address):

```json
{
  "id": "e90d9f20cce9c203f439129b0943a8bb",
  "value": "92.78.176.182",
  "hostname": "dslb-092-078-176-182.092.078.pools.vodafone-ip.de",
  "as": "3209",
  "network": "ARCOR-DSL-NET17",
  "country": "DE",
  "flags": [
    "broadband",
  ],
  "reputation": "ok"
}
```

> JSON Response example (suspicious ip address):

```json
{
  "id": "a46c391e4a75e4a3734042b6077e8cfc",
  "value": "91.200.12.5",
  "hostname": null,
  "as": "35804",
  "network_name": "VHOSTER-NET",
  "country_code": "UA",
  "flags": [
    "brute_force_login",
    "comment_spam",
    "suspicious_scan"
  ],
  "reputation": "bad"
}
```

See the example on the side.

To learn more about all the properties of an address object, see [the address object table](#address-object).
