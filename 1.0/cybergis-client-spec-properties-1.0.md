Properties Specification, Version 1.0
================

## Description

The properties file is used to configue which layers and controls to show on the map. The properties file also contains pointers to shared external resources that are not specific to individual layers, such as P-Codes, Glossaries, Bookmarks, etc.


## Specifications


```json
{
	"element":"",
	"name": "",
	"title":"",
	"domain":"",
	"context":"",
	"pages":
	{
		"main":"",
		"thumbnail":"",
		"embed":""
	},
	"classification":"Unclassified",
	"projection":"EPSG:900913",
	"zoom":7,
	"minZoom":0,
	"maxZoom":18,
	"resolutions":[],
	"controls":{},	
	"apps":[],
	"wikis":[],
	"datasources":[],
	"bookmarks":{},
	"glossaries":[],
	"hashmaps":{},
	"pcodes":[]
}
```


### Element



 
## Examples

- [Properties, Version 1.0](https://github.com/state-hiu/cybergis-client-spec/blob/master/1.0/cybergis-client-example-properties-1.0.json)

## Contributing

HIU is currently not accepting pull requests for this repository.

## License
This project constitutes a work of the United States Government and is not subject to domestic copyright protection under 17 USC § 105.
