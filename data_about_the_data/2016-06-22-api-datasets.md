---
category: Data about the data
path: '/data_about_the_data'
title: 'datasets'
type: 'GET'

layout: nil
---

This is the \"data about the data\" endpoint. It contains a record for each dataset. Use `/v1/api/datasets` to list available datasets and metadata.

### Query Parameters

All query parameters are optional.

|Parameter Name  | Parameter Default | Parameter Description|
|--------------- | ----------------- | :---------------------|
|`dataset_name`    | none              | Machine version of a specific dataset name|


### Response

One record per shape dataset.




| **Attribute Name** 	| **Attribute Description**                                                                   	|
|----------------	|------------------------------------------------------------------------------------------	|
| `description`    	| Verbose, official description of the dataset.                                            	|
| `source_url`     	| If available, the URL where the data was originally sourced.                             	|
| `obs_from`       	| Oldest date available in the dataset                                                     	|
| `obs_to`         	| Newest date available in the dataset.                                                    	|
| `human_name`     	| Human-friendly name for the dataset.                                                     	|
| `dataset_name`   	| Machine name for the dataset. Values are passed into the queries below as `dataset_name` 	|
| `update_freq`    	| Update frequency.                                                                        	|


## Example

[http://plenar.io/v1/api/datasets/](http://plenar.io/v1/api/datasets/) returns a list of datasets available in Plenario.
