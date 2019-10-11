# Location Autosuggestion

Two types of requests can be made:

* list of places (with corresponding IDs) that match the query string

* information about a specific place given its ID (for example city name and country name for an airport)

The country and language must be included in the query so that the most relevant results can be returned, in the correct language.

*API endpoint*

`/places/autosuggest/v1.0/{country}/{currency}/{locale}?`

## List of places

```shell
GET "https://www.skyscanner.net/g/chiron/api/v1/
    places/autosuggest/v1.0/
     `{market}`/
     `{currency}`/
     `{locale}`?
     query={query}"
```

*HEADERS*
| Key | Description |
| --------- | ------- |
| ```api-key``` <br><span class="required">REQUIRED</span> | ```The API key needed to access the endpoint.``` |

*REQUEST PARAMETERS*

| Parameter | Description |
| --------- | ------- |
| ```query``` <br><span class="required">REQUIRED</span> | The query string, must be at least 2 characters long. |
| ```api-key``` <br><span class="required">REQUIRED</span> | The API Key to identify the customer (could be full or short). |

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
| ```Places``` | Contains the list of markets (array of countries as name-value pairs). |


## Place Information

```shell
GET "https://www.skyscanner.net/g/chiron/api/v1/
    autosuggest/v1.0/
     `{market}`/
     `{currency}`/
      `{locale}`?
    id={place_id}"
```

*REQUEST PARAMETERS*

| Parameter | Description |
| --------- | ------- |
| ```id``` <br><span class="required">REQUIRED</span> | The place id. |
| ```api-key``` <br><span class="required">REQUIRED</span> | The API Key to identify the customer (could be full or short). |

> Example response for id=cdg

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


*RESPONSE PARAMETERS*

| Parameter | Description |
| --- | --- |
| ```Places``` | Contains the information about the place such as name (in chosen locale), city, country. |
