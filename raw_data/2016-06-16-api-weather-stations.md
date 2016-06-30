---
category: Raw data
path: '/raw_data'
title: 'weather stations'
type: 'GET'

layout: nil
---

Query weather stations from NOAA\'s [Quality Controlled Local Climatological Data](http://www.ncdc.noaa.gov/?prior=N).

### Query Parameters

All query parameters are optional

| Parameter    | Description                                                                                                       |
|--------------|-------------------------------------------------------------------------------------------------------------------|
| station_name | Name of weather station                                                                                           |
| call_sign    | Call sign of weather station                                                                                      |
| wban_code    | Weather Bureau Army Navy (WBAN) code of weather station                                                           |
| begin        | Date of first weather observation                                                                                 |
| end          | Date of last weather observation                                                                                  |
| elevation    | Elevation of station (in feet)                                                                                    |
| county       | County name                                                                                                       |
| state        | Two-digit state code                                                                                              |
| location     | Latitude and longitude location of weather station. Can be queried with a GeoJSON shape using `location__within`. |


### Query Operators

| Operator | Description                                                          |
|----------|----------------------------------------------------------------------|
| __gt     | greater than (`>`)                                                   |
| __ge     | greater than or equal to (`>=`)                                      |
| __lt     | less than (`<`)                                                      |
| __le     | less than or equal to (`<=`)                                         |
| __ne     | not equal (`!=`)                                                     |
| __like   | like value with % wildcards, case sensitive (`LIKE`, `'State%'`)     |
| __ilike  | like value with % wildcards, case insensitive (`ILIKE`,  `'state%'`) |
| __in     | within a list of provided values (`IN ('list', 'of', 'values')`)     |


### Response

List of weather stations and attributes (described above) that match the provided query parameters.
