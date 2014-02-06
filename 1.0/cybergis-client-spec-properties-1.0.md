Properties Specification, Version 1.0
================

## Description

The properties file is used to configue which layers and controls to show on the map. The properties file also contains pointers to shared external resources that are not specific to individual layers, such as P-Codes, Glossaries, Bookmarks, etc.


## Specifications

### Blank Configuration

```JSON
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
	"classification":"",
	"projection":"",
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
### Properties

The following properties are specified in the properties file.
- [Element](#element)
- [Name](#name)
- [Title](#title)
- [Domain](#context)
- [Context](#context)
- [Pages](#pages)

#### Element

The element property is a string.  It specifies the DIV that will contain the OpenLayers map.

Example

`"element":"map"`

#### Name

The name property is a string.  It specifies the name of the CyberGIS client application.  The name is used for the page headers, about dialog, and other ways on the page.

Example

`"name":"Demo"`

#### Title

The title property is a string.  It specifies the title of the CyberGIS client application.  The title is used for the page title (read: browser history).

Example

`"title":"Demo - Organization"`

#### Domain

The domain property is a string.  It specifies the domain that the application is on.  Actually, the string should include the protocol + domain (http + example.com).  It should not have a trailing slash.

Example

`"domain":"http://example.com"`

#### Context

The context property is a string.  It specifies the context path that the application is on.  It should have a preceding slash.

Example

`"context":"/cybergis/apps"`

#### Pages

The pages property is an object that contains the page names for the main page, thumbnail page, and embed page.

Example

```JSON
"pages":
{
	"main":"hello-world.html",
	"thumbnail":"hello-world-thumbnail.html",
	"embed":"hello-world-embed.html"
}
```

#### Classification

The classification property is a string.  It specifies the classification marking of the application.  It does not represent the classification of the application name or metadata.  The property represents the highest classification level of the data contained in the application.

Examples

* `"classification":"Unclassified"`
* `"classification":"Unclassified//SBU"`
* `"classification":"Unclassified//FOUO"`

#### Projection

The projection property is a string.  It specifies the EPSG code of the projection of the map.  It should almost always be set to `"EPSG:900913"`.

Example

`"projection":"EPSG:900913"`


## Examples

- [Properties, Version 1.0](https://github.com/state-hiu/cybergis-client-spec/blob/master/1.0/cybergis-client-example-properties-1.0.json)

## Contributing

HIU is currently not accepting pull requests for this repository.

## License
This project constitutes a work of the United States Government and is not subject to domestic copyright protection under 17 USC § 105.
