---
category: Aggregate data
path: '/aggregate_data/:id'
title: 'timeseries'
type: 'GET'

layout: nil
---

This endpoint contains a record for every row in every dataset with brief temporal and spatial information about the row. This can give a user of the platform a quick overview about what is available within their constraints.

### Query Parameters

All query parameters are optional.

| Parameter Name       | Parameter Default | Parameter Description                                                                                                                                                                                                                                          |
|----------------------|-------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `agg`                  | week              | Time resolution to aggregate observation counts by.  Supported values: * day * week * month * quarter * year                                                                                                                                                   |
| `obs_date__ge`         | 90 days ago       | Obversations greater than or equal to a given date.  Dates must be formatted as YYYY-MM-DD                                                                                                                                                                     |
| `obs_date__le`         | 90 days ago       | Obversations less than or equal to a given date.  Dates must be formatted as YYYY-MM-DD                                                                                                                                                                        |
| `dataset_name`         | none              | Machine version of the dataset name as you get it from the `/v1/api/datasets` endpoint. If not provided, returns all available datasets. More than one dataset can be requested by using `dataset_name__in` and listing multiple comma separated dataset names. |
| `location_geom_within` | none              | A URL encoded [GeoJSON](http://geojson.org/) polygon representing the area of interest                                                                                                                                                                         |
| `data_type`            | json              | Response data format. Current options are `json` and `csv`.    


### Response


The API responds with a list of datasets with a dense matrix of counts grouped by temporal aggregation.

| **Attribute Name** | **Attribute Description**             |
|--------------------|-------------------------------------- |
| `dataset_name`     | Machine version  of that dataset name |
| `items`            | | **Parameter** | **Description**            | 
		       | ------------- | ------------------         |
                       | `count`       | Record count               |
                       | `datetime`    | Temporal aggregation group |
                                                             |

