---
category: Raw data
path: '/raw_data'
title: 'detail'
type: 'GET'

layout: nil
---

Query a particular dataset and get back the raw individual records.

### Query Parameters

All query parameters are optional except for `dataset_name`.

| Parameter Name       | Parameter Default | Parameter Description                                                                                                                                                                                              |
|----------------------|-------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| dataset_name         | none              | *Required*. Machine version of the dataset name as you get it from the `/v1/api/` endpoint.                                                                                                                        |
| [dataset_field]*     | none              | Any available dataset field. Discoverable via the `/v1/api/fields/<dataset_name>/` endpoint. Any number of these query parameters can be chained together and are linked together with a SQL `AND` under the hood. |
| obs_date__ge         | 90 days ago       | Obversations greater than or equal to a given date.  Dates must be formatted as YYYY-MM-DD                                                                                                                         |
| obs_date__le         | 90 days ago       | Obversations less than or equal to a given date.  Dates must be formatted as YYYY-MM-DD                                                                                                                            |
| location_geom_within | none              | A URL encoded [GeoJSON](http://geojson.org/) polygon representing the area of interest                                                                                                                             |
| data_type            | json              | Response data format. Current options are `json` and `csv`                                                                                                                                                         |
| geom                 | none              | Join to a shape dataset; columns in the shape dataset can also be used as filters with the `[dataset_field]*` parameter                                                                                            |
| offset               | none              | Used to paginate through results of more than 1000.  Example: `offset=1000` will fetch the second page of results.                                                                                                 |


### Response

The API responds with a list of raw records for the particular dataset. The fields returned will vary per dataset. Response is limited to 1000 results, which can be paginated by using the `offset` parameter.
