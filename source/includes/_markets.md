# Markets

Retrieve the market countries that we support.

Most suppliers (airlines, travel agents and car hire dealers) set their fares based on the market (or country of purchase). It is therefore necessary to specify the market country in every query.

```shell
GET "https://www.skyscanner.net/g/chiron/api/v1/pricing/v1.0/
    reference/v1.0/countries/
     `{locale}`"
```

*API endpoint*

`/localisation/reference/v1.0/countries`

*HEADER VALUES*

| Header | Value |
| --- | --- |
| `api-key` <br><span class="required">REQUIRED</span> | `<<your API key>>` |

*REQUEST PARAMETERS*

| Parameter | Description |
| --------- | ------- |
| ```locale``` <br><span class="required">REQUIRED</span> | The language you want the results in (ISO locale) |

```json
{
  "Countries": [
    {
      "Code": "AD",
      "Name": "Andorra"
    },
    {
      "Code": "AE",
      "Name": "United Arab Emirates"
    },
    {
      "Code": "AF",
      "Name": "Afghanistan"
    },
  ...
  ]
}
```


*RESPONSE PARAMETERS*

| Parameter | Description |
| --- | --- |
| ```Countries``` | Contains the list of markets (array of countries as name-value pairs). |
