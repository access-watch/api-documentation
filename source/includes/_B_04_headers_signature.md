## Headers Signature object

> Sample Headers Signature object:

```json
{
  "id": "7ecc3a36d6eae49e535f7a956778a166",
  "language_code": "en",
  "country_code": "us"
}
```

### Properties of an Headers Signature object

Parameter     | Type   | Required | Description
------------- | ------ | -------- | -----------------------------------------------
id            | string |    yes   | internal identifier
language_code | string |    no    | a language code, parsed from the Accept-Language header
country_code  | string |    no    | a country code, parsed from the Accept-Language header
