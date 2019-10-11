## Browse Dates (grid)

Retrieve the cheapest dates for a given route from our cache, with the results formatted as a two-dimensional array to be easily displayed as a calendar.

```shell
curl "https://www.skyscanner.net/g/chiron/api/v1/flights/browse/browsegrid/v1.0/{country}/{currency}/{locale}/
  {originPlace}/
  {destinationPlace}/
  {outboundPartialDate}/
  {inboundPartialDate}"
  -X GET
  -H "Accept: application/json"
  -H "api-key: << your api key >>"

```

*API endpoint*

GET `/flights/browse/browsegrid/v1.0/{country}/{currency}/{locale}/{originPlace}/{destinationPlace}/{outboundPartialDate}/{inboundPartialDate}`

*HEADER VALUES*

| Header | Value |
| --- | --- |
| `api-key` <br><span class="required">REQUIRED</span> | `<<your API key>>` |
| ```Accept```<br><span class="optional">OPTIONAL</span> | ```application/json``` or ```application/xml```<br>The default response format is XML |

*REQUEST PARAMETERS*

| Parameter | Description |
| --------- | ------- |
| ```country``` <br><span class="required">REQUIRED</span> | The [market country](#markets) your user is in |
| ```currency``` <br><span class="required">REQUIRED</span> | The [currency](#currencies) you want the prices in |
| ```locale``` <br><span class="required">REQUIRED</span> | The [locale](#locales) you want the results in (ISO locale) |
| ```originPlace``` <br><span class="required">REQUIRED</span> | The origin place (see [places](#places)) |
| ```destinationPlace``` <br><span class="required">REQUIRED</span> | The destination place (see [places](#places)) |
| ```outboundPartialDate``` <br><span class="required">REQUIRED</span> | The outbound date. Format "yyyy-mm-dd", "yyyy-mm" or "anytime". |
| ```inboundPartialDate``` <br><span class="optional">OPTIONAL</span> | The return date. Format "yyyy-mm-dd", "yyyy-mm" or "anytime". Use empty string for oneway trip. |

The following tables show the level of precision supported for the origin and destination places, and the outbound and return dates:

![diagram](/images/browsegrid_places.png)

![diagram](/images/browsegrid_dates.png)

> Example response from US to anywhere:

```json
{
  "Dates": [
    [
      null,
      {
        "DateString": "2017-01"
      },
      {
        "DateString": "2017-02"
      },
      {
        "DateString": "2017-03"
      },
    ...
    ],
    ...
  ],
  "Places": [
    {
      "PlaceId": 837,
      "Name": "United Arab Emirates",
      "Type": "Country",
      "SkyscannerCode": "AE"
    },
  ...
  ],
  "Carriers": [
    {
      "CarrierId": 29,
      "Name": "Mombasa Air Safari"
    },
    {
      "CarrierId": 173,
      "Name": "Silver Airways"
    },
  ...
  ],
  "Currencies": [
    {
      "Code": "EUR",
      "Symbol": "€",
      "ThousandsSeparator": " ",
      "DecimalSeparator": ",",
      "SymbolOnLeft": false,
      "SpaceBetweenAmountAndSymbol": true,
      "RoundingCoefficient": 0,
      "DecimalDigits": 2
    }
  ]
}
```


*RESPONSE PARAMETERS*

| Parameter | Description |
| --- | --- |
| ```Dates``` | Matrix of all the dates available with associated price. |
| ```Places``` | Contains the list of markets (array of countries as name-value pairs). |
| ```Carriers``` | Contains the list of markets (array of countries as name-value pairs). |
| ```Currencies``` | Contains the list of markets (array of countries as name-value pairs). |

