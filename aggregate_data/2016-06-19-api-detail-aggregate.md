---
category: Aggregate data
path: '/aggregate_data'
title: 'detail-aggregate'
type: 'GET'

layout: nil
---

Very similar to the `/v1/api/timeseries/` API endpoint, but for one dataset. Additional dataset-specific query parameters can be used to filter the results.

### Query Parameters

All query parameters are optional except for `dataset_name`.

| Parameter Name       | Parameter Default | Parameter Description                                                                                                                                                                                              |
|----------------------|-------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| dataset_name         | none              | *Required*. Machine version of the dataset name as you get it from the `/v1/api/` endpoint.                                                                                                                        |
| [dataset_field]*     | none              | Any available dataset field. Discoverable via the `/v1/api/fields/<dataset_name>/` endpoint. Any number of these query parameters can be chained together and are linked together with a SQL `AND` under the hood. |
| agg                  | week              | Time resolution to aggregate observation counts by.   Supported values: * day * week * month * quarter * year                                                                                                      |
| obs_date__ge         | 90 days ago       | Obversations greater than or equal to a given date.  Dates must be formatted as YYYY-MM-DD                                                                                                                         |
| obs_date__le         | 90 days ago       | Obversations less than or equal to a given date.  Dates must be formatted as YYYY-MM-DD                                                                                                                            |
| location_geom_within | none              | A URL encoded [GeoJSON](http://geojson.org/) polygon representing the area of interest                                                                                                                             |
| data_type            | json              | Response data format. Current options are `json` and `csv`.                                                                                                                                                        |


### Response

| Attribute Name | Attribute Description      |
|----------------|----------------------------|
| count          | Record count               |
| datetime       | Temporal aggregation group |



