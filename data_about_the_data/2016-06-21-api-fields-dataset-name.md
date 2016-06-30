---
category: Data about the data
path: 'data_about_the_data/:id'
title: 'dataset_name'
type: 'GET'

layout: nil
---

Gives you a listing of all the fields and their data types for the given dataset. This is useful for figuring out how to structure a query against the `/v1/api/detail/`, `/v1/api/shapes/`, or `/v1/api/detail-aggregate/` endpoints.

### Query Parameters

This API endpoint doesn\'t take in any query parameters.

### Response

| Attribute Name | Attribute Description                                                                                                              |
|----------------|------------------------------------------------------------------------------------------------------------------------------------|
| `field_type`     | [Postgres data type](https://www.postgresql.org/docs/9.3/static/datatype.html) for given field.                                                                                                |
| `field_name`     | Name of database field. Useful for performing additional queries using the `/v1/api/detail-aggregate/` and `/v1/api/detail/` endpoints. |


## Example

http://plenar.io/v1/api/fields/crimes_2001_to_present/ gives field definitions for the Chicago crimes dataset.
