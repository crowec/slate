# Localisation

All Skyscanner services are localised by market, language and currency, so these three parameters must be added to every request.

## Locales

Retrieve the locales that we support to translate your content.

```shell
GET "https://www.skyscanner.net/g/chiron/api/v1/localisation/
    reference/v1.0/locales"
```

*API endpoint*

`GET /localisation/reference/v1.0/locales`



*HEADERS*

| Parameter | Description |
| --------- | ------- |
| ```api-key``` <br><span class="required">REQUIRED</span> | Your API Key. |

> Example response

```json
{
  "Locales": [
    {
      "Code": "ar-AE",
      "Name": "العربية (الإمارات العربية المتحدة)"
    },
    {
      "Code": "az-AZ",
      "Name": "Azərbaycan­ılı (Azərbaycan)"
    },
    {
      "Code": "bg-BG",
      "Name": "български (България)"
    },
    {
      "Code": "ca-ES",
      "Name": "català (català)"
    },
  ...
  ]
}
```


*RESPONSE PARAMETERS*

| Parameter | Description |
| --- | --- |
| ```Locales``` | Contains the list of locales that we support with name and code. |


## Currencies

Retrieve the currencies that we support.

```shell
GET "https://www.skyscanner.net/g/chiron/api/v1/localisation/
    reference/v1.0/currencies"
```
*API endpoint*

`GET /localisation/reference/v1.0/currencies`


*HEADERS*

Parameter | Description |
--------- | ------- |
```api-key``` <br><span class="required">REQUIRED</span> | Your API Key. |

> Example response

```json
{
  "Currencies": [
      {
          "Code": "USD",
          "Symbol": "$",
          "ThousandsSeparator": ",",
          "DecimalSeparator": ".",
          "SymbolOnLeft": true,
          "SpaceBetweenAmountAndSymbol": false,
          "RoundingCoefficient": 0,
          "DecimalDigits": 2
      },
  ...
  ]
}
```


*RESPONSE PARAMETERS*

| Parameter | Description |
| --- | --- |
| ```Currencies``` | The list of currencies that we support, with corresponding symbol and formatting information for internationalisation. |


## Markets

Retrieve the market countries that we support.

Most suppliers (airlines, travel agents and car hire dealers) set their fares based on the market (or country of purchase). It is therefore necessary to specify the market country in every query.

```shell
GET "https://www.skyscanner.net/g/chiron/api/v1/localisation/
    reference/v1.0/countries/
    {locale}"
```

*API endpoint*

`GET /localisation/reference/v1.0/countries/{locale}`


*REQUEST PARAMETERS*

| Parameter | Description |
| --------- | ------- |
| ```locale``` <br><span class="required">REQUIRED</span> | The language you want the results in (ISO locale). See [locales](#locales) for locales that we support. |
| ```api-key (header, not param)``` <br><span class="required">REQUIRED</span> | Your API Key. |

> Example response

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
