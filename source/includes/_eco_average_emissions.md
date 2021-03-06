# Eco Average Emissions

This is an experimental endpoint which provides you access to cached roughly calculated CO<sup>2</sup> emissions for direct flights.

## Single Eco Average Emissions

Retrieve the eco average emissions for a single direct flight.

```shell
GET 'https://www.skyscanner.net/g/chiron/api/v1/
    eco/average-emissions?
    routes="{Origin, Destination}"'
```

*API endpoint*

`GET /eco/average-emissions`

*HEADERS*

Parameter | Description |
--------- | ------- |
```api-key``` <br><span class="required">REQUIRED</span> | The API Key to identify the customer |

*REQUEST PARAMETERS*

| Parameter | Description |
| --------- | ------- |
| ```routes``` <br><span class="required">REQUIRED</span> | Origin and Destination |

> Example response

```json
[{
  "originId" : 15083,
  "originCode" : "ORY",
  "destinationId" : 11235,
  "destinationCode" : "EDI",
  "emissions" : 11861.723,
  "routeCodeId" : "ORY,EDI",
  "routeId" : "15083,11235"
}]
```


*RESPONSE PARAMETERS*

| Parameter | Description |
| --- | --- |
| ```originId``` | Internal ID of the origin. |
| ```originCode``` | The code for the origin. |
| ```destinationId``` | Internal ID of the destination. |
| ```desticationCode``` | The code for the destination. |
| ```emissions``` | The amount of CO<sup>2</sup> emissions for the provided route. |
| ```routeCodeID``` | The code for the route. |
| ```routeId``` | Internal ID of the route. |


## Bulk Eco Average Emissions

Retrieve the eco average emissions for multiple direct flights.

```shell
GET 'https://www.skyscanner.net/g/chiron/api/v1/
    eco/average-emissions?
    routes="{Origin1, Destination1; Origin2, Destination2;...}"'
```
*API endpoint*

`GET /eco/average-emissions`

*HEADERS*

Parameter | Description |
--------- | ------- |
```api-key``` <br><span class="required">REQUIRED</span> | The API Key to identify the customer |

*REQUEST PARAMETERS*

| Parameter | Description |
| --------- | ------- |
| ```routes``` <br><span class="required">REQUIRED</span> | Origin and Destination |

> Example response

```json
[ {
    "originId" : 15083,
    "originCode" : "ORY",
    "destinationId" : 11235,
    "destinationCode" : "EDI",
    "emissions" : 11861.723,
    "routeCodeId" : "ORY,EDI",
    "routeId" : "15083,11235"
}, {
    "originId" : 12712,
    "originCode" : "JFK",
    "destinationId" : 13554,
    "destinationCode" : "LHR",
    "emissions" : 139558.38,
    "routeCodeId" : "JFK,LHR",
    "routeId" : "12712,13554"
}]
```


*RESPONSE PARAMETERS*

| Parameter | Description |
| --- | --- |
| ```originId``` | Internal ID of the origin. |
| ```originCode``` | The code for the origin. |
| ```destinationId``` | Internal ID of the destination. |
| ```desticationCode``` | The code for the destination. |
| ```emissions``` | The amount of CO<sup>2</sup> emissions for the provided route. |
| ```routeCodeID``` | The code for the route. |
| ```routeId``` | Internal ID of the route. |
