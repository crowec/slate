# Places

Places can be of 4 different types:

1. Country
2. City
3. Airport
4. Anywhere (flights browse API)

You can use any of the following endpoints to get information about places:

* our [Autosuggest](#list-of-places) endpoint to obtain a list of places and corresponding IDs that match a query string

* our [Autosuggest](#place-information) endpoint to get information about a specific place given its ID (for example city name and country name for an airport)

* our [Geo catalog](#geo-catalog) to get the full list of places that we support (please [contact us](https://partners.skyscanner.net/contact/) to request access)

<aside class="warning">
The country and language must be included in the Autosuggest query so that the most relevant results can be returned, in the correct language.
</aside>



## List of places

Get a list of places that match a query string.

```shell
GET "https://www.skyscanner.net/g/chiron/api/v1/
    places/autosuggest/v1.0/
    {country}/{currency}/{locale}?
    query={query}
```
*API endpoint*

`GET /places/autosuggest/v1.0/{market}/{currency}/{locale}`

*HEADERS*

| Key | Description |
| --------- | ------- |
| ```api-key``` <br><span class="required">REQUIRED</span> | ```The API key needed to access the endpoint.``` |


*REQUEST PARAMETERS*

| Parameter | Description |
| --------- | ------- |
| ```country``` <br><span class="required">REQUIRED</span> | The [market/country](#markets) your user is in |
| ```currency``` <br><span class="required">REQUIRED</span> | The [currency](#currencies) you want the prices in |
| ```locale``` <br><span class="required">REQUIRED</span> | The [locale](#locales) you want the results in (ISO locale) |
| ```query``` <br><span class="required">REQUIRED</span> | The query string, must be at least 2 characters long. |


> Example response for query=pari

```json
{
  "Places": [
    {
      "PlaceId": "PARI-sky",
      "PlaceName": "Paris",
      "CountryId": "FR-sky",
      "RegionId": "",
      "CityId": "PARI-sky",
      "CountryName": "France"
    },
    {
      "PlaceId": "CDG-sky",
      "PlaceName": "Paris Charles de Gaulle",
      "CountryId": "FR-sky",
      "RegionId": "",
      "CityId": "PARI-sky",
      "CountryName": "France"
    },
    {
      "PlaceId": "ORY-sky",
      "PlaceName": "Paris Orly",
      "CountryId": "FR-sky",
      "RegionId": "",
      "CityId": "PARI-sky",
      "CountryName": "France"
    },
  ...
  ]
}
```


*RESPONSE PARAMETERS*

| Parameter | Description |
| --- | --- |
| ```Places``` | Contains the list of places that match the query string. The places can be countries, cities or airports. |


<aside class="notice">
If you are using this endpoint from client-side code, we recommend to use a token as value for apiKey request parameter. This way you will overcome the potential security risk of exposing account API keys.
See <a href="#token-generation">token generation</a> section for more details.
</aside>



## Place Information

Get information about a country, city or airport using its ID.

*API endpoint*

`GET /places/autosuggest/v1.0/{country}/{currency}/{locale}`

```shell
GET "https://www.skyscanner.net/g/chiron/api/v1
    places/autosuggest/v1.0/
    {market}/{currency}/{locale}?
    id={place_id}
```

*HEADERS*

| Key | Description |
| --------- | ------- |
| ```api-key``` <br><span class="required">REQUIRED</span> | ```The API key needed to access the endpoint.``` |

*REQUEST PARAMETERS*

| Parameter | Description |
| --------- | ------- |
| ```country``` <br><span class="required">REQUIRED</span> | The [market/country](#markets) your user is in |
| ```currency``` <br><span class="required">REQUIRED</span> | The [currency](#currencies) you want the prices in |
| ```locale``` <br><span class="required">REQUIRED</span> | The [locale](#locales) you want the results in (ISO locale) |
| ```id``` <br><span class="required">REQUIRED</span> | The place id (e.g. "CDG-sky") <b>or</b> the user's ip address (e.g. "188.39.95.140-ip") |
| ```apiKey``` <br><span class="required">REQUIRED</span> | Your API Key |

> Example response for United Kingdom: id=uk

```json
{
  "Places": [
    {
      "PlaceId": "UK-sky",
      "PlaceName": "United Kingdom",
      "CountryId": "UK-sky",
      "CityId": "-sky",
      "CountryName": "United Kingdom"
    }
  ]
}
```

> Example response for Charles de Gaulle airport: id=cdg

```json
{
  "Places": [
    {
      "PlaceId": "CDG-sky",
      "PlaceName": "Paris Charles de Gaulle",
      "CountryId": "FR-sky",
      "CityId": "PARI-sky",
      "CountryName": "France"
    }
  ]
}
```
> Example response for user IP address 188.39.95.140: id=188.39.95.140-ip

```json
{
  "Places": [
    {
      "PlaceId": "LOND-sky",
      "PlaceName": "London",
      "CountryId": "UK-sky",
      "CityId": "LOND-sky",
      "CountryName": "United Kingdom"
    }
  ]
}
```


*RESPONSE PARAMETERS*

| Parameter | Description |
| --- | --- |
| ```Places``` | Contains the information about the place such as name (in chosen locale), city, country. |

<aside class="notice">
You can use this endpoint to retrieve the user's location from their IP address:
<code>https://www.skyscanner.net/g/chiron/api/v1/places/autosuggest/v1.0/UK/GBP/en-GB?id=188.39.95.140-ip&apikey=&lt;apiKey&gt;</code>
</aside>

## Geo Catalog


Get the full list of all the places that we support.

```shell
GET "https://www.skyscanner.net/g/chiron/api/v1/
    places/geo/v1.0
```

*API endpoint*

`GET /places/geo/v1.0`

*HEADERS*

| Key | Description |
| --------- | ------- |
| ```api-key``` <br><span class="required">REQUIRED</span> | ```The API key needed to access the endpoint.``` |

*REQUEST PARAMETERS*

| Parameter | Description |
| --------- | ------- |
| ```languageid``` | A locale in ISO format, for example ```fr-FR``` |

> Response extract:

```json
{
  "Continents": [
    {
      "Countries": [
        {
          "CurrencyId": "AFN",
          "Regions": [],
          "Cities": [
            {
              "SingleAirportCity": true,
              "Airports": [
                {
                  "CityId": "BINA",
                  "CountryId": "AF",
                  "Location": "67.823611, 34.804167",
                  "Id": "BIN",
                  "Name": "Bamiyan"
                }
              ],
              "CountryId": "AF",
              "Location": "67.823611, 34.804167",
              "IataCode": "BIN",
              "Id": "BINA",
              "Name": "Bamiyan"
            },
            ...
          ]
        },
        ...
      ]
    },
    ...
  ]
 }

```

*RESPONSE PARAMETERS*

| Parameter | Description |
| --- | --- |
| ```Continents``` | Contains the list of all the continents. |
| ```Countries``` | Contains the list of all the countries. |
| ```Regions``` | Contains the list of all the regions. |
| ```Cities``` | Contains the list of all the cities. |
| ```Airports``` | Contains the list of all the airports. |




## Schemas

> Example place codes:

```shell
EDIN-sky
```
```shell
CDG-iata
```
```sell
-37.4849,144.5747-latlong
```

Each place can be referred to via different schemas, described below.

*SCHEMAS*

| Parameter | Description |
| --- | --- |
| sky | Skyscanner code. The response from [Autosuggest](#place-information) provides these ids. |
| iata / iso | Airports and cities often use the internationally recognized IATA and ISO schemas.<br>For <b>Flights</b> we recommend that you use the Skyscanner code which is very similar but solves ambiguous cases where a city and one of its airports share the same code. For <b>Car Hire</b> please use the IATA code.|
| latlong |	Latitude and longitude of the place in the following form: "latitude,longitude". The nearest city with airport will be used. |
| ip | IP of a user. The nearest city with airport will be used. Format: `188.39.95.93`|
| GeoNameCodes | GeoNameCodes from the GeoNames schema (see [geonames.org](www.geonames.org))|
| GeoNameIDs | GeoNameIDs from the GeoNames schema (see [geonames.org](www.geonames.org))|


If the default Skyscanner schema is not used, the schema name must be appended to the place id as follows:
`placeCode-locationSchema`
