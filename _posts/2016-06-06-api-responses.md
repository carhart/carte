---
title: 'Response Format'

layout: nil
---

All JSON API calls return their data in the `objects` block. dditional information is returned in the `meta` block:

| Parameter | Description                                                         |
|-----------|---------------------------------------------------------------------|
| `status`  | **ok** if query was successful, **error** if not.                   |
| `query`   | Original query parameters passed in.                                |
| `message` | if `status` is **error**, a detailed message as to what went wrong. |


Here is an example from the `/v1/api/timeseries/` endpoint:

~~~~
{
   "meta":{
      "status":"ok",
      "query":{
         "agg":"week",
         "dataset_name__in":"cdph_environmental_complaints",
         "obs_date__ge":"2007-12-12",
         "obs_date__le":"2008-01-12"
      },
      "message":""
   },
   "objects":[
      {
         "items":[
            {
               "count":8,
               "datetime":"2007-12-10T00:00:00"
            },
            {
               "count":8,
               "datetime":"2007-12-17T00:00:00"
            },
            {
               "count":5,
               "datetime":"2007-12-24T00:00:00"
            },
            {
               "count":7,
               "datetime":"2007-12-31T00:00:00"
            },
            {
               "count":22,
               "datetime":"2008-01-07T00:00:00"
            }
         ],
         "dataset_name":"cdph_environmental_complaints"
      }
   ]
}
~~~~

